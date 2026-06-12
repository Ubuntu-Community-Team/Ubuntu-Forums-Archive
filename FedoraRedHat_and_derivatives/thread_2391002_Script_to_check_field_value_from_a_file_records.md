---
title: "Script to check field value from a file records"
date: 2018-05-04
forum: Fedora/RedHat and derivatives
---

### Post by vivekn2 on 2018-05-04
[COLOR=#000000][FONT=verdana]I need a script to check the records in a file , if any value match transfer the record in [COLOR=#170072][FONT=monospace]error.txt[/FONT][/COLOR] file.


1- If any of the any field value is NULL(nothing in this field) 



Code:
Record1|Record2|Record3|Record4|Record5|DATE1|DATE2[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Example:[/FONT][/COLOR]



[COLOR=#000000][FONT=verdana]Code:[/FONT][/COLOR]
11111111|22222222|NULL|12|444|27042018|27042018 (Record3 is null)

99999999|88888888|007172FD|NULL|975|02052018|27042018 (Record4 is null)

[COLOR=#000000][FONT=verdana]2- If any of the field value is set as [/FONT][/COLOR][COLOR=#170072][FONT=monospace]0[/FONT][/COLOR][COLOR=#000000][FONT=verdana], except Record4 [/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Example:[/FONT][/COLOR]



[COLOR=#000000][FONT=verdana]Code:[/FONT][/COLOR]
Record1|Record2|Record3|Record4|Record5|DATE1|DATE2
[COLOR=#000000][FONT=verdana]Record1 = 0 or ‘00000000’[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Record2 = 0 or ‘0000000000’[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Record3 = 0 or ‘0000000000’[/FONT][/COLOR]



[COLOR=#000000][FONT=verdana]Code:[/FONT][/COLOR]
11111111111|000080809643|00000000|64|374|02052018|27042018
11111111111|000000000000|45678987|64|374|02052018|27042018
0000000000|000082079914|0071170B|1|308|27042018|27042018
[COLOR=#000000][FONT=verdana]3- If Next DATE1/DATE2 values are not in [/FONT][/COLOR][COLOR=#170072][FONT=monospace]DDMMYYYY[/FONT][/COLOR][COLOR=#000000][FONT=verdana] format[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]4- If Record5 value is negative[/FONT][/COLOR]



[COLOR=#000000][FONT=verdana]Code:[/FONT][/COLOR]
11111111111|000045672345|45678987|64|-222|02052018|27042018

---

