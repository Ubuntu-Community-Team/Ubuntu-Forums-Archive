---
title: "Recovering mdadm superblocks"
date: 2009-03-20
forum: General Help
---

### Post by deck- on 2009-03-20
Hello everyone

I have a raid5 mdadm array which has four drives.  My new motherboard has inexplicably cleared three of the super blocks, and I am now left with only one intact superblock.

**fdisk -l**

```

Disk /dev/sda: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03930393

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1982    15920383+  83  Linux
/dev/sda2            1983        2491     4088542+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000


Disk /dev/sdc: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000


Disk /dev/sdd: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000


Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000


Disk /dev/sdf: 1044 MB, 1044250624 bytes
33 heads, 32 sectors/track, 1931 cylinders
Units = cylinders of 1056 * 512 = 540672 bytes
Disk identifier: 0x9348a58e


```

**mdadm --examine /dev/sdb**

```

mdadm: No md superblock detected on /dev/sdb

```

**mdadm --examine /dev/sdc**

```

mdadm: No md superblock detected on /dev/sdc

```

**mdadm --examine /dev/sdd**

```

mdadm: No md superblock detected on /dev/sdd

```


**mdadm --examine /dev/sde**

```

/dev/sde:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : f781ba39:3975fa64:c36d41f1:ea056919
  Creation Time : Mon Jan  5 14:18:27 2009
     Raid Level : raid5
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
     Array Size : 2930287488 (2794.54 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Mar 19 22:39:52 2009
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 54f44664 - correct
         Events : 0.92

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       32        3      active sync   /dev/sdc

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       64        1      active sync   /dev/sde
   2     2       8       48        2      active sync   /dev/sdd
   3     3       8       32        3      active sync   /dev/sdc

```



I have now moved the raid array back to the original file server, but the superblocks are still missing.  I am able to assemble the array with only the one drive, but obviously the array cannot be started.  I am also unsure about the order of the drives connected to the old server and I am worried that the drives are no longer connected in the same physical order that they originally were.

I am hoping someone with more knowledge than myself can answer a few question:

1. Can this raid array be restored?  I am confident that none of the actual data has been impacted, I have only lost my superblocks...


2. If I try to recreate the raid array using *mdadm --create --assume-clean* and the order of the devices is not the same as the original configuration, will mdadm erase the data on the drives?


3. If I were to buy four more identical drives to the ones that comprise the raid array, dd everything to the new drives, would I be able to test recreating the array on the new drives?


4. Is there anyway to recover data from a mdadm raid array without successfully recreating the array?  I am sure the data is still there, I just can't construct the array.


thanks in advance for any advice on how to proceed with this problem.

---

### Post by fjgaude on 2009-03-21
The big question is how could the superblocks be wiped out?

A suggestion: first re-name or delete the **/etc/mdadm/mdadm.conf** file, remove (purge) **mdadm** from the system. Then reboot, re-install mdadm and see if we can assemble the array:

```
sudo mdadm --assemble --scan
```

That likely will do it for you.

---

### Post by deck- on 2009-03-22
Thanks for the reply fjgaude.  Reading the Ubuntu forum threads related to mdadm is see your name several times.  The other threads were helpful also.   

> **fjgaude said:**
> The big question is how could the superblocks be wiped out?

This is the question I am asking myself also.  It may be partly my own fault.  I installed the raid array on to the drives raw (without creating partitions).  My theory is that the motherboard must have tried to init those drives in some way and subsequently overwrote the superblocks.  In the future, I will definately create partitions to hold my raid array.  



> **fjgaude said:**
> A suggestion: first re-name or delete the **/etc/mdadm/mdadm.conf** file, remove (purge) **mdadm** from the system. Then reboot, re-install mdadm and see if we can assemble the array:

```
sudo mdadm --assemble --scan
```

That likely will do it for you.

I will try this again when I get home, but I don't beleive this solve the problem.  The new pc where I was trying to re-assemble the raid array was a clean installation and did not have an mdadm.conf on it. When I moved the drives to this new box, the first thing I did was to examine each of the drives using mdadm and already at this point the superblocks on three of the drives were gone.  When I saw this, I tried to reassemble the array by providing the needed paramters rather than trying to scan for the array. ie:

mdmadm --assemble /dev/md0 /dev/sdb /dev/sdc /dev/sdd /dev/sde

At this point mdadm informed me that the array could not be assembled because of the missing superblocks. 

If I call madadm --assemble --scan without any parameters, does mdadm scan all of my harddrvies superblocks for an existing array?

---

### Post by deck- on 2009-03-22
fjgaude,

I tried your suggestion, but now mdadm reports:

```

mdadm: No arrays found in config file

```


If I do the same with the config file present, the array assembles with one drive but does not start.


Any other ideas?

---

### Post by fjgaude on 2009-03-23
> If I call madadm --assemble --scan without any parameters, does mdadm scan all of my harddrvies superblocks for an existing array?

The --scan is very important. Using your drives names bypasses what is to be done by what I suggested. Start all over, it's that important.

---

### Post by deck- on 2009-03-27
Hello everyone,

Just wanted to post my solution to this problem.

Another thread had mentioned the process of recreating the array with the "missing" option to force the raid array to be reconstructed without attempting to resync.  I was a little hesitent to do this at first, because I was unsure how this process would react to multiple missing superblocks.  Turns out, it is not a problem.

Basically what I had to do to reconstruct my array was to attempt to recreate the array with every possible combination of physical drive orders. I have a four drive array of which I knew the position of only one drive.  This means there are six possible combinations that could represent the same physical order that the array was originally constructed in.  So I created a simple chart which had all six possible combinations and tried creating the array for combination:

```

mdadm --create /dev/md0 /dev/sdb /dev/sdc missing /dev/sde

```

I then tried to do a read only fsck against the created array to see if the filesystem was intact.

```

fsck -fn /dev/md0

```

If fsck found that the file system was not intact, I shutdown my comp and tried another combination.  I repeated this process until finally on the sixth combination my array was created with an intact file system.  I then re-added the drive which I had marked as missing and mdadm resynced the array and everything was good.

```

mdadm --add /dev/md0 /dev/sdd

```


One thing i learned through this process is that you should always create your raid array using partitions defined on the drive.  I created my array raw (witout creating partitions on the drives themselves).  I beleive this is why my motherboard cleared the superblock because it was trying to initialize the drives.  

fjgaude, thanks for your help.

---

### Post by fjgaude on 2009-03-27
Okay, I'll make sure to remember what you have done so to help others that might go through the same issue. Will remember to always use partitions instead of whold drive... actually I've always used the whole drive but with one partition that took all the drive's space.

Thanks for getting back so that others may learn.

---

### Post by strips on 2009-10-03
> **fjgaude said:**
> The big question is how could the superblocks be wiped out?

A suggestion: first re-name or delete the **/etc/mdadm/mdadm.conf** file, remove (purge) **mdadm** from the system. Then reboot, re-install mdadm and see if we can assemble the array:

```
sudo mdadm --assemble --scan
```

That likely will do it for you.

I had a RAID0 disapearing on me after upgrading to 9,10 beta. I tried to reassemble but i did not work. But your solution worked perfect. 

thanks!

---

### Post by santhony on 2009-11-10
I'm trying to swap out a new drive for a faulty and having some minor issues here...

Gonna give your solution a try Frank.. 

I'll let you know.

---

### Post by santhony on 2009-11-16
Well I have good news and Bad News... 

I did get my array up and running..  All was beautiful and fine...

I came back home after a long weekend to find out two of my drives are not showing a UUID.  The other members of the raid set do show all the same UUID.  

I'm pretty sure the data is still on the drives, but I cannot assemble them.

Where should I start?

---

### Post by santhony on 2009-11-17
I just found and fixed my problems after 3 days of scrubbing.....

My MDADM Raid 5 partitions, on two of the member disks, just mysterously disappeared.

I have a 7 disk Raid 5 Array.  After system updates and a reboot.  Two of my drives no longer had their partitions showing.  

GParted did show the two drives as intact, that they were members of a raid array.  

fdisk -l also showed the drives correctly with their partitions.

BUT, the disk Utility, Palimpseset showed the two drives with no partition table.

The FIXX:  REMOVE DMRAID.

After unistalling DMRAID using the Synaptic Package Manager... The drives all of a sudden showed up correctly and assembled all on their own..

Wall Lah..  

I hope this helps anyone with the same situation.

Good Luck and please post any tricks or tips you find!!

---

