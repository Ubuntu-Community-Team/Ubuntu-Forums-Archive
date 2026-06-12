---
title: "Software raid problem"
date: 2006-08-05
forum: Desktop Environments
---

### Post by aceracer24 on 2006-08-05
I have 2 sata drives that were previously configured raid in windows using nvidia raid. Worked great no problmes. Since installing Ubuntu, I decided i wanted that raid back because it has alot of my games already set up that I can transfer to cedega. I wasn't sure what raid utilities were available in Ubuntu but a search came up with mdadm. So I apt-get and followed a guid for setting up the raid for raid-0. Worked great! Shows it was set up on md0, but i had no access to it. SO I modified fstab the same way it was already done for my other NTFS drives and rebooted. When I rebooted, the boot messages read "starting raid....failed" When I got back into ubuntu I tried using mdadm to check the raid and I am getting mdadm: error opening /dev/md0: No such file or directory. So, no go...hoping someone has an idea what to do?

---

### Post by Ocxic on 2006-08-05
ok assuming that you haven't touched the partitons fr your raid setup try

sudo mdadm -A /dev/sda1 /dev/sdb1 /dev/md0

this should activate the raid array, and then you can mount /dev/md0 normally

---

### Post by aceracer24 on 2006-08-05
thanks for the quick reply! Not working here is the command I first used to make the array:

```
sudo mdadm --create --verbose /dev/md0 --level=0 --raid-devices=2 /dev/sda /dev/sdb
```

WHen I firts did that, the creation worked. After the reboot this command no longer functions. So I searched the forums finding nothing to went over to the gentoo forums and found a couple things that activated md0 again. ```
sudo modprobe raid0 
```

```
modprobe dm-mod
```
```
sudo mknod /dev/md0 b 9 1
```

This made the md0 again and then i redid the first command I posted to make the array. But when I reboot I loose it all again so your fi doesn't work. 
```
david@AceRacer:~$ sudo mdadm -A /dev/sda1 /dev/sdb1 /dev/md0 mdadm: error opening /dev/sda1: No such file or directory
david@AceRacer:~$ sudo mdadm -A /dev/sda /dev/sdb /dev/md0
mdadm: /dev/sda does not appear to be an md device
david@AceRacer:~$
```

I have tried with sda/sdb and sda1/sdb1. I can only create the array suing sda/sdb not sda1/sdb1

---

### Post by aceracer24 on 2006-08-07
hmm, guess no more help with this... :(

---

### Post by peabody on 2006-08-07
Uhmmm, this is just a guess I have truly zero experience with raid, but is nvidia's software raid compatible with linux's software raid?

---

### Post by aceracer24 on 2006-08-07
Honestly I do not know. I was hoping, like nvidia's raid, it could work with a pre existing raid set up isntead of completely rebuilding. I have games and stuff I use on the raid drives and would like to keep them intact.

It would seem not many people know much about software raids at this point.....

---

### Post by RAOF on 2006-08-08
I'd check out [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto), but I think you'll need some extra steps.  Particularly, you need to work out **how** the RAID information is stored by the nvidia drivers, and set up your linux RAID with that information (stripe size, starting block, whatever).  Actually, [http://www.die.net/doc/linux/man/man8/dmraid.8.html](http://www.die.net/doc/linux/man/man8/dmraid.8.html) (which is the man page for dmraid) seems to say that dmraid can understand the nVidia RAID formatting.  Cool for you!

Slightly less cool for you: does your RAID still work in Windows?  I thought that by recreating the raid in linux, you'd have wiped the info needed for the nVidia drivers to do the raid.  Maybe I'm wrong :)

---

### Post by Ocxic on 2006-08-08
RAOF what you say could be true, but i do not believe it is so, so long as the newly created raid setup wasn't formated or touched at all and scince he has yet to acces it, i'm pretty sure all the data is there. 

try using testdisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) it may help in finding the info about your drives, and is avalable in synaptic

---

### Post by aceracer24 on 2006-08-08
Yep I have since tried it in windows and all is well. I made the raid in linux but I never reformated or anything else. I have since re installed Dapper but the 32 bit version and messing with boot screens, I happen to see something upon boot that said md0 is working already witha total space of 160+ gigs which tells me it set up both my sata drives as the raid...good for it :). I also noticed though that it could not understand the format.....I have not had the time to verify as of this moment but maybe tonight or the next. ALso ROAF and Ocxic, I'll check them links out, thanks much appreciated.

---

### Post by aceracer24 on 2006-08-09
> **Ocxic said:**
> RAOF what you say could be true, but i do not believe it is so, so long as the newly created raid setup wasn't formated or touched at all and scince he has yet to acces it, i'm pretty sure all the data is there. 

try using testdisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) it may help in finding the info about your drives, and is avalable in synaptic


Well I have not had the chance to set up/fix/test software raid yet but I did however run into a bit of a snag with my windows partition. It stopped booting for some reason. That link for Testdisk fixed my problems so a big thank you to Ocxic :P

---

### Post by aceracer24 on 2006-08-09
well I have tried everything, including searches and i can't find anything to make this raid set up work. md0 is currently showing but when I try to mount it I get:

```
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```


sudo fdisk -l /dev/md0 shows me :

```
Disk /dev/md0: 163.9 GB, 163928473600 bytes
2 heads, 4 sectors/track, 40021600 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
```

so....help? There must be a way to do this. I can't believe in all linux glory that this can't be done. Seriously, the raid is obviously created and linux IS seeing it but I have no access to it.

EDIT: BTW, I thought this was set up on nvidia raid but i was mistaken, dmraid showed it's actually using the sil raid chip instead. I tried using dmraid but from the oput I got on one of the tools, it would seem I can't use dmraid for what ever reason. mdadm seems to work...mostly and I think was already installed and set up to work but it's just not fully working atm.

More info:

```
david@AceRacer:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Aug  5 18:08:15 2006
     Raid Level : raid0
     Array Size : 160086400 (152.67 GiB 163.93 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Aug  5 18:08:15 2006
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : 6b87c3b0:57a75238:e08944ea:bf5ca2cb
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
```

and:

```
david@AceRacer:~$ sudo mdadm /dev/md0
/dev/md0: 152.67GiB raid0 2 devices, 0 spares. Use mdadm --detail for more detail.
/dev/md0: No md super block found, not an md component.
```

---

### Post by RAOF on 2006-08-09
What is the actual **mount** command you're trying?

It's something like this, right?
```
sudo mount -t ntfs /dev/md0 /media/WinXP
```

After you run that, what is in your dmesg?  As it says, there's often useful information there :)

The other possibility is that md0 is **not** properly set up.  Sure, it's beeing seen as a RAID, but do the stripe size, starting block, etc match what Windows thinks they are?  (I don't really have any idea how to check this, though).  If they don't, then you'll be able to see md0, but it won't seem to contain any coherent data, 'cause you'll be getting bits of one stripe mixed up with bits of other stripes.

---

### Post by aceracer24 on 2006-08-09
This is what I get with dmesg:

```
david@AceRacer:~$ dmesg | tail
[17179898.536000] printk: 28 messages suppressed.
[17179898.536000] NTFS-fs error (device md0): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17179898.536000] NTFS-fs error (device md0): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17179898.536000] NTFS-fs error (device md0): ntfs_fill_super(): Not an NTFS volume.
[17179955.236000] NTFS-fs error (device md0): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17179955.236000] NTFS-fs error (device md0): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17179955.236000] NTFS-fs error (device md0): ntfs_fill_super(): Not an NTFS volume.
[17183159.028000] NTFS-fs error (device md0): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17183159.028000] NTFS-fs error (device md0): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17183159.028000] NTFS-fs error (device md0): ntfs_fill_super(): Not an NTFS volume.
```

and yes, the mount command I am using is 
```
sudo mount -t ntfs /dev/md0 /media/raid
```

---

### Post by RAOF on 2006-08-09
I'd guess you have the latter problem: mdadm's RAID settings aren't matching those used by windows, so the data from md0 is all mixed up.

I don't know what you can do now, sorry.

---

### Post by aceracer24 on 2006-08-09
grrr, this is the ONLY thing left I have to unstrap me from windows....other then some games that cedega won't run. I do not have another drive to copy the info to otherwise i would and redue the raid drives...

Well, no worries anymore, I messed with to many raid tools and the raid drive is now not understood by WIndows either lol. Oh well, guess now I can use it for linux :)

---

