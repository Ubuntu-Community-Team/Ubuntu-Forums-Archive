---
title: "HELP I lost all my existing files when installing ubuntu"
date: 2008-12-24
forum: General Help
---

### Post by wlan-11g on 2008-12-24
I installed Ubuntu on my laptop (7.10)

I think I accidentally re-partitioned the drive and now all my previous files are gone. 

I removed the HDD from the laptop plugged it into my Ubuntu Desktop (using an external HDD USB adapter) and all I can find now is the system files.

I plugged the HDD in my Windows Machine, it doesn't even recognize the drive (although it does detect that the hardware is there).

So my question is, is there any way to recover the previous partition / files? If so, what software would be able to do this?

---

### Post by wlan-11g on 2008-12-25
Further to the above,

I was attempting to install Ubuntu on the same drive over my existing Vista O/S.

The Vista O/S is now seemingly disappeared.

Any suggestions?

---

### Post by Sef on 2008-12-25
QUOTE] So my question is, is there any way to recover the previous partition / files? If so, what software would be able to do this?[/QUOTE]

Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by caljohnsmith on 2008-12-25
How about opening a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
```
With the HDD in question connected. If you can figure out from the fdisk output which is the partition you want to access (in the form sdXY, like sdb1 for example), then try doing:
```
sudo mount /dev/sdXY /mnt
ls -l /mnt
```
And please post the output.

---

