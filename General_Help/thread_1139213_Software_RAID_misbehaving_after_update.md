---
title: "Software RAID misbehaving after update"
date: 2009-04-26
forum: General Help
---

### Post by david_frey on 2009-04-26
After upgrading to Jaunty, my software RAID0 is misbehaving.

Here's the content of /proc/mdstat


```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md_d0 : active raid0 sda2[0] sdc1[1]
      976816064 blocks 64k chunks

unused devices: <none>
```

You can see that the devices being used are sda2 and sdc1.  When I originally created the array, the devices were sdb2 and sdc1.  Due to another problem (long story) I ended up moving my SATA cables around and the device name changed.

Until I upgraded to Jaunty, my RAID array continued to work even though one of the devices had changed from sdb2 to sda2.  Now every time I boot, I get dropped into the admin console because my RAID is failing to be brought up.  I don't recall the exact error message.

This I think is the key to the puzzle:

```
# mdadm --examine /dev/sda2
/dev/sda2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : df4f4d9a:7b1a6066:7d406edc:70d87b6f (local to host zergling)
  Creation Time : Tue Mar 24 20:45:13 2009
     Raid Level : raid0
  Used Dev Size : 0
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Tue Mar 24 20:45:13 2009
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 854239b0 - correct
         Events : 1

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       18        0      active sync   /dev/sdb2

   0     0       8       18        0      active sync   /dev/sdb2
   1     1       8       33        1      active sync   /dev/sdc1
```


Notice that the "this" entry at the bottom mentions sdb2 instead of sda2.  I think the superblocks on the devices need to be updated, but I don't know what the correct commands to do that are.  Can someone tell me?

Thanks!

---

### Post by david_frey on 2009-04-28
I'm still looking for help on this problem.  I have read through the mdadm man page and I didn't see anything applicable.

---

### Post by fjgaude on 2009-04-28
Here's a suggestion: remove mdadm, re-name or delete /etc/mdadm.conf file, re-boot. Then re-install mdadm and run this command:

```
sudo mdadm --assemble --scan
```

That will create a new mdadm.conf file and you should be able to mount the array. BTW, the upgrade changed the UUID of the array.

---

