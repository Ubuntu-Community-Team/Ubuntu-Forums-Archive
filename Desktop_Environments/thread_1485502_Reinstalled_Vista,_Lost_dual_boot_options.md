---
title: "Reinstalled Vista, Lost dual boot options"
date: 2010-05-16
forum: Desktop Environments
---

### Post by piper739 on 2010-05-16
I had my desktop set up as a dual boot with 9.04 and windows. I had to reinstall the windows system and when it finished and rebooted I no longer have the OS selection screen to choose my OS. Is there an easy way to restore the OS selection screen. Thank you

---

### Post by 3Miro on 2010-05-16
Installing Windows messes up Grub (the bootloader). So you have to reinstall it from the Ubuntu live CD (use the one for the version that you are using).

Check this HowTo:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

There is also a nice YouTube video about it:
[http://www.youtube.com/watch?v=WtBBl6HvdpM](http://www.youtube.com/watch?v=WtBBl6HvdpM)

Note: 9.04 uses grub one (the howto and video), if you are using 9.10 or 10.04 you need to work with grub 2 and you will need a grub 2 HowTo.

---

### Post by piper739 on 2010-05-17
Thanks 3Miro, but I realize I'm using 9.10, do you know where I can get the information for grub2?

---

### Post by oldfred on 2010-05-17
If your 9.10 was an upgrade it may still use grub legacy (0.97). If it was a clean install it will have grub2 (1.97). Lucid is grub2 ( 1.98 ).

You will need your liveCD for Karmic and follow these directions:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

