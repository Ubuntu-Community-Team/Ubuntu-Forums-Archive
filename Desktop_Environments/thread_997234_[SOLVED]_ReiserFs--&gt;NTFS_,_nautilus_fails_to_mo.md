---
title: "[SOLVED] ReiserFs--&gt;NTFS , nautilus fails to mount it."
date: 2008-11-29
forum: Desktop Environments
---

### Post by sksbir on 2008-11-29
Hello

I have an external disk which was Reiserfs formatted.

I reformated it NTFS under windows.

Now, when pugged in , nautilus refuse to mount it , because it still try to recognize a reiserfs disk.

If someone have a idea ??

Thank you
:)

> 
] usb 4-1: new high speed USB device using ehci_hcd and address 3
] usb 4-1: configuration #1 chosen from 1 choice
] usbcore: registered new interface driver libusual
] Initializing USB Mass Storage driver...
] scsi2 : SCSI emulation for USB Mass Storage devices
] usbcore: registered new interface driver usb-storage
] USB Mass Storage support registered.
] scsi 2:0:0:0: Direct-Access     ST320082 2A               3.01 PQ: 0 ANSI: 0 CCS
] sd 2:0:0:0: [sdc] 390721968 512-byte hardware sectors (200050 MB)
] sd 2:0:0:0: [sdc] Write Protect is off
] sd 2:0:0:0: [sdc] 390721968 512-byte hardware sectors (200050 MB)
] sd 2:0:0:0: [sdc] Write Protect is off
]  sdc: sdc1
] sd 2:0:0:0: [sdc] Attached SCSI disk
] sd 2:0:0:0: Attached scsi generic sg3 type 0
] ReiserFS: sdc1: found reiserfs format "3.6" with standard journal
] ReiserFS: sdc1: using ordered data mode
] ReiserFS: sdc1: warning: sh-462: bad transaction max size (1091568769). FSCK?
] ReiserFS: sdc1: warning: sh-2022: reiserfs_fill_super: unable to initialize journal space

---

### Post by Charles4809 on 2008-11-30
I suggest you back up your data and reformat your drive but not under windows. Since it is still recognized as a reiser file system I guess that windows did a bad job in formatting it. Use gparted or something the like.

---

### Post by sksbir on 2008-12-02
> **Charles4809 said:**
> I suggest you back up your data and reformat your drive but not under windows. Since it is still recognized as a reiser file system I guess that windows did a bad job in formatting it. Use gparted or something the like.

Thank you , you where right :) 

I needed to install gparted and ntfsprogs ( either, formatting NTFS is grayed out), reformatting the volume.

After that, the disk was well mounted by ubuntu and by windows.

I don't think that windows is doing a bad job. The disk worked perfect under windows.
I think that windows don't clean the whole disk for non system disk ( e.g. : the boot sector ), and this data are used by nautilus to get the fs type.

---

