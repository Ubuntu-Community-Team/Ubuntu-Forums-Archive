---
title: "Xorg not working anymore."
date: 2005-09-29
forum: Desktop Environments
---

### Post by escobar on 2005-09-29
After a recent kernel image update, I get an error saying xorg failed to load. 

Since I've rebooted and the same screen keeps appearing, then I get forwarded to the command line to login. It does ask if you'd like to see a log, and should I select 'yes' it tells me that a bunch of files failed to load. I don't want to come off as lazy so I didn't write the files down but there are quite a few. Booting into failsafe mode yields the same results. The issue is very similar to the below thread:

[http://ubuntuforums.org/showthread.php?t=59472&highlight=image+xorg](http://ubuntuforums.org/showthread.php?t=59472&highlight=image+xorg)

The difference being this person is actually able to login before everything crashes, I wish I could get that far.

On that note, why is it updating the Kernel Images hoses Grub? Not a bif inconvenience because I know how to fix it, just curious.

***EDIT***

The error reads:

I cannot start the X Server your graphical interface. It is likely it is not setup correctly. Would you like to view the log? I select yes and get the following:

Skipping /usr/x11r6/lib/modules/extensions/libglcore.a:m_debug_clip.o

/usr/x11r6/lib/modules/extensions/libglcore.a:m_debug_norm.o
---
From there, I get kicked back to the command line if I wish to continue. Thanks to any that can help.

---

### Post by escobar on 2005-09-29
bump

---

### Post by mlomker on 2005-09-29
Have you tried running **dpkg-reconfigure xserver-xorg** from the command prompt?  It's hard to say, but perhaps something went awry with your xorg.conf file and that will create a new one.

---

### Post by escobar on 2005-09-30
Been using Ubuntu for about 6 months now, re-configured xorg like a million times, and couldn't figure that one out ](*,)


Anyway. That did it. Thanks a lot.

---

