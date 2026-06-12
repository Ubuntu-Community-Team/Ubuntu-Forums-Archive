---
title: "Help Requested, usplash theme causes kernel panic on boot, dead system"
date: 2008-03-19
forum: Desktop Environments
---

### Post by gotlinuxed on 2008-03-19
I used startupmanager to install this usplash theme:
[http://www.ubuntu-art.org/content/show.php/Splash+usplash+theme?content=75366](http://www.ubuntu-art.org/content/show.php/Splash+usplash+theme?content=75366)
I'm running 7.10 on a thinkpad. I clicked on install theme, quit startup manager, and reboot.
After that the system was toast.
 
Immediately on reboot, Ubuntu instantly kernel panics after grub.
I booted into recovery mode, and it prints out this:

> 
RAMDISK: Compressed image found at block 0
RAMDISK: ran out of compressed data
invalid compressed format (err-1)
VFS: Cannot open root device "UUID-a74b9026-0234-4d00-98c8-0aff90a4" or unknown-block(0,0)
Please append a correct "root-" boot option; here are the available partitions:
Kernel panic: - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

Three other people on the forums appear to have had their systems fried in the same way, with no responses:
[http://ubuntuforums.org/showthread.php?t=641989](http://ubuntuforums.org/showthread.php?t=641989)
[http://ubuntuforums.org/showthread.php?t=625923](http://ubuntuforums.org/showthread.php?t=625923)
[http://ubuntuforums.org/showthread.php?t=387731](http://ubuntuforums.org/showthread.php?t=387731)

This is, unfortunately, someone else's computer, and I appear to have fried it and lost all their data. Does anyone have any suggestions on how we could get an official bug report in, as it appears normal use of startupmanager can currently catastrophically destroy any ubuntu box... would be a good thing to fix.:confused:

---

### Post by jken146 on 2008-03-19
[http://ubuntuforums.org/showthread.php?t=620860](http://ubuntuforums.org/showthread.php?t=620860) is a thread where this got sorted out.

---

### Post by gotlinuxed on 2008-03-19
My forum search skills apparently fail it.

Starting the process you documented, I'll let you know how it turns out.

You're pretty quick on the draw at 1am!

---

### Post by gotlinuxed on 2008-03-19
That fixed it! Whew! Thanks man.

---

