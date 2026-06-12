---
title: "ubuntu 9.04 gets stuck Booting! Please Help me!"
date: 2009-05-24
forum: General Help
---

### Post by hmongboi33 on 2009-05-24
After I upgraded to 9.04, I started having boot-up problems. It begins normally, but then freezes right before the loading bar.  The screen it gets stuck on says "Boot from (hd0,0) ext3 44cf877c-dda0-4bb8-804d-7d639a4c5be2 Starting up..."

Any help is extremely appreciated.  If you need anymore information from me, please don't hesitate to ask because I can't live without my computer.

---

### Post by mtthwbrnd on 2009-05-28
I have a similar problem. I am running Ubuntu 64 on VMWare fusion, it was working very well. A program I wrote got stuck in a loop and I could not bring up a terminal to kill the process so I rebooted instead. 

Now it gets stuck at start up similar to here apart from I get to the nice looking "progress bar" which goes to completion but then instead of presenting the box asking for user name and password I get a black screen with the hour-glass mouse pointer and lots of CPU usage ... it does not seen to stop.

Does anybody know how I can re-install whatever is going wrong without deleting my data files? I tried the live-cd install but it wanted to create new partitions, which would delete my data.

Have left it for over an hour now.

---

### Post by mtthwbrnd on 2009-05-28
I had installed a program called zlib:
[http://jsoftware.com/pipermail/programming/2009-May/014892.html](http://jsoftware.com/pipermail/programming/2009-May/014892.html)

This resulted in /usr/local/lib/libz.so.1 which was causing the problem. (something to do with Python complaining that it could not find the version of that library ... I never did like Python).

Anyway, in my case renaming to libz.so.1.hold solves the problem and can boot normally.

---

### Post by VMC on 2009-05-28
> **hmongboi33 said:**
> After I upgraded to 9.04, I started having boot-up problems. It begins normally, but then freezes right before the loading bar.  The screen it gets stuck on says "Boot from (hd0,0) ext3 44cf877c-dda0-4bb8-804d-7d639a4c5be2 Starting up..."

Any help is extremely appreciated.  If you need anymore information from me, please don't hesitate to ask because I can't live without my computer.Boot from licecd and type this from terminal:

```
sudo fdisk -l
```

and 

```
cat /etc/fstab
```

---

