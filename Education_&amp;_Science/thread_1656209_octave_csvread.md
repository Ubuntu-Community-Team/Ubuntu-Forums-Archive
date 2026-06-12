---
title: "octave csvread"
date: 2010-12-30
forum: Education &amp; Science
---

### Post by phillyj on 2010-12-30
[SIZE=2]I'm new to octave having been using matlab.

I'm trying to read a csv file that has dates and a header. I get an error:[/SIZE] 

[COLOR=#ff0000][FONT=Liberation Mono]error: `f' undefined near line 32 column 16[/FONT][/COLOR]
 [COLOR=#ff0000][FONT=Liberation Mono]error: evaluating argument list element number 1[/FONT][/COLOR]
 [COLOR=#ff0000][FONT=Liberation Mono]error: evaluating argument list element number 1[/FONT][/COLOR]


[COLOR=#ff0000][FONT=Liberation Mono][COLOR=Black]Anyone know what the problem is? I tried to read it w/o the header but same problem. Could it be a date problem?[/COLOR]
[/FONT][/COLOR]

---

### Post by PC_load_letter on 2011-01-01
csvread is part of the io package, type:```
pkg list
``` and check that there is an "*" next to io, an asterisk next to a package name means it's loaded and ready to use. If not, type```
pkg load io
```

If io is already loaded, maybe (I'm guessing here) the csv file is not in the path of Octave. In this case, type ```
path
``` and copy the csv file to any of the directories in the Octave path. 

Hope that helps, let's know if it works.

---

