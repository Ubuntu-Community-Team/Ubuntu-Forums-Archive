---
title: "Hardy UDF Patch"
date: 2008-12-30
forum: General Help
---

### Post by Sin@Sin-Sacrifice on 2008-12-30
So yeah... I had to back up my entire system on winblows because of some media faults I couldn't get help with in ubuntu. Then I had to reformat because winblows doesn't like to let you have all your stuff. Anyway... now some of my DVDs (the RWs) are udf and linux hates winblows standards as much as I do (from now on I vow to backup immediately). So I tried to do this : [http://ubuntuforums.org/showthread.php?t=718744&page=2](http://ubuntuforums.org/showthread.php?t=718744&page=2) and I got this error right after rmmod udf and during insmod src/udf.ko : ```
:~/udf-filesystem-2.5$ sudo insmod src/udf.ko
insmod: error inserting 'src/udf.ko': -1 Invalid module format

```

Any help would be greatly appreciated. I only have a few that are UDF but I accidentally added some important info on one of them. Thanks in advance.

---

### Post by Sin@Sin-Sacrifice on 2008-12-30
Post Script: I don't have windows anymore because my "recovery disks" failed... so, in frustration, I just reformatted and installed ubuntu.

---

### Post by Sin@Sin-Sacrifice on 2008-12-30
[SIZE="1"]bump...?[/SIZE]

---

### Post by mankygitt on 2008-12-30
Just glancing through, because I'm planning a system rebuild in the coming week.
At worst, you could run up a VirtualBox VM and temporarily install a windows machine, with the optical drive mounted to the VM so you can access the data.

I've not tried your particular situation, however I've found the Windows VM option handy for other "windows only" problems. 
VirtualBox has two flavours - I'm using the PUEL version simply because it allows me to connect USB devices to the VM and operate them (iPod, Nokia Phone ...)

You would try this for your optical drive. VirtualBox enables you to share host folders with the guest machine, so you could restore from your UDF disks via windows vm into your 'nix host.

Good luck either way.

Manky

---

### Post by Sin@Sin-Sacrifice on 2008-12-30
Yeah.... I only had the winblow vista that was on the drive before I reformatted. I could "borrow" a torrent in place of it I guess but I think that's still illegal even though the copy of vista I had crapped out on 2 levels... The restore wouldn't boot and the restore disks wouldn't either. All 3 had the same problem so I just erased it. No more windows for me unless I feel like shelling out $150 and no... I don't. Hoping someone knows something about the patch. People out there have it working. Or at maybe has a precompiled kernel to hand out... I don't want to reinstall AGAIN so I am hesitant to compile it myself. Wish this patch would work.

---

### Post by Sin@Sin-Sacrifice on 2008-12-30
Last attempt at a bump...

---

### Post by mc4man on 2008-12-30
What kernel are you using?
```
uname -a
```

I enabled udf 2.50 on my other box a while back, worked no problems, am going to do this one now.
Using 2.6.24-22-generic 

Note: the only disks made in vista that aren't readable in hardy are 'live system' in udf 2.50, by default the 'live system' uses udf 2.01 which is readable as long as the disk was finalized.

I'd ck. ```
dmseg | tail
```
A 2.50 disk will show this error

> [16793.789758] ISOFS: Unable to identify CD-ROM format.
[16857.595225] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'UDF Volume', timestamp 2008/12/30 22:31 (1ed4)
[17043.216284] cdrom: sr0: dirty DVD+RW media, "finalizing"
[17430.365332] UDF-fs: minUDFReadRev=250 (max is 201)
[17440.881626] ISOFS: Unable to identify CD-ROM format.


Edit:
went fine on this box, here's complete terminal output to compare
> 
doug@doug-desktop:~/udf-filesystem-2.5$ make
make -C /lib/modules/2.6.24-22-generic/build M=/home/doug/udf-filesystem-2.5 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-22-generic'
  CC [M]  /home/doug/udf-filesystem-2.5/src/balloc.o
  CC [M]  /home/doug/udf-filesystem-2.5/src/dir.o
  CC [M]  /home/doug/udf-filesystem-2.5/src/file.o
  CC [M]  /home/doug/udf-filesystem-2.5/src/ialloc.o
  CC [M]  /home/doug/udf-filesystem-2.5/src/inode.o
  CC [M]  /home/doug/udf-filesystem-2.5/src/lowlevel.o
  CC [M]  /home/doug/udf-filesystem-2.5/src/namei.o
  CC [M]  /home/doug/udf-filesystem-2.5/src/partition.o
  CC [M]  /home/doug/udf-filesystem-2.5/src/super.o
  CC [M]  /home/doug/udf-filesystem-2.5/src/truncate.o
  CC [M]  /home/doug/udf-filesystem-2.5/src/symlink.o
  CC [M]  /home/doug/udf-filesystem-2.5/src/fsync.o
  CC [M]  /home/doug/udf-filesystem-2.5/src/crc.o
  CC [M]  /home/doug/udf-filesystem-2.5/src/directory.o
  CC [M]  /home/doug/udf-filesystem-2.5/src/misc.o
  CC [M]  /home/doug/udf-filesystem-2.5/src/udftime.o
  CC [M]  /home/doug/udf-filesystem-2.5/src/unicode.o
  LD [M]  /home/doug/udf-filesystem-2.5/src/udf.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/doug/udf-filesystem-2.5/src/udf.mod.o
  LD [M]  /home/doug/udf-filesystem-2.5/src/udf.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-22-generic'
doug@doug-desktop:~/udf-filesystem-2.5$ sudo insmod src/udf.ko
[sudo] password for doug: 
doug@doug-desktop:~/udf-filesystem-2.5$ sudo cp src/udf.ko /lib/modules/`uname -r`/kernel/fs/udf/
doug@doug-desktop:~/udf-filesystem-2.5$

And now same udf 2.50 disk
> [  105.601508] sr0: rw=0, want=9180420, limit=9180416
[  105.632807] attempt to access beyond end of device
[  105.632814] sr0: rw=0, want=9180420, limit=9180416
[  105.941087] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'UDF Volume', timestamp 2008/12/30 22:51 (1ed4)

---

### Post by Sin@Sin-Sacrifice on 2008-12-31
Here it is... ```
sin@Purgitory:~$ uname -a
Linux Purgitory 2.6.24-23-rt #1 SMP PREEMPT RT Thu Nov 27 20:37:26 UTC 2008 i686 GNU/Linux
sin@Purgitory:~$ dmesg | tail
[ 8082.052616] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 8082.087250] ISO 9660 Extensions: RRIP_1991A
[ 8186.562431] UDF-fs: No VRS found
[ 8186.587192] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 8186.587485] ISOFS: changing to secondary root
[ 8371.184662] UDF-fs: No VRS found
[ 8371.212295] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 8371.212676] ISOFS: changing to secondary root
[ 9191.748846] UDF-fs: No fileset found
[ 9191.765403] ISOFS: Unable to identify CD-ROM format.
sin@Purgitory:~$ 

```


Made this disk in Vista using OS burn software. I've read that it defaults to UDF 2.5.

---

### Post by mc4man on 2008-12-31
> Made this disk in Vista using OS burn software. I've read that it defaults to UDF 2.5. 
That's debatable, on a vista install I have on a laptop making data dvds using the 'live system' defaults (and is noted as such) to udf 2.01 though you can certainly switch to 2.50 if you choose to.

2.6.24-22 in 8.04 is able to read udf 2.01, maybe your kernel isn't.

---

### Post by Sin@Sin-Sacrifice on 2009-01-03
A bump for fun

---

