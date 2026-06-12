---
title: "Unable to Access Storage Partition"
date: 2009-06-05
forum: General Help
---

### Post by jmg999 on 2009-06-05
Hi,

First time poster, long time reader of the forums...

So, I'm running Ubuntu 8.04.1 LTS for servers.  I run the OS on its own 250GB HDD.  I also have an EXT3 3.2TB RAID-5 array.  This is what's become unreachable.  I've been having an issue w/ the onboard NIC, I believe.  It causes kernel panics every so often, and the system has to be given a hard shutdown.  Yesterday, when I attempted to restart it, I ran into some major difficulties.

First off, there was an indicator upon boot that there was some damage to the array.  The suggestion was to run fsck.  This took me into a management shell.  Running an fsck didn't help, and I was given this message:
```

jeffe@USC:~$ sudo fsck /dev/sda1
[sudo] password for jeffe: 
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```So, trying this method for all my alternate superblocks, I was presented w/ this:
```

jeffe@USC:~$ sudo fsck -b 32768 /dev/sda1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

```However, the partition is not mounted, nor are there any processes running that are tied to it.  Even running fuser couldn't resolve this.  I then took a look at fdisk -l.  It showed the partition had this filesystem type: EFI GPT.  This is not correct.  After reading everything I could find online, I finally made the decision to use fdisk to change the label back to 83 Linux.  I did this, but it didn't help anything.  When I try to run fsck or e2fsck, it still gets me nowhere:
```

jeffe@USC:~$ sudo e2fsck /dev/sda1 
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

jeffe@USC:~$ sudo e2fsck -b 98304 /dev/sda1
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

jeffe@USC:~$ dmesg |tail
[  386.826582] VFS: Can't find ext3 filesystem on dev sda1.

```I've tried from both single-user mode and logged in as myself.  I've also booted to a live CD, hoping that the device would not appear to be in use; no luck.  I even tried booting to a GParted live CD, but it was unable to see the partition that the array is on.  If anyone has any new ideas, I'm open to trying it.  This array has a great deal of data on it that is irreplaceable.  Any help would be immensely appreciated.  Thank you very much.

Jeff

---

### Post by JCoster on 2009-06-05
Hi Jeff,
I can't actually help you with your problem as I do not know enough about RAIDs but when posting, if you post all shell output and code in [ code ] [ /code ] tags (but without the spaces) then it makes it a lot easier for us to read and help you with your problem.
Also, you will not get '8)' rather than ```
8)
```.
Sorry I couldn't help you with your specific problem, but following these codes of practise in the future will help.

---

### Post by jmg999 on 2009-06-05
Will do.  Thank you for the tip. :)

---

### Post by jmg999 on 2009-06-05
Does anyone have any ideas on this?  I'm really screwed if I can't gain access to the data on this server.  There has to be some way to retrieve it.  Thanks, again.

---

