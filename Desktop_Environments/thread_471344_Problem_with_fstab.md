---
title: "Problem with fstab"
date: 2007-06-11
forum: Desktop Environments
---

### Post by JoeS on 2007-06-11
I have a IDE hard drive.   When I installed Ubuntu 6.10 the hard drive partitions were listed as hda, but when I installed 7.04 they are listed as sda.  I don't recognize the fstab from Ubuntu 6.10. 

Can anyone tell me what the problem is here or how to fix it?

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ce0c7602-9ab5-4ad0-8f61-a23601a49247 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=55cab43a-d848-4aca-bb3f-fcb42827a743 /home           ext3    defaults        0       2
# /dev/sda2
UUID=7f8b0a41-8c5a-461b-8dc9-f4da26663f98 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by merlinus on 2007-06-11
If you upgrade to the new kernel (-16), it will go back to hd's.

Since fstab is using UUIDs for your partitions, there should not be any problems either way.

-merlin

---

### Post by JoeS on 2007-06-12
What are UUIDs; how do I know if they are right?

I got a lot of error messages in K3b after I installed Ubuntu 7.04.  

> joe@joe-Ubuntu:~$ k3b
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open devicejoe@joe-Ubuntu:~$ k3b
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
joe@joe-Ubuntu:~$ kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
(K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_model_CD_RW_CED_8080B to device /dev/scd0
/dev/scd0 resolved to /dev/scd0
/dev/scd0 is block device (0)
/dev/scd0 seems to be cdrom
bus: 1, id: 0, lun: 0
(K3bDevice::Device) /dev/scd0: init()
(K3bDevice::ScsiCommand) failed: 
joe@joe-Ubuntu:~$ kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
(K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_model_CD_RW_CED_8080B to device /dev/scd0
/dev/scd0 resolved to /dev/scd0
/dev/scd0 is block device (0)
/dev/scd0 seems to be cdrom
bus: 1, id: 0, lun: 0
(K3bDevice::Device) /dev/scd0: init()
including a list like:
> (K3bDevice::ScsiCommand) failed:
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0

---

### Post by mcduck on 2007-06-12
> **JoeS said:**
> What are UUIDs; how do I know if they are right?


UUID is unique string of characters, given to a partition when the partition is formatted (or during Ubuntu install). You can get UUID's for your partitions by running following command:
```
ls -la /dev/disk/by-uuid
```

---

### Post by merlinus on 2007-06-12
For me, this works better in terms of UUIDs:
```

blkid

```

In any event, the results need to match the entries in /etc/fstab.

-merlin

---

### Post by JoeS on 2007-06-12
> **merlinus said:**
> If you upgrade to the new kernel (-16), it will go back to hd's.

I searched the Ubuntu site ; I can't find information on how to upgrade to the new kernel.  Can you direct me to some information;  I need to learn this.

---

### Post by merlinus on 2007-06-12
When updates become available, I get a red icon near the right-hand side of my upper task bar, to the left of date and time.

You might also try System/Administration/Update Manager.

-merlin

---

### Post by JoeS on 2007-06-13
I update whenever I get a notification, but it doesn't fix the fstab.

---

