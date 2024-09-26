 DATA: it_hide TYPE STANDARD TABLE OF zrap_I_header WITH DEFAULT KEY.



    it_hide = CORRESPONDING #( it_original_data ).
    LOOP AT it_hide ASSIGNING  FIELD-SYMBOL(<fs_hide>) .

      DATA(index) = sy-tabix.
      ASSIGN COMPONENT to_upper( 'hidefacet' ) OF STRUCTURE
                      ct_calculated_data[ index ] TO FIELD-SYMBOL(<fs1>).
      IF <fs_hide>-Status = 'X'.
        <fs1> = abap_false.
      ELSE.
        <fs1> = abap_true.
      ENDIF.
    ENDLOOP.
