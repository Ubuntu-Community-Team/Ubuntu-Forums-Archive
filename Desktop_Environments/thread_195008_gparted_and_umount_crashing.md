---
title: "gparted and umount crashing"
date: 2006-06-12
forum: Desktop Environments
---

### Post by metro.tramp on 2006-06-12
I'm trying to reformat the second harddrive (/dev/hdb) on my box.

I apt-got gparted and loaded it up. It can see the drive fine, but when I try the unmount option I receive the message 

> Could not unmount /dev/hdb1

Device or resource busy

I tried umount in terminal but got 

> umount: /: device is busy
umount: /: device is busy

So i did a quick google and found that the -l option for umount will unmount the disk quickly. However, this causes the terminal to fail - it loads up but there is no "user@box:~$" and the screen stays blank.

When i try to restart, it freezes for a while then goes to the login screen. The mouse fails at this point and I have to restart with the power switch.

What am I doing wrong?
How can I unmount and reformat my second drive?

---

### Post by lamego on 2006-06-12
According to the error message you are trying to unmount the disk where your system root "/" is installed. You can't format the disk when you are "running" from it.

---

