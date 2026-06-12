---
title: "GRUB Error 17 After TestDisk"
date: 2009-04-17
forum: General Help
---

### Post by dz_alias on 2009-04-17
Mmk so it goes like this. My Windows XP OS got attacked by a nasty virus (Win32:Vitro). So I emailed Dell to send me a copy of my OS so I can restore it. In the meantime, I decided to install Ubuntu because I used it briefly once before and liked it. For some reason when I installed Ubuntu it was unable to keep my original partitions. So I created a partition at the end of my HDD of approx. 5 gigabytes, essentially overwriting the one there previously (Dell Restore or something). This left my main partition untouched (although still officially absent from the partition table.) The OS worked perfectly fine, and I spent a decent amount of time customizing this and that to suit my needs. Eventually I installed TestDisk to salvage my old main partition (for the purpose of backing up files), however I accidentally revived the Dell partations before and after my main one, so my Linux partition no longer exists (or at least isn't recognized.) Well I'm now using the LiveCD and reinstalled TestDisk, however whenever I do a deep scan and try to recover my Linux partition, I get an error...

[IMG]http://img16.imageshack.us/img16/4324/helpzme.jpg[/IMG]

I'm sort of a nubcake. I really love Ubunutu though! It's great! I like how involved you have to be with the OS to get things working.

I'm assuming I have to change the parameters in TestDisk concerning my HDD, but I'd rather have some guidance.

---

### Post by zvacet on 2009-04-18
Maybe [this]("http://users.bigpond.net.au/hermanzone/p15.htm#17") will be helpful.

---

### Post by dz_alias on 2009-04-18
> **zvacet said:**
> Maybe [this]("http://users.bigpond.net.au/hermanzone/p15.htm#17") will be helpful.

First I need to revive my Linux partition, but I can't. Once I do that, I'll set it as my bootable partition, as it was before. I just don't know how to fix the error in TestDisk that tells me it can't restore the Linux partition because there's not enough room on my HDD...

---

### Post by dz_alias on 2009-04-18
I didn't want to have to resort to this, but...

... sum1 plz help me liek noaw lololol!!!1111eleven11111two111!!11!

I probably should've labeled my thread differently, since my problem deals with TestDisk, really. And I should've been more brief in my initial post.

Regardless. I needz ur 1337ness lawlz.

---

### Post by meierfra. on 2009-04-18
Could you post the results of the deep search?  (that is the screen after you clicked "continue" at the screen you already posted)
Just use copy and paste (no need to take a screen shot)

Could you also post the output of

```
sudo fdisk -lu
sudo sfdisk -d
```

---

### Post by dz_alias on 2009-04-18
> **meierfra. said:**
> Could you post the results of the deep search?  (that is the screen after you clicked "continue" at the screen you already posted)
Just use copy and paste (no need to take a screen shot)

Could you also post the output of

```
sudo fdisk -lu
sudo sfdisk -d
```

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeb275b50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63       80324       40131    6  FAT16
/dev/sda2           80325   302552144   151235910    7  HPFS/NTFS
/dev/sda3       302552145   312496379     4972117+   c  W95 FAT32 (LBA)

```

```

ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=    80262, Id= 6, bootable
/dev/sda2 : start=    80325, size=302471820, Id= 7
/dev/sda3 : start=302552145, size=  9944235, Id= c
/dev/sda4 : start=        0, size=        0, Id= 0

```

What're the commands to download/extract/install/run testdisk? I forgot.

---

### Post by meierfra. on 2009-04-18
> What're the commands to download/extract/install/run testdisk? I forgot. 
Enable the universe repositories.
Then

```
sudo apt-get install testdisk
sudo testdisk /dev/sda 
```

---

### Post by drs305 on 2009-04-18
> **dz_alias said:**
> 
What're the commands to download/extract/install/run testdisk? I forgot.

*Testdisk* is in the universe repository. If you have that enabled:
```

sudo apt-get install testdisk

```

---

### Post by dz_alias on 2009-04-18
> **drs305 said:**
> *Testdisk* is in the universe repository. If you have that enabled:
```

sudo apt-get install testdisk

```

I figured it out! I'm deeper searching now.

---

### Post by dz_alias on 2009-04-18
```

TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 160 GB / 149 GiB - CHS 19452 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1     4 254 63      80262 [DellUtility]
P HPFS - NTFS              5   0  1 18832 254 63  302471820
D FAT32 LBA            18833   0  1 19451 254 63    9944235 [DellRestore]
D Linux                18844   0  1 19451 254 63    9767520









Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT16, 41 MB / 39 MiB

```

If it helps, here's the info about my HDD:
```

Select a media (use Arrow keys, then press Enter):
Disk /dev/sda - 160 GB / 149 GiB - ATA ST3160828AS

```

---

### Post by meierfra. on 2009-04-18
So testdisk  did find your Ubuntu partition.

Select the last partition, then use the "left arrow" key to mark it as "L" so that the screen looks like

```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19452 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1     4 254 63      80262 [DellUtility]
P HPFS - NTFS              5   0  1 18832 254 63  302471820
D FAT32 LBA            18833   0  1 19451 254 63    9944235 [DellRestore]
[COLOR="Red"]L[/COLOR] Linux                18844   0  1 19451 254 63    9767520

```

Press "enter" to continue. 
Choose "write". 
Press "Y" to confirm writing a partition table.

Reboot and hope for the best.

---

### Post by drs305 on 2009-04-18
> **dz_alias said:**
> ```

TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 160 GB / 149 GiB - CHS 19452 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1     4 254 63      80262 [DellUtility]
P HPFS - NTFS              5   0  1 18832 254 63  302471820
D FAT32 LBA            **[COLOR="DarkRed"]18833   0  1 19451[/COLOR]** 254 63    9944235 [DellRestore]
D Linux                [COLOR="DarkRed"]18844   0  1 19451[/COLOR] 254 63    9767520

```

That is probably your problem. the FAT32 probably should be stopping somewhere short of 18844 but I don't know if there need to be any buffers between the two or not.

---

### Post by dz_alias on 2009-04-18
> **drs305 said:**
> That is probably your problem. the FAT32 probably should be stopping somewhere short of 18844 but I don't know if there need to be any buffers between the two or not.
But I don't want the Dell Restore partition, and Ubuntu installed beforehand with no problem. Even though TestDisk lists the Linux partition, I don't think it's being recovered (even if I try to otherwise.) I don't think I've tried "L", just tried setting it as the bootable partition.

The problem I'm having is that TestDisk is throwing an error because my HDD is seemingly too small concerning the Linux partition. So I'm assuming that I have to adjust the disk geometry or something in the bios so that it'll properly save my Linux partition, so I can restore it and boot from it... I dunno.

EDIT: So you're saying it was a bad idea to "overwrite" the FAT32 partition with Linux ext3? I don't understand, really :3.

---

### Post by meierfra. on 2009-04-19
> Even though TestDisk lists the Linux partition, I don't think it's being recovered (even if I try to otherwise.) I don't think I've tried "L", just tried setting it as the bootable partition.

What happens if you select the Linux partition and press "P". Does it show your files on the Ubuntu partition?

If yes, you should really be able to recover the partition. At least give the advice from my previous post a try.


> The problem I'm having is that TestDisk is throwing an error because my HDD is seemingly too small concerning the Linux partition

Ignore that error. Your hard drive is not to small. 160GB is a standard size.

> it was a bad idea to "overwrite" the FAT32 partition with Linux ext3

No. That should not cause any problems.

---

### Post by dz_alias on 2009-04-19
> **meierfra. said:**
> What happens if you select the Linux partition and press "P". Does it show your files on the Ubuntu partition?

If yes, you should really be able to recover the partition. At least give the advice from my previous post a try.



Ignore that error. Your hard drive is not to small. 160GB is a standard size.



No. That should not cause any problems.

"L" is not a valid characteristic. "P" is, but where would I boot from, if I set it as my primary and not my primary bootable? Do I just use the first as my bootable? And what should I set my NTFS partition as?

---

### Post by meierfra. on 2009-04-19
Use "P" for Ubuntu  and don't change any of the others. The boot flags are irrelevant for booting with Grub.

---

### Post by dz_alias on 2009-04-19
> **meierfra. said:**
> Use "P" for Ubuntu  and don't change any of the others. The boot flags are irrelevant for booting with Grub.

Rebooted and still got error 17 with GRUB. On LiveCD I checked for partitions in GParted, and they're there. I tried exploring my Linux partition in "Places", and at first it complained that there wasn't an object to mount, but I tried it again and it opened fine. All of my files are there. So maybe it's just a matter of altering a GRUB file at this point?

---

### Post by meierfra. on 2009-04-19
> So maybe it's just a matter of altering a GRUB file at this point?

It should be. In a terminal in Ubuntu Live CD, type

```
sudo grub
```

and then at the grub prompt:

```
root (hd0,2)
setup (hd0)
quit
```

Reboot  and see whether you can now boot into Ubuntu.

---

### Post by dz_alias on 2009-04-19
> **meierfra. said:**
> It should be. In a terminal in Ubuntu Live CD, type

```
sudo grub
```

and then at the grub prompt:

```
root (hd0,2)
setup (hd0)
quit
```

Reboot  and see whether you can now boot into Ubuntu.

It worked! Thank you so much meierfra.! You too drs305! And zvacet in the beginning for trying!

^_____________^

---

### Post by meierfra. on 2009-04-19
> It worked! 
Great. 

> Thank you so much
You are welcome.

---

