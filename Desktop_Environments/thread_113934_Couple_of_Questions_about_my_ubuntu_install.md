---
title: "Couple of Questions about my ubuntu install"
date: 2006-01-07
forum: Desktop Environments
---

### Post by ch13f121 on 2006-01-07
Ok, I fixed my sound....somewhat...I try to use teamspeak, and it mutes my input/output (I can't talk or hear anything)  and I can't undo it. I don't know how to fix this, or is this a server side problem?  Well anyway, I can't log into system admin (root) either.  How do I log into root, so I can install my ati linux drivers, and how do I fix that little teamspeak/soundcard problem?

---

### Post by cotcot on 2006-01-07
I do not know about your sound problem.
Login as root is not provided during install of Ubuntu. 
However it is possible to create a root account. This is well discribed in the unofficial guide (5.04 but usuable) of ubuntu see :           [http://ubuntuguide.org/](http://ubuntuguide.org/)       under Users Administration point 3.
Hope this is of any help.

---

### Post by Nikusan on 2006-01-07
You can't log it to root on ubuntu because by default root does not have a password. It is possible to give root a password but I would not recommend it. Instead, you can give yourself temporary super user privilages using the sudo command. To install ATI's binary drivers follow the [guide located at the wiki]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI").

---

