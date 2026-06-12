---
title: "New Installation: Grub error 18"
date: 2009-01-04
forum: General Help
---

### Post by gelix on 2009-01-04
I am new to Ubuntu and just installed it to a pc with an exising Windows XP os.  All went well until first reboot then Grub returned an "Error 18".  Can't get into either os except from the live session disk.  Any ideas how to fix? remember i'm a real novice ubuntu/linux user.

---

### Post by melojo on 2009-01-04
open a terminal and type
```

fdisk -l


```

post the output to give us more info

---

### Post by gelix on 2009-01-04
Results of fdisk -l

Cannot open /dev/sda
Cannot open /dev/sdb

Disk /dev/sdc: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         976     7839698    b  W95 FAT32

---

### Post by melojo on 2009-01-04
Sorry from the live cd do

```

sudo su

```
then

```

fdisk -l

```

post again

---

### Post by gelix on 2009-01-04
OK:

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f420246

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         784     6297448+  12  Compaq diagnostics
/dev/sda2   *         785       24792   192844260    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ba44b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       13654   109675723+   7  HPFS/NTFS
/dev/sdb2           13655       30401   134520277+   5  Extended
/dev/sdb5           13655       30217   133042266   83  Linux
/dev/sdb6           30218       30401     1477948+  82  Linux swap / Solaris

Disk /dev/sdc: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         976     7839698    b  W95 FAT32

---

### Post by gelix on 2009-01-04
BTW: The disk "sdc" is a memory stick with nothing by user files.

---

### Post by logos34 on 2009-01-04
you installed 8.10?

---

### Post by gelix on 2009-01-04
Yes. 8.10

---

### Post by logos34 on 2009-01-04
try rebooting without sdc connected

---

### Post by gelix on 2009-01-04
sdc?

---

### Post by gelix on 2009-01-04
unplugged the memory stick, rebooted, same "error 18"

---

### Post by caljohnsmith on 2009-01-04
I notice from your fdisk output that your Ubuntu partition starts at about 110 GB into the drive; a Grub error 18 typically occurs when you have a BIOS that can't access anything on a HDD past either 8.4 GB or 137 GB, depending on how old the BIOS is, so that might apply to you. Usually you can fix the problem by creating a ~200 MB boot partition at the front of the drive, and hence all of the Grub and Ubuntu boot files are easily accessible to the BIOS. Then when you go through the Ubuntu installer, simply set the mount point on the new boot partition as "/boot", and that should hopefully solve the Grub error 18 problem if all goes well. How about giving that a shot and let us know how it goes.

---

### Post by gelix on 2009-01-04
What you say makes sense.  If only I knew how to do what you're suggesting:
a, how do I create a 200mb partition at the front of the drive, and 
b, I don't recall in the Ubuntu installer where I'd specify the mount point as "/boot".
Thanks.

---

### Post by caljohnsmith on 2009-01-04
> **gelix said:**
> What you say makes sense.  If only I knew how to do what you're suggesting:
a, how do I create a 200mb partition at the front of the drive, and 
b, I don't recall in the Ubuntu installer where I'd specify the mount point as "/boot".
Thanks.
What is in your sdb1 NTFS partition? Is that just for data or does it have Windows? Also please post the output of:
```
sudo sfdisk -VluS
```

---

### Post by gelix on 2009-01-04
The first partition is Windows XP and windows type applications.  All important document and user files are on a USB external drive.  Partition 2 is Ubuntu.

sudo sfdisk -VluS

Disk /dev/sda: 24792 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1            63  12594959   12594897  12  Compaq diagnostics
/dev/sda2   *  12594960 398283479  385688520   7  HPFS/NTFS
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda: OK

Disk /dev/sdb: 30401 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1            63 219351509  219351447   7  HPFS/NTFS
/dev/sdb2     219351510 488392064  269040555   5  Extended
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty
/dev/sdb5     219351573 485436104  266084532  83  Linux
/dev/sdb6     485436168 488392064    2955897  82  Linux swap / Solaris
Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK

---

### Post by caljohnsmith on 2009-01-04
What about your sda2 NTFS partition then? That's the partition marked as bootable, so I would think that is your Windows installation. How about posting the output of: 
```
sudo mkdir /mnt/sda2 /mnt/sdb1
sudo mount /dev/sda2 /mnt/sda2
sudo mount /dev/sdb1 /mnt/sdb1
ls -l /mnt/sda2 /mnt/sdb1
```

---

### Post by gelix on 2009-01-04
sudo mkdir /mnt/sda2 /mnt/sdb1
root@ubuntu:/home/ubuntu# sudo mount /dev/sda2 /mnt/sda2
root@ubuntu:/home/ubuntu# sudo mount /dev/sdb1 mnt/sdb1
fuse: failed to access mountpoint mnt/sdb1: No such file or directory
root@ubuntu:/home/ubuntu# ls- l /mnt/sda2 /mnt/sdb1
bash: ls-: command not found
root@ubuntu:/home/ubuntu# ls -l mnt/sda2 /mnt/sdb1
ls: cannot access mnt/sda2: No such file or directory
/mnt/sdb1:
total 0

---

### Post by caljohnsmith on 2009-01-04
Can you maybe copy and paste the lines from my post? You have a couple of typos in the commands you did.

---

### Post by gelix on 2009-01-04
Here's what I get with a copy of your post pasted to terminal.

sudo mkdir /mnt/sda2 /mnt/sdb1
mkdir: cannot create directory `/mnt/sda2': File exists
mkdir: cannot create directory `/mnt/sdb1': File exists
root@ubuntu:/home/ubuntu# sudo mount /dev/sda2 /mnt/sda2
fuse: mount failed: Device or resource busy
root@ubuntu:/home/ubuntu# sudo mount /dev/sdb1 /mnt/sdb1
root@ubuntu:/home/ubuntu# ls- l /mnt/sda2 /mnt/sdb1
bash: ls-: command not found
root@ubuntu:/home/ubuntu#

---

### Post by caljohnsmith on 2009-01-04
I apologize, that last command was my typo, not yours. While you still have the partitions mounted, please post:
```
ls -l /mnt/sda2 /mnt/sdb1
```

---

### Post by gelix on 2009-01-04
root@ubuntu:/home/ubuntu# ls -l /mnt/sda2 /mnt/sdb1
/mnt/sda2:
total 1291243
-rwxrwxrwx 1 root root         0 2004-09-02 01:43 AUTOEXEC.BAT
drwxrwxrwx 1 root root         0 2006-11-18 02:31 b3a6a0d62646e2b1bffdf396
-rwxrwxrwx 1 root root       211 2008-12-10 19:30 boot.ini
-rwxrwxrwx 2 root root      7574 2006-05-14 00:47 caavsetup.log
-rwxrwxrwx 2 root root     36270 2008-01-26 01:41 caavsetupLog.txt
-rwxrwxrwx 1 root root    974548 2008-10-14 21:12 caisslog.txt
drwxrwxrwx 1 root root     16384 2008-01-25 01:16 Click to DVD 2
drwxrwxrwx 1 root root      4096 2008-12-19 20:58 Config.msi
-rwxrwxrwx 1 root root         0 2008-12-10 19:30 config.sys
drwxrwxrwx 1 root root      4096 2005-04-24 16:01 Documents and Settings
-rwxrwxrwx 1 root root        81 2007-04-18 00:19 DVDPATH.TXT
drwxrwxrwx 1 root root         0 2004-12-14 01:23 EPSONREG
-rwxrwxrwx 2 root root        80 2006-05-26 02:23 FilterLog.log
drwxrwxrwx 1 root root     32768 2007-01-07 17:13 Giga Pocket V5
-rwxrwxrwx 1 root root 527880192 2009-01-05 02:55 hiberfil.sys
-rwxrwxrwx 1 root root       246 2008-12-05 19:09 INSTALL.LOG
-rwxrwxrwx 1 root root         0 2004-09-02 01:43 IO.SYS
-rwxrwxrwx 1 root root       244 2005-01-27 03:28 IPH.PH
-rwxrwxrwx 2 root root         0 2004-12-16 03:07 itouch_config_crash_info.txt
-rwxrwxrwx 2 root root         0 2004-12-16 02:50 itouch_crash_info.txt
-rwxrwxrwx 1 root root         0 2004-09-02 01:43 MSDOS.SYS
drwxrwxrwx 1 root root      4096 2007-02-18 20:12 MyWorks
-rwxrwxrwx 2 root root       571 2008-10-14 20:19 NTDClient.log
-rwxrwxrwx 1 root root     47564 2004-08-04 12:00 NTDETECT.COM
-rwxrwxrwx 1 root root    250048 2008-10-22 21:40 ntldr
-rwxrwxrwx 1 root root 792723456 2009-01-05 02:55 pagefile.sys
drwxrwxrwx 1 root root     36864 2008-12-19 20:56 Program Files
drwxrwxrwx 1 root root      4096 2004-11-30 01:20 RECYCLER
-rwxrwxrwx 2 root root        92 2006-01-02 21:48 ResumeOmgApDeliveryMgrCntrl_SonicStage_EmdDownloadObj.dmf
-rwxrwxrwx 1 root root     12614 2009-01-05 03:05 rollback.ini
drwxrwxrwx 1 root root         0 2005-09-02 02:18 SixSigma
drwxrwxrwx 1 root root         0 2008-01-28 01:26 SonySupport
drwxrwxrwx 1 root root      4096 2004-11-30 00:21 System Volume Information
-rwxrwxrwx 1 root root      1248 2004-12-19 18:11 twacker.log
drwxrwxrwx 1 root root      4096 2008-12-17 22:53 ubuntu
drwxrwxrwx 1 root root         0 2008-12-10 19:30 ubuntu-backup
drwxrwxrwx 1 root root      4096 2008-11-14 01:54 Video
drwxrwxrwx 1 root root    163840 2008-12-20 00:55 WINDOWS

/mnt/sdb1:
total 725056
-rwxrwxrwx 2 root root    748544 2007-03-13 15:36 $0 Paperwork.ppt
-rwxrwxrwx 2 root root     58070 2007-08-28 19:00 1-2-3 Model for Successful Six Sigma Project Selection.pdf
drwxrwxrwx 1 root root      4096 2008-02-24 03:12 2003 Tax
drwxrwxrwx 1 root root      4096 2008-02-24 03:12 2004 Tax
drwxrwxrwx 1 root root         0 2008-12-19 13:35 2008 Tax
-rwxrwxrwx 2 root root   6857216 2006-03-13 10:36 3_1_06_Champion_training-2006Mar01.ppt
-rwxrwxrwx 2 root root     33813 2007-05-02 19:01 38 Ways to Win an Argument.pdf
-rwxrwxrwx 2 root root     17915 2006-03-10 22:36 512compflashcrd.pdf
-rwxrwxrwx 2 root root    149504 2007-02-27 22:39 7016-Lean_Six_Sigma_Project_Charter-2006May12.doc
-rwxrwxrwx 2 root root   1659504 2005-10-23 22:30 A12423063007.pdf
-rwxrwxrwx 2 root root    806806 2005-10-23 22:28 A12523062826.pdf
-rwxrwxrwx 2 root root    988574 2005-10-23 22:32 A12523063232.pdf
-rwxrwxrwx 2 root root     46592 2007-04-06 20:16 Agenda 070410.doc
-rwxrwxrwx 2 root root     26112 2006-01-11 13:48 Air Force Improving Production with Smart Operations 21.doc
-rwxrwxrwx 1 root root       136 2007-10-30 21:16 Alexa.url
-rwxrwxrwx 2 root root     38635 2006-11-30 17:04 Appraisal 061130.pdf
-rwxrwxrwx 2 root root   1293232 2005-11-22 04:17 apriljune2003cookrep.pdf
-rwxrwxrwx 2 root root     23006 2005-12-29 02:23 Behind the smiles, trans-Atlantic bile.pdf
-rwxrwxrwx 2 root root    130560 2006-12-04 16:03 benefits election.doc
drwxrwxrwx 1 root root      4096 2008-12-17 04:50 billy
drwxrwxrwx 1 root root     12288 2008-11-18 01:58 bin
-rwxrwxrwx 2 root root    130256 2007-04-26 12:58 Bio Henry Lixfield.pdf
-rwxrwxrwx 2 root root      3925 2005-11-11 18:04 bk_download (1).csv
-rwxrwxrwx 2 root root      5190 2005-12-28 13:47 bk_download (2).csv
-rwxrwxrwx 2 root root      2243 2005-11-01 18:43 bk_download.csv
drwxrwxrwx 1 root root      4096 2008-02-24 03:13 Bobby
-rwxrwxrwx 2 root root 480211257 2007-01-07 17:13 Bobby_wrestle.zip
-rwxrwxrwx 1 root root     64877 2008-04-04 16:58 bookmark.htm
drwxrwxrwx 1 root root         0 2008-04-08 20:12 Bridger
drwxrwxrwx 1 root root         0 2008-02-24 03:13 Budget
drwxrwxrwx 1 root root      8192 2008-11-06 19:40 CA
-rwxrwxrwx 2 root root     11056 2008-03-07 15:16 ca best practices.pdf
drwxrwxrwx 1 root root      4096 2008-04-08 20:12 CA docs
-rwxrwxrwx 2 root root   1748355 2008-01-25 15:25 ca_gis_propa.pdf
-rwxrwxrwx 1 root root    193987 2005-08-26 15:31 CAhrR80.csv
drwxrwxrwx 1 root root         0 2008-01-26 01:37 CA iss
-rwxrwxrwx 2 root root   6950912 2008-03-02 12:27 CA Jumpstart to Six Sigma.ppt
-rwxrwxrwx 2 root root     45270 2006-06-14 21:25 canet.ca.com.mdi
-rwxrwxrwx 2 root root   1018880 2007-06-05 16:50 CAO BOD Update 061207 Investments Only v7.ppt
drwxrwxrwx 1 root root      4096 2008-02-24 03:14 CA templates
-rwxrwxrwx 2 root root     23720 2007-10-30 21:11 Catrina 10K.pdf
drwxrwxrwx 1 root root      4096 2008-11-10 01:26 CAWorld
-rwxrwxrwx 2 root root   1274368 2007-03-13 15:14 CFIT Delivery Exec Summary 2007-2-22.ppt
-rwxrwxrwx 2 root root    509357 2004-11-11 22:23 Christening.jpg
-rwxrwxrwx 2 root root     37412 2008-01-18 14:30 Circuit City Receipt  Confirmation for Order 4440-217799.htm
drwxrwxrwx 1 root root     12288 2008-04-08 20:12 Class materials
-rwxrwxrwx 2 root root    106496 2006-10-03 21:33 contacts0804.mdb
-rwxrwxrwx 2 root root    340876 2005-10-31 19:21 contacts0804.txt
-rwxrwxrwx 2 root root    106496 2006-10-03 21:33 contacts0804.txt.mdb
-rwxrwxrwx 2 root root    919040 2005-10-22 16:53 contacts0804.xls
drwxrwxrwx 1 root root      4096 2008-04-08 20:16 Conversations
-rwxrwxrwx 2 root root     40448 2008-04-07 17:59 Copy of Hoshin Template.XLS
-rwxrwxrwx 2 root root     17920 2007-10-16 12:17 CTBO Reporting Template.xls
-rwxrwxrwx 2 root root     26112 2008-03-18 20:21 CTBO Team - Reengineering Opportunities v2 gelgbs.xls
drwxrwxrwx 1 root root         0 2008-02-24 03:17 Cyberlink
-rwxrwxrwx 2 root root     17920 2007-11-08 23:00 cycle time file.xls
-rwxrwxrwx 2 root root    568320 2007-05-01 19:15 DD_Quality_REV.doc
-rwxrwxrwx 2 root root     19968 2008-03-07 18:51 Deliverables to John.doc
-rwxrwxrwx 2 root root     48128 2005-12-27 18:58 Dissertation Checklist.doc
drwxrwxrwx 1 root root      4096 2008-11-12 00:24 DNB Artifacts
-rwxrwxrwx 1 root root     61952 2005-12-08 07:53 drawing.vsd
-rwxrwxrwx 2 root root    229519 2005-12-29 15:50 Dymphna maps.pdf
drwxrwxrwx 1 root root     24576 2008-02-24 03:17 Ed
-rwxrwxrwx 2 root root   3898368 2006-05-18 19:15 Einstein on Six Sigma Poke Yoke.ppt
-rwxrwxrwx 2 root root    393216 2007-05-08 21:56 ELT pres.ppt
-rwxrwxrwx 2 root root     37376 2005-11-04 20:26 email error.ppt
-rwxrwxrwx 2 root root     68433 2006-10-17 14:50 Emperor of Math.pdf
-rwxrwxrwx 2 root root     68192 2007-08-28 19:09 Excel_Keyboard_Shortcuts.pdf
-rwxrwxrwx 2 root root   2783810 2006-10-29 02:54 fastrockclimb.wmv
-rwxrwxrwx 2 root root    233508 2005-09-28 17:07 Ferrer & Spellman.pdf
-rwxrwxrwx 2 root root     24576 2005-10-12 16:46 FMEA Form.xls
-rwxrwxrwx 2 root root   1267688 2006-12-05 22:59 fotbal kid.wmv
-rwxrwxrwx 2 root root     30934 2008-01-18 15:34 Full page fax print.pdf
-rwxrwxrwx 2 root root    578048 2007-08-08 17:54 FY 07 Enterprise Product Scorecard Criteria and Metrics August 07.ppt
-rwxrwxrwx 2 root root    306176 2007-05-25 12:44 FY 07 Enterprise Product Scorecard Q1 May 07 v5.xls
-rwxrwxrwx 2 root root    303616 2007-08-08 17:57 FY 07 Enterprise Product Scorecard Q2 July 07 v3a.xls
-rwxrwxrwx 2 root root    213623 2007-11-20 15:05 Gartner BPM Magic Quadrant 2007.pdf
-rwxrwxrwx 2 root root   1827840 2007-11-15 14:12 GB Examples.ppt
-rwxrwxrwx 2 root root    119808 2008-04-01 20:57 George Lixfield Interview Schedule 3 (4-08).doc
-rwxrwxrwx 2 root root   2426514 2006-03-09 18:14 GermanCoastGuard.zip
drwxrwxrwx 1 root root      4096 2008-04-08 20:16 Hammer audit
-rwxrwxrwx 2 root root     18430 2007-05-22 14:17 hammer execsum.pdf
-rwxrwxrwx 2 root root     37888 2006-01-11 13:52 Hayes Lemmerz Realigns its Wheel Groups and Appoints Fred Bentley as Chief Operating Officer and President of its Global Wheel Group.doc
-rwxrwxrwx 2 root root    410624 2007-05-23 00:22 High level processes.ppt
-rwxrwxrwx 1 root root     10898 2007-10-10 20:45 hold.pdf
-rwxrwxrwx 2 root root     21504 2005-11-04 15:20 hong kong.doc
drwxrwxrwx 1 root root      4096 2008-04-08 20:16 Hoshin
-rwxrwxrwx 2 root root     14848 2007-10-03 22:02 hotel break point.xls
-rwxrwxrwx 2 root root     33881 2007-08-28 18:57 How To Select A Six Sigma Quality Improvement Project.pdf
-rwxrwxrwx 2 root root     52824 2005-10-04 12:53 http___qms.ca.pdf
-rwxrwxrwx 2 root root    173189 2006-04-21 00:29 hyderabad history.pdf
-rwxrwxrwx 2 root root     13712 2007-10-05 15:41 IBM Green Sigma.pdf
-rwxrwxrwx 2 root root     28427 2006-09-01 14:04 industrious bacteria.pdf
-rwxrwxrwx 2 root root     72445 2006-04-28 13:13 International Dialing Codes.pdf
-rwxrwxrwx 1 root root      2238 2004-09-30 22:35 iogear.ico
-rwxrwxrwx 1 root root     36352 2005-11-04 15:43 Janet.doc
drwxrwxrwx 1 root root      4096 2008-04-08 20:16 job descriptions
-rwxrwxrwx 2 root root     34816 2008-03-07 17:53 Job Overview for TE.doc
-rwxrwxrwx 2 root root   4154880 2007-10-19 17:33 Kaizen Sales Contract Process 10-19.ppt
-rwxrwxrwx 2 root root    231424 2007-11-01 14:59 Kaizen Update 11-1.ppt
-rwxrwxrwx 2 root root    233984 2007-11-08 13:28 Kaizen Update 11-8.ppt
-rwxrwxrwx 1 root root    981982 2006-12-09 12:40 karate1.wmv
-rwxrwxrwx 2 root root     32427 2006-01-04 15:56 Leadership drives customer focus.pdf
-rwxrwxrwx 2 root root     47826 2008-04-04 17:18 license renewal.pdf
-rwxrwxrwx 2 root root     24413 2007-10-13 02:14 Lixfield 1880 census.pdf
-rwxrwxrwx 2 root root    181843 2006-03-30 22:22 Mimio-600-0035-Xi-5500MI10.pdf
-rwxrwxrwx 2 root root   1650431 2007-02-08 23:44 mistake proofing six sigma.pdf
-rwxrwxrwx 2 root root     27828 2007-02-20 19:53 More Julian Beever Art.htm
-rwxrwxrwx 1 root root 178697216 2007-11-13 14:25 movie.avi
-rwxrwxrwx 2 root root     48722 2006-09-24 16:23 MS-DOS subst command help.pdf
-rwxrwxrwx 2 root root   1201051 2007-10-18 21:28 MtWashington.PDF
drwxrwxrwx 1 root root      4096 2008-02-24 03:17 My Digital Editions
drwxrwxrwx 1 root root      4096 2008-02-24 03:17 My eBooks
drwxrwxrwx 1 root root      4096 2008-02-24 03:17 My Google Gadgets
drwxrwxrwx 1 root root     57344 2008-12-04 21:21 My Music
drwxrwxrwx 1 root root     77824 2008-12-07 22:16 My Pictures
drwxrwxrwx 1 root root         0 2008-02-24 03:54 My Received Files
drwxrwxrwx 1 root root         0 2008-02-24 03:54 My Shapes
drwxrwxrwx 1 root root      4096 2008-11-12 00:20 My Videos
drwxrwxrwx 1 root root      4096 2008-02-24 03:54 My Zinio Library
-rwxrwxrwx 2 root root    816778 2005-11-22 04:13 NEOC_Times.pdf
drwxrwxrwx 1 root root         0 2008-02-24 03:54 NewsStand
-rwxrwxrwx 2 root root    172544 2006-04-03 15:19 One share one vote NYT.doc
-rwxrwxrwx 2 root root     36993 2006-04-03 15:19 One share one vote NYT.pdf
-rwxrwxrwx 2 root root     28034 2006-04-03 15:16 One Share, One Vote_ One Big Test - New York Times.pdf
-rwxrwxrwx 2 root root    113298 2005-09-14 18:20 opera6.txt.txt
-rwxrwxrwx 2 root root     83456 2007-05-23 11:45 Operational Strategic Assessment Status 05242007 v2a.ppt
-rwxrwxrwx 2 root root    468480 2007-05-22 17:17 Opportunity LifeCycle.ppt
drwxrwxrwx 1 root root     16384 2009-01-04 05:22 Other
-rwxrwxrwx 2 root root     28160 2007-11-08 22:30 our input to Bryant report.doc
-rwxrwxrwx 2 root root    385024 2007-03-26 19:10 Overall criteria 070326.ppt
drwxrwxrwx 1 root root         0 2008-01-26 01:10 Partitions
drwxrwxrwx 1 root root     24576 2008-12-19 13:36 Personal
-rwxrwxrwx 1 root root       443 2005-11-10 22:51 phones.txt
-rwxrwxrwx 1 root root        77 2006-05-15 01:48 Picasa.ini
-rwxrwxrwx 2 root root       194 2005-10-31 23:44 play (1).pls
-rwxrwxrwx 1 root root       186 2005-10-31 23:41 play.pls
-rwxrwxrwx 2 root root   1765376 2005-08-30 20:37 Policy Deployment Training.ppt
-rwxrwxrwx 2 root root   3431770 2005-11-22 04:11 POP Vol2 Issue1.pdf
drwxrwxrwx 1 root root      4096 2008-02-24 03:54 Procedures
-rwxrwxrwx 2 root root    616763 2008-02-20 19:31 Process Audit Hammer.doc
-rwxrwxrwx 2 root root     54272 2007-02-16 16:10 Process Engineer Worldwide Excellence and Quality Job Description.doc
-rwxrwxrwx 2 root root    752128 2005-09-21 13:24 Process Mapping.ppt
drwxrwxrwx 1 root root      4096 2008-02-24 03:54 processmodel
drwxrwxrwx 1 root root     12288 2008-04-08 20:28 Projects
-rwxrwxrwx 2 root root    254976 2006-08-02 19:50 Project_Template_Rev_5.xls
-rwxrwxrwx 2 root root     24064 2006-01-11 17:41 quotes on change.doc
-rwxrwxrwx 2 root root       321 2008-02-21 18:20 Racquetball league final update.txt
-rwxrwxrwx 2 root root     97871 2006-03-13 10:29 RCA-Qualification Mtg-2006Mar03.jpg
-rwxrwxrwx 2 root root       621 2008-03-24 19:49 RCA Small Wonder.lnk
drwxrwxrwx 1 root root         0 2008-02-24 03:55 receipts
drwxrwxrwx 1 root root         0 2008-10-12 19:29 RECYCLER
drwxrwxrwx 1 root root      8192 2008-02-24 03:55 Reports
drwxrwxrwx 1 root root    110592 2008-04-08 20:28 Resources
drwxrwxrwx 1 root root      4096 2008-11-06 19:41 Resume
-rwxrwxrwx 2 root root   3419820 2006-07-27 12:31 Resurgence from Scandal.pdf
-rwxrwxrwx 2 root root     19968 2005-11-04 14:47 rich stone.doc
-rwxrwxrwx 2 root root     22102 2008-04-01 00:57 RMV .pdf
-rwxrwxrwx 2 root root     31770 2007-04-12 21:04 running a lean learning function.pdf
drwxrwxrwx 1 root root         0 2008-02-24 05:02 salary nego
-rwxrwxrwx 2 root root    433152 2007-08-08 19:29 Sales Accounting Quote Process Redesign v4.xls
-rwxrwxrwx 2 root root    528384 2007-11-07 16:48 Savings 11_07_2007.ppt
drwxrwxrwx 1 root root         0 2008-02-24 05:02 Scouting
-rwxrwxrwx 2 root root     22069 2006-03-27 15:09 search and unintended consequences.pdf
-rwxrwxrwx 2 root root     36342 2005-07-21 13:01 Signature.bmp
drwxrwxrwx 1 root root     86016 2008-11-12 18:22 SixSigma
-rwxrwxrwx 2 root root     52720 2005-10-23 21:43 Six Sigma - A Critical Perspective.pdf
-rwxrwxrwx 2 root root     19968 2005-08-26 17:02 Six Sigma.doc
-rwxrwxrwx 2 root root     86318 2007-08-28 18:56 Six Sigma Project Selection- Don't Follow – Ready, Fire, Aim.pdf
-rwxrwxrwx 2 root root    190976 2008-01-16 21:43 SixSigmaQuotationProcess.xls
-rwxrwxrwx 2 root root     49152 2005-10-04 19:48 Six Sigma Tools for Green Belts.doc
-rwxrwxrwx 2 root root     20480 2005-10-28 15:38 Six Sigma Training Welcome.doc
-rwxrwxrwx 1 root root    192000 2006-09-13 18:41 SLAs.ppt
-rwxrwxrwx 2 root root     64593 2006-09-14 17:12 software and quality.pdf
drwxrwxrwx 1 root root      4096 2008-02-24 05:02 Speaking
-rwxrwxrwx 2 root root     14336 2007-02-08 17:40 SSA Cost Estimates.xls
drwxrwxrwx 1 root root         0 2008-04-08 20:29 staff
-rwxrwxrwx 2 root root     26624 2007-12-26 18:46 Statistics.doc
drwxrwxrwx 1 root root         0 2008-04-08 20:29 survey
-rwxrwxrwx 2 root root   4912640 2008-02-04 20:01 Survey_Job_Descriptions-2007Aug22.xls
-rwxrwxrwx 2 root root   1129472 2007-10-17 13:07 Survey Tollgate-2.ppt
-rwxrwxrwx 2 root root     62001 2006-09-14 17:13 sw QFD.pdf
-rwxrwxrwx 1 root root       319 2008-01-03 17:54 SWWATER.INI
drwxrwxrwx 1 root root      4096 2008-01-25 22:16 System Volume Information
drwxrwxrwx 1 root root      4096 2008-02-24 05:02 Team Materials
-rwxrwxrwx 2 root root     68419 2008-01-16 21:03 technology & team effectiveness.pdf
drwxrwxrwx 1 root root         0 2008-11-14 01:36 Temp Card Contents
-rwxrwxrwx 1 root root     12901 2008-04-01 23:24 T&E.pdf
-rwxrwxrwx 2 root root     65450 2005-11-18 19:44 time to develop Survey.pdf
-rwxrwxrwx 2 root root    160768 2008-03-17 19:26 Tuition Approval.ppt
drwxrwxrwx 1 root root         0 2008-12-05 16:16 ubuntu-backup
-rwxrwxrwx 1 root root    306392 2006-02-13 03:04 UC.pdf
drwxrwxrwx 1 root root         0 2008-04-08 20:29 Updater5
-rwxrwxrwx 2 root root     44032 2006-01-11 13:35 value stream or process map.doc
-rwxrwxrwx 2 root root    288256 2006-09-19 14:52 VIP throughput report.xls
-rwxrwxrwx 2 root root   2055068 2007-01-06 05:37 Warranty and Customer Support.pdf
drwxrwxrwx 1 root root         0 2008-04-08 20:29 WebEx
-rwxrwxrwx 2 root root    128781 2007-09-20 13:32 Wiesbaden bei nacht.jpg
-rwxrwxrwx 2 root root   2196992 2008-03-07 16:21 WIP CTBO Overview_v0 10gl.ppt
-rwxrwxrwx 2 root root   2385920 2008-03-10 18:50 WIP CTBO Overview_v0 15 2 GeL.ppt
-rwxrwxrwx 2 root root   2279424 2008-03-07 18:49 WIP CTBO Overview_v0 15.ppt
-rwxrwxrwx 2 root root    298929 2006-02-13 03:31 W_Lixfield.pdf
-rwxrwxrwx 1 root root       162 2005-09-14 13:11 ~$words4.doc
-rwxrwxrwx 1 root root    131072 2008-02-20 18:27 words4.doc
-rwxrwxrwx 1 root root     91236 2007-04-05 14:57 words4.pdf

---

### Post by caljohnsmith on 2009-01-04
OK, as I suspected your Windows is actually on sda2 and not sdb1; that's good news because you should be able to use the Ubuntu partition editor gparted (System > Admin > Partition Editor) to shrink your sdb1 partition from the beginning and make ~200 MB of space for your new boot partition. Once you've shrunk sdb1 to make that space, simply create a new ~200 MB primary ext3 partition with gparted using that space for your boot partition. How about trying that first and let me know how it goes, and we can work from there.

---

### Post by gelix on 2009-01-04
OK.  I opened the partition editor and the first partition "dev/sdb1"is 104gb with 77gb in use.  What you are suggesting is that I shrink that partition, and create another partition of ~200mb as a boot partition.  That I understand.  The part I don't understand is the "a new ~200 MB primary ext3 partition with gparted for your boot partition".  How do I make it a 'primary ext3 partition' and how do I make it a boot partition.
BTW, I really appreciate the time and help.

---

### Post by gelix on 2009-01-04
do I have to unmount the drive before I can resize it?
  Right now the menu commands to resize are grayed out.

---

### Post by caljohnsmith on 2009-01-04
Make sure you shrink sdb1 from the front of the partition, not at the end; also, first right-click the swap partition and select "swapoff", and also make sure to unmount all your other partitions. You can do that in the command line by doing:
```
cd / && sudo umount -a
```
Then use gparted to create a primary partition with the space you create by shrinking sdb1, and have gparted format it to ext3. You won't need to set the mount point as /boot until you go through the Ubuntu installer, so don't worry about that yet. Let me know how it goes.

---

### Post by gelix on 2009-01-04
I have shrunk sdb1 and created a new primary ext3 partition at the front of 211mb.

---

### Post by caljohnsmith on 2009-01-04
> **gelix said:**
> I have shrunk sdb1 and created a new primary ext3 partition at the front of 211mb.
Great, just to check that it went OK, please post:
```
sudo fdisk -lu

```

---

### Post by gelix on 2009-01-04
sudo fdisk -lu

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0f420246

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1          417690    12562829     6072570   12  Compaq diagnostics
/dev/sda2   *    12594960   398283479   192844260    7  HPFS/NTFS
/dev/sda3              63      417689      208813+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ba44b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   219351509   109675723+   7  HPFS/NTFS
/dev/sdb2       219351510   488392064   134520277+   5  Extended
/dev/sdb5       219351573   485436104   133042266   83  Linux
/dev/sdb6       485436168   488392064     1477948+  82  Linux swap / Solaris

Disk /dev/sdc: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              44    15679439     7839698    b  W95 FAT32
root@ubuntu:/#

---

### Post by Xiangxianni on 2009-01-04
> **gelix said:**
> I am new to Ubuntu and just installed it to a pc with an exising Windows XP os.  All went well until first reboot then Grub returned an "Error 18".  Can't get into either os except from the live session disk.  Any ideas how to fix? remember i'm a real novice ubuntu/linux user.

[http://www.tips5.com/how-to-retore-grub-after-reinstall-your-windows](http://www.tips5.com/how-to-retore-grub-after-reinstall-your-windows)

Or you can use your Windows install cd to fix your disk mbr using command "fixmbr" or "fixboot",I cann't remember the exact command

---

### Post by caljohnsmith on 2009-01-04
According to fdisk, it looks like you shrunk your sda2 partition from the end and added the new 200 MB partition at the end of your sda drive. You need the boot partition on your sdb drive though. When you pull up gparted, be sure to select the /dev/sdb drive in the drop down menu near the upper right corner of the screen. Then try to shrink sdb1 from the beginning, and create a 200 MB partition with that space. Also, I should mention that it would be a good idea to make sure you have everything important backed up before doing any partition changes.

---

### Post by gelix on 2009-01-04
hi.  My screen locked up and I had to reboot.  Now I can't see sdb drive as an alternative in the partition editor.  Is there a command I need to rerun in terminal so it shows?

---

### Post by caljohnsmith on 2009-01-04
If you do:
```
sudo fdisk -lu
```
Does it show the sdb drive? If so, I'm not sure why gparted wouldn't see it.

---

### Post by rushikesh988 on 2009-01-04
this may occur due to unsafe shutdown of ur windows Xp  ... START Xp and then shut down it safely I hope ur problem will get solved

---

### Post by gelix on 2009-01-04
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0f420246

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    12145202     6072570   12  Compaq diagnostics
Partition 1 does not end on cylinder boundary.
/dev/sda2   *    12594960   398283479   192844260    7  HPFS/NTFS

Disk /dev/sdf: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              44    15679439     7839698    b  W95 FAT32

---

### Post by gelix on 2009-01-04
There was a second usb external drive still plugged in which I unplugged when the system crashed.

---

### Post by caljohnsmith on 2009-01-04
For some reason your sdb drive is not even being detected by Ubuntu. How about rebooting again, but if the sdb drive is external, switch it off and back on before rebooting, and run the fdisk command again to see if the sdb drive shows up. If not, it sounds like you might have a hardware issue.

---

### Post by gelix on 2009-01-04
OK will do as you suggest.

---

