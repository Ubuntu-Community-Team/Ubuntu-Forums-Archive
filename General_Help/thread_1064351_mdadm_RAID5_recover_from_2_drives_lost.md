---
title: "mdadm RAID5 recover from 2 drives lost"
date: 2009-02-08
forum: General Help
---

### Post by lilrabbit129 on 2009-02-08
Hello all,

I recently had some trouble with mdadm. Some background: I run a 4 disk RAID5, 4x750GB ( /dev/sd[b-e] ). Recently, 2 of the drives became unavailable, and mdadm marked them as faulty. I turned the machine off and checked the drives, they seem ok ( I think the SATA card they're attached to hiccuped). As far as I know the data itself on the drives is fine ( I wasn't writing any data during the event). My question is how do I get the raid up and running again? I'm a bit over my head so I haven't tried anything except get info on it. 

> 
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1aa684bc:8b66935e:c7106029:7c577801 (local to host downy)
  Creation Time : Wed Sep 24 17:55:33 2008
     Raid Level : raid5
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
     Array Size : 2197715712 (2095.91 GiB 2250.46 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Feb  6 08:28:55 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 50c18fe4 - correct
         Events : 0.487370

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed



> 
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1aa684bc:8b66935e:c7106029:7c577801 (local to host downy)
  Creation Time : Wed Sep 24 17:55:33 2008
     Raid Level : raid5
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
     Array Size : 2197715712 (2095.91 GiB 2250.46 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Feb  6 08:28:55 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 50c18ff6 - correct
         Events : 0.487370

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed



> 
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1aa684bc:8b66935e:c7106029:7c577801 (local to host downy)
  Creation Time : Wed Sep 24 17:55:33 2008
     Raid Level : raid5
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
     Array Size : 2197715712 (2095.91 GiB 2250.46 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Feb  5 23:46:21 2009
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 50c1155e - correct
         Events : 0.487358

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       33        2      active sync   /dev/sdc1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1

> 
/dev/sde1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1aa684bc:8b66935e:c7106029:7c577801 (local to host downy)
  Creation Time : Wed Sep 24 17:55:33 2008
     Raid Level : raid5
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
     Array Size : 2197715712 (2095.91 GiB 2250.46 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Feb  5 23:46:21 2009
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 50c11570 - correct
         Events : 0.487358

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       49        3      active sync   /dev/sdd1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1


> 
sudo mdadm --detail /dev/md0
mdadm: md device /dev/md0 does not appear to be active.


Please let me know if there is any other info you may require.

Thank you in advance!

---

### Post by lilrabbit129 on 2009-02-09
bump to front page

---

### Post by fjgaude on 2009-02-09
I can't say what might be wrong. Run this:

```
sudo mdadm -D /dev/md0
```

That gives some idea of the health of the total array.

Try forcing an assembly:

```
sudo mdadm --assemble --force /dev/sdb /dev/sdc /dev/sdd /dev/sde
```

and see if that works. If it does you need to run **fsck** on a stopped and unmounted array to get rid of any errors in the data.

I assume you have a line in your fstab file that auto mounts the array.

Some items to study if need be:

[http://www.hscripts.com/tutorials/linux-services/mdadm.html](http://www.hscripts.com/tutorials/linux-services/mdadm.html)
[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)
[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
```
man mdadm
```

Let us know how you are doing.

---

### Post by lilrabbit129 on 2009-02-09
I've tried 
```
mdadm -D /dev/md0
```
and it returns 
```
mdadm: md device /dev/md0 does not appear to be active.
```

I think I'm not making my question clear. Basically the array should be fine, the data on the drives being good. Its just that in the superblocks, its convinced that 2 of the drives are faulty ( because they were unavailable for a few seconds). What I'm asking is what would be the preferred way to convince mdadm that they're still good and to just put the RAID back together?

Is there any way to check to see if the data on the drives is in fact "in sync"? 

Thanks for all your help so far. 

PS, I haven't tried out your suggestion with the --force option yet because I'm not quiet sure what it does. I will read up on it tonight though.

---

### Post by fjgaude on 2009-02-10
Since the -D command indicates the array is not assembled, period.

Try the forced assemble as indicated. No data will be lost one way or the other.

Without assembly there is no way to know if data is intact or not.

Something caused drives to be marked as faulty... can you think of what might have caused this?

---

### Post by lilrabbit129 on 2009-02-10
That is good to know. I haven't had a chance to try out your suggestions on the array but I'll try to get to it tonight. 

As for the what made the data faulty I have a hunch. The setup in that server is somewhat ... roundabout. Let me explain: It is a very old 1.3Ghz Athlon. The motherboard itself does not have any SATA connectors so I'm using 2 PCI to SATA cards (each having 2 connectors for a total of 4 drives). The motherboard has a total of 6 PCI slots, each of which is filled. I have a NIC, a sound card and 2xUSB2 cards. One of the USB2 cards is a VIA chipset, and I've noticed it does not play well with USB hard drives.  

The morning of the event, I plugged in a USB HD (with the intent on clearing it off). I accidentally plugged it into the "temperamental" USB2 card. For an unrelated reason I issued the command ```
sudo mdadm --detail /dev/md0
``` This stalled until I unplugged the USB HD. After issuing the command again, 2 of the drives were marked faulty).

I have a hunch that the USB2 card somehow brought down or interfered ( IRQ conflict possibly?) with one of the PCI/SATA cards, thus momentarily making the 2 drives attached to it unavailable. MDADM, seeing that it was not able to communicate with 2 drives reasoned that they were dead and marked them faulty.

That is my hunch, the feasibility of all that happening I'm not sure. 

Thank you again for all your help. 

> **fjgaude said:**
> Since the -D command indicates the array is not assembled, period.

Try the forced assemble as indicated. No data will be lost one way or the other.

Without assembly there is no way to know if data is intact or not.

Something caused drives to be marked as faulty... can you think of what might have caused this?

---

### Post by lilrabbit129 on 2009-02-10
Hello,

I tried your suggestion:

```
sudo mdadm --assemble --force /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
```

I compensated for the drive letters having been moved around. Unfortunately the command failed. I took a closer look at the man page and saw that the first parameter should be the raid device so I tried:

```
sudo mdadm --assemble --force /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
```

That gave me the error: no recogniseable superblock on /dev/sdb1. I tried to --examine that drive and there is in fact no more superblock on there. Did I just shoot myself on the other foot? 

I saved the output of --examine on each drive before running the command, is there any way to recreate this superblock? 

PS, yes this happened on one of the drives that was not marked faulty.

---

### Post by fjgaude on 2009-02-11
I've never re-created superblocks... don't know how if it is possible. Maybe someone here does.

There many redundant superblocks on each drive.

sudo e2fsck -b 32768 98304 163840 /dev/sda3

Gives you an idea about the many superblocks on each drive. But don't remember what's it all about... rean the man pages and see if you can use the one just past the first. The first one is likely the only one you deleted, the next should be good.

```
man e2fsck -b /dev/<device-name>
```

Let us know what you find.

---

### Post by lilrabbit129 on 2009-02-12
I fixed the problem!

First of all, I didn't really over-write the raid superblock like I thought I did. Apparently when you mistakenly specify a raid component as a raid device, it simply breaks the /dev/sd* entry for your system ( hence the missing superblock ). A simple reboot fixed that.

After the reboot I was back where I started. I ran the command you suggested ( after modifying the order of the drives, and making sure to specify /dev/md0). That cleared the faulty flags on the last 2 drives and the array came right up.

Next I ran a fsck.ext3 check on /dev/md0 to make sure everything was fine and mounted it. 

Thanks for all your help! :P

---

### Post by fjgaude on 2009-02-12
Great! Glad you got everything fixed. Lots of things to learn when things go wrong, eh?

---

### Post by lilrabbit129 on 2009-02-12
Yup exactly. It also teaches me to remove any non-critical PCI cards from my server.

---

