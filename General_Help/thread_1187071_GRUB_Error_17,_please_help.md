---
title: "GRUB Error 17, please help"
date: 2009-06-14
forum: General Help
---

### Post by jgrossm1 on 2009-06-14
OK I feel like a bit of an idiot right now, but I'm hoping there is some way to fix my idiocy without completely starting over. I was trying to install some updated firmare on an ipod:

dd if=ipod.firmware.whatever of=/dev/sda1

Obviously, this overwrote something pretty vital, either in my ubuntu or in GRUB. When I boot from my hard disk, I get GRUB Error 17. All I really need on my disk is a set of text files contained in a single folder, so if there is a way to get to that then that would be great and pretty much all I need. Any help would be very very very much appreciated. Thanks in advance for any help at all.

---

### Post by gradinaruvasile on 2009-06-14
You have overwritten a part of your hard drive... The first partition.
How many partitions do u have and where u have ubuntu installed?

---

### Post by jgrossm1 on 2009-06-14
> **gradinaruvasile said:**
> You have overwritten a part of your hard drive... The first partition.
How many partitions do u have and where u have ubuntu installed?

thanks for the reply.

I only have one partition, the one with Ubuntu installed on it, should be on sda1 unfortunately

---

### Post by jgrossm1 on 2009-06-14
actually, here's the output of sudo fdisk -l

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34af8c74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9356    75152038+  83  Linux
/dev/sda2            9357        9729     2996122+   5  Extended
/dev/sda5            9357        9729     2996091   82  Linux swap / Solaris
```

---

### Post by gradinaruvasile on 2009-06-14
> **jgrossm1 said:**
> actually, here's the output of sudo fdisk -l

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34af8c74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9356    75152038+  83  Linux
/dev/sda2            9357        9729     2996122+   5  Extended
/dev/sda5            9357        9729     2996091   82  Linux swap / Solaris
```

 Then u are toasted... :(

U could try something like testdisk to try recovering your partition though... I never used it myself.

You can install packages from the live cd too. First activate the repositories from "software sources", click reload, open a terminal and type
sudo su -
apt-get install testdisk 

testdisk
enlarge the terminal window (needs 1 more row downwards) 

Select no log
Select /dev/sda
Select Intel
Select Analyse
Select Quick search
press n
You get a list. 

You can press q here and select deeper search. I think this is what u need.
Thats all i can help you with.

Pressing "q" is cancel (it will get you back on the previous page.


Here is some documentation
[http://www.cgsecurity.org/wiki/Data_Recovery_Examples]("http://www.cgsecurity.org/wiki/Data_Recovery_Examples")

---

### Post by mike555 on 2009-06-14
You might want to try supergrub from ...
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

