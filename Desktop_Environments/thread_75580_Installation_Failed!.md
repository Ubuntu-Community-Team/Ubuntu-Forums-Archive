---
title: "Installation Failed!"
date: 2005-10-13
forum: Desktop Environments
---

### Post by jdmpike on 2005-10-13
Hello all,

I just tried installing 5.10 and it is failing when configuring the gstreamer0.8 something or other.

This causes other packages not to get installed, so I can't do things like run apt-get update.

dpkg is totally hosed:

jordan@jdmlaptop:~$ sudo dpkg --configure -a
dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed.
Aborted

how do I fix this???

Thanks all!

---

### Post by Ampersand on 2005-10-14
If you've got to the point where you can log into gnome, run Synaptic. Otherwise, run 'sudo aptitude'. You can then unselect Gstreamer and continue with  the installation.

The easiest way to make sure you've got everything is to make sure the 'ubuntu-desktop' package is selected.

---

### Post by bugrider on 2005-11-16
[QUOTE=jdmpike]Hello all,

I just tried installing 5.10 and it is failing when configuring the gstreamer0.8 something or other.

This causes other packages not to get installed, so I can't do things like run apt-get update.

dpkg is totally hosed:

jordan@jdmlaptop:~$ sudo dpkg --configure -a
dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed.
Aborted

how do I fix this???

Thanks all![/QUOTE]
Hi, 


Same issue on a 5.10 PPC installation ! I guess it's a bug !
Strange few people reported it. 

As written in [http://www.ubuntulinux.org/support/documentation/faq/upgrade-sarge](http://www.ubuntulinux.org/support/documentation/faq/upgrade-sarge)
I had to do use dpkg --configure --force-depends -a  to get rid of the
error. 
:confused:

---

### Post by Oldan on 2005-12-04
[QUOTE=jdmpike]
I just tried installing 5.10 and it is failing when configuring the gstreamer0.8 something or other.

This causes other packages not to get installed, so I can't do things like run apt-get update.

dpkg is totally hosed:

jordan@jdmlaptop:~$ sudo dpkg --configure -a
dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed.
Aborted
[/QUOTE]

I just had the same problem. After 5.04 installed so cleanly and an upgrade worked so well, I thought a 5.10 would be a breeze... (no pun intended). But it failed badly.

So I used aptitude to remove "blt" and then the final but of the installation went on without much of a hitch.

--Oldan

---

### Post by divali on 2006-10-10
"I had to do use dpkg --configure --force-depends -a to get rid of the
error."   

Thanks. works for me. Hoooray.

---

