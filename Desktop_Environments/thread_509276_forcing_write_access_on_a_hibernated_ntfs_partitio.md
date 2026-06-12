---
title: "forcing write access on a hibernated ntfs partition"
date: 2007-07-25
forum: Desktop Environments
---

### Post by scicode on 2007-07-25
Hi folks
this is a tricky problem so let me first explain how i got into this unfortunate situation

A while ago I upgraded my sytem from Windows to Ubuntu. I made some free space (unformated) on my hd so I could install Ubuntu. Then I shut down Windows for the last time. Because I was very careless I used hibernate mode like always did. Next I inserted the Ubuntu CD and rebooted, installed Ubuntu on the unfromated free space. Everything worked fine except .. here it comes

When I try to start Windows (grub boot menu) i get an hal.dll error because the Windows boot table is not correct. The formely unformated space is now a linux partition, wich moved my windows **partition number**. All I would have to do is to change one integer in my windows **boot.ini**, but this is impossible because I can not get **write access to a hibernated NTFS partition**. 

Is there a switch in ntfs-3g so i can froce write access on hibernated partitions? I know this is dangerous becaus manipulating the file tabe leads to desaster, but all I have to do is manipulate one byte of data. It is very frustrating to see the contents of the file but not being able to change it.
I hope you can help me.

---

### Post by jcarlock on 2007-07-25
I used this option when my ntfs drive had a pending chkdsk and I needed to mount it.  Not sure if it works for hibernated drives...

mount -t ntfs-3g DEVICE DIRECTORY -o force 

JC

---

### Post by james0tucson on 2007-08-02
> **jcarlock said:**
> I used this option when my ntfs drive had a pending chkdsk and I needed to mount it.  Not sure if it works for hibernated drives...

mount -t ntfs-3g DEVICE DIRECTORY -o force 

JC

Indeed it does not.  I have a windows partition that is the result of recovering a system.  I made the disk image using dd.  I now want to mount it in order to do some data recovery.  I don't actually *care* if some data are lost, or even if the image is not usable in Windows.  It's not even possible to mount it under windows as the error message suggests - although I would like to see instructions for using such an image under VMWare. 

But I would like to force ntfs-3g to mount a copy of this image read-write, and it appears that ntfs-3g knows better than me.  I hate that enough to edit the source and override this check.

---

### Post by rubo77 on 2007-11-08
i mounted it read-only, that works, and  is enough for me:

```
mount -t ntfs-3g /dev/sda1 /media/sda1/ -o ro,force
```

---

### Post by jcarlock on 2008-04-08
You don't need to use the 3g driver if read-only is an option.  The stockdriver for ntfs from 05/06 would mount read-only....

Just an FYI.

JC

---

### Post by szaka on 2008-04-09
Read-write mount of hibernated volumes are possible using the 'remove_hiberfile' option which is supported since NTFS-3G 1.2216.

---

### Post by scicode on 2008-04-11
thanks thats good news, i eventually got it by messing aournd with the source code of ntfs-3g and sucessfully removed the read only switch, unfortunately editing the boot.ini did not help me booting my win parition, I still get a hal.dll error. well it was worth the try.

---

