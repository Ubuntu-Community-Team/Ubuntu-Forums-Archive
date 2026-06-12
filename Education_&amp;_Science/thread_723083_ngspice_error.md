---
title: "ngspice error"
date: 2008-03-13
forum: Education &amp; Science
---

### Post by mafifk on 2008-03-13
Hello,
when i start the the ngspice, the spice give me this error.

[COLOR="Red"]external error:  no graphics interface; please check compiling instructions
[/COLOR]

:mad: What is the method to solve this problem ?
Im use ubuntu 7.10. It in the virtual image, I'm use VMware.

---

### Post by jdh18 on 2008-03-14
I have exactly the same problem. ngspice was compiled from the latest gEDA cd. I fixed it on my old pc but have forgotten how. Will try to remember.

---

### Post by ferch on 2008-03-25
I had the same problem, but i found an older geda-installation from gEDA Suite .iso file 2007022.

So i just copied/overwrited the ngspice-binary and this works!
cp /media/sda2/home/ferch/geda-install/bin/ngspice /opt/geda/bin/ngspice

The version is the newest.
/opt/geda/bin/ngspice -v
ngspice compiled from ng-spice-rework revision 17
Written originally by Berkeley University
Currently maintained by the NGSpice Project

Copyright (C) 1985-1996,  The Regents of the University of California
Copyright (C) 1999-2005,  The NGSpice Project


You can download my ngspice-binary  (5MB!!) here 
[http://www.olvenstedt.de/pcb/ngspice.bz2](http://www.olvenstedt.de/pcb/ngspice.bz2)

---

### Post by mafifk on 2008-05-14
I got the solution:
here is my post....
[http://ubuntuforums.org/showthread.php?p=4953252#post4953252]("http://ubuntuforums.org/showthread.php?p=4953252#post4953252")
\\:D/

---

### Post by rehin on 2008-06-09
I have the same problem with Ubuntu 8.04 too. What is the reason? and what can't I do with ngspice if I have such a problem?

---

