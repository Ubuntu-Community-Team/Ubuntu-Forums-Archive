---
title: "Xterm default window size?"
date: 2009-03-05
forum: Desktop Environments
---

### Post by kynov on 2009-03-05
Hello all!  I am using Xterm as an AS400 client.  Problem most of the end users have is that the default window size/font is just way too small.  The font selection HUGE (ctrl+right-click in xterm) is best for these employees.  Is there a way to set this as default size?

---

### Post by Brandon.Viking on 2009-03-05
man xterm 
the -fs is the option to specify the size on the commandline when starting xterm
 -fs size
               This  option  sets  the  pointsize  for  fonts  selected from the FreeType library if support for that
               library was compiled into xterm.  This corresponds to the faceSize resource.


Hope this helps.
Brandon

---

### Post by kynov on 2009-03-05
> **Brandon.Viking said:**
> man xterm 
the -fs is the option to specify the size on the commandline when starting xterm
 -fs size
               This  option  sets  the  pointsize  for  fonts  selected from the FreeType library if support for that
               library was compiled into xterm.  This corresponds to the faceSize resource.


Hope this helps.
Brandon


Eh... maybe I am doing it wrong, but when I type xterm -fs 10x20 everything is still the same.  Is that the incorrect syntax?  Is there a configuration file I can edit somewhere to change the default size?

---

