---
title: "Yet Another NTFS Question"
date: 2008-07-12
forum: Desktop Environments
---

### Post by DrewT on 2008-07-12
I have three Windows 2000 NTFS partitions on a 25-gig hard drive set as master on the IDE bus. When I fun fdisk -l, they look like this:

> Disk /dev/sda: 27.3 GB, 27373731840 bytes
255 heads, 63 sectors/track, 3328 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3a4a3a49

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         639     5132736    7  HPFS/NTFS
/dev/sda2             640        3328    21599392+   f  W95 Ext'd (LBA)
/dev/sda5             640        3328    21599361    7  HPFS/NTFS


The primary partition (sda1) is c: under Windows, and I have labeled it Crap to reflect its contents. When I boot Hardy and look at the Computer view in Nautilus, I see "Crap" as an unmounted partition. That's perfect -- exactly what I want.

The problem is with the rest of that drive, which is d: in Windows (labeled Data). I can mount it using the following command:

> sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sda5 /media/windows

I can then browse it through the filesystem. I have not yet succeeded in getting it to mount at boot by editing fstab -- the directory I create for that purpose (media/Windows) seems to disappear when I reboot. But that's not really what I want anyway. What I'd like is to get "Data" to show up as an unmounted drive in Nautilus, the way "Crap" does. I'm pretty sure this is what I was seeing under an earlier install of Windows, but I was having so many problems that I did a clean reinstall, and since then the d:/Data drive has to be mounted through the filesystem. I guess it's a small inconvenience, but if there's a fix I'd love to find it.

Is it possible there's a problem with my Windows filesystem? I've run chkdisk on the d: drive from Windows with no results, but maybe that's the wrong utility, or maybe it has to run in safe mode?

---

### Post by logos34 on 2008-07-12
> **DrewT said:**
> What I'd like is to get "Data" to show up as an unmounted drive in Nautilus, the way "Crap" does. 

Run:

**sudo tune2fs -L Data /dev/sda5**


> I have not yet succeeded in getting it to mount at boot by editing fstab -- the directory I create for that purpose (media/Windows) seems to disappear when I reboot. But that's not really what I want anyway.

In the event you change your mind, to have sda1 mount at boot ntfs-config will fix fstab for you:

sudo apt-get install ntfs-config

gksudo ntfs-config

-->'enable write support internal devices' and set mount point

---

### Post by DrewT on 2008-07-12
Thanks, I may fall back on that. But I tried your first suggestion first, and got this result:

```

~$ sudo tune2fs -L Data /dev/sda5
tune2fs 1.40.8 (13-Mar-2008)
tune2fs: Bad magic number in super-block while trying to open /dev/sda5
Couldn't find valid filesystem superblock.
```
Is that a problem in the Windows filesystem?

---

### Post by logos34 on 2008-07-12
sorry, my brain isn't working tonight or I'm having a senior moment...

sudo apt-get install ntfsprogs

sudo ntfslabel -v /dev/sda5 Data

---

### Post by DrewT on 2008-07-13
Interesting. The first time I ran that, it reported that a filesystem check was scheduled and that I could either boot into Windows twice to clear it, or force a mount. I took the first choice and sure enough, when Windows loaded it ran a check on d:. I booted into Windows again for good measure, then back into Ubuntu, where the command ran without returning any error (or other) message. Only trouble is, I don't see the d:/Data drive anywhere, even after rebooting Ubuntu. Where is it supposed to be?

---

### Post by logos34 on 2008-07-13
> **DrewT said:**
> Interesting. The first time I ran that, it reported that a filesystem check was scheduled and that I could either boot into Windows twice to clear it, or force a mount. I took the first choice and sure enough, when Windows loaded it ran a check on d:. I booted into Windows again for good measure, then back into Ubuntu, where the **command ran without returning any error (or other) message.** Only trouble is, I don't see the d:/Data drive anywhere, even after rebooting Ubuntu. Where is it supposed to be?

odd, I specified verbose ('-v' option)...

It should show up as 'Data' in your file browser side pane (at least it does in Nautilus), as well as  on your desktop if you have volume icons 'visible' enabled in gconf-editor

---

### Post by DrewT on 2008-07-13
> odd, I specified verbose ('-v' option)...

My apologies. It seemed that the output on the first run (as described above) was pretty self-explanatory, and required further action from me before it was worth reporting back here. On the second run there was no output. It looks like this:

```
****@****:~$ sudo ntfslabel -v /dev/sda5 Data
****@****:~$ 
```

> It should show up as 'Data' in your file browser side pane (at least it does in Nautilus), as well as on your desktop if you have volume icons 'visible' enabled in gconf-editor

I ran gconf-editor which opened the graphical interface, but I don't see where to set that value.

---

### Post by logos34 on 2008-07-13
The command is correct I think:

> $ ntfslabel -h

Usage: ntfslabel [options] device [label]

gconf-editor>apps>nautilus>desktop>'Volumes_visible'

---

### Post by DrewT on 2008-07-14
Yeah, something else is wrong. I don't know if any of this is diagnostic, but when I open NTFS Configuration Tool, the first choice it presents me is to select the partition(s) I want to configure. The only one available is Crap; no Data. If I browse Places_Computer with Nautilus, Crap is there as an unmounted drive, and I can easily mount it. Data is not there at all. If I browse to File System_dev_by-label, Crap is there, Data is not. 

The icons visible under File System_dev include sda, sda1 (Crap), sda2 (extended), and sda5 (Data). I succeeded in browsing sda5 using another method, but as originally noted I was hoping to get it to act like Crap. 

(At least my choice of label for that partition is providing some unexpected amusement.)

---

### Post by DrewT on 2008-07-14
Oh, and this is all after setting the gconf-editor value as suggested.

---

