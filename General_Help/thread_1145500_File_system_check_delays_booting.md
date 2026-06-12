---
title: "File system check delays booting"
date: 2009-05-01
forum: General Help
---

### Post by ee19921 on 2009-05-01
While booting my laptop, the file system check takes more than a 90 seconds (out of 2-3 min boot time). Most of the time spent is on partition /dev/sda1 of size 45 MB with some DELL utility files. Probably came with the laptop. When run fsck on that partition using live CD or after booting, it completes in a second. This consumes time only during regular booting.

do we have a workaround this? 

I am attaching the log file from /var/log/fsck

checkroot
```
Fri May  1 17:41:28 2009

fsck 1.41.4 (27-Jan-2009)
/dev/sda6: clean, 230992/2605056 files, 4382262/5197019 blocks (check in 4 mounts)

Fri May  1 17:41:28 2009
----------------

```

checkfs
```

Log of fsck -C3 -R -A -a 
Fri May  1 17:41:29 2009

fsck 1.41.4 (27-Jan-2009)
dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
/dev/sda1: 86 files, 3731/28034 clusters
dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  430:4e/52, 431:54/65, 432:4c/6d, 433:44/6f, 434:52/76, 435:20/65, 436:69/20
  , 437:73/64, 438:20/69, 439:6d/73, 440:69/6b, 442:73/20, 443:69/6f
  , 444:6e/72, 445:67/20, 446:ff/6f, 447:0d/74, 448:0a/68, 449:44/65
  , 450:69/72, 451:73/20, 452:6b/6d, 453:20/65, 454:65/64, 455:72/69
  , 456:72/61, 457:6f/2e, 458:72/ff, 459:ff/0d, 460:0d/0a, 461:0a/44
  , 462:50/69, 463:72/73, 464:65/6b, 465:73/20, 466:73/65, 467:20/72
  , 468:61/72, 469:6e/6f, 470:79/72, 471:20/ff, 472:6b/0d, 473:65/0a
  , 474:79/50, 475:20/72, 476:74/65, 477:6f/73, 478:20/73, 479:72/20
  , 480:65/61, 481:73/6e, 482:74/79, 483:61/20, 484:72/6b, 485:74/65
  , 486:0d/79, 487:0a/20, 488:00/74, 489:00/6f, 490:00/20, 491:00/72
  , 492:00/65, 493:00/73, 494:00/74, 495:00/61, 496:00/72, 497:00/74
  , 498:00/0d, 499:00/0a, 506:bf/cb, 507:cc/d8
  Not automatically fixing this.
/dev/sda2: 71243 files, 1142377/1310162 clusters
dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
/dev/sda5: 4256 files, 1946396/1964030 clusters

Fri May  1 17:43:04 2009
----------------

```

Thank you!

---

### Post by ee19921 on 2009-05-02
bump!


anybody else facing similar problem?

---

### Post by unutbu on 2009-05-02
Please post your /etc/fstab. This is the file that would tell Ubuntu to mount /dev/sda1.

If you don't tell Ubuntu to mount /dev/sda1, it won't fsck it.
Since it is a static Dell utility partition, you shouldn't need to mount it while in Ubuntu.

---

### Post by ee19921 on 2009-05-02
OK. I will boot after commenting out the line with /dev/sda1.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda8       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda2       /media/c        vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda5       /media/e        vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda7       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

---

### Post by unutbu on 2009-05-02
Open a terminal (Applications>Accessories>Terminal)
```

gksu gedit /etc/fstab
```

Change
```

/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda2       /media/c        vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda5       /media/e        vfat    defaults,utf8,umask=007,gid=46 0       1

```
to

```
[COLOR="Red"]#[/COLOR] /dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       [COLOR="Red"]2[/COLOR]
/dev/sda2       /media/c        vfat    defaults,utf8,umask=007,gid=46 0       [COLOR="Red"]2[/COLOR]
/dev/sda5       /media/e        vfat    defaults,utf8,umask=007,gid=46 0       [COLOR="Red"]2[/COLOR]

```
(Changes have been marked in red).

Save and exit. The # sign "comments-out" /dev/sda1, so it will no longer be mounted at boot time. According to the man page for fstab, only the root filesystem should have a value of 1 at the end of its entry. All others should have a 2 or a 0.

Reboot.

---

### Post by ee19921 on 2009-05-02
OK. I made those changes. The reboot immediately after that took around 7 mins, most of the time spent on checking discs. I figured it might be due to the changes made to fstab file, so I rebooted again. This time it again FS checked the partition /dev/sda1, which I didn't mount. :confused:

```
Log of fsck -C3 -R -A -a 
Sat May  2 17:07:52 2009

fsck 1.41.4 (27-Jan-2009)
dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  430:4e/52, 431:54/65, 432:4c/6d, 433:44/6f, 434:52/76, 435:20/65, 436:69/20
  , 437:73/64, 438:20/69, 439:6d/73, 440:69/6b, 442:73/20, 443:69/6f
  , 444:6e/72, 445:67/20, 446:ff/6f, 447:0d/74, 448:0a/68, 449:44/65
  , 450:69/72, 451:73/20, 452:6b/6d, 453:20/65, 454:65/64, 455:72/69
  , 456:72/61, 457:6f/2e, 458:72/ff, 459:ff/0d, 460:0d/0a, 461:0a/44
  , 462:50/69, 463:72/73, 464:65/6b, 465:73/20, 466:73/65, 467:20/72
  , 468:61/72, 469:6e/6f, 470:79/72, 471:20/ff, 472:6b/0d, 473:65/0a
  , 474:79/50, 475:20/72, 476:74/65, 477:6f/73, 478:20/73, 479:72/20
  , 480:65/61, 481:73/6e, 482:74/79, 483:61/20, 484:72/6b, 485:74/65
  , 486:0d/79, 487:0a/20, 488:00/74, 489:00/6f, 490:00/20, 491:00/72
  , 492:00/65, 493:00/73, 494:00/74, 495:00/61, 496:00/72, 497:00/74
  , 498:00/0d, 499:00/0a, 506:bf/cb, 507:cc/d8
  Not automatically fixing this.
/dev/sda2: 71244 files, 1188716/1310162 clusters
dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
/dev/sda5: 4256 files, 1946396/1964030 clusters

Sat May  2 17:09:27 2009

```

---

### Post by drs305 on 2009-05-02
Have you tried fixing this partition with dosfsck's "-a" switch? This may or may not fix the error, but if you are at the point where you aren't using the device because of errors it is worth considering.

---

### Post by ee19921 on 2009-05-02
> **drs305 said:**
> Have you tried fixing this partition with dosfsck's "-a" switch? This may or may not fix the error, but if you are at the point where you aren't using the device because of errors it is worth considering.

I have run fsck on that partition and they always completed within a second. So dosfsck work different from fsck? I don't get what you mean by "you aren't using the device because of errors". I am still using the harddrive which has this partition. But I am not using that partition at all. I don't know if it is being used while booting Windows. 

I see "dosfsck -a" is to fix errors, given my HDD partitions, is it safe to do it?

The list of files in that partition. 

```
Adaptec2.mdm  CABLES.mdm   CsAudio.mdm   DellSys.msm   IEEE1394.mdm  Memory.mdm   Nbtherm.MDM   Raid.mdm    symtree.ini   UsbMouse.mdm
Adaptec.mdm   Cache.mdm    DDInit.mim    delltbui.exe  IMchEcc.mdm   MiscPci.mdm  nic8254x.MDM  Scsi.mdm    SYSBDMON.mdm  USBOHCI.mdm
ami_raid.mdm  command.com  ddinit.mlm    dir.lst       int15_88.com  Mouse.mdm    Nic.mdm       seal.exe    System.mdm    UsbTm.mdm
autoexec.bat  config.bts   dell          Diskette.mdm  IoApic.mdm    MpCache.mdm  Parallel.mdm  seal.ini    Usb2.mdm      UsbUfi.mdm
autoexec.up   config.sys   Dellboot.exe  Disk.mdm      io.sys        msdos.sys    Pci.mdm       Serial.mdm  UsbDevID.mdm  USBUHCI.mdm
BiosMp.mdm    config.up    delldiag.com  Dvd.mdm       IR.mdm        NbBatt.MDM   Perc2Ada.mdm  Smbios.mdm  UsbKbd.mdm    Video.mdm
bootlog.prv   copyup.bat   delldiag.exe  GenAudio.mdm  Keyboard.mdm  Nbfan.MDM    pm.mdm        SMBus.mdm   UsbMass.mdm
bootlog.txt   Cpu.mdm      DellDiag.INI  Iaudio.mdm    LSI.mdm       NbSvc.MDM    Pnp.mdm       Smi.mdm     Usb.mdm

```

---

### Post by drs305 on 2009-05-02
I read your post as "didn't mount" instead of "I didn't mount". In any case, the man page says the -a switch tries to repair it with the "least destructive" method. Don't know how comforting that is to you. On the other had, the descrepancies are between the partition and its backup. You could first run it with the "-i" switch just to see what kind of repair it wants to do.

Everyone's tolerance is different.If it were my machine I would try to copy all the files if I could and then run the test rather than put up with extensive delays on boot. 

By the way, with fsck, you can abort the check by pressing ESC, don't know about dosfsck.

There is an excellent app called TestDisk that can also run tests on your partition tables. You can find quite a few posts about it on these forums.

---

### Post by Yellow Pasque on 2009-05-02
> By the way, with fsck, you can abort the check by pressing ESC, don't know about dosfsck.

fsck just calls dosfsck (or whatever other fsck subprogram is appropriate for the filesystem type), so it should behave similarly, no?

I would try setting it to '0' in /etc/fstab instead of '2', based on the -A section of the fsck man page.

> Walk through the /etc/fstab file and try to check all file systems in one run. This option is typically used from the /etc/rc system initialization file, instead of multiple commands for checking a single file system.

The root filesystem will be checked first unless the -P option is specified (see below). After that, filesystems will be checked in the order specified by the fs_passno (the sixth) field in the /etc/fstab file. Filesystems with a fs_passno value of 0 are skipped and are not checked at all. Filesystems with a fs_passno value of greater than zero will be checked in order, with filesystems with the lowest fs_passno number being checked first. If there are multiple filesystems with the same pass number, fsck will attempt to check them in parallel, although it will avoid running multiple filesystem checks on the same physical disk.

Hence, a very common configuration in /etc/fstab files is to set the root filesystem to have a fs_passno value of 1 and to set all other filesystems to have a fs_passno value of 2. This will allow fsck to automatically run filesystem checkers in parallel if it is advantageous to do so. System administrators might choose not to use this configuration if they need to avoid multiple filesystem checks running in parallel for some reason --- for example, if the machine in question is short on memory so that excessive paging is a concern. 

---

### Post by ee19921 on 2009-05-02
> **drs305 said:**
> In any case, the man page says the -a switch tries to repair it with the "least destructive" method. Don't know how comforting that is to you. On the other had, the descrepancies are between the partition and its backup. You could first run it with the "-i" switch just to see what kind of repair it wants to do.

There is an excellent app called TestDisk that can also run tests on your partition tables. You can find quite a few posts about it on these forums.

I will try TestDisk. One more question. When you said "descrepancies are between the partition and its backup" I assume you are referring to the checkfs message "There are differences between boot sector and its backup.". But what does that mean?

---

### Post by ee19921 on 2009-05-02
> **Temüjin said:**
> fsck just calls dosfsck (or whatever other fsck subprogram is appropriate for the filesystem type), so it should behave similarly, no?

I would try setting it to '0' in /etc/fstab instead of '2', based on the -A section of the fsck man page.

I tried Esc key, but it only typed '^[' on screen. dosfsck took it's own time. 

OK. You would assign the same number as the root filesystem so that the check won't run in parallel. Am I right? But when I checked the fsck logs, the timestamps indicate that they still run serially. 

checkroot
```
Log of fsck -C3 -a -t ext3 /dev/sda6 
Sat May  2 19:07:15 2009

fsck 1.41.4 (27-Jan-2009)
/dev/sda6: clean, 231374/2605056 files, 4399455/5197019 blocks

Sat May  2 19:07:15 2009

```

checkfs - ```
Sat May  2 19:07:16 2009

```

---

### Post by ee19921 on 2009-05-02
What if I do a fresh install of ubuntu and windows after repartitioning with just 2 partitions? Will it solve those "discrepancies"?

---

### Post by drs305 on 2009-05-02
If you set the fsck check status to 0 it won't be checked. So the last two entries of the sda1 line would be 0 0. The system partition is generally given a value of 1, with other partitions given a value of 2. The ones assigned a 2 *would* run serially with 1, but if it is listed with 0 in fstab the partition won't be checked at all. 

This may lead to a compounding of errors until the partition simply fails, so you have to weigh the risks and rewards.

With fsck at least, if you are in the boot sequence there is a message that says you can terminate an fsck check by pressing ESC. I wasn't referring to running an fsck check from a terminal. I imagine hitting an ESC key while a fsck check was being performed in a terminal would produce a similar result to the one you got. 

And don't forget that mounted partitions should not normally be checked while mounted, if you are running these checks from terminal instead of during the initial boot.

---

### Post by ee19921 on 2009-05-02
> **drs305 said:**
> If you set the fsck check status to 0 it won't be checked. So the last two entries of the sda1 line would be 0 0. The system partition is generally given a value of 1, with other partitions given a value of 2. The ones assigned a 2 *would* run serially with 1, but if it is listed with 0 in fstab the partition won't be checked at all. 

This may lead to a compounding of errors until the partition simply fails, so you have to weigh the risks and rewards.

With fsck at least, if you are in the boot sequence there is a message that says you can terminate an fsck check by pressing ESC. I wasn't referring to running an fsck check from a terminal. I imagine hitting an ESC key while a fsck check was being performed in a terminal would produce a similar result to the one you got. 

And don't forget that mounted partitions should not normally be checked while mounted, if you are running these checks from terminal instead of during the initial boot.

dumb me! I got it wrong. 

I did hit Esc while booting. May be the text interface is shown only after fsck has started. I mean, I see the fancy ubuntu logo and the thin progress bar and the messages are shown just in time to fsck the partition.

---

### Post by ee19921 on 2009-05-03
OK. I got rid of those ridiculous number of partitions. I reinstalled ubuntu. Now, the booting and logging in takes less than 50s. 

Thanks to drs305 and unutbu for replying back.

---

