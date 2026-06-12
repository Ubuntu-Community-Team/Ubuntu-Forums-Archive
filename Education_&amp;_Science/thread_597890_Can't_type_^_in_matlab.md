---
title: "Can't type ^ in matlab"
date: 2007-10-30
forum: Education &amp; Science
---

### Post by jpjandrade on 2007-10-30
Hey guys,

I'm running Matlab 7.5 on Gusty and everything works fine, except that I can't type the power symbol "^". After I press shift+^ key, if I type anything it will print a superscript number just like a power operation, but matlab does not recognize it. Does anyone know what can it be? Thanks for the help, I'm really going nuts on this one!

---

### Post by mauritzius on 2007-11-06
same problem here, also on gutsy, but unfortunately no solution either!

---

### Post by Zugzwang on 2007-11-06
Stupid question: Did you try to press SPACEBAR after "SHIFT+^" so the "^" character actually appears on the screen? :)

---

### Post by olejorgen on 2007-11-06
[http://ubuntuforums.org/showthread.php?t=554952](http://ubuntuforums.org/showthread.php?t=554952)

---

### Post by mauritzius on 2007-11-06
> **olejorgen said:**
> [http://ubuntuforums.org/showthread.php?t=554952](http://ubuntuforums.org/showthread.php?t=554952)

Thank you very much, that saved my day! 
I had to adapt the script a bit to the german layout, but it's working now!

I start matlab now like this:

```

#!/bin/bash
echo keycode 49 = asciicircum degree asciicircum degree notsign notsign notsign notsign | xmodmap -
/opt/matlab/bin/matlab
echo keycode 49 = dead_circumflex degree asciicircum degree notsign notsign notsign notsign | xmodmap -

```

greetings

---

### Post by tuwe on 2007-11-07
hi there,

i followed the following suggestion to insert the two lines about java and awt toolkit into matlab's startup script for running matlab with compiz-fusion:
```
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/
export AWT_TOOLKIT=MToolkit
```

matlab worked fine in general, but i ran into two problems, one of which is why i post here :)
the problems were:
1. can't type ^, ~, ` (or any other dead keys i believe, haven't tried though)
2. can't type any text after switching to a figure window and then back to matlab's command window

however, i found out that the second line of code (export AWT_TOOLKIT=MToolkit) is not needed anymore with recent versions of sun java.

see [http://gentoo-wiki.com/Compiz/Troubleshooting](http://gentoo-wiki.com/Compiz/Troubleshooting), Section "JAVA program does not show contents" for details.

by removing the second line, both of my problems are solved (no xmodmap modifications needed), and matlab (and simulink!) still run fine.

java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

matlab version: 7.5.0.338 (R2007b)

uname -r: 2.6.22-14-generic

---

### Post by photonx on 2008-01-09
Hi,

I had the same problem. Just solved it by typing in the matlab console:

!setxkbmap -variant nodeadkeys

Hope this helps!

Josep C.-
Barcelona

---

