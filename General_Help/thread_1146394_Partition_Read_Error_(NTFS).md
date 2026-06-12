---
title: "Partition Read Error (NTFS)"
date: 2009-05-02
forum: General Help
---

### Post by talon12311 on 2009-05-02
Hey Everyone,

I just finished a new install of Jaunty and I'm having problems accessing an old NTFS partition.  I looked through old posts for similar issues but the only ones I've found referred to mounting the partition whereas I can't even see mine.

I ran fdisk -l in the terminal and got this as my output:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14593   117217248+   5  Extended
/dev/sda5               1        1316    10568704    7  HPFS/NTFS
/dev/sda6            1317        1814     4000153+  82  Linux swap / Solaris
/dev/sda7            1815        4304    20000893+  83  Linux
/dev/sda8            4305       14593    82646361   83  Linux

To me, this seems to be saying that that sda1 (which I definitely did not deliberately create during the install; I only created /, /home, and /swap and left the NTFS partition untouched) is somehow overlapping with all of my other partitions.  I also installed GParted and it is only able to see a 111.79GB unallocated partition.  The installation partition program for both Ubuntu 8.04 and 9.04 give the same result.  The installation partition program for openSuse 11.1 gives a result similar to fdisk and can see both the sda1 partition and the other partitions.

Any thoughts?

Many thanks.:)

---

### Post by taurus on 2009-05-02
/dev/sda1 is the extended partition and all your partitions, logical, are under that extended partition.  You have on ntfs partition (/dev/sda5), one Linux swap partition (/dev/sda6), and two Linux partitions (/dev/sda7 & /dev/sda8 ).

---

### Post by talon12311 on 2009-05-02
Alright, thank you, that makes much more sense.  The question becomes then...

1. Why can I not see/access the NTFS partition?
2. Why do things like the Ubuntu install fail to recognize any operating systems on my computer and programs like GParted see only a giant unallocated file?
3. Is there any way to extract the information from the NTFS without actually mounting it and so that I could them simply reinstall over the whole drive?

Thanks,

talon

---

### Post by talon12311 on 2009-05-03
Well, I've been attempting some things on my own and this is the current state of the drive.  If I've somehow destroyed the NTFS data, well, that's disappointing but I'll live with it and learn to back-up in the future.

**fdsik -lu output:**

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   194434695   234436544    20000925   83  Linux
/dev/sda2       154432845   194434694    20000925   83  Linux
/dev/sda3       152440785   154432844      996030   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 128 MB, 128974848 bytes
6 heads, 63 sectors/track, 666 cylinders, total 251904 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x97d3030f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63      251903      125920+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(665, 5, 63) logical=(666, 2, 30)

**sfdisk -d output:**

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=194434695, size= 40001850, Id=83, bootable
/dev/sda2 : start=154432845, size= 40001850, Id=83
/dev/sda3 : start=152440785, size=  1992060, Id=82
/dev/sda4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=   251841, Id= 6, bootable
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0

---

### Post by caljohnsmith on 2009-05-03
What did you do in the time between your first post and your last post where you no longer have an NTFS partition? Depending on what you did, you might be able to still recover your original partition table (with the NTFS partition) using "testdisk". Let me know first what you did though, because maybe there's hope of recovering your NTFS partition.

John

---

### Post by talon12311 on 2009-05-05
I attempted to model a fix for a similar problem on this thread: [http://ubuntuforums.org/showthread.php?t=1138776](http://ubuntuforums.org/showthread.php?t=1138776)

The summary as I understand it is that a crafted .txt file is used to replace the old partition table using this command: 

sudo sfdisk -f --no-reread  -O ~/Desktop/OldPT.save /dev/sda < ~/Desktop/PT.txt
It creates a back-up partition table which I have stored on a flash drive.  (This largely being what gave me the courage to try; well, that and a healthy dose of frustration).

---

### Post by caljohnsmith on 2009-05-05
Using sfdisk in the manner that you did only creates a new partition table, fortunately it does not destroy any data on your drive; therefore I would recommend using testdisk to reconstruct your correct partition table. To use testdisk, how about downloading the [testdisk-6.11.1.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.11.1.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.11.1.linux26.tar.bz2
sudo testdisk-6.11/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select the correct HDD and then "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and also which of those partitions seem to be your existing partitions. We can work from there.

John

---

### Post by talon12311 on 2009-05-10
Thanks for the help and I apologise for the slow reply.

Here are the results.  All of the partitions in italics contain files.  I didn't check to see if I could see files for the "Initial Result" partition.

**Initial Result**

Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63

The harddisk (120 GB / 111 GiB) seems too small! (< 130 GB / 121 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
  Linux                13335   0  1 15824 254 61   40001848

**After Pressing Enter**

Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
     Partition               Start        End    Size in sectors
D Linux                    0   2  1  1253 254 63   20145384
[I]D HPFS - NTFS              0  32 33  1315 221 58   21137408 [My Files]
D HPFS - NTFS           1315 254 28  4303 202 59   47998976[/I]
D Linux                 1316   0  1  1324 254 62     144584
D Linux Swap            1316   1  1  1813 254 44    8000288
*D HPFS - NTFS           1316 129 30 14593  33 32  213288960 [OS]*
*D Linux                 1814   1  1  4303 254 60   40001784*
D Linux                 3046   1  1  5535 254 60   40001784
*D HPFS - NTFS           4303 235 29 14592 223 31  165292032*
D Linux                 4304   1  1 14592 254 61  165292720
D Linux Swap            9489   0  1  9612 254 43    1992040
*D Linux                 9613   0  1 12102 254 61   40001848*
*D Linux                12103   0  1 14592 254 61   40001848*
Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT3 Large file Sparse superblock, 10314 MB / 9836 MiB

The last two partitions should be my current /home and / partitions respectively.  The [My Files] partition looks to be the one with my stuff on it (plus that is the name I gave it).

Thanks again,

talon

---

### Post by talon12311 on 2009-06-02
Can anyone else pick this up?  We seem to have stalled.

talon

---

### Post by talon12311 on 2009-06-09
I would like to direct everyone to: [http://ubuntuforums.org/showthread.php?t=387922](http://ubuntuforums.org/showthread.php?t=387922)

This is a how-to that gives a simple overview of how to use testdisk to recover lost files as well as links to further resources.  It worked wonderfully for me.

talon

Edit: The info on the first post on that thread is slightly out of date.  One of the users there mentions that there is now a testdisk package in the repositories.  You can also get testdisk as caljohnsmith outlines in post #7 above.

---

