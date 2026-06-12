---
title: "RAID seems to have failed"
date: 2008-12-16
forum: General Help
---

### Post by NickZA on 2008-12-16
Hi all

I'd not consciously made any changes/updates to my fileserver, but one of my software RAID-1 volumes is now not firing up. **/dev/md0** is the array; it consists(consisted!) of **/dev/sdb1** and **/dev/sdc1**.

I think there are some different methods of creating software RAID, so just to make it known I did everything with mdadm when I created it a few months back. The array is not my boot volume, either.

What I have tried so far:

> sudo mdadm --stop /dev/md0
mdadm: stopped /dev/md0

sudo mdadm --assemble /dev/md0
mdadm: /dev/md0 has been started with 1 drive (out of 2).

EDIT: also did
> sudo mdadm -E /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 2db36f66:a61410dc:3576a38d:0ffd48ab
  Creation Time : Sat Aug  9 12:15:08 2008
     Raid Level : raid1
  Used Dev Size : 117218176 (111.79 GiB 120.03 GB)
     Array Size : 117218176 (111.79 GiB 120.03 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Sun Dec 14 19:47:10 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 5b4636d5 - correct
         Events : 0.8


      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync
nick@server:~$ 

note sdc1 wouldn't show up as such:
> sudo mdadm -E /dev/sdc1
mdadm: cannot open /dev/sdc1: No such file or directory


I don't know if gparted works correctly with RAID volumes, but it currently shows an exclamation mark beside sdc1 and cannot get volume info, whilst sdb1 is fine (but this may have always been the case in gparted, for all I can rmemeber).

I really don't know what to do next, I'm still an Ubuntu neonate. I have no idea if there are other utilities I could use but I need to be very careful here -- there is a reason this is a RAID volume -- it has all my critical data on it.

(To be fair, I should have bought a hardware RAID adapter a while back but, well, too late now.)

Can anyone offer any idea into what measures I can use to probe this situation? :confused:

EDIT: come to think of it, the only change I made to this system of late was to plug in a CD-ROM drive (IDE) and then plug it back out again. Maybe this caused reordering of the volumes somehow?

Many thanks,

-Nick

---

### Post by fjgaude on 2008-12-16
Well, **gparted** doesn't show correctly for a raid array, but does for a drive within the array.

From what you have shown you have a bad drive and need to replace it. Here's a good link to what you have:

[http://radu.rendec.ines.ro/howto/raid1.html](http://radu.rendec.ines.ro/howto/raid1.html) 

Hopefully a careful study of this should help you get back on the road with a working raid1 array.

---

### Post by NickZA on 2008-12-17
Hi fjgaude

Strangest thing, after fiddling around with those commands I mentioned (the only changes being mdadm --stop and --assemble) I booted the machine today and it's back to normal.

Weird, but I am very glad!

Thanks for your help, and will keep that link handy for when D-Day *does* arrive!

-Nick

---

### Post by fjgaude on 2008-12-17
Good, but do check your cables to the drives, and anything that might be lose.

---

