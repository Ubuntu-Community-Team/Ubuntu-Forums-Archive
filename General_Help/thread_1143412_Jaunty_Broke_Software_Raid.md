---
title: "Jaunty Broke Software Raid"
date: 2009-04-29
forum: General Help
---

### Post by flick152 on 2009-04-29
I did the Jaunty yesterday and after reboot my mdadm raid won't work

I had one raid 0 at /dev/md0 made up from /dev/sda and /dev/sdb since the upgrade those disks are now /dev/sdc and /dev/sdd

Please help.

```
root@griffie:/home/nutchy# mdadm -Asv
mdadm: looking for devices for /dev/md0
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: /dev/sdc has wrong uuid.
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: /dev/sdd has wrong uuid.
mdadm: no devices found for /dev/md0
mdadm: looking for devices for further assembly
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: cannot open device /dev/sdd: Device or resource busy

```

```
root@griffie:/home/david# mdadm -E /dev/sdc /dev/sdd
mdadm: metadata format 00.90 unknown, ignored.
mdadm: metadata format 00.90 unknown, ignored.
/dev/sdc:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 616e78cd:fc386bed:b928cd6d:81a874bc (local to host griffie)
  Creation Time : Sat Mar  7 18:56:48 2009
     Raid Level : raid0
  Used Dev Size : 0
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Sat Mar  7 18:56:48 2009
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : d5088fc1 - correct
         Events : 1

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        0        0      active sync   /dev/sda

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
/dev/sdd:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 616e78cd:fc386bed:b928cd6d:81a874bc (local to host griffie)
  Creation Time : Sat Mar  7 18:56:48 2009
     Raid Level : raid0
  Used Dev Size : 0
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 127

    Update Time : Sat Mar  7 18:56:48 2009
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : d5089052 - correct
         Events : 1

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       16        1      active sync   /dev/sdb

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb

```

```
root@griffie:/home/david# cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE /dev/sdc /dev/sdd ##partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Thu, 25 Dec 2008 17:01:49 +1300
# by mkconf
ARRAY /dev/md0 level=raid0 num-devices=2 metadata=0.90 UUID=616e78cd:fc386bed:b928cd6d:81a874bc
#devices=/dev/sdc,/dev/sdd

```

```
root@griffie:/home/david# fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x869726ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9872    79296808+  83  Linux
/dev/sda2            9873        9964      738990    5  Extended
/dev/sda5            9873        9964      738958+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94719471

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table
```

---

### Post by flick152 on 2009-04-30
Ok so i've played around some it looks a bit more promising but still no cigar

```
root@griffie:/home/nutchy# mdadm -Asv
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdc is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdd is identified as a member of /dev/md0, slot 1.
mdadm: added /dev/sdd to /dev/md0 as 1
mdadm: failed to add /dev/sdc to /dev/md0: Invalid argument
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.
mdadm: looking for devices for further assembly
mdadm: cannot open device /dev/sdd: Device or resource busy
/dev/md0: File exists
mdadm: /dev/sdc is identified as a member of /dev/md/0, slot 0.
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: looking for devices for further assembly
```

---

### Post by gurak2005 on 2009-04-30
same problem with a test raid5 in a vmware virtual machine

updating kernel crash the raid at boot time

but the info is still in the raid

---

### Post by fjgaude on 2009-04-30
The old /etc/mdadm/mdadm.conf file is no longer valid. Try this and then re-boot:

```
sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```

That should do it, if not, come back here.

---

### Post by gurak2005 on 2009-04-30
thanks, it's works for me.

---

### Post by flick152 on 2009-04-30
```
root@griffie:/home/nutchy# mdadm --examine --scan
ARRAY /dev/md0 level=raid0 num-devices=2 UUID=616e78cd:fc386bed:b928cd6d:81a874bc
root@griffie:/home/nutchy# mdadm --examine --scan >> /etc/mdadm/mdadm.conf
```

Then I #'ed out the old line in mdadm.conf

```
root@griffie:/home/nutchy# mdadm -Asv
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdc is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdd is identified as a member of /dev/md0, slot 1.
mdadm: added /dev/sdd to /dev/md0 as 1
mdadm: failed to add /dev/sdc to /dev/md0: Invalid argument
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.
mdadm: looking for devices for further assembly
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: /dev/sdc is identified as a member of /dev/md/0, slot 0.
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: looking for devices for further assembly

```

---

### Post by fjgaude on 2009-04-30
Flick152: Show us your mdadm.conf file... we can get to the bottom of this with patience (and knowledge).

---

### Post by flick152 on 2009-05-01
This is my mdadm.conf as it is atm

```
root@griffie:/home/david# cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE /dev/sdc /dev/sdd #partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Thu, 25 Dec 2008 17:01:49 +1300
# by mkconf
#ARRAY /dev/md0 level=raid0 num-devices=2 metadata=0.90 UUID=616e78cd:fc386bed:b928cd6d:81a874bc

ARRAY /dev/md0 level=raid0 num-devices=2 UUID=616e78cd:fc386bed:b928cd6d:81a874bc

```

---

### Post by fjgaude on 2009-05-01
Hmmm... this is not the mdadm.conf file created by the --scan.

```
DEVICE /dev/sdc /dev/sdd #partitions
```

Also I'm not sure if this hurts or not. Please just use this:

```
DEVICE partitions
```

See if this gets your array to mount.

---

### Post by flick152 on 2009-05-02
Ok I made that change

```
root@griffie:/home/nutchy# cat /etc/mdadm/mdadm.conf
...
DEVICE partitions
...
ARRAY /dev/md0 level=raid0 num-devices=2 UUID=616e78cd:fc386bed:b928cd6d:81a874bc

```

got this...

```
root@griffie:/home/nutchy# mdadm -Asv
[COLOR="Silver"]mdadm: looking for devices for /dev/md0
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: /dev/sdb1 has wrong uuid.
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: /dev/sdb has wrong uuid.
mdadm: cannot open device /dev/sda5: Device or resource busy
mdadm: /dev/sda5 has wrong uuid.
mdadm: no RAID superblock on /dev/sda2
mdadm: /dev/sda2 has wrong uuid.
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: /dev/sda1 has wrong uuid.
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/sda has wrong uuid.
[/COLOR]mdadm: /dev/sdd is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdc is identified as a member of /dev/md0, slot 0.
mdadm: added /dev/sdd to /dev/md0 as 1
mdadm: failed to add /dev/sdc to /dev/md0: Invalid argument
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.
mdadm: looking for devices for further assembly
mdadm: cannot open device /dev/sdd: Device or resource busy[COLOR="Silver"]
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: cannot open device /dev/sda5: Device or resource busy
mdadm: no RAID superblock on /dev/sda2
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy
[/COLOR]mdadm: /dev/sdc is identified as a member of /dev/md/0, slot 0.
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
[COLOR="Silver"]mdadm: looking for devices for further assembly
mdadm: no recogniseable superblock on /dev/sda2[/COLOR]

```

dmesg output 
```
[   52.186155] md: sdd has same UUID but different superblock to sdc
[   52.186162] md: sdd has different UUID to sdc
[   52.186164] md: export_rdev(sdd)
[COLOR="Silver"][   52.676682] ppdev0: registered pardevice
[   52.759687] ppdev0: unregistered pardevice
[   60.352032] eth1: no IPv6 routers present[/COLOR]
[   99.310705] md: md0 stopped.
[   99.310729] md: unbind<sdc>
[   99.310841] md: export_rdev(sdc)
[   99.342162] md: bind<sdd>
[   99.342727] md: sdc has same UUID but different superblock to sdd
[   99.342731] md: sdc has different UUID to sdd
[   99.342733] md: export_rdev(sdc)
[   99.348211] md: array md0 already has disks!
[126944.368242] md: md0 stopped.
[126944.368266] md: unbind<sdd>
[126944.368463] md: export_rdev(sdd)
[126944.419330] md: bind<sdd>
[126944.419822] md: sdc has same UUID but different superblock to sdd
[126944.419826] md: sdc has different UUID to sdd
[126944.419828] md: export_rdev(sdc)
[126944.446430] md: array md0 already has disks!

```

---

### Post by fjgaude on 2009-05-02
Well, some folks have had issues using the whole drive and not a partition of the drive, like sdb1 instead of sdb... even through sdb1 is a partition of the whole drive. Can't say if that is an issue here.

The only thing left is to try a forced assembly:

```
sudo mdadm --assemble --force /dev/md0
```

There's something at issue with sdc from reading the logs, eh?

---

### Post by flick152 on 2009-05-03
Can't even force it

```
root@griffie:/home/nutchy# mdadm -Af /dev/md0
mdadm: SET_ARRAY_INFO failed for /dev/md0: Device or resource busy

root@griffie:/home/nutchy# mdadm --assemble --force /dev/md0 /dev/sdc /dev/sdd
mdadm: failed to add /dev/sdc to /dev/md0: Invalid argument
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.

```

```
[77881.759077] md: md0 still in use.
[77881.817910] md: array md0 already has disks!
[77881.982294] md: sdc has same UUID but different superblock to sdd
[77881.982301] md: sdc has different UUID to sdd
[77881.982304] md: export_rdev(sdc)
[78980.828088] md: md0 still in use.
[78980.883480] md: array md0 already has disks!
[78980.926417] md: sdc has same UUID but different superblock to sdd
[78980.926424] md: sdc has different UUID to sdd
[78980.926427] md: export_rdev(sdc)
[79015.283112] md: md0 stopped.
[79015.283136] md: unbind<sdd>
[79015.283255] md: export_rdev(sdd)
[79015.286421] md: bind<sdd>
[79015.286662] md: sdc has same UUID but different superblock to sdd [COLOR="Red"]<-- Is this relevant?[/COLOR]
[79015.286665] md: sdc has different UUID to sdd
[79015.286667] md: export_rdev(sdc)
[79015.370519] md: sdc has same UUID but different superblock to sdd
[79015.370525] md: sdc has different UUID to sdd
[79015.370528] md: export_rdev(sdc)
```

```
root@griffie:/home/nutchy# mdadm -Ev /dev/sdc
/dev/sdc:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 616e78cd:fc386bed:b928cd6d:81a874bc (local to host griffie)
  Creation Time : Sat Mar  7 18:56:48 2009
     Raid Level : raid0
  Used Dev Size : 0
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0 [COLOR="Red"]<--**  Should these be different?[/COLOR]

    Update Time : Sat Mar  7 18:56:48 2009
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : d5088fc1 - correct
         Events : 1

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        0        0      active sync   /dev/sda

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb

```
```
root@griffie:/home/nutchy# mdadm -Ev /dev/sdd
/dev/sdd:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 616e78cd:fc386bed:b928cd6d:81a874bc (local to host griffie)
  Creation Time : Sat Mar  7 18:56:48 2009
     Raid Level : raid0
  Used Dev Size : 0
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 127[COLOR="Red"]<--**[/COLOR]

    Update Time : Sat Mar  7 18:56:48 2009
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : d5089052 - correct
         Events : 1

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       16        1      active sync   /dev/sdb

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb

```

---

### Post by fjgaude on 2009-05-03
Gosh, there's something decidedly wrong here. When you examine sdc/d the data shows that sda/b is of the array.

Did you use the sda/b drives in the md0 array before?

---

### Post by flick152 on 2009-05-03
Yes before I upgraded to jaunty these two hard disks where at sda & sdb 

I have 4 hdds currenly sda/b are on the standard IDE controller and sdc/d are on my raid controller (pseudo raid I ditched dmraid for mdadm)

so jaunty switched sda/b and sdc/d around

```
root@griffie:/home/nutchy# fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x869726ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9872    79296808+  83  Linux
/dev/sda2            9873        9964      738990    5  Extended
/dev/sda5            9873        9964      738958+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94719471

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

```

---

### Post by fjgaude on 2009-05-03
The switching of drive names is unimportant to **mdadm**, as it uses the array UUID to assemble. That UUID is the same for each drive of an array.

So, we have issues with your setup...

What does this show:

```
sudo mdadm -D /dev/md0
```

Being able to run this command means the array is assembled!

---

### Post by flick152 on 2009-05-04
```
root@griffie:/home/david# mdadm -D /dev/md0
mdadm: md device /dev/md0 does not appear to be active.

```

---

### Post by fjgaude on 2009-05-04
Looking your log sheets, it seems you are in a bad way. 

> [79015.286662] md: sdc has same UUID but different superblock to sdd <-- Is this relevant?

Yes, it is. Indicates drive used in anothe array, or something like that.

> Preferred Minor : 0 <--**  Should these be different?

That's okay... the "0" is the start point for device ID for /md0 arrays.

I don't have any suggestion other than to start over. That will require you to zero the superblocks of the two drives to be used in the new array.

I guess you could go back to your old OS and see what happens.

---

### Post by joeinbend on 2009-05-05
I've been battling with the same problem on my setup: I have a RAID5 NAS that was running 8.10, with MDADM 2.6.8, when I updated to 9.04 I got similar results: array failed to assemble, stating that two of the 4 disks were unavailable. examining each disk, they have the correct UUID. I was able to force them to assmeble:
sudo mdadm --assemble /dev/md0 /dev/sdb /dev/sdc /dev/sdd /dev/sde --force

Doing that it assmbled clean, I just had to re-mount it for my Samba share to be visable. I am completing a full backup of my criticial data from the array, and am going to wipe and do a clean install of 8.04 LTS, and I should be able to mount the array clean without --force. 

Not sure exactly what the issue is with MDADM on 9.04. I tried removing mdadm and re-adding it (sudo apt-get purge mdadm, sudo apt-get install mdadm, reboot), which rolled me to version 2.6.7.1, with the same results.

I imagine the perminant fix will be a new version release of MDADM, if that is possible.

---

### Post by fjgaude on 2009-05-05
> Not sure exactly what the issue is with MDADM on 9.04. I tried removing mdadm and re-adding it (sudo apt-get purge mdadm, sudo apt-get install mdadm, reboot), which rolled me to version 2.6.7.1, with the same results.

From what little I've seen is 9.04 changes the UUID value of the array, and we then need to get the new one into the mdadm.conf file. That's it. One way to do that is:

```
sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```

Or you can auto create a new mdadm.conf file by uninstalling mdadm, re-naming or deleting mdadm.conf, then re-booting, re-installing mdadm, and run this:

```
sudo mdadm --assemble --scan
```

Then you are good to go with a new auto-created mdadm.conf file.

---

### Post by joeinbend on 2009-05-05
I found on mine i was actually able to fix it by changing the ARRAY line in my mdadm.conf. the UUID was correct still, but I changed:

ARRAY /dev/md0 uuid=insert:uuid:here

to.... :
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=insert:uuid:here


Rebooted, everything worked normally after that. very strange.

---

### Post by micster on 2009-05-05
I was experiencing similar symptoms as you, I was getting "device busy" and mismatching "superblock" when I was trying to create my mdadm software RAID.

If I booted with my RAID drives connected I would get an error "Initialization of HAL failed!" and if I disconnected them during boot everything would be fine. I checked my syslog and came across a segfault error for hald.

Here is a bug report [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/361689]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/361689") that seemed to address my problem exactly.

I upgraded Hal using the PPA listed in the above bug report and now my problem is fixed! I can successfully boot and mount my software raid again (and I no longer lose my keyboard and mouse either).

-Mic

---

### Post by flick152 on 2009-05-07
I have noticed that one disk will assemble onto md0 and the other will assemble onto md127 they switch depending what I set the md to be in mdadm.conf

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/[COLOR="Red"]md127[/COLOR] level=raid0 num-devices=2 UUID=616e78cd:fc386bed:b928cd6d:81a874bc

```

This mdadm.conf yeilds...

```
root@griffie:/home/nutchy# mdadm -Asv
mdadm: looking for devices for /dev/md127
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: /dev/sdc has wrong uuid.
[COLOR="Silver"]mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: /dev/sdb1 has wrong uuid.
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: /dev/sdb has wrong uuid.
mdadm: cannot open device /dev/sda5: Device or resource busy
mdadm: /dev/sda5 has wrong uuid.
mdadm: no RAID superblock on /dev/sda2
mdadm: /dev/sda2 has wrong uuid.
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: /dev/sda1 has wrong uuid.
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/sda has wrong uuid.[/COLOR]
mdadm: /dev/sdd is identified as a member of /dev/md127, slot 1.
mdadm: no uptodate device for slot 0 of /dev/md127
mdadm: added /dev/[COLOR="Red"]sdd[/COLOR] to /dev/[COLOR="Red"]md127[/COLOR] as 1
mdadm: /dev/md127 assembled from 1 drive - not enough to start the array.
[COLOR="Silver"]mdadm: looking for devices for further assembly
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: cannot open device /dev/sda5: Device or resource busy
mdadm: no recogniseable superblock on /dev/sda2
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy[/COLOR]

```

If I change THE ARRAY line to md0 I get the other hdd

```
ARRAY /dev/[COLOR="Red"]md0[/COLOR] level=raid0 num-devices=2 UUID=616e78cd:fc386bed:b928cd6d:81a874bc
```

```
root@griffie:/home/nutchy# mdadm -Asv
mdadm: looking for devices for /dev/md0
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: /dev/sdd has wrong uuid.
[COLOR="Silver"]mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: /dev/sdb1 has wrong uuid.
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: /dev/sdb has wrong uuid.
mdadm: cannot open device /dev/sda5: Device or resource busy
mdadm: /dev/sda5 has wrong uuid.
mdadm: no RAID superblock on /dev/sda2
mdadm: /dev/sda2 has wrong uuid.
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: /dev/sda1 has wrong uuid.
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/sda has wrong uuid.[/COLOR]
mdadm: /dev/sdc is identified as a member of /dev/md0, slot 0.
mdadm: no uptodate device for slot 1 of /dev/md0
mdadm: added /dev/[COLOR="Red"]sdc[/COLOR] to /dev/[COLOR="Red"]md0[/COLOR] as 0
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.
[COLOR="Silver"]mdadm: looking for devices for further assembly
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: cannot open device /dev/sda5: Device or resource busy
mdadm: no recogniseable superblock on /dev/sda2
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy[/COLOR]

```

These match up with the prefered minor in the superblocks

---

### Post by flick152 on 2009-05-09
Is there a way to change the prefered minor number?

---

### Post by flick152 on 2009-05-14
[SIZE="7"]**FIXED!**[/SIZE] :D\\:D/:guitar: 

but not sure quite what did it

[LIST]
[*]Installed mdadm from Jonas Pedersen PPA
[*]Rebooted got repair console ("Enter root password or Control-D to continue")
[*]ran mdadm -As -U super-minor
[/LIST]

It assembled and is working great.

Not sure if it was the ppa or the -AU super-minor used straight after a reboot.
Both drives' superblocks' have prefered minors of 0 now.

I haven't risked a reboot yet gonna do a backup first.

---

### Post by fjgaude on 2009-05-14
> ran mdadm -As -U super-minor

I would say running the above command did the trick... Thank God for man pages, eh?

Happy to see you are up and running again.

---

### Post by cyberkost on 2009-06-21
I'm suspecting Jaunty upgrade of hurting my RAID setup too ... I posted below in a different thread, but did not receive any responses ... guilty of cross-posting, but hoping someone here may spot what the problem might be.  Please HELP!

I've got 4 320GB Seagate 7200.11 drives and have the following RAIDs (using mdadm) across them:```
/dev/md0  /boot  RAID0
/dev/md1  /      RAID10
/dev/md2  /home  RAID10
```
I'm monitoring the status of my RAIDs via conky (screenshot below) ... I've noticed a strange thing that after about a day of running /dev/sdb fails for both of my RAID10 devices:```

cyberkost@raidbox:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid10 sdb3[4](F) sdc3[3] sda3[1] sdd3[2]
      552779776 blocks 256K chunks 2 far-copies [4/3] [_UUU]

md1 : active raid10 sda2[1] sdc2[3] sdb2[4](F) sdd2[2]
      67103232 blocks 64K chunks 2 far-copies [4/3] [_UUU]

md0 : active raid1 sda1[1] sdc1[3] sdb1[0] sdd1[2]
      1052160 blocks [4/4] [UUUU] 

unused devices: <none>
```
This is also signaled by the HDD activity LED being constantly on (though no audible HDD activity).  If I try to add /dev/sdb[2,3] partitions back to their respective arrays, I get:```

cyberkost@raidbox:~$ sudo mdadm --add /dev/md1 /dev/sdb2 
mdadm: Cannot open /dev/sdb2: Device or resource busy
```
The HDD activity LED goes off after about a day or two and I can add the partition back after that.  Alternatively, I can just reboot the machine and although it takes a while (2-3 hours) to come up, I can add the /dev/sdb[2,3] partitions back to their RAID devices when start-up is completed (the machine comes up with /dev/sdb[2,3] missing).

Originally I thought that the HDD that corresponds to /dev/sdb is going bad or the corresponding SATA cable/channel on the motherboard have become faulty, but from reading [post1](http://ubuntuforums.org/showpost.php?p=7294387&postcount=25) and [post2 it references](http://ubuntuforums.org/showpost.php?p=7220050&postcount=19) I started to suspect that it's the upgrade to Jaunty 9.04 that messed my mdadm RAID up.

My suspicions are further deepened by the following facts:
1. sudo smartctl -a /dev/sdb days the drive is fine (and the output for /dev/sdb looks VERY similar to that for the other 3 drives)
2. I first noticed the problem shortly after the upgrade to 9.04, I have not had a problem for a year prior to that.
3. /proc/mdstat used to list /sdaX /sdbX /sdcX /sddX for all 3 RAID devices prior to upgrade (ABCD order).  It now has ACBD for /dev/md[0,1] and BCAD for /dev/md2.
4. Looking at mdadm.conf I find UUID contsucts to look rather suspicious -- the last two blocks are the same for all /dev/md[1,2,3], while the first two are different:```

cyberkost@raidbox:~$ cat /etc/mdadm/mdadm.conf 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=4 UUID=20eef32f:87dc5eba:e368bf24:bd0fce41
ARRAY /dev/md1 level=raid10 num-devices=4 UUID=bacf8d29:0b16d983:e368bf24:bd0fce41
ARRAY /dev/md2 level=raid10 num-devices=4 UUID=67665d86:1cc558d5:e368bf24:bd0fce41

# This file was auto-generated on Thu, 01 Jan 2009 00:37:24 +0000
# by mkconf $Id$
```
I'd naively expect those UUID fields to be the same across all 3 RAID devices (e.g., if each block is a reference to a particular physical HDD) or be completely different (e.g., if each block is a reference to a particular superblock/parition).
5. Lastly, I see that mdadm.conf has the date of my upgrade to Ubuntu 9.04 Jaunty Jackalope:```

cyberkost@raidbox:~$ ls -la /etc/mdadm/mdadm.conf 
-rw-r--r-- 1 root root 874 2009-04-25 23:09 /etc/mdadm/mdadm.conf
``` ... and no, there's no backup file left :(

I checked if following the advice offered in [post2](http://ubuntuforums.org/showpost.php?p=7220050&postcount=19) is going to help, but it seems that it will not ... b/c the command returns the configuration that's already part of my 9.04 mdadm.conf```

cyberkost@raidbox:~$ sudo mdadm --examine --scan --config=mdadm.conf
[sudo] password for kost: 
ARRAY /dev/md0 level=raid1 num-devices=4 UUID=20eef32f:87dc5eba:e368bf24:bd0fce41
ARRAY /dev/md1 level=raid10 num-devices=4 UUID=bacf8d29:0b16d983:e368bf24:bd0fce41
ARRAY /dev/md2 level=raid10 num-devices=4 UUID=67665d86:1cc558d5:e368bf24:bd0fce41

```

EDIT TO ADD:
My /dev/md0 raid1 just got affected!!!```

cyberkost@raidbox:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid10 sdb3[4](F) sdc3[3] sda3[1] sdd3[2]
      552779776 blocks 256K chunks 2 far-copies [4/3] [_UUU]
      
md1 : active raid10 sda2[1] sdc2[3] sdb2[4](F) sdd2[2]
      67103232 blocks 64K chunks 2 far-copies [4/3] [_UUU]
      
md0 : active raid1 sda1[1] sdc1[3] sdb1[4](F) sdd1[2]
      1052160 blocks [4/3] [_UUU]
      
unused devices: <none>
```

---

### Post by joeinbend on 2009-06-22
CyberKost:
Thanks for doing a real post! Nothing makes people crazier faster than when someone comes in and posts "It broke, I cant figure out what's wrong, fix it for me now!!" with zero details! ...I digress...

I had very similar symptoms to what you are experiencing when I first upgraded to 9.04. For me, the fix was to force the arrays to assemble, then a change to my mdadm.conf (which yours already looks fine), reboot and I havent had a seconds' trouble. Try doing a force assemble with: 

sudo mdadm --assemble /dev/md0 /dev/sdb /dev/sdc /dev/sdd /dev/sde --force
(with your actual /dev/'s of course!)

...and let us know if that does the trick.

---

