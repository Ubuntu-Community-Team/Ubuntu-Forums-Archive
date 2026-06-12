---
title: "GParted - Formatted Wrong Drive."
date: 2009-01-20
forum: General Help
---

### Post by ErmyDermy on 2009-01-20
Using GParted on the LiveCD I clicked on "Create Partition Table" but  accidentally had the wrong drive selected, I quickly realized and clicked cancel as soon as it started, but now the laptop wont startup (in Windows Vista). Is there a way to recover the Drive? This was only a "Quick Format" I think. Will Data still be there? This was not my Laptop and I really need help!

---

### Post by caljohnsmith on 2009-01-20
Creating a new partition table fortunately does not overwrite the data on the drive, and most likely you can use "testdisk" to recover your partitions. To use testdisk, first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources (from the Live CD), and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
Make sure you are using version 6.9 or later (it will tell you in the start up screen what version it is), because earlier versions tend to crash when trying to list the directories of NTFS partitions. If you are using a previous version, let me know and I can give you further directions for getting the latest testdisk.

So after starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing. We can work from there if you want.

---

### Post by ErmyDermy on 2009-01-20
Thank you very much for your help and quick reply! 

I may not get enough time to finish the "Deep Search" tonight, So I may have to do the "Deep Search" tomorrow and then post the output.

---

### Post by ErmyDermy on 2009-01-21
```

Quick Search:

Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63

     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  1528 254 63   24563322 [PQSERVICE]
 2 P HPFS - NTFS           1529   0  1 10460 254 63  143492580
 3 P HPFS - NTFS          10506 209  8 19457  21 20  143785984 [DATA]

```

What I know about the partitions:

[PQSERVICE] is the Factory default recovery partition (I think)
[ACER] is the main important partition with Windows Vista on it. 
[DATA] was a secondary empty partition.  

```

Deep Search:

Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63

     Partition               Start        End    Size in sectors

* HPFS - NTFS              0   1  1  1528 254 63   24563322 [PQSERVICE]
D HPFS - NTFS           1529   0  1 10460 254 63  143492580
D HPFS - NTFS           1529   5 13 10506 209  7  144228352 [ACER]
D HPFS - NTFS          10461   0  1 19393 254 63  143508645
D HPFS - NTFS          10506 209  8 19457  21 20  143785984 [DATA]
D HPFS - NTFS          19394   0  1 19456 254 63    1012095 [ACER_SERVIC]

```

```

* HPFS - NTFS              0   1  1  1528 254 63   24563322 [PQSERVICE]

dr-xr-xr-x     0     0         0 21-Aug-2008 17:03 .
dr-xr-xr-x     0     0         0 21-Aug-2008 17:03 ..
-r--r--r--     0     0     37376 21-Aug-2008 17:04 BOOT.DAT
-r--r--r--     0     0       490 21-Aug-2008 17:04 ACERBP.P2
-r--r--r--     0     0        36  6-Dec-2008 11:59 aimdrs.dat
dr-xr-xr-x     0     0         0 21-Aug-2008 17:04 AUTORUN
-r--r--r--     0     0       356 21-Aug-2008 17:04 BACKUP.NAP
-r--r--r--     0     0    259584 21-Aug-2008 17:04 BCDEDIT.EXE
dr-xr-xr-x     0     0         0 21-Aug-2008 17:06 BitLocker
dr-xr-xr-x     0     0         0 21-Aug-2008 17:04 Boot
-r--r--r--     0     0    438840 21-Aug-2008 17:04 bootmgr
-r--r--r--     0     0     87552 21-Aug-2008 17:04 BootSect.exe
dr-xr-xr-x     0     0         0 21-Aug-2008 17:04 D2D
-r--r--r--     0     0    888832 21-Aug-2008 17:06 D2D32.EXE
-r--r--r--     0     0        78 22-Aug-2008 09:26 DrAssign2C.ini
dr-xr-xr-x     0     0         0 21-Aug-2008 17:12 FACTORY
-r--r--r--     0     0      6656 21-Aug-2008 17:04 FATBOOT.BIN
-r--r--r--     0     0       153 21-Aug-2008 17:04 FmtFAT32.INI
-r--r--r--     0     0    126976 21-Aug-2008 17:04 HiddenStart.exe
-r--r--r--     0     0     69632 21-Aug-2008 17:04 int15.sys
-r--r--r--     0     0       512 21-Aug-2008 17:04 MBR.BIN
-r--r--r--     0     0      1359 21-Aug-2008 17:04 model.dat
-r--r--r--     0     0        67 21-Aug-2008 17:04 NAPP.DAT
-r--r--r--     0     0       329 22-Aug-2008 09:13 NewPartDisk.ini
-r--r--r--     0     0       232 22-Aug-2008 09:26 OBR3.acr
-r--r--r--     0     0        70 21-Aug-2008 17:04 OBR3.ini
-r--r--r--     0     0        11 21-Aug-2008 17:04 P1.DAT
-r--r--r--     0     0       125 21-Aug-2008 17:04 PARTITION.ALL
dr-xr-xr-x     0     0         0 22-Aug-2008 09:13 Program Files
dr-xr-xr-x     0     0         0 22-Aug-2008 09:13 ProgramData
-r--r--r--     0     0       215 21-Aug-2008 17:06 RCD.DAT
-r--r--r--     0     0       382 21-Aug-2008 17:04 RestoreFAT32.INI
dr-xr-xr-x     0     0         0 21-Aug-2008 17:06 RYTOOLS
-r--r--r--     0     0       117 21-Aug-2008 17:06 SCD.DAT
dr-xr-xr-x     0     0         0 22-Aug-2008 09:13 sources
-r--r--r--     0     0        81 21-Aug-2008 17:06 SWCD.DAT
dr-xr-xr-x     0     0         0 22-Aug-2008 08:37 System Volume Information
-r--r--r--     0     0    131072 21-Aug-2008 17:04 UNICODE.BIN
dr-xr-xr-x     0     0         0 22-Aug-2008 09:13 Users
dr-xr-xr-x     0     0         0 22-Aug-2008 09:13 Windows

```

```

D HPFS - NTFS           1529   0  1 10460 254 63  143492580

Can't open filesystem. Filesystem seems damaged.

```

```

D HPFS - NTFS           1529   5 13 10506 209  7  144228352 [ACER]

dr-xr-xr-x     0     0         0 18-Mar-2008 14:06 .
dr-xr-xr-x     0     0         0 18-Mar-2008 14:06 ..
-r--r--r--     0     0    333203 18-Mar-2008 14:11 bootmgr
dr-xr-xr-x     0     0         0 18-Mar-2008 14:07 Acer
-r--r--r--     0     0        24 18-Mar-2008 14:11 autoexec.bat
-r--r--r--     0     0    699280 18-Mar-2008 14:11 bknowsetup.log
dr-xr-xr-x     0     0         0 18-Mar-2008 14:11 Book
dr-xr-xr-x     0     0         0 18-Mar-2008 14:11 Boot
-r--r--r--     0     0      8192 18-Mar-2008 14:11 BOOTSECT.BAK
-r--r--r--     0     0        10 18-Mar-2008 14:11 config.sys
dr-xr-xr-x     0     0         0  5-Dec-2008 05:11 Convesoft
dr-xr-xr-x     0     0         0 18-Mar-2008 14:11 Documents and Settings
dr-xr-xr-x     0     0         0 18-Mar-2008 14:11 DRV
dr-xr-xr-x     0     0         0 18-Mar-2008 14:13 Intel
-r--r--r--     0     0     40960 16-Aug-2005 15:49 junction.exe
-r--r--r--     0     0       512 18-Mar-2008 14:13 MDR.iss
dr-xr-xr-x     0     0         0 18-Mar-2008 14:13 MSOCache
-r--r--r--     0     0   2450776064 22-Aug-2008 08:34 pagefile.sys
dr-xr-xr-x     0     0         0 18-Mar-2008 14:14 PerfLogs
dr-xr-xr-x     0     0         0 18-Mar-2008 14:14 Program Files
dr-xr-xr-x     0     0         0 18-Mar-2008 14:28 ProgramData
-r--r--r--     0     0       426 18-Mar-2008 14:29 RHDSetup.log
-r--r--r--     0     0        86 18-Mar-2008 14:29 setup.log
dr-xr-xr-x     0     0         0 18-Mar-2008 14:29 System Volume Information
dr-xr-xr-x     0     0         0 18-Mar-2008 14:29 Users
dr-xr-xr-x     0     0         0 18-Mar-2008 14:30 Windows

```

```

D HPFS - NTFS          10461   0  1 19393 254 63  143508645

Can't open filesystem. Filesystem seems damaged.

```

- Doing the deep search again for the last two partitions, I accidentally closed the terminal.

---

### Post by caljohnsmith on 2009-01-21
So the "DATA" partition is empty? If you don't want to recover the DATA partition, then when your run testdisk again and get the "deep search" results, select each of the partitions like you did before, but use the right/left arrow keys to mark the partitions as highlighted in red below:
```
     Partition               Start        End    Size in sectors

[COLOR="Red"]P[/COLOR] HPFS - NTFS              0   1  1  1528 254 63   24563322 [PQSERVICE]
[COLOR="Red"]D[/COLOR] HPFS - NTFS           1529   0  1 10460 254 63  143492580
[COLOR="Red"]*[/COLOR] HPFS - NTFS           1529   5 13 10506 209  7  144228352 [ACER]
[COLOR="Red"]D[/COLOR] HPFS - NTFS          10461   0  1 19393 254 63  143508645
[COLOR="Red"]D[/COLOR] HPFS - NTFS          10506 209  8 19457  21 20  143785984 [DATA]
[COLOR="Red"]D[/COLOR] HPFS - NTFS          19394   0  1 19456 254 63    1012095 [ACER_SERVIC]
```
In other words, all partitions except your PQSERVICE and ACER partitions should be marked as "D" for deletion, and then you will recover the PQSERVICE and ACER partitions if you mark them as "P" and "*" respectively as shown above. Once you are sure all the partitions are marked exactly as shown above, press enter to go to the next screen where you can choose to write the new partition table. Once you do that, reboot, and please post the new output of:
```
sudo fdisk -lu
sudo mkdir /mnt/sda1 /mnt/sda2
sudo mount /dev/sda1 /mnt/sda1 && ls -l /mnt/sda1
sudo mount /dev/sda2 /mnt/sda2 && ls -l /mnt/sda2
```
And we can work from there if you want.

---

### Post by ErmyDermy on 2009-01-21
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x261680fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    24563384    12281661    7  HPFS/NTFS
/dev/sda2   *    24563712   168792063    72114176    7  HPFS/NTFS

```

```

ubuntu@ubuntu:~$ sudo mkdir /mnt/sda1 mnt/sda2
mkdir: cannot create directory `mnt/sda2': No such file or directory

```

Is that right? Shall I try the next command?

---

### Post by caljohnsmith on 2009-01-21
> **ErmyDermy said:**
> 
```

ubuntu@ubuntu:~$ sudo mkdir /mnt/sda1 mnt/sda2
mkdir: cannot create directory `mnt/sda2': No such file or directory

```

Is that right? Shall I try the next command?
Did you make sure you rebooted after you wrote the new partition table with testdisk? Also, please copy/paste the commands if possible, because you have a typo above; there should be a leading slash before "mnt":
```
sudo mkdir /mnt/sda1 [COLOR="Red"]/[/COLOR]mnt/sda2
```

---

### Post by ErmyDermy on 2009-01-21
> **caljohnsmith said:**
> Did you make sure you rebooted after you wrote the new partition table with testdisk? Also, please copy/paste the commands if possible, because you have a typo above; there should be a leading slash before "mnt":
```
sudo mkdir /mnt/sda1 [COLOR="Red"]/[/COLOR]mnt/sda2
```

My Bad, Well Spotted!


```

ubuntu@ubuntu:~$ sudo mkdir /mnt/sda1 /mnt/sda2
mkdir: cannot create directory `/mnt/sda1': File exists

```

```

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/sda1 && ls -l /mnt/sda1
total 2048
-rwxrwxrwx 1 root root    490 2005-09-29 09:35 ACERBP.P2
-rwxrwxrwx 1 root root     36 2008-12-06 11:59 aimdrs.dat
drwxrwxrwx 1 root root      0 2008-08-21 17:06 AUTORUN
-rwxrwxrwx 1 root root    356 2005-07-15 06:25 BACKUP.NAP
-rwxrwxrwx 1 root root 259584 2006-11-03 01:44 BCDEDIT.EXE
drwxrwxrwx 1 root root      0 2008-08-21 17:06 BitLocker
drwxrwxrwx 1 root root   4096 2008-08-21 17:06 Boot
-rwxrwxrwx 1 root root  37376 2005-07-30 01:13 BOOT.DAT
-rwxrwxrwx 1 root root 438840 2006-11-02 09:53 bootmgr
-rwxrwxrwx 1 root root  87552 2006-11-02 08:30 BootSect.exe
drwxrwxrwx 1 root root   4096 2008-12-12 19:05 D2D
-rwxrwxrwx 1 root root 888832 2007-01-18 22:12 D2D32.EXE
-rwxrwxrwx 2 root root     78 2008-08-22 09:26 DrAssign2C.ini
drwxrwxrwx 1 root root      0 2008-08-22 09:27 FACTORY
-rwxrwxrwx 1 root root   6656 2005-06-27 17:28 FATBOOT.BIN
-rwxrwxrwx 1 root root    153 2005-12-15 11:12 FmtFAT32.INI
-rwxrwxrwx 2 root root 126976 2007-01-30 01:36 HiddenStart.exe
-rwxrwxrwx 1 root root  69632 2003-10-01 06:29 int15.sys
-rwxrwxrwx 1 root root    512 2005-06-26 03:49 MBR.BIN
-rwxrwxrwx 1 root root   1359 2006-11-13 01:57 model.dat
-rwxrwxrwx 1 root root     67 2007-09-07 10:35 NAPP.DAT
-rwxrwxrwx 2 root root    329 2008-08-22 09:13 NewPartDisk.ini
-rwxrwxrwx 1 root root    232 2008-08-22 08:50 OBR3.acr
-rwxrwxrwx 1 root root     70 2005-09-12 16:20 OBR3.ini
-rwxrwxrwx 1 root root     11 2005-07-08 03:31 P1.DAT
-rwxrwxrwx 2 root root    125 2005-12-29 04:12 PARTITION.ALL
drwxrwxrwx 1 root root      0 2006-11-02 10:22 ProgramData
drwxrwxrwx 1 root root      0 2006-11-02 10:23 Program Files
-rwxrwxrwx 1 root root    215 2008-03-18 15:15 RCD.DAT
-rwxrwxrwx 2 root root    382 2005-12-19 14:54 RestoreFAT32.INI
drwxrwxrwx 1 root root  12288 2008-08-21 17:06 RYTOOLS
-rwxrwxrwx 1 root root    117 2008-05-27 06:44 SCD.DAT
drwxrwxrwx 1 root root      0 2008-08-22 09:13 sources
-rwxrwxrwx 1 root root     81 2008-05-27 07:11 SWCD.DAT
drwxrwxrwx 1 root root      0 2008-08-22 08:37 System Volume Information
-rwxrwxrwx 1 root root 131072 2005-08-24 03:02 UNICODE.BIN
drwxrwxrwx 1 root root      0 2006-11-02 10:22 Users
drwxrwxrwx 1 root root   4096 2006-11-11 10:53 Windows

```

```

ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt/sda2 && ls -l /mnt/sda2
total 2394488
drwxrwxrwx 1 root root       4096 2008-12-05 05:11 Acer
-rwxrwxrwx 1 root root         24 2006-09-18 21:43 autoexec.bat
-rwxrwxrwx 2 root root     699280 2008-03-18 13:23 bknowsetup.log
drwxrwxrwx 1 root root          0 2008-03-17 17:44 Book
drwxrwxrwx 1 root root       4096 2008-12-21 12:03 Boot
-rwxrwxrwx 1 root root     333203 2008-01-21 02:24 bootmgr
-rwxrwxrwx 1 root root       8192 2008-03-17 17:47 BOOTSECT.BAK
-rwxrwxrwx 2 root root         10 2006-09-18 21:43 config.sys
drwxrwxrwx 1 root root          0 2008-12-05 05:11 Convesoft
drwxrwxrwx 1 root root          0 2006-11-02 13:02 Documents and Settings
drwxrwxrwx 1 root root       4096 2008-03-17 17:44 DRV
drwxrwxrwx 1 root root          0 2008-03-17 18:08 Intel
-rwxrwxrwx 1 root root      40960 2005-08-16 15:49 junction.exe
-rwxrwxrwx 1 root root        512 2007-09-13 09:56 MDR.iss
drwxrwxrwx 1 root root          0 2008-03-18 10:58 MSOCache
-rwxrwxrwx 1 root root 2450776064 2009-01-19 22:15 pagefile.sys
drwxrwxrwx 1 root root          0 2008-01-21 02:32 PerfLogs
drwxrwxrwx 1 root root       4096 2008-12-26 20:30 ProgramData
drwxrwxrwx 1 root root      12288 2008-12-26 20:32 Program Files
drwxrwxrwx 1 root root       4096 2009-01-08 18:03 $RECYCLE.BIN
-rwxrwxrwx 1 root root        426 2008-03-17 18:14 RHDSetup.log
-rwxrwxrwx 1 root root         86 2008-03-18 13:23 setup.log
drwxrwxrwx 1 root root       8192 2009-01-15 16:09 System Volume Information
drwxrwxrwx 1 root root       4096 2009-01-08 18:21 Users
drwxrwxrwx 1 root root      28672 2009-01-11 12:27 Windows

```

---

### Post by caljohnsmith on 2009-01-21
Congratulations, it looks like you successfully recovered both of your lost partitions. :) Next I would run gparted again, and using the empty space after the sda2 partition, create an extended partition, and inside of the extended partition create all of your Ubuntu partitions as logical partitions. You'll need at least a main partition for Ubuntu and a swap partition, and any other partitions you might want to create inside of the extended partition is up to you. I would recommend creating at least one data partition where you can keep all your personal files, because it is a good idea I think to keep your personal files separate from your Windows/Ubuntu main partitions. Let me know how that goes or if you run into problems.

---

### Post by ErmyDermy on 2009-01-21
I successfully booted into Windows Vista! :D Thank you so much for your Help. I wouldn't have had any idea what to do! :-k

---

