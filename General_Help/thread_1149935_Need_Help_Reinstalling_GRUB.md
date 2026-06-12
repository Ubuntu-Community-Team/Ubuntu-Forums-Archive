---
title: "Need Help Reinstalling GRUB"
date: 2009-05-05
forum: General Help
---

### Post by DeaconJones on 2009-05-05
Hi all,

So a couple weeks ago I was forced to reinstall XP on my dual boot machine, which of course wrote over the MBR. Haven't booted into Ubuntu in a while and now I'd like to fix it.

I have 9.04 Live CD, and am fairly comfortable with command line.

Partitions:

DISK 0/1: XP , 0/2: Data (NTFS)
DISK 1/1: Ubuntu (EXT) , 1/2 (Swap)

Anyone want to help me reinstall GRUB?

Thanks

DJ

---

### Post by zvacet on 2009-05-05
[Here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by DougieFresh4U on 2009-05-05
> **zvacet said:**
> [Here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Ok, I followed the commands from the link and get this
```


[CODE]   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      204800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       18168   145724609+   7  HPFS/NTFS
/dev/sda3           18169       38913   166634212+   5  Extended
/dev/sda5           38067       38913     6803496   82  Linux swap / Solaris
/dev/sda6           18169       26872    69914817   83  Linux
/dev/sda7           26873       38066    89915773+  83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 

```














 [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,5)
 (hd0,6)

grub> grub> setup (hd0)

Error 27: Unrecognized command

grub> grub> setup (hd5,6)

Error 27: Unrecognized command

grub> grub> setup (hd0,5,6)

Error 27: Unrecognized command

grub> find /boot/grub/stage1[/CODE]
Can some one please guide, as my system is only booting to Windows

---

