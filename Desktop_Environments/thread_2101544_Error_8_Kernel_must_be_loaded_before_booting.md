---
title: "Error 8: Kernel must be loaded before booting"
date: 2013-01-04
forum: Desktop Environments
---

### Post by highrun on 2013-01-04
So I dual booted Ubuntu 12.04.1 LTS x64 with my Windows 7 laptop. I have it burned to a dvd, so I booted the CD, selected to try Ubuntu, then installed inside the "trial" environment. I installed the boot partition as sda6 as /boot, then my root partition was sda7 as /, I made another partition for my home on sda8 as /home. I then made a 4gb swap partition. I did NOT allow it to update, but even when I did allow it to update, the same issue occured. I have another NTFS partition as use as my media partition which is why my boot partition does not start as sda5.
Any suggestions, ideas, comments? I'm practically ignorant of Linux, so y'all will have to greatly simplify any suggestions. Thanks in advance!

Edit- I should also say how I got to this screen. I went to the windows side and set up the boot screen to "see" the Ubuntu boot partition using easyBCD.
I then tried to boot to the partition which came up to a command prompt like screen with grub. I typed "boot" and this error message is what occurred.

---

### Post by gnush on 2013-01-04
Sounds like there's something wrong with GRUB. Can you post your GRUB configuration file?

Have you tried to use Google? There are quite many results.

[http://kksol.wordpress.com/2012/02/12/error-8-kernel-must-be-loaded-before-booting-in-solaris-10-x86/](http://kksol.wordpress.com/2012/02/12/error-8-kernel-must-be-loaded-before-booting-in-solaris-10-x86/)
[http://www.linuxquestions.org/questions/linux-newbie-8/kernel-must-be-loaded-before-booting-4175427664/](http://www.linuxquestions.org/questions/linux-newbie-8/kernel-must-be-loaded-before-booting-4175427664/)
[http://forums.fedoraforum.org/showthread.php?t=211383](http://forums.fedoraforum.org/showthread.php?t=211383)

---

### Post by highrun on 2013-01-04
I can try to post it, how would I do that however? Novice here :/. 
I tried google, but most of them occurred on different distributions, so I didn't want to assume they would all work the same. What confuses me, is that it worked before, but I decided to just wipe EVERYTHING on my laptop, including W7. I then did the same process as before to install Ubuntu and wound up with this error.

---

### Post by gnush on 2013-01-04
Have you tried to re-install it? If not, go for it. If you've wiped everything, you haven't got much to lose anyway. If it still doesn't work after that, then we'll see if we can't fix it.

Oh, and is there any particular reason as to why you don't let the Ubuntu installer choose the partitioning layout? I have a faint suspicion that the error may be somewhere there.

---

### Post by highrun on 2013-01-05
Sure, I'll reinstall and try that. If that doesn't solve the problem then we'll pick up from there. I assume when you say let Ubuntu decide, you mean select the option "install along windows 7"?

---

### Post by highrun on 2013-01-05
No good. I selected the install alongside Windows option and let the installer do the partitioning. I still get the same exact error.

---

