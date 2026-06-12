---
title: "Updating to kernel 2.6.27-11-server broke mdadm"
date: 2009-04-27
forum: General Help
---

### Post by doctordope on 2009-04-27
I have updated to 9.10 mdadm fails to see the raid when I go back to the previous version of kernel it seems to work.
 uname -a
Linux babyjesus 2.6.24-23-server #1 SMP Wed Apr 1 22:14:30 UTC 2009 x86_64 GNU/Linux
 cat /proc/version_signature
Ubuntu 2.6.24-23.52-server
 Also for some reason when I backup the filesystem the whole system crashes

---

### Post by fjgaude on 2009-04-27
I believe that 9.10 upgrade changes the array UUID and if you still are using the old mdadm.conf file then things are sure to not work.

A suggestion: remove mdadm, delete or rename the old mdadm.conf file. Reboot, then re-install mdadm. Then run this command:

```
sudo mdadm --assemble --scan
```

A new mdadm.conf file is created and you should be good to go after another re-boot.

I'm not about to upgrade to 9.10... just too new, with too many bugs. In three months, maybe. <smile>

---

### Post by doctordope on 2009-04-27
mdadm --assemble --scan 
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.

mdadm -D /dev/md0 
mdadm: md device /dev/md0 does not appear to be active.


/dev/sda:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 5f2f58bc:25b44d62:9b8c7f44:2e4a8283 (local to host babyjesus)
  Creation Time : Sat Jun 28 19:32:07 2008
     Raid Level : linear
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Apr 27 18:34:16 2009
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : b5ee7cb8 - correct
         Events : 61

       Rounding : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        0        0      active sync   /dev/sda

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd
/dev/sdb:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 5f2f58bc:25b44d62:9b8c7f44:2e4a8283 (local to host babyjesus)
  Creation Time : Sat Jun 28 19:32:07 2008
     Raid Level : linear
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Apr 27 18:34:16 2009
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : b5ee7cca - correct
         Events : 61

       Rounding : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       16        1      active sync   /dev/sdb

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd
/dev/sdc:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 5f2f58bc:25b44d62:9b8c7f44:2e4a8283 (local to host babyjesus)
  Creation Time : Sat Jun 28 19:32:07 2008
     Raid Level : linear
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Apr 27 18:34:16 2009
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : b5ee7cdc - correct
         Events : 61

       Rounding : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       32        2      active sync   /dev/sdc

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd
/dev/sdd:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 5f2f58bc:25b44d62:9b8c7f44:2e4a8283 (local to host babyjesus)
  Creation Time : Sat Jun 28 19:32:07 2008
     Raid Level : linear
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Apr 27 18:34:16 2009
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : b5ee7cee - correct
         Events : 61

       Rounding : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       48        3      active sync   /dev/sdd

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd

---

### Post by fjgaude on 2009-04-28
From the data there's nothing wrong with your array. Did you do exactly as I said?

Also compare the UUID of the drives to the UUID you find in mdadm.conf. If they are different then...

---

### Post by doctordope on 2009-05-06
I did try to remove mdadm and removed mdamd.conf. 

Rebooted the server. 

Reinstall the server with a new mdadm and run mdadm --scan --assemble and still have the same problems . 

Ilaiy

---

### Post by doctordope on 2009-05-08
This is what was done . looks like it cannot start the array . the uuid match 

mdadm --examine --scan --config=tt > /etc/mdadm/mdadm.conf

root@babyjesus:~# cat /etc/mdadm/mdadm.conf 
ARRAY /dev/md0 level=linear num-devices=4 UUID=5f2f58bc:25b44d62:9b8c7f44:2e4a8283

root@babyjesus:~# mdadm --examine /dev/sd[abcd]
/dev/sda:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 5f2f58bc:25b44d62:9b8c7f44:2e4a8283
  Creation Time : Sat Jun 28 19:32:07 2008
     Raid Level : linear
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Apr 27 19:08:00 2009
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : b5ee8465 - correct
         Events : 63

       Rounding : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        0        0      active sync   /dev/sda

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd
/dev/sdb:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 5f2f58bc:25b44d62:9b8c7f44:2e4a8283
  Creation Time : Sat Jun 28 19:32:07 2008
     Raid Level : linear
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Apr 27 19:08:00 2009
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : b5ee8477 - correct
         Events : 63

       Rounding : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       16        1      active sync   /dev/sdb

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd
/dev/sdc:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 5f2f58bc:25b44d62:9b8c7f44:2e4a8283
  Creation Time : Sat Jun 28 19:32:07 2008
     Raid Level : linear
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Apr 27 19:08:00 2009
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : b5ee8489 - correct
         Events : 63

       Rounding : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       32        2      active sync   /dev/sdc

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd
/dev/sdd:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 5f2f58bc:25b44d62:9b8c7f44:2e4a8283
  Creation Time : Sat Jun 28 19:32:07 2008
     Raid Level : linear
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Apr 27 19:08:00 2009
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : b5ee849b - correct
         Events : 63

       Rounding : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       48        3      active sync   /dev/sdd

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd
root@babyjesus:~#

---

### Post by doctordope on 2009-05-08
root@babyjesus:~# cat /proc/mdstat 
Personalities : 
unused devices: <none>
root@babyjesus:~# mdadm --assemble --scan 
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.
root@babyjesus:~# cat /proc/mdstat 
Personalities : 
md0 : inactive dm-0[1](S)
      2197723520 blocks
       
unused devices: <none>

---

### Post by fjgaude on 2009-05-09
I can't say what you are missing... do you have a mountpoint for the array, and is there a line in your /etc/mdadm file for it to auto mount?

After booting did you try to manually mount the array like so:

```
sudo mount /dev/md0
```

Let us know what is happening here, please.

---

### Post by doctordope on 2009-05-13
Not sure what the problem is I still get the same error . I also tried marking 1 drive a faulty and it doesn't mark it as faulty. That is really weird . 

I booted it back to the old kernel and am trying to take a backup of the raid but it keeps dying with a segmentation fault and wierd errors like smbd is not tainted . 

*Ilaiy *

---

### Post by doctordope on 2009-05-13
Could this be the fix 

root@babyjesus:~# ls -la /dev/disk/by-uuid/
total 0
drwxr-xr-x 2 root root 100 2009-05-13 00:23 .
drwxr-xr-x 5 root root 100 2009-05-13 00:23 ..
lrwxrwxrwx 1 root root  10 2009-05-13 00:23 62ddfcd9-cbdc-4af6-94f1-d91072823009 -> ../../sde1
lrwxrwxrwx 1 root root  10 2009-05-13 00:23 9cdb3c19-0716-40c2-91b6-813ff80e0a0d -> ../../sde5
lrwxrwxrwx 1 root root   9 2009-05-13 00:23 c6dfc0db-ce92-441b-b819-7f5aec22aca6 -> ../../md0

Can I change the UUID in mdadm.conf 

root@babyjesus:~# cat /etc/mdadm/mdadm.conf 
ARRAY /dev/md0 level=linear num-devices=4 UUID=5f2f58bc:25b44d62:9b8c7f44:2e4a8283

---

### Post by fjgaude on 2009-05-13
No, no. The UUID you have is for mounting the array, not really necessary ever. For the array name never changes and it's best to use the name.

The UUID you see in the mdadm.conf file is one that is first created by mdadm and that could change as you go to a new computer or upgrade an old one. It's best to do this:

```
sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```

A new mdadm.conf UUID will be created. You then should be good to go. There are other ways to get your system working that may be in this thread.

---

### Post by ainawing on 2010-06-05
thanks for the help, fjgaude. I actually had another problem with another kernel, but your hint worked for me.

Just a small description for other users experiencing the same:
My computer crashed overnight (don't know why, maybe some power issue) when my raid was syncing.

Afterwards I found a ghost md device (md_d0) in my mdstat that somehow used one or two (random after reboot) of my raid disks, so my raid couldn't assemble (resyncing -> already degraded). The ghost device wasn't in my mdadm.conf... so what was there to do?

I'm not quite sure, what the difference is with your code, except that now (after disabling all prior settings), mdadm doesn't scan devices and the syncing disk is included in the array to begin with (spares=1).

It is not my first time experiencing problems with raid on linux. My last problem made me upgrade my raid to level 6 (the hard way) and I hope that this attempt at getting my raid back up will work...

---

