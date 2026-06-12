---
title: "Jaunty won't boot!"
date: 2009-05-04
forum: General Help
---

### Post by jediknight64 on 2009-05-04
Hello. I'm as new as can be to this and am willing to listen and take directions. I have an Acer Aspire 5535-2238. I recently upgraded to Jaunty and after a couple of blissful weeks, have found that jaunty will no longer boot. I have the dual boot option come up, Windows works fine, but when I choose Ubuntu it goes to the countdown screen (Press esc to enter menu). After that it displays the loading bar, the screen blinks about 5 times and . . . . . . darkness. I let it sit for 3 hours once and realised, "He's dead Jim." I'm determined not to give up and go back to Windows. So if it means I have to pull my head out of the sand and learn how to type commands, then so be it. Any help in this matter will be greatly appreciated.

I hit Ctrl-Alt-F1 when the loading bar was moving. It showed a list of commands but after it sat for awhile , it was back to the blank screen and no log-in prompt.

I also downloaded System Rescue to CD and used that to no avail it booted to the blank screen and I was back where I started. How ever, that has changed and now it is as follows;


Booting 'Ubuntu 9.04, kernel 2.6.28-11-generic'

Filesystem type is ntfs, partition type 0x07
The current working directory(i.e., the relative path)is /ubuntu/disks
[Linux-bzImage, setup=0x3000, size=0x353cd0]
[Linux-initrd @ 0x7af1d000, 0x7739bf bytes]
Loading, please wait...
ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell!


BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)


My last session was a few days ago, I was adding upgrades like a newb in a Linux candy store. Must...have...more...candy. LOL. My bad, obviously.

---

### Post by Brainy142 on 2009-05-04
Hmm.... something doesn't exist.... have you tried recovery mode?

---

### Post by garythegoth on 2009-05-04
> **jediknight64 said:**
> Hello. I'm as new as can be to this and am willing to listen and take directions. I have an Acer Aspire 5535-2238. I recently upgraded to Jaunty and after a couple of blissful weeks, have found that jaunty will no longer boot. I have the dual boot option come up, Windows works fine, but when I choose Ubuntu it goes to the countdown screen (Press esc to enter menu). After that it displays the loading bar, the screen blinks about 5 times and . . . . . . darkness. I let it sit for 3 hours once and realised, "He's dead Jim." I'm determined not to give up and go back to Windows. So if it means I have to pull my head out of the sand and learn how to type commands, then so be it. Any help in this matter will be greatly appreciated.

I hit Ctrl-Alt-F1 when the loading bar was moving. It showed a list of commands but after it sat for awhile , it was back to the blank screen and no log-in prompt.

I also downloaded System Rescue to CD and used that to no avail it booted to the blank screen and I was back where I started. How ever, that has changed and now it is as follows;


Booting 'Ubuntu 9.04, kernel 2.6.28-11-generic'

Filesystem type is ntfs, partition type 0x07
The current working directory(i.e., the relative path)is /ubuntu/disks
[Linux-bzImage, setup=0x3000, size=0x353cd0]
[Linux-initrd @ 0x7af1d000, 0x7739bf bytes]
Loading, please wait...
ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell!


BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)


My last session was a few days ago, I was adding upgrades like a newb in a Linux candy store. Must...have...more...candy. LOL. My bad, obviously.

Oh my this looks **familiar**. Im having a similar issue to this on my laptop. Whenever I try to boot a LiveUSB it gives that sort of error message. Yet a LiveCD works fine. It may be an issue with Jaunty itself, because Intrepid works fine :/

---

### Post by Brainy142 on 2009-05-04
Oddly enough, my friend has the same problem.

---

### Post by wlg on 2009-05-04
Same problem, woked OK for a while, now wo't boot.  I tried to reinstall from ISO disk and it kept trying to boot from hard disk. Hard to run live 8,04 CD to get help.

---

