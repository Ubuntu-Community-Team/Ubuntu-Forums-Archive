---
title: "Upgraded kernel to 686-smp - can't install software"
date: 2006-08-07
forum: Desktop Environments
---

### Post by zambizzi on 2006-08-07
The 386 kernel was installed by default so I upgraded to the 686-smp since I have a P4 cpu w/ HT.

Now, when I try to install certain programs, like acroread or Sun JRE I get messages like this (while using the add/remove programs app):

> 
'acroread' is not available in any software channel

The application might not support your system architecture.


Can I not run certain apps w/ a 686 kernel?

---

### Post by cantormath on 2006-08-07
> **zambizzi said:**
> The 386 kernel was installed by default so I upgraded to the 686-smp since I have a P4 cpu w/ HT.

Now, when I try to install certain programs, like acroread or Sun JRE I get messages like this (while using the add/remove programs app):



Can I not run certain apps w/ a 686 kernel?

do you still have the correct repositories added to the sourcelist.

you know you could try this.
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

oh, another thing, I have the same setup, after I upgraded, there were a bunch of updates.....make sure you check..

---

### Post by zambizzi on 2006-08-07
> **cantormath said:**
> do you still have the correct repositories added to the sourcelist.

I don't know...I've enabled every single one of the repos listed in the "Software Properties" app...sources even...what could I be missing?  If the apps (i.e. acroread, java 5, etc.) show up in the Add/Remove menu...doesn't that show that I have the correct repos setup?

> **cantormath said:**
> 
you know you could try this.
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)


...new to Ubuntu (been using Gentoo for about 2 yrs.) so I'm not familiar w/ the "Automatix" program...will read more into it.

> **cantormath said:**
> 
...after I upgraded, there were a bunch of updates....

No updates after upgrading kernel....just checked again to be sure.

---

### Post by cantormath on 2006-08-13
> **zambizzi said:**
> I don't know...I've enabled every single one of the repos listed in the "Software Properties" app...sources even...what could I be missing?  If the apps (i.e. acroread, java 5, etc.) show up in the Add/Remove menu...doesn't that show that I have the correct repos setup?



...new to Ubuntu (been using Gentoo for about 2 yrs.) so I'm not familiar w/ the "Automatix" program...will read more into it.



No updates after upgrading kernel....just checked again to be sure.

automatix installs that stuff for you.

---

### Post by PriceChild on 2006-08-13
Isnt' the smp kernel for multi core systems...? - your post suggests you use only one p4.

Tried just using the 686 kernel?

---

### Post by Dubbayoo on 2006-08-13
my understanding was there is no 686-smp kernel, because the 686 kernel has smp turned on already. Try removing the kernel you have and just installing the straight 686 kernel

---

