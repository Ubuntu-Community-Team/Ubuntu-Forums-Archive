---
title: "External hard drivce not being detected. Was working before"
date: 2006-02-12
forum: Desktop Environments
---

### Post by ade234uk on 2006-02-12
External hard drive has been working great but has suddenly stopped being detected by Ubuntu.

I have noticed that if it is ON whilst Ubuntu is booting, Ubuntu freezes at the line that says hotplugging system.

If I turn it off and restart my machine Ubuntu loads without any problems.

When I turn the hard drive on whilst using Ubuntu the drive does not appear on the desktop.

---

### Post by ade234uk on 2006-02-12
PLease can someone help meI does not appear on the desktop.

---

### Post by christhemonkey on 2006-02-12
You need to make sure to have it listed in your fstab file.

---

### Post by ade234uk on 2006-02-12
It appears that it is no longer listed in the fstab file. What do I need to enter?
Is it somethink like /dev/usb* ??????

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0```

```

---

### Post by cdhotfire on 2006-02-12
Do
```

$ sudo fdisk -l

```
and look if its there.

---

### Post by ade234uk on 2006-02-13
Ok I just entered the command in to shell and I have copied and pasted the following. 

There is no mention of a usb drive. At least I am learning something here. Thank you for your continued help. If you could guide me through the rest I will write this down just in case it happens again.

Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4664    37463548+  83  Linux
/dev/hdc2            4665        4865     1614532+   5  Extended
/dev/hdc5            4665        4865     1614501   82  Linux swap / Solaris
adrian@ubuntu:~$

---

### Post by ade234uk on 2006-02-13
I hope someone can help us

---

### Post by cdhotfire on 2006-02-13
Hmm, try disconnecting it and reconnecting it, and then turn it on, and do the command again.
Something like this should come out
```

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *       15611       19457    30901027+  83  Linux
/dev/hda2           15368       15610     1951897+  82  Linux swap / Solaris
/dev/hda3               1       14151   113667876   83  Linux
/dev/hda4           14152       15367     9767520   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 255 MB, 255066112 bytes
16 heads, 32 sectors/track, 973 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         973      249037+   6  FAT16

```
Second drive being the external.

If it still doesnt show up, try rebooting and turning on drive again.  If it still doesnt show up, let me know, I will try and think of something else. :)

---

### Post by Oxygene on 2006-02-13
Is it a USB drive?

Try "lsusb" on the console, this should show you if the usb device is connected properly. I have two USB drives and a USB hub plugged in at the moment and it gives me the following output:

```
Bus 004 Device 004: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter
Bus 004 Device 003: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter
Bus 004 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```

You could also install the hal-device-manager (use synaptic for this pupose) and run it. Look for USB devices there and see if something happens when you plug in the device.

---

### Post by ade234uk on 2006-02-13
**cdhotfire** 
I tried the command again and followed the instructions and it is still showing only one hard drive as follows

Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4664    37463548+  83  Linux
/dev/hdc2            4665        4865     1614532+   5  Extended
/dev/hdc5            4665        4865     1614501   82  Linux swap / Solaris
adrian@ubuntu:~$

**Oxygene** 
Yes it is a USB drive. I tried the command and nothing comes up. I hope my hard drive has not gone wrong because I got loads of data on it.

Like I said if I have the external hard drive on whilst Ubuntu is booting up it stalls at the line hotplugging.

Any more ideas would be great.

---

### Post by Oxygene on 2006-02-13
check some log files for error messages.
Open a console window and type
```
tail -f /var/log/kern.log
```
The -f stands for "follow" and it will show you new entries in the log file on-the-fly. Now plug your device in and see if something is shown in the logs.

Here an example of what appears in the kern.log when i plugin my usb harddrive:
```

Feb 14 00:19:24 localhost kernel: [4329452.787000] usb 4-1: new high speed USB device using ehci_hcd and address 5
Feb 14 00:19:24 localhost kernel: [4329452.893000] scsi2 : SCSI emulation for USB Mass Storage devices
Feb 14 00:19:24 localhost kernel: [4329452.897000] usb-storage: device found at 5
Feb 14 00:19:24 localhost kernel: [4329452.897000] usb-storage: waiting for device to settle before scanning
Feb 14 00:19:30 localhost kernel: [4329457.902000]   Vendor: WDC WD12  Model: 00JB-00CRA1       Rev: 0000
Feb 14 00:19:30 localhost kernel: [4329457.902000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Feb 14 00:19:30 localhost kernel: [4329457.912000] SCSI device sdb: 234441648 512-byte hdwr sectors (120034 MB)
Feb 14 00:19:30 localhost kernel: [4329457.912000] sdb: assuming drive cache: write through
Feb 14 00:19:30 localhost kernel: [4329457.927000] SCSI device sdb: 234441648 512-byte hdwr sectors (120034 MB)
Feb 14 00:19:30 localhost kernel: [4329457.927000] sdb: assuming drive cache: write through
Feb 14 00:19:30 localhost kernel: [4329457.927000]  /dev/scsi/host2/bus0/target0/lun0: p1
Feb 14 00:19:30 localhost kernel: [4329457.949000] Attached scsi disk sdb at scsi2, channel 0, id 0, lun 0
Feb 14 00:19:30 localhost kernel: [4329457.957000] usb-storage: device scan complete
```

---

### Post by ade234uk on 2006-02-13
Looks like my Ubuntu is ill. This is all good experience Im learning loads.

adrian@ubuntu:~$ tail -f /var/log/kern.log
Feb 13 23:20:48 localhost kernel: [4314202.027000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Feb 13 23:20:48 localhost kernel: [4314202.027000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Feb 13 23:26:24 localhost kernel: [4314537.232000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Feb 13 23:26:24 localhost kernel: [4314537.232000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Feb 13 23:26:24 localhost kernel: [4314537.698000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Feb 13 23:26:24 localhost kernel: [4314537.698000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Feb 13 23:27:27 localhost kernel: [4314601.152000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Feb 13 23:27:27 localhost kernel: [4314601.152000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Feb 13 23:29:09 localhost kernel: [4314702.948000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Feb 13 23:29:09 localhost kernel: [4314702.948000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.

---

### Post by Oxygene on 2006-02-13
uh.... this seems to have nothing to do with your usb drive. maybe you have a keyboard with some special buttons that are not supported by your current keyboard configuration, but this should do no harm.

are other USB devices working correctly? Did you try out another USB port?

---

### Post by ade234uk on 2006-02-14
OK i checked the other usb ports and the drive is not being detected here either. I tried the drive in Windows and it is being detected.

All my other USB devices are working correctly as well.

Strange I dont know what else to try at the moment, apart from a complete reinstall however this seems a bit harsh for such a minor problem.

---

### Post by www.rzr.online.fr on 2008-04-28
I am testing this drive w/ brasero, will tell if it works w/ hardy 


* edit: It worked flawlessly out of the box on a DVDRW

-- 
[http://rzr.online.fr/q/ide](http://rzr.online.fr/q/ide)

---

### Post by vanadium on 2008-04-28
It if is not seen by the "sudo fdisk -l" command then it is likely a hardware problem, which can range from a defect on the drive to a bad USB cable or USB connection. Test different USB ports, try another cable, try another machine.

The behaviour you decribe in your first post to me sounds like a problem with the drive itself.

With respect to the dmesg command, you should connect the drive and after that run the dmesg command. We now only saw messages related to something else.

---

