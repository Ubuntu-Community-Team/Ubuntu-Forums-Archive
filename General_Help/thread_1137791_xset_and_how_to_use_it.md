---
title: "xset and how to use it?"
date: 2009-04-25
forum: General Help
---

### Post by Gizim on 2009-04-25
Just installed Jaunty got it setup launched World of Warcraft and it seems there is a stutter problem when you walk "repeat key". Everything that i have seen says to do xset -r to turn off repeat keys. But when i do that it does the complete opposite the r key keeps getting repeated and in the terminal its like someone is holding down ENTER and it just scrolls until i do xset r or xset r on.

Any thoughts?

PS. I know it is repeating the keys because if i hold SPACE i jump OVER AND OVER

---

### Post by kerry_s on 2009-04-26
in a terminal type: man xset
"man" is the tool to read the manual.

so according to the manual you need to specify the key. you can use "xev" to get the key #

>        r       The r option controls the autorepeat.  Invoking with "-r", or "r off",  will  dis-
               able  autorepeat,  whereas  "r",  or "r on" will enable autorepeat.  Following the
               "-r" or "r" option with an integer keycode between  0  and  255  will  disable  or
               enable  autorepeat  on  that  key respectively, but only if it makes sense for the
               particular keycode.  Keycodes below 8 are not typically valid  for  this  command.
               Example: "xset -r 10" will disable autorepeat for the "1" key on the top row of an
               IBM PC keyboard.

               If the server supports the XFree86-Misc extension, or the XKB  extension,  then  a
               parameter of 'rate' is accepted and should be followed by zero, one or two numeric
               values. The first specifies the delay before  autorepeat  starts  and  the  second
               specifies  the  repeat  rate.  In the case that the server supports the XKB exten-
               sion, the delay is the number of milliseconds before autorepeat  starts,  and  the
               rate  is  the number of repeats per second.  If the rate or delay is not given, it
               will be set to the default value.


---

### Post by Gizim on 2009-04-26
> **kerry_s said:**
> in a terminal type: man xset
"man" is the tool to read the manual.

so according to the manual you need to specify the key. you can use "xev" to get the key #

Yeah, doesn't it also say to turn it off completely to just do xset -r ?
Because its every key that is being repeated not just WASD.

---

### Post by Gizim on 2009-04-26
Might be a bug?
[http://ubuntuforums.org/showthread.php?t=1137828&highlight=xset](http://ubuntuforums.org/showthread.php?t=1137828&highlight=xset)

---

