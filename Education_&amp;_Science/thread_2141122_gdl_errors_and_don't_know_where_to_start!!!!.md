---
title: "gdl errors and don't know where to start!!!!"
date: 2013-05-01
forum: Education &amp; Science
---

### Post by malapradej on 2013-05-01
I have the following example script. 

```


 ; reads data columns from file and plots it.
; columns are: year, month, day, hour, minute, second, msec, uvel, vvel, wvel, temp, co2, h2o, press

files = ['wc151_1804_new.txt', 'wc151_18010_new.txt', 'wc151_18016_new.txt', $
   'wc151_18112_new.txt']

n = SIZE(files, /N_ELEMENTS)
FOR i = 0, n-1 DO BEGIN
    f = files[i]
    l = FILE_LINES(f)
    cols = 14
    data = FLTARR(cols, l)
    OPENR, iunit, f, /GET_LUN
    FOR j = 0, l-1 DO BEGIN
        READF, iunit, year, month, day, hour, minute, second, msec, uvel, $
        vvel, wvel, temp, co2, h2o, press
        temp = [year, month, day, hour, minute, second, msec, uvel, $
                vvel, wvel, temp, co2, h2o, press]
        FOR k = 0, cols-1 DO BEGIN
            data[k, j] = temp[k]
        ENDFOR
    ENDFOR

    FREE_LUN, iunit

    PLOT, data[10,*], data[13,*], $
        TITLE = 'temperature vs pressure', $
        XTITLE = 'degrees celsius', $
        YTITLE = 'pascal'
ENDFOR


```

I am new to IDL and would appreciate if someone can inform me why I get these errors.

```


 % Attempt to subscript FILES with I is out of range.
% Execution halted at: $MAIN$          
% FILE_LINES: String expression required in this context: F.
% Execution halted at: $MAIN$          
% FLTARR: Variable is undefined: L.
% Execution halted at: $MAIN$          
% OPENR: Filename argument must be a scalar string: F.
% Execution halted at: $MAIN$          
% Variable is undefined: L.
% Execution halted at: $MAIN$          
% READF: Variable is undefined: IUNIT.
% Execution halted at: $MAIN$          
% Variable is undefined: YEAR.
% Execution halted at: $MAIN$          
% Variable is undefined: TEMP.
% Execution halted at: $MAIN$          

        ENDFOR
         ^
% Syntax error.
  At: /home/malapradej/Documents/Programming/IDL/exercises/bowman/ch11/read_file_plot.pro, Line 21

    ENDFOR
     ^
% Syntax error.
  At: /home/malapradej/Documents/Programming/IDL/exercises/bowman/ch11/read_file_plot.pro, Line 22
% FREE_LUN: Variable is undefined: IUNIT.
% Execution halted at: $MAIN$          
% Variable is undefined: DATA.
% Execution halted at: $MAIN$          

ENDFOR
 ^
% Syntax error.
  At: /home/malapradej/Documents/Programming/IDL/exercises/bowman/ch11/read_file_plot.pro, Line 30

```

---

