---
title: "Grub Error 2: BIG TIME"
date: 2009-04-08
forum: General Help
---

### Post by Wangsta on 2009-04-08
I was running Xubuntu, when my dad accidentally turned it off by holding the power button down (after attempting to put it in standby multiple times. All of which failed to do anything). When I turned it on again, I got some weird version of linux, only in command-line form without any of my files, just like 30 commands or something too. I also couldn't figure out how to get it to quit.

I held the power button until it shut down, but when I turned it back on, I got the Grub 1.5 Error 2 message. Using a LiveCD, and after initiating grub in a terminal, I entered: "find /boot/grub/stage1." After getting several errors, I went looking for the /boot/grub folder.


It DOESN'T EXIST. :shock: It's gone. The boot folder holds only 5 files and no folders: abi-...-generic, config-...-generic, memtest86+.bin, System.map-...-generic, and vmccoreinfo-...-generic.  (The dots[...] stand for 2.6.27-7)

After I tried "sudo fdisk -l" I got this:

 ```
Device   Boot  Start   End  Blocks    Id  System
/dev/sda1  *     1      2325  (big #)  83  Linux
/dev/sda2        2326   2431  851445   5   Extended
/dev/sda5        2326   2431  851413+  82  Linux swap / Solaris
```

What the HECK am I supposed to do?!  Please PLEASE help!

---

### Post by oldos2er on 2009-04-08
If you have a LiveCD you can boot from, try running fsck against your boot partition. Are you able to boot into recovery mode?

---

### Post by Wangsta on 2009-04-09
I can't boot from the hard drive in recovery mode, it goes to Error 2 before I can do ANYTHING, except for editing the BIOS.

What exactly is "running fsck against your boot partition"?

---

### Post by oldos2er on 2009-04-09
fsck = file system check. See [https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)

---

### Post by Wangsta on 2009-04-09
I tried this:
```

ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda1: recovering journal
Resize inode not valid.  Recreate<y>? yes

Clearing orphaned inode 16382 (uid=1000, gid=1000, mode=0140755, size=0)
Clearing orphaned inode 2240230 (uid=1001, gid=1001, mode=0100600, size=0)
Clearing orphaned inode 2240229 (uid=1001, gid=1001, mode=0100600, size=0)
Clearing orphaned inode 2240228 (uid=1001, gid=1001, mode=0100600, size=0)
Clearing orphaned inode 2240227 (uid=1001, gid=1001, mode=0100600, size=0)
Clearing orphaned inode 2240226 (uid=1001, gid=1001, mode=0100600, size=0)
/dev/sda1 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Root inode is not a directory.  Clear<y>? yes

Inode 8, i_blocks is 0, should be 262416.  Fix<y>? yes


Running additional passes to resolve blocks claimed by more than one inode...
Pass 1B: Rescanning for multiply-claimed blocks
Multiply-claimed block(s) in inode 425213: 857853
Multiply-claimed block(s) in inode 425501: 857853
Pass 1C: Scanning directories for inodes with multiply-claimed blocks
Pass 1D: Reconciling multiply-claimed blocks
(There are 2 inodes containing multiply-claimed blocks.)

File ??? (inode #425213, mod time Wed Apr  8 11:26:24 2009) 
  has 1 multiply-claimed block(s), shared with 1 file(s):
	??? (inode #425501, mod time Wed Apr  8 22:13:29 2009)
Clone multiply-claimed blocks<y>? yes

File ??? (inode #425501, mod time Wed Apr  8 22:13:29 2009) 
  has 1 multiply-claimed block(s), shared with 1 file(s):
	??? (inode #425213, mod time Wed Apr  8 11:26:24 2009)
Multiply-claimed blocks already reassigned or cloned.

Pass 2: Checking directory structure
Entry '..' in ??? (32705) has deleted/unused inode 2.  Clear<y>? yes

Entry '..' in ??? (98113) has deleted/unused inode 2.  Clear<y>? yes

Entry '..' in ??? (277985) has deleted/unused inode 2.  Clear<y>? yes

Entry '..' in ??? (425153) has deleted/unused inode 2.  Clear<y>? yes

Entry 'auth.log.0' in .../log (425162) has deleted/unused inode 425485.  Clear<y>? yes

Entry 'kern.log.2.gz' in .../log (425162) has deleted/unused inode 425487.  Clear<y>? yes

Entry 'auth.log.3.gz' in .../log (425162) has deleted/unused inode 425482.  Clear<y>? yes

Entry 'aptitude.5.gz' in .../log (425162) has deleted/unused inode 425473.  Cle
```

Is this bad?

---

### Post by djbushido on 2009-04-09
No, this shows that it is fixing something.
If you are using the livecd, can you post the output of this command:
```
sudo fdisk -l
```
Please?
EDIT:
Oops, you already did.
Try running this:
```
sudo grub-install hd0
sudo grub-install (hd0,0)
```
Assuming that the only drive in is the Linux drive "sda" and that partition 1 "(hd0,**0**)" is where Linux is stored.
Should work. Hope so.

---

### Post by khelben1979 on 2009-04-09
I think you can gain some wisdom by spending some time with the [Grub Wiki]("http://wiki.linuxquestions.org/wiki/GRUB") (see link).
And one other thing, when the Linux system has been messed up: stay calm. :-k

---

