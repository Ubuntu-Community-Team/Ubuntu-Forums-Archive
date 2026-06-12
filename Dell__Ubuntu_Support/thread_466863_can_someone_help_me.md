---
title: "can someone help me"
date: 2007-06-07
forum: Dell  Ubuntu Support
---

### Post by vdub03 on 2007-06-07
ok i hvaw a dell inspiron 9400, i want to install ubuntu on it for daul booting but i don't know how. yet i have 4 partitions and not sure how to resize them and then what i'm supposed to rename them.

this is what i see

/dev/ sda
  /dev/sda1  fat16     57mb    33mb
  /dev/sda2  ntfs  /media/sda2       10737mb  3200mb
  /dev/sda3  ntfs  /media/sda3   147097mb    22500mb
  /dev/sda5  fat32  /media/sda5   2146mb   842mb

if someone could tell me which one i'm supposed to use and almost walk me through step by step on how to resize it and edit it and so on

---

### Post by bmeyer on 2007-06-07
Are you intending to completely reformat everything, installing Ubuntu and reinstalling Windows?  It doesn't look like you'll be able to install Ubuntu while leaving Windows alone.

---

### Post by vdub03 on 2007-06-07
so the only way i can daul boot is to wipe out windows and reinstall it, via finding it on bit tornado or somewhere, and create my partiton for ubuntu

---

### Post by Luc1fer on 2007-06-10
There is no need to wipe out windows.

The windows installation should be located in sda2 and therefor you should leave that partition alone.

sda1 and sda5 (at least one of them) is most likely partitions used by dell diagnostics and windows repairs. My guess is that sda1 is dell diagnostics and sda5 is a windows repair partition. If you got a cd called "Drivers and utilities" (mine is blue) you can most likely remove both of those partitions to gain some space. But you should probably check that the diagnostic programs exist on the cd (it's bootable) before you do anything with them.

sda3 should be mounted as D: in windows and that is the partition that you can wipe out without affecting windows and install ubuntu on. But you should make sure that you don't have anything on it that you want to keep.

// Lucifer

---

### Post by ridgeland on 2007-06-10
I just got my Dell-Ubuntu E520N. :)
I have 
/dev/sda1 = fat16 = 47 MB
/dev/sda2 = fat32 = 2 GB
/dev/sda3 = ext3 = 196 MB
/dev/sda4 = extended
/dev/sda5 = linux-swap = 2.5 GB
/dev/sda6 = ext3 = 228 GB

On my PC sda1 is the Dell Diagnostics. sda2 is system recovery, grub has an option to reinstall just like from the factory.  I can see how a factory-reinstall would be a wonderful feature for windows users but not so important for Linux.
sda3 = boot, sda5 = swap, sda6 = root (plus all user data).

By Windows do you mean Windows XP?

My GUESS is on your PC
sda1 = Dell diagnostics
sda5 = windows reinstall as shipped - available thru BIOS boot (if sda1 and sda5 are OK)

If you make a fresh install of Windows from CDs I would worry that Windows will destroy all the partitions, even the diagnostics ones, so it can take sda1.  I have resized ntfs partitions using gparted from a LiveCd (SysRescueCD).  This lets you make room for Linux.  If you try this be sure to defrag the hard drive first and after resizing boot into windows and let it run it's blue screen of fixing drive C:

First step should always be a backup of everything you want to keep.  Second step understand why the 3.2 GB and 22.5 GB partitions.  Does windows show both C: and D: as hard drives?  What are the "drive" sizes in GB?  What's on them? 
Does the PC have a reinstall as shipped option in the BIOS boot?
see  [https://support.dell.com/support/topics/global.aspx/support/dsn/en/document?journalid=B47E412B13DF11DC8EE4F3814F6AFF02&docid=DC47E7957E35BBC0E030A68F27280D16](https://support.dell.com/support/topics/global.aspx/support/dsn/en/document?journalid=B47E412B13DF11DC8EE4F3814F6AFF02&docid=DC47E7957E35BBC0E030A68F27280D16)

My plan would be resize the 22.5 GB partition to 14 GB and create a 0.5 GB partition for swap and an 8 GB partition of ext3 for Ubuntu.  If you have 6 GB or more free, it should be possible to resize and install.

---

