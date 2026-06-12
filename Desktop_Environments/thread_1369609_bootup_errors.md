---
title: "bootup errors"
date: 2010-01-01
forum: Desktop Environments
---

### Post by endamurtagh@hotmail.com on 2010-01-01
I have ubuntu installled on my Vista machine using Wubi to intstall it into windows,which worked fine until i switched on my Pc  this morning and selected Ubuntu and i get a black screen with the message "[   3.346857] Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block (0,0) " As i am a complete beginner at linux i havent a clue how to sort it out. Anbody out there know how to sort it.

---

### Post by ajgreeny on 2010-01-01
I will point you to another post with the same problem where I answered
[http://ubuntuforums.org/showthread.php?p=8591532#post8591532](http://ubuntuforums.org/showthread.php?p=8591532#post8591532)
> I have never used wubi so I don't know if you get an option at boot-up to boot to a previous kernel as you do normally from grub, but if you do get that option, try booting to a previous kernel, if you have one. There have been a few cases of the new 2.6.312-16 kernel causing problems at boot time, and if this is your problem, the older kernel may solve it for you.
Good luck.  I hope this may help you.

---

### Post by drs305 on 2010-01-01
For Wubi, I believe the standard menu construction has you first select Ubuntu, then the next screen allows you to choose which kernel you want to boot.

Is this happening when you click on the Ubuntu option, or when you try to select a kernel (second menu)?  It sounds like it may be the first, but if you get to the actual Ubuntu menu, you can highlight an entry and press "e". This will open the contents, and the linux line should show something similar to this:
> 
linux /boot/vmlinuz-2.6.31-16-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro


If this is where you are at, post here and I'll provide further instructions on how to boot.

You can also visit the Grub 2 community doc on booting from the command line: [https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode") if you want to see how it might be done.

---

