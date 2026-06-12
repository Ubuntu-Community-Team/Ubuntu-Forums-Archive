---
title: "Reorganize a HD"
date: 2009-04-18
forum: General Help
---

### Post by causeitsme on 2009-04-18
Long Story Short:
Get new computer, runs Vista 1 year with Dual-Boot Ubuntu, Vista crashes won't boot, Wife must have have Office 2007 for job. Since Ubuntu still boots fine I install Sun xVM VirtualBox and install XP in that and Office 2007 in that. All is good.....

Once it was evident that I'd never get Vista going again without a clean install and Wife was happier with her new setup, I formatted the first partition and split it into the /dev/sda1 and sda2 you see below. Installed Puppy Linux on sda1 and Arch on sda2. Puppy won't boot and Arch messed up grub, so I overwrote Arch with a 8.04 LiveCD.

Now I want to redo the entire hard drive, I'd like to have a /home partition like I've read about and put the OS(s) on separate partitions.

I currently have: 

```
$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7769    62404461   83  Linux
/dev/sda2           30314       30401      706860   82  Linux swap / Solaris
/dev/sda3           18238       30313    97000470    5  Extended
/dev/sda4   *        7770       18237    84084210   83  Linux
/dev/sda5           18238       30313    97000438+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161   83  Linux
```


/dev/sda1  Has Puppy Linux installed (Won't boot, can't figure Puppy and Grub)
/dev/sda2  Linux Swap
/dev/sda3  Extended
/dev/sda4  Has 8.04 64bit installed (Isn't used)
/dev/sda5  It has 8.10 32bit installed with Sun xVM VirtualBox running XP and Mac4Lin Theme.

/dev/sdb  80GB external HD (What is on here is the result of sudo rsync -av --resursive --delete /home/username/ /media/disk/backup) 

I guess my questions are as follows:

1. The backup contains, among others:
```

>.VirtualBox
   >HardDisks
      NewHardDisk1.vdi  
      XP.vdi
   >Machines
      >XP
         >Logs
            VBox.log
            VBox.log.1
            VBox.log.2
            Vbox.log.3
         >Snapshots
            {501db~}.vdi
            {814eb~}.vdi
            {b3cf5~}.vdi
            {c7eeb~}.vdi         
      >XP2
         >Snapshots
	    {53260~}.vdi
```

Will her XP function if this file is simply copied into a new install if I reformat the entire HD and move her 8.10 over to sda1?

2. Will her Mac4Lin theme still be there from the backup I made?

3. Is there an easier way to do this than with rsync, should I rsync / instead of /home/username?

4. Should I put the /home partition at the front or end of the HD setup? (I would like to have 3 partitions, one for /home, one for the 8.10-VIrtualBox XP and another for trying out different distro's)

---

### Post by blazemore on 2009-04-18
The easiest thing to do would be to back up the virtual XP. You can do this easily by copying the files onto removable media.
Then back up all your personal files (music, videos, doc etc).

Then totally wipe the hard-drives, reinstalling Ubuntu. Remember to set your /swap to roughly 1.5 * your RAM size.

You should put the root (/) and home (/home) partitions on the seperate drives. The swap partition should go on the faster drive (most probably the 250gb one if it's newer).

Which one you put /home on depends on how much music, videos etc you have. If you don't have a large collection, it might be a good idea to put the /home partition on the smaller drive, because / will benefit more from the faster drive (which I'm again assuming is the 250gb one).

If you have a large music or video collection, or you can see it growing in the future, I'd recommend using the 250gb drive as /home and /swap, and using the 80gb one for /. The root partition doesn't get too full up anyway, unless you install loads of programs, since all the large files tend to be in /home.

You can then copy your personal files back, and the XP virtual machine, which can be opened again in Virtualbox without any issues.

RE: Mac4Lin, just reinstall it, it doesn't take long.

---

### Post by causeitsme on 2009-04-18
> **blazemore said:**
> The easiest thing to do would be to back up the virtual XP. You can do this easily by copying the files onto removable media.
Then back up all your personal files (music, videos, doc etc).

Then totally wipe the hard-drives, reinstalling Ubuntu. Remember to set your /swap to roughly 1.5 * your RAM size.

You should put the root (/) and home (/home) partitions on the seperate drives. The swap partition should go on the faster drive (most probably the 250gb one if it's newer).

Which one you put /home on depends on how much music, videos etc you have. If you don't have a large collection, it might be a good idea to put the /home partition on the smaller drive, because / will benefit more from the faster drive (which I'm again assuming is the 250gb one).

If you have a large music or video collection, or you can see it growing in the future, I'd recommend using the 250gb drive as /home and /swap, and using the 80gb one for /. The root partition doesn't get too full up anyway, unless you install loads of programs, since all the large files tend to be in /home.

You can then copy your personal files back, and the XP virtual machine, which can be opened again in Virtualbox without any issues.

RE: Mac4Lin, just reinstall it, it doesn't take long.

I hadn't thought of using separate drives for the / and /home. Mmmmm.....thinks of possibilities;)

If I don't use separate drives, then I guess it doesn't really matter where / and /home are located on the physical drive?

I guess I'm just worried that the .vdi files for XP will just copy over and 'just work'.

Well, thanks for the info esp. about the swap file size. I have 3 Gigs of RAM so swap should be 4.5 Gigs?

---

### Post by blazemore on 2009-04-19
Because you have a large amount of RAM, and a relatively small hard-disk, just use a 2gb swap partition, and put it on the fastest drive.

There's an article about swap here: [http://forums.linuxmint.com/viewtopic.php?f=42&t=10941&start=0](http://forums.linuxmint.com/viewtopic.php?f=42&t=10941&start=0)

---

### Post by causeitsme on 2009-04-20
> **blazemore said:**
> Because you have a large amount of RAM, and a relatively small hard-disk, just use a 2gb swap partition, and put it on the fastest drive.

There's an article about swap here: [http://forums.linuxmint.com/viewtopic.php?f=42&t=10941&start=0](http://forums.linuxmint.com/viewtopic.php?f=42&t=10941&start=0)

Thank you, I'm gonna mark this as solved and do the whole reorganize this weekend.

---

