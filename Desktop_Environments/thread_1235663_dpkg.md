---
title: "dpkg"
date: 2009-08-09
forum: Desktop Environments
---

### Post by Ian Woods on 2009-08-09
Just installed ubuntu 9.04 64 bit on my desktop from a disk that came with linux Format which showed how to install VLC media player which i did but now when I try to add or subtract programs I get an error message as follows.

E:dpkgwas interrupted you must manual run
'sudo dpkg--configure-a
E:_cache-> open() failed, please report

any help would be much appreciated

---

### Post by mcduck on 2009-08-09
Try doing what the error message suggests, and run "sudo dpkg --configure -a" in a terminal. ;)

---

### Post by Joeb454 on 2009-08-09
Oh I see that it now gives the more useful message and says you need to use sudo.

That would explain why I don't see so many dpkg threads :) - That should indeed solve the issue

---

### Post by Ian Woods on 2009-08-09
> **mcduck said:**
> Try doing what the error message suggests, and run "sudo dpkg --configure -a" in a terminal. ;)
tried it says command not known
heres the error message
dpkg: error processing a (--configure):
 no package named `a' is installed, cannot configure
Errors were encountered while processing:
 a

---

### Post by Ian Woods on 2009-08-09
I now have to locate a broken package on my system by using the "Broken" filter to locate it. sorry im a real newbee giv us a clue as to how to do this

---

### Post by mcduck on 2009-08-09
> **Ian Woods said:**
> tried it says command not known
heres the error message
dpkg: error processing a (--configure):
 no package named `a' is installed, cannot configure
Errors were encountered while processing:
 a

Are you sure you didn't forget the dash in front of the "a"? Because the error sounds like you did..

---

