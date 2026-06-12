---
title: "Error message + Question About Grub"
date: 2006-05-03
forum: Desktop Environments
---

### Post by idontknow9999 on 2006-05-03
**Problem #1 & Question #1**

I put in my 200 GB sata 2 HDD.

I put in win xp, made a partition for 100 GB. Installed it, it worked.
I put in linux, installed it, it worked. 

I rebooted, all seemed fine. I could get in win xp and linux. So, I got on linux, and got some warning about some update. If there were 80s items, I downloaded 68 before I got some error (but I did install the 68 I did dl). I eventually rebooted. Now, Win xp works fine, but ubuntu is already broken…

I get this after the ubuntu splash screen

> 
/bin/sg: can’t access tty; job control turned off
# [4294690.638000] sdd: assuming drive cache: write through


I also once ended up with this message: (eh, I think when I used the older version)

> 
Uncompressing Lunix… Ok, booting the kernel
ALERT! /dev/sda2 dropping a shell!


I also did try the "safe mode", no go.

**Question #2**

On a side note, how would I put Windows XP as the first selected for grub?

---

### Post by TLE on 2006-05-03
About Q. 2
The file /boot/grub/menu.lst is the one that sets up your bootloader, so edit this file as root and find the place where it says
```
default (some number)
```
and change that number to the number item Windoze is in your bootloader menu. Also see this [thread]("http://www.ubuntuforums.org/showthread.php?t=159098")
This file is a system file so it is a good idea to back it up before you start editing it.
Don't know about your broken system, but if you don't get help, maybe you should consider reinstalling. It does sound a little like a kernel upgrade problem. So if you do reinstall, maybe you should remove the kernel upgrades from the upgrade list and then do then do them seperately. But hold on a little longer maybe someones got the solution

---

