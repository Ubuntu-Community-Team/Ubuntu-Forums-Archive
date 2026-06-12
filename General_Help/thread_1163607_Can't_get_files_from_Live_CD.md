---
title: "Can't get files from Live CD"
date: 2009-05-18
forum: General Help
---

### Post by sixsidepentagon on 2009-05-18
Hi all,

I tried to install Windows 7 to my system (already dual boots to Jaunty and OS X), but I've only had problems since. At first, it removed my ability to boot to Jaunty. Then, I tried to use rEFIt to update the MBR table. However, that made it so when I tried to boot to Windows, it told me the operating system was missing.

I want to fix those issues later, but what I need to do now is get some files off my Jaunty partition. I tried to put in a live CD (the most recent one I had was of Kubuntu 7.10) and access the drive, but when I did, it told me that the drive "belonged to UID 999 instead of UID 0".

I am beginning to worry the whole drive is unreadable for some reason. Before the live CD, I tried to use EXT2FS from OS X, but it told me there was an error.

Is there anything I can do? These files are very important.

---

### Post by taurus on 2009-05-18
From Ubuntu LiveCD, post the output of this command.

```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
```
That would be a lower case letter L, not number 1.

---

### Post by sixsidepentagon on 2009-05-18
sudo fdisk -l produced:

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41bccef7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2              26       12017    96321732+  af  Unknown
/dev/sda3   *       16064       19312    26086914+  83  Linux
/dev/sda4           19312       19458     1172357   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by taurus on 2009-05-18
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda3 /media/ubuntu
ls -la /media/ubuntu
```

---

### Post by sixsidepentagon on 2009-05-18
Brilliant! That worked perfectly, thanks so much, can't tell you how much I needed those files. This also makes me really happy because it means my Jaunty is recoverable, right?

---

### Post by taurus on 2009-05-18
You probably just need to reinstall GRUB back to MBR so you can boot Ubuntu again.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

