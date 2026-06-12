---
title: "Ok to download of libc6- 21?"
date: 2005-06-27
forum: Desktop Environments
---

### Post by vtechstu on 2005-06-27
Everytime i to install something, i get this error about having the wrong version of libc6.  Right now i have the standard ubuntu13 version installed, but need 21 instead.  Last time i tried updating this it jacked up my locales completely, so i'm VERY hesistant to update libc6 because fixing the locales took forever to do.  

Any ideas?

libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13

---

### Post by wdso on 2005-06-27
Installing the official ubuntu version of libc6 should be fine. Check with apt-cache policy libc6.

If you encounter problems with your locales, check locale.gen

---

### Post by vtechstu on 2005-06-27
Apt-get 'ting libc6 says i already have the newest version, the ubuntu version.  I need 21 not ubuntu20.  Any other ideas?

---

### Post by cowlip on 2005-06-29
[QUOTE=vtechstu]Apt-get 'ting libc6 says i already have the newest version, the ubuntu version.  I need 21 not ubuntu20.  Any other ideas?[/QUOTE]
 Hey, just wanted to say I need help wth w. version 21 of libc as well. TIlda 0.7 seems to require it.

---

### Post by Paulus on 2005-06-29
splashy needs it too... :o

---

### Post by vtechstu on 2005-06-29
Ok so i found libc6_2.3.2.ds1-22_i386.deb version off the debian packages server.  I dpkg'ed it, and ran the tzconfig.  I selected US , and then Eastern for the time zone, since i live on the East coast.  The only problem is, for East coast it tells me that the current time is 4 hours less then what it really is.  And i can't seem to modify the time manually.  Any ideas?

---

### Post by Jonathan2007 on 2005-06-29
Well I went through this whole deally and found out it was definately not worth it. I need version 21 for the aMule 2.0 CVS since it hadn't been backported yet. I ended up uninstalling the aMule CVS and the version 21 libc6 and puting back version 20 and using the new backported version of aMule.

Here is my experience about it in [this](http://ubuntuforums.org/showthread.php?t=41929&highlight=locale)  thread. Hope that helps

Basically the response I got was **not to use libc6 21** , Sorry that probably isn't what you wanted to hear.

---

### Post by cowlip on 2005-06-30
Hey, you could try to do "sudo dpkg -i --force-depends PACKAGEHERE.DEB"

---

