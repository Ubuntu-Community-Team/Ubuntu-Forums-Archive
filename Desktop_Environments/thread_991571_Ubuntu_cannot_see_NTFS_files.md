---
title: "Ubuntu cannot see NTFS files"
date: 2008-11-23
forum: Desktop Environments
---

### Post by sc4s2cg on 2008-11-23
Hi,

I'm using Ubuntu 8.10 by booting from a disk, it is not installed on my hardrive.I'm trying to access my main NTFS file system in order to backup a couple of files before reinstalling XP.

I followed the following tutorial to the T:
[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/#comment-61631](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/#comment-61631)

However, while I can access the drive without an error, I cannot see the files. I know they are there, it says that there is a 26Gb free space out of the total 130gb. How can I access the files to backup?

Any help would be appreciated.

Thank you in advance,
sc

---

### Post by Swagman on 2008-11-23
You should be seeing the contents of your NTFS drive but try pressing ctrl + H to show hidden files

---

### Post by sc4s2cg on 2008-11-24
I tried ctrl h as per your suggestion, but it didn't do much either.

---

### Post by forexsystemprofi on 2008-11-24
What is the output of ```
fdisk -l
``` ?

---

### Post by sc4s2cg on 2008-11-26
> **forexsystemprofi said:**
> What is the output of ```
fdisk -l
``` ?

Hi, I don't think the command worked:

> ubuntu@ubuntu:~$ fdisk -1
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors


I apologize for the long wait for a reply, my laptop just got back from Geek Squad as it was being backed up for me.

sc

---

### Post by Wally_dog on 2008-11-26
Hmm, well it's too bad you weren't able to do it. You could've tried installing the ntfs-3g package. I did that and can read/write NTFS perfectly.

---

### Post by bford16 on 2008-11-26
Also, if you look at your post (sc4s2cg), you will see that you tried to run 'fdisk -1' instead of 'fdisk -l.'  That last character is a letter l, not a number 1.

---

