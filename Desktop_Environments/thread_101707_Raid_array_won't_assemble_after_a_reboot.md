---
title: "Raid array won't assemble after a reboot"
date: 2005-12-10
forum: Desktop Environments
---

### Post by ioliver on 2005-12-10
I just rebooted my main server, which has two raid arrays.

/dev/md0 is a raid 5 built from /dev/sd[a-d]
/dev/md1 is a raid 0 built from /dev/sd[e-h]

md0 has assembled and mounted fine, but I can't get md1 to assemble. This is odd as it's worked many times before. At boot time it says no devices found.

Here is what I get if I try manually -
sudo mdadm --assemble /dev/md1 /dev/sd[e-h]
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: /dev/sde has no superblock - assembly aborted

But --examine is happy with all the drives that make up the array
sudo mdadm --examine /dev/sde
/dev/sde:
          Magic : a92b4efc
        Version : 00.90.01
           UUID : 22522c98:40ff7e71:c16d6be5:d6401d24
  Creation Time : Fri May 20 13:56:01 2005
     Raid Level : raid0
    Device Size : 293036096 (279.46 GiB 300.07 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1

    Update Time : Fri May 20 13:56:01 2005
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 3abea2a9 - correct
         Events : 0.1

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8      112        3      active sync   /dev/sdh

   0     0       8       64        0      active sync   /dev/sde
   1     1       8       80        1      active sync   /dev/sdf
   2     2       8       96        2      active sync   /dev/sdg
   3     3       8      112        3      active sync   /dev/sdh

Any ideas what else I can try?

The array definitely doesn't exist as this shows -
cat /proc/mdstat
Personalities : [raid5]
md0 : active raid5 sda[3] sdb[2] sdd[1] sdc[0]
      732595392 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

unused devices: <none>

Is it right that the devices are shown as active?

Thanks

Ian

---

### Post by ioliver on 2005-12-11
Is there anything else I can do to check the status of the drives?  Why might they be busy?

I can dd from the underlying drives just fine, so I'm not sure why mdadm can't access them.

Ian

---

### Post by ioliver on 2005-12-11
More info from using strace

open("/dev/sde", O_RDONLY|O_EXCL)       = -1 EBUSY (Device or resource busy)
write(2, "mdadm: cannot open device /dev/s"..., 60mdadm: cannot open device /dev/sde: Device or resource busy
) = 60
write(2, "mdadm: /dev/sde has wrong uuid.\n", 32mdadm: /dev/sde has wrong uuid.
) = 32

It looks like the exclusive open to sde is failing. I tried using lsof to see what else had sde open but can't see anything.

Help!

Ian

---

### Post by ioliver on 2005-12-13
I guess I need to slap this on bugzilla.  Anyone care to suggest a category?
Ian

---

### Post by ioliver on 2005-12-14
[http://bugzilla.ubuntu.com/show_bug.cgi?id=20949](http://bugzilla.ubuntu.com/show_bug.cgi?id=20949)

---

### Post by abaddon80 on 2005-12-15
I'm having a similar problem.  I've setup a linear array using the following command:

```
mdadm --create /dev/md1 --level linear --raid-devices 2 /dev/hde1 /dev/hdg1
```

While that starts the linear array just fine, it doesn't restart the linear array after a reboot.  I have another RAID1 array setup, and that starts up at boot-time just fine.  All drives have been set to RAID Autodetect.

Once the system boots, the contents of /proc/mdstat looks like this:
```
# cat /proc/mdstat 
Personalities : [linear] [raid1] 
md1 : inactive linear hde1[0] hdg1[1]
      390716672 blocks 64k rounding
      
md0 : active raid1 hda1[0] hdb1[1]
      245111616 blocks [2/2] [UU]

```

Then I try running 'mdrun':
```
# mdrun 
mdadm: cannot open device /dev/hde1: Device or resource busy
mdadm: /dev/hde1 has no superblock - assembly aborted
mdadm: cannot open device /dev/hde1: Device or resource busy
mdadm: /dev/hde1 has no superblock - assembly aborted
```

Just like your situation, the superblocks of the partitions involved look fine when I run:
```
# mdadm --examine /dev/hde1
/dev/hde1:
          Magic : a92b4efc
        Version : 00.90.01
           UUID : 6312b2cd:d1b19a67:396ccd2b:bad86532
  Creation Time : Thu Dec 15 21:37:52 2005
     Raid Level : linear
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1

    Update Time : Thu Dec 15 21:37:52 2005
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 651f0eaa - correct
         Events : 0.6

       Rounding : 64K

      Number   Major   Minor   RaidDevice State
this     0       7        0        0      active sync   /dev/hde1

   0     0       7        0        0      active sync   /dev/hde1
   1     1       7        1        1      active sync   /dev/hdg1

# mdadm --examine /dev/hdg1
/dev/hdg1:
          Magic : a92b4efc
        Version : 00.90.01
           UUID : 6312b2cd:d1b19a67:396ccd2b:bad86532
  Creation Time : Thu Dec 15 21:37:52 2005
     Raid Level : linear
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1

    Update Time : Thu Dec 15 21:37:52 2005
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 651f0ead - correct
         Events : 0.6

       Rounding : 64K

      Number   Major   Minor   RaidDevice State
this     1       7        1        1      active sync   /dev/hdg1

   0     0       7        0        0      active sync   /dev/hde1
   1     1       7        1        1      active sync   /dev/hdg1

```

I realized the mdrun message "Device or resource busy" makes a little sense since the /dev/md1 array is detected, just not active.  I have to manually run:
```
mdadm --run /dev/md1
``` to get it running.

The strange thing is, if I setup /dev/md1 as a RAID0, it works just fine.  I seem to only have this problem when setting it up as a linear array.  Can anyone shed some light on this problem?

Side note: I tried your /dev/loop workaround... didn't work for me. :(

---

### Post by ioliver on 2005-12-22
Can you try

strace mdrum

this should let you see exactly which OS call is failing and with which error code.

Thanks

Ian

---

### Post by abaddon80 on 2006-01-04
The messages I got during bootup were so early in the process, I believe it was some problem in the kernel and not a problem with the init scripts.  The message was something about "invalid argument" during the array construction.  I was actually able to find in the kernel source where that message was generated, but not being a kernel hacker, that was about all I could do.  My theory was that it couldn't start the linear array because the kernel option wasnt compiled in, so it had to wait until after the system booted and loaded the module before the linear array could be started.  Unfortunately, I just added a third drive and decided to use a RAID5 instead of doing linear because we needed to get the box online ASAP.

If I get some time, I'll set up another box and try to get some more useful, detailed, information.

---

