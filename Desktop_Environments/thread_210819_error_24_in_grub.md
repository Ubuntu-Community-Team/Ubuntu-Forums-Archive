---
title: "error 24 in grub"
date: 2006-07-07
forum: Desktop Environments
---

### Post by Aviatrixie on 2006-07-07
I'm using a fresh (as in 4 weeks old) install of Dapper. About a week ago my son was using my pc and it wouldn't boot, returning a grub error 24 on post. After attempting a couple more resets it finally booted and has worked flawlessly until today when I was browsing. When I tried to open up a second browser window the new window appeared and just as suddenly disappeared. Numerous attemps to get Firefox to run failed, so I tried a reboot, but upon post as grub was loading it returned a grub error 24 and ceased booting. Now it simply will not boot, always reporting error 24. I've run live linux cd's and fdisk on a windows floppy. All show the HD and report it's size, but nothing will report file system info.

I've searched Google and Ubuntu forums. Though not extremely common I have received numerous hits but no solutions. As my HD seems to be working ok I suspect (as do many others in posts I've just read) that this may be a Grub bug, I thought I'd field this before doing a reinstall.

Any suggestions?

edit: I should add that I'm using a default installation with only Ubuntu and the default swap, so it shouldn't be a partition issue as suggested in many of the posts I read about error 24.

---

### Post by FredB on 2006-07-07
I got this when searching error 24 :

> 
24 : Attempt to access block outside partitionThis error is returned if a linear block address is outside of the disk partition. This generally happens because of a corrupt filesystem on the disk or a bug in the code handling it in GRUB (it's a great debugging tool).

Maybe - just an idea - try repairing your linux partition, using e2fsck ?!

---

### Post by Aviatrixie on 2006-07-07
> **FredB said:**
> I got this when searching error 24 :



Maybe - just an idea - try repairing your linux partition, using e2fsck ?!


ok... I'm willing to learn new things. A search on e2fsck indicates it's sort of like Norton Disk Doctor. Is it a standard part of linux? I'm currently using my Dapper gnome live CD. Can I access e2fsck on this or do I need to use another live CD? Live CD's that I have that work on my PC include Breezy, Dapper, Xubuntu, Slax Popcorn and Kill Bill, Beatrix, Damn Small (v1.5 thru 2.0as well as a few later RC's), Dyne:bolic v2.0, and 1.4.1, Chubby Puppy 1.0.5, MediaInLinux v.5rc5,Wolvix 1.0.4 Games Ed., Vector v5.1 Std Ed, and a few others. Please point me towards how to use e2fsck.

TIA,

Erika

---

### Post by [S|G] on 2006-07-07
e2fsk is a standard tool, and you can use it from a live CD. Just boot the live CD, open a terminal window and type:
```

sudo e2fsk /dev/hda1

```

This assumes that your ubuntu partition is the first one on the primary master disk. Just change it to your needs :)

---

### Post by FredB on 2006-07-08
I never have to use this tool, so I was just guessing. Let's hope it will work !

---

### Post by Aviatrixie on 2006-07-08
Well... I spent some time researching just so I would have a clue what I was doing and then had at it. I opened a terminal, did this, and got these results:

ubuntu@ubuntu:~$ sudo e2fsck /dev/hdb1
e2fsck 1.38 (30-Jun-2005)
e2fsck: Filesystem revision too high while trying to open /dev/hdb1
The filesystem revision is apparently too high for this version of e2fsck.
(Or the filesystem superblock is corrupt)


The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


So I followed the program's advice and got this:

ubuntu@ubuntu:~$  sudo e2fsck -b 8193  /dev/hdb1
e2fsck 1.38 (30-Jun-2005)
e2fsck: Bad magic number in super-block while trying to open /dev/hdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


I'm not sure what's going on here, but I think it's telling me either my default Dapper file-system isn't compatable with e2fsck or my file-system is borked beyond repair.  (btw, I just learned that e2fsck stands for ext. 2 file-system check).

any ideas how to fix this or is it time to reinstall?

---

### Post by [S|G] on 2006-07-08
Well, first thing, are you sure that your partition is /dev/hdb1 ? Try this:
```

sudo fdisk /dev/hdb -l

```

This will print out a listing of partitions in your /dev/hdb. If you can't find your linux partition there, try using it on /dev/hda. It'll output something like this:
```

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/hda1   *           1        1305    10482381    c  W95 FAT32 (LBA)
/dev/hda2            1306        1321      128520   83  Linux
/dev/hda3            1322       13510    97908142+  83  Linux
/dev/hda4           13511       14946    11534670    5  Estendida
/dev/hda5           13511       14402     7164958+  83  Linux
/dev/hda6           14403       14810     3277228+  83  Linux
/dev/hda7           14811       14946     1092388+  82  Linux swap / Solaris

```

My linux partitions are /dev/hda2, /dev/hda3, /dev/hda5 and /dev/hda6.

---

### Post by Aviatrixie on 2006-07-08
quote:

Well, first thing, are you sure that your partition is /dev/hdb1 ?

------------------------------


Yes, I'm sure. Since I figured the only way to really learn Linux was to make it my only installed OS I've only been using one HD and gave the whole drive to Ubuntu. The way my PC is configured now is:

IDE 1 primary: dvd-rom
IDE 1 slave: hard drive
IDE 2 primary: dvd-rw
IDE 2 slave: empty since I installed Ubuntu, but usually has a second drive.

Disk Manager reports my system as hdb1 and my swap as hdb5.

Don't ask me why my HD's are slaves... my ex-husband set it up that way before he became my ex, but he always insisted that it was better that way.

Anyway, I finally decided that as much as I would like to have learned how to fix my old installation it was getting to the point where a clean install would have been easier. But when I tried to reinstall Dapper it hung at 0% for 15 minutes with the dvdrom busy light flickering the whole time. I aborted the install and reformated with my old 98SE disk. Now when I enter this into terminal:

sudo fdisk /dev/hdb -l

It returns this:

Disk /dev/hdb: 20.8 GB, 20847697920 bytes
255 heads, 63 sectors/track, 2534 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2534    20354323+   c  W95 FAT32 (LBA)

:lol: 


Anyway, grub is apparently still there as now it reports a grub error 17.

I'm going to attempt to reinstall Dapper again, but I'm afraid the drive itself may need zeroed out to use again. ](*,)  I'll let you know how it goes.

BTW... thanks for all your help. It truly is appreciated!:) 


Erika

---

### Post by JohnBoy55 on 2006-07-08
If it's not too late (i.e, you haven't already started the re-installation), you may want to consider checking your hard drive's physical cable connections. I don't know how old your machine is (Are the HD's EIDE or SATA?). I have seen both these errors on two of my desktops running Ubuntu and EIDE drives. I use removeable drive bays so as not to fight with my Micro$oft OS installations. Sometimes when a drive carrier is not inserted into the bay properly, I will see these errors on bootup. Reseating the drives always fixes it. My thought is that if there are continuity problems on any of the data connectors for your drives, you might see this problem.

Good luck!

---

### Post by Aviatrixie on 2006-07-08
Hi JohnBoy :) 

Yes, I did check my IDE connections and they were good. I knew the power connections were good since Disk Manager could see the drive.

Anyway, the reinstall was a success. I'm using my new Dapper install at the moment even! 106 updates completed as well. FiOS is a wonderful thing!

I forget where I learned it but I did read recently during my search for an answer to my grub problem that when grub is so borked that you can't even do a clean install on it often a fat32 format from an old windows disk will fix the problem. It does seem to be the case, as my Dapper installed and boots up just fine now.

Well... another half hour and I'll have my codecs, drivers, apps, and printer installed and configured.  ttfn!  \\:D/  


> **JohnBoy55 said:**
> If it's not too late (i.e, you haven't already started the re-installation), you may want to consider checking your hard drive's physical cable connections. I don't know how old your machine is (Are the HD's EIDE or SATA?). I have seen both these errors on two of my desktops running Ubuntu and EIDE drives. I use removeable drive bays so as not to fight with my Micro$oft OS installations. Sometimes when a drive carrier is not inserted into the bay properly, I will see these errors on bootup. Reseating the drives always fixes it. My thought is that if there are continuity problems on any of the data connectors for your drives, you might see this problem.

Good luck!

---

### Post by JohnBoy55 on 2006-07-08
Oh well, I guess the re-installation practice doesn't doesn't hurt any of us. God knows, I've done enough re-installs of various OS's over the years due to  
our good friend Mr. Murphy (Murphy's Law). I caught the blurb about you using old windows install disks for re-formatting your hard drive. Don't know if you know about PowerQuest's PartionMagic software. Costs about $70. It performs formatting, partion blasting, creating, resizing, etc. Wonderful software. Don't need to buy it though. There is a wonderful freeware Linux version called GPartEd. It can be downloaded from SourceForge as an 'iso' file and burned to a CD which will be bootable. It does pretty much everything PartionMagic does and it's free. Since it comes from SourceForge.com, you can be sure it's clean too. I include the following link to download it:
  [http://prdownloads.sourceforge.net/gparted/gparted-livecd-0.2.5-2.iso?download](http://prdownloads.sourceforge.net/gparted/gparted-livecd-0.2.5-2.iso?download)

Just download it, burn it to CD, and you should never have to use a micro$oft disk again to blast a hard drive clean.

---

### Post by Aviatrixie on 2006-07-08
hi JohnBoy,

   I have heard of Partition Magic (and understand that it is good) but have never used it before. We always went the multiple hard drive route. I've shyed away from partitioning so far due to all of the problems I've read about them in the forums.I do have a spare 60 GB drive laying around that I plan on using as a second drive and will probably split it into 3 partitions so I can play around with multibooting soon. I just downloaded GPartEd from that link you gave me and burned the image. I'll give it a try... thanks!

Erika

---

### Post by Aviatrixie on 2006-07-10
update:

My new Dapper install broke on me again about an hour ago. This time it got beyond post and into loading ubuntu but crashed at filesystem check and told me to run fsck. Apparently the filesystem was too borked to do that because I couldn't get it to run. As I pondered what the heck could be going on I recalled having a problem several years ago doing a clean XP install on a new HD where it kept hanging up midway through the install. As I had reused the old IDE cable, on a hunch I stuck a new one in and tried again, this time successfully.

This is the same old cable that I've pulled off and on dozens of time doing drive swaps. Let's hope this solves the problem.

Anyway, I rebooted with the CD and used e2fsck to fix about a hundred errors (I had no clue so just replied yes to every request to fix figuring it couldn't be any more borked than it already was! LOL). When done I rebooted and smiled when I found myself looking at my desktop.  :) 

If the problem reoccurs I'll try installing on a different drive. If THAT doesn't work it has to be a grub problem or something else in my OS.

I'll keep you posted so that it may help others later.

Erika

---

