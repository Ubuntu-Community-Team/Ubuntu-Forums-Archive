---
title: "PAE Installed on Ubuntu 10.10"
date: 2011-05-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by luisln01 on 2011-05-20
Sorry for the ignorance, I'm a bit new to Ubuntu. I just installed 6GB of RAM on my Ubuntu 32-bit System. As I searched online I came across that if I INSTALL and ENABLE the "PAE" it will allow me to use all 6GB. As of right now it only lets me use 3.5GB

free -m
             total       used       free     shared    buffers     cached
Mem:          3517       1026       2491          0        114        387
-/+ buffers/cache:        523       2993
Swap:            0          0          0


I tried this guide, but nothing after I reboot.
[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

Currently running. Ubuntu. 10.10

Please help!

---

### Post by papibe on 2011-05-20
I believe the PAE kernel is installed automatically ONLY IF in the process of installation you have a working connection to the internet.

Did you have your computer connected while installing it?

Regards.

---

### Post by luisln01 on 2011-05-21
Yes, I had a working internet connection . I've kept looking online to see if someone has had the same problem, but I can't find anything. I believe the PAE Kernel is installed but it's not letting me use all of the RAM I have on my system. Can the PAE Kernel be installed but not enabled?

I'm running on Ubuntu 10.10 Kernel 2.6.35-23-generic

---

### Post by papibe on 2011-05-21
To make sure which version of the kernel you're running do this:
```
$ uname -a
```
Regards.

---

### Post by luisln01 on 2011-05-21
luis@luis-PC:~$ uname -r
2.6.35-23-generic

---

