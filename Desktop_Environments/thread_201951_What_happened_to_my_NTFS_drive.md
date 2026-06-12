---
title: "What happened to my NTFS drive?"
date: 2006-06-22
forum: Desktop Environments
---

### Post by bluezdood on 2006-06-22
Hey all,

So after successfully making my laptop dual-boot I went back to a complete WinXP install and deleted the Ubuntu partitions.  I recently decided that I wanted to make the laptop a permanent dual boot machine.  However, after shrinking my NTFS windows partition and creating two new partitions for Ubuntu (through the install program) my NTFS drive no longers shows up on the desktop like it did the first time I installed Ubuntu.  When I try to look at it it says that I don't have the permissions to browse that drive.  Somebody please help and keep in my that I am rather new to Linux so step by step would be helpful.  I do have automatix installed as well as the latest 686 kernel, so I'm not a complete noob but still.](*,) :-k ](*,)

---

### Post by Ramses de Norre on 2006-06-22
What's the output of ```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by bluezdood on 2006-06-22
Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8193    65810241    7  HPFS/NTFS
/dev/hda2            8194       11996    30547597+  83  Linux
/dev/hda3           11997       12161     1325362+   5  Extended
/dev/hda5           11997       12161     1325331   82  Linux swap / Solaris

---

### Post by Ramses de Norre on 2006-06-22
And fstab? ;)

---

### Post by bluezdood on 2006-06-22
:rolleyes: whoops

Ok, I don't have an internet connection on the laptop right now so I'll have to type it out best I can.

#<file system> <mount point>  <type>  <options>      <dump>  <pass>
proc                 /proc              proc     defaults        0           0
/dev/hda2         /                    ext3     defaults,errors=remount-ro 0
/dev/hda5         none               swap    sw               0           0
/dev/hdc          /media/cdrom0  udf,iso9660 user,noauto   0           0

---

