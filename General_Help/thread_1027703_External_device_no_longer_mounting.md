---
title: "External device no longer mounting"
date: 2009-01-01
forum: General Help
---

### Post by Greevous on 2009-01-01
I've used a Maxtor OneTouch for a while now, successfully under Intrepid, formatted as ext3, but now suddenly Ubuntu won't mount it.

I believe that it has something to do with me booting into windows for a minute to take care of something, and when I restarted that's when the problems began. 

sdb is not listed in an fdisk -l command, and running gparted outputs "Could not stat device /dev/sdb - No such file or directory."

---

### Post by dcstar on 2009-01-01
> **Greevous said:**
> I've used a Maxtor OneTouch for a while now, successfully under Intrepid, formatted as ext3, but now suddenly Ubuntu won't mount it.

I believe that it has something to do with me booting into windows for a minute to take care of something, and when I restarted that's when the problems began. 

sdb is not listed in an fdisk -l command, and running gparted outputs "Could not stat device /dev/sdb - No such file or directory."

Post the output of **dmesg** when you plug the drive in.

---

### Post by Greevous on 2009-01-01
It repeats this over and over:
> [97022.787436] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[97022.787445] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information


then prints this:
```
[97028.460098] usb 1-3: USB disconnect, address 2
[97028.510422] scsi 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[97028.510432] end_request: I/O error, dev sdb, sector 320170752
[97028.510438] Buffer I/O error on device sdb, logical block 40021344
[97028.510458] Buffer I/O error on device sdb1, logical block 1
[97028.510462] Buffer I/O error on device sdb1, logical block 2
[97028.510465] Buffer I/O error on device sdb1, logical block 3
[97028.510468] Buffer I/O error on device sdb1, logical block 4
[97028.510471] Buffer I/O error on device sdb1, logical block 5
[97028.510474] Buffer I/O error on device sdb1, logical block 6
[97028.510477] Buffer I/O error on device sdb1, logical block 7
[97028.510480] Buffer I/O error on device sdb1, logical block 8
[97028.510483] Buffer I/O error on device sdb1, logical block 9
[97028.510492] scsi 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[97028.510496] end_request: I/O error, dev sdb, sector 63
[97038.992102] usb 1-3: new high speed USB device using ehci_hcd and address 10
[97039.182510] usb 1-3: configuration #1 chosen from 1 choice
[97039.231732] scsi11 : SCSI emulation for USB Mass Storage devices
[97039.242793] usb-storage: device found at 10
[97039.242808] usb-storage: waiting for device to settle before scanning
[97044.240166] usb-storage: device scan complete
[97044.446580] scsi 11:0:0:0: Direct-Access     Maxtor   OneTouch         0201 PQ: 0 ANSI: 0 CCS
[97044.516261] sd 11:0:0:0: [sdb] 320171008 512-byte hardware sectors (163928 MB)
[97044.723011] sd 11:0:0:0: [sdb] Write Protect is off
[97044.723020] sd 11:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[97044.723023] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[97044.727350] sd 11:0:0:0: [sdb] 320171008 512-byte hardware sectors (163928 MB)
[97044.935047] sd 11:0:0:0: [sdb] Write Protect is off
[97044.935065] sd 11:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[97044.935072] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[97044.936784]  sdb: sdb1 sdb2
[97044.995390] sd 11:0:0:0: [sdb] Attached SCSI disk
[97045.008677] sd 11:0:0:0: Attached scsi generic sg3 type 0

```

then it repeats the original two lines.

---

### Post by taurus on 2009-01-01
So you have two partitions, /dev/sdb1 & /dev/sdb2, on that external harddrive? 

Can you post the output of this command again?

```
sudo fdisk -l
```

---

### Post by Greevous on 2009-01-01
Yes, two partitions is correct.
This is the output from fdisk -l:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7b0e7b0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4246    34105963+   7  HPFS/NTFS
/dev/sda2            4247        9728    44034165    5  Extended
/dev/sda5            4247        5551    10482381   83  Linux
/dev/sda6            5552        5812     2096451   82  Linux swap / Solaris
/dev/sda7            5813        9728    31455238+  83  Linux

```

Nothing there about the external drive, which is a 160 GB volume.

---

### Post by zero777zero on 2009-01-01
i had a similar problem with a NTFS drive. when you start windows, windows will mount the drive automatically. i'm not sure your issue will work out like mine did, but i suggest you boot into windows turn your ext drive on, right click the drive symbol and choose "safely remove", then shut the drive off and boot back into ubuntu.. that worked for my issue. i think the problem has something to do with the way windows treats drives that aren't removed in this manner.

---

### Post by Greevous on 2009-01-01
> **zero777zero said:**
> i had a similar problem with a NTFS drive. when you start windows, windows will mount the drive automatically. i'm not sure your issue will work out like mine did, but i suggest you boot into windows turn your ext drive on, right click the drive symbol and choose "safely remove", then shut the drive off and boot back into ubuntu.. that worked for my issue. i think the problem has something to do with the way windows treats drives that aren't removed in this manner.

Yeah, I thought about this, but windows didn't exactly mount the drive. Maybe it's because windows doesn't "do" ext3, or maybe not, but there was no way to safely remove. However, unplugging and plugging in the drive does garner a reaction, with the little "new hardware" sound, etc.

---

### Post by taurus on 2009-01-01
Try

```
lsusb
```
Wait for a few seconds and then run this command again to see if the external drive shows up at all.

```
sudo fdisk -l
```

---

### Post by zero777zero on 2009-01-01
> **Greevous said:**
> Yeah, I thought about this, but windows didn't exactly mount the drive. Maybe it's because windows doesn't "do" ext3, or maybe not, but there was no way to safely remove. However, unplugging and plugging in the drive does garner a reaction, with the little "new hardware" sound, etc.

idk about that. for whatever reason vista doesnt properly recognize a NTFS drive i use for ubuntu. if i plug it in while i'm booted on vista it asks to format the drive. if i STILL don't safely remove it, then the drive doesnt work in ubuntu. so i have to boot back over to windows, right click, safely remove, shut down, then it works again. like i said, might not be the same for u but worth a try.

---

### Post by Greevous on 2009-01-01
Taurus, still not showing up, even though lsusb does print a line about the Maxtor drive:

```
Bus 001 Device 010: ID 0d49:7000 Maxtor OneTouch

```

---

### Post by taurus on 2009-01-01
Plug it back in again.

---

### Post by Greevous on 2009-01-01
That didn't change anything, taurus.

---

