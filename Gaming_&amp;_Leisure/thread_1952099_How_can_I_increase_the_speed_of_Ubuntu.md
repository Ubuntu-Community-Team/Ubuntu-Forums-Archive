---
title: "How can I increase the speed of Ubuntu?"
date: 2012-04-03
forum: Gaming &amp; Leisure
---

### Post by demonkingj on 2012-04-03
Well, I was playing a game through pygame and I was getting 2fps. I also notice that when I do use Ubuntu everything just feels slow, compared to using Win7. I am using virtualbox. Just hoping could help me.

---

### Post by madjr on 2012-04-03
> **demonkingj said:**
> Well, I was playing a game through pygame and I was getting 2fps. I also notice that when I do use Ubuntu everything just feels slow, compared to using Win7. I am using virtualbox. Just hoping could help me.

if you're using ubuntu virtualized inside virtualbox dont expect it to be fast.

try Wubi (window installer) instead.


[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

---

### Post by Dlambert on 2012-04-06
Also a lighter Dm could help as well, such as LXDE or XFCE

---

### Post by sudodus on 2012-04-06
Or make a dual boot system, that can boot either Windows or Ubuntu.

Wubi is running Ubuntu on the computer directly, but its file system is inside a file in the NTFS file system, and it is not as stable as a 'regular' dual boot install, where Ubuntu is installed to a partition. It is a good idea to test Ubuntu with a wubi install, but in the long run you should go for dual boot.

---

### Post by OrangeCrate on 2012-04-06
I agree, that a dual boot would be a good/best option. Instructions on how to do, can be found here:

[http://ubuntuguide.org/wiki/Ubuntu_Oneiric_Installation](http://ubuntuguide.org/wiki/Ubuntu_Oneiric_Installation)

---

### Post by anontheanon on 2012-04-13
Or smaller partitions for your OS, and a large /data partition in NTFS or Fat32, or a separate hard drive for data.

Windows 7 can run a lot of Unix and Linux apps natively. It might not be necessary to use emulation.

---

