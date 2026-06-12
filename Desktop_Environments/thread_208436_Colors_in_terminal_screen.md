---
title: "Colors in terminal screen"
date: 2006-07-03
forum: Desktop Environments
---

### Post by mjkey on 2006-07-03
Could someone explain what the different colored text showing in a terminal screen represents? ie: pink, green, blue and of course the standard black.:confused:

---

### Post by scxtt on 2006-07-03
it's just a variable ($LS_COLORS, do an "echo $LS_COLORS" to see current settings) that ls uses to colorcode files based on their extensions -- you can make them whatever you want ...

unless you're talking about other coloring ...

---

### Post by jayemef on 2006-07-03
By default:
Black - regular files
Green - executable files
Pink - symbolic links (think shortcuts)
Blue - directories

A slightly more informative way to view the settings than $LS_COLORS is the dircolors command, ie
```
$ dircolors -p | less
```
Unfortunately, in either case, you still won't know what the exact colors are without being familiar with the ANSI values.

---

### Post by mjkey on 2006-07-03
Thank you, thought colors had other meanings - such as permissions, etc.:D

---

