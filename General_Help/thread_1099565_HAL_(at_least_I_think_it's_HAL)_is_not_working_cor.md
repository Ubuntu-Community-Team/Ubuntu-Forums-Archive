---
title: "HAL (at least I think it's HAL) is not working correctly with mass storage devices"
date: 2009-03-18
forum: General Help
---

### Post by happyisland on 2009-03-18
Last year I had problems on this computer with getting it to automatically recognize an mp3 player (an Iriver Lplayer to be exact). It was strange, because other computers (windows, mac, and ubuntu) were able to access it without problem. I ended up having to manually mount the player every time I connected it, which was a huge PITA.

Fast forward a few months - I now have a much nicer mp3 player (a cowon S9 - the thing is AWESOME) but am having problems connecting to my phone. When I plug the phone (a Samsung SGHF480L) in to USB it shows up as a mass storage folder. I can browse it in gnome and drag and drop files onto it. 

When I unmount it, it takes a pretty long time (~15 secs) to unmount. When I browse the phone's internal folders the files I transferred via gnome are not there.

If I do the exact same operation on my girlfriend's ubuntu laptop everything works perfectly. 

What gives? Is there a problem with the HAL on this computer? If so, is there something I can do to fix it?

Thanks in advance for any help,

HI

---

### Post by heavenly6mx on 2009-05-09
i have the same problem in ubuntu 9.04 amd64

[13394.050383] Initializing USB Mass Storage driver...
[13394.050562] scsi4 : SCSI emulation for USB Mass Storage devices
[13394.050670] usb-storage: device found at 4
[13394.050674] usb-storage: waiting for device to settle before scanning
[13394.050677] usbcore: registered new interface driver usb-storage
[13394.050685] USB Mass Storage support registered.
[13399.048400] usb-storage: device scan complete
[13399.054744] scsi 4:0:0:0: Direct-Access     SAMSUNG  SGHF480L         1.00 PQ: 0 ANSI: 2
[13399.072386] sd 4:0:0:0: [sdb] 1989632 512-byte hardware sectors: (1.01 GB/971 MiB)
[13399.088113] sd 4:0:0:0: [sdb] Write Protect is off
[13399.088119] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[13399.088122] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[13399.104383] sd 4:0:0:0: [sdb] 1989632 512-byte hardware sectors: (1.01 GB/971 MiB)
[13399.110365] sd 4:0:0:0: [sdb] Write Protect is off
[13399.110370] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[13399.110373] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[13399.110382]  sdb: sdb1
[13399.132461] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[13399.132553] sd 4:0:0:0: Attached scsi generic sg1 type 0
[13475.980060] usb 2-1: reset full speed USB device using ohci_hcd and address 4
[13481.181389] usb 2-1: can't restore configuration #1 (error=-110)
[13481.181458] sd 4:0:0:0: Device offlined - not ready after error recovery
[13481.181471] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[13481.181476] end_request: I/O error, dev sdb, sector 227712
[13481.181517] sd 4:0:0:0: rejecting I/O to offline device
[13481.181536] sd 4:0:0:0: rejecting I/O to offline device
[13481.181540] sd 4:0:0:0: rejecting I/O to offline device
[13481.181566] sd 4:0:0:0: rejecting I/O to offline device
[13481.181601] sd 4:0:0:0: rejecting I/O to offline device
[13481.181624] sd 4:0:0:0: rejecting I/O to offline device
[13481.181646] sd 4:0:0:0: rejecting I/O to offline device
[13481.181669] sd 4:0:0:0: rejecting I/O to offline device
[13481.181691] sd 4:0:0:0: rejecting I/O to offline device
[13481.181714] sd 4:0:0:0: rejecting I/O to offline device
[13481.181739] sd 4:0:0:0: rejecting I/O to offline device
[13481.181762] sd 4:0:0:0: rejecting I/O to offline device
[13481.181784] sd 4:0:0:0: rejecting I/O to offline device
[13481.181807] sd 4:0:0:0: rejecting I/O to offline device
[13481.181829] sd 4:0:0:0: rejecting I/O to offline device
[13481.181851] sd 4:0:0:0: rejecting I/O to offline device
[13481.181873] sd 4:0:0:0: rejecting I/O to offline device
[13481.181895] sd 4:0:0:0: rejecting I/O to offline device
[13481.181919] sd 4:0:0:0: rejecting I/O to offline device
[13481.181943] sd 4:0:0:0: rejecting I/O to offline device
[13481.181971] sd 4:0:0:0: rejecting I/O to offline device
[13481.181976] sd 4:0:0:0: rejecting I/O to offline device
[13481.181983] Buffer I/O error on device sdb1, logical block 28
[13481.181986] lost page write due to I/O error on sdb1
[13481.181990] Buffer I/O error on device sdb1, logical block 29
[13481.181993] lost page write due to I/O error on sdb1
[13481.181998] sd 4:0:0:0: rejecting I/O to offline device
[13481.182001] Buffer I/O error on device sdb1, logical block 271
[13481.182003] lost page write due to I/O error on sdb1
[13481.182008] Buffer I/O error on device sdb1, logical block 272
[13481.182010] lost page write due to I/O error on sdb1
[13481.182016] sd 4:0:0:0: rejecting I/O to offline device
[13481.182019] Buffer I/O error on device sdb1, logical block 488
[13481.182021] lost page write due to I/O error on sdb1
[13481.182026] sd 4:0:0:0: rejecting I/O to offline device
[13481.182029] Buffer I/O error on device sdb1, logical block 583
[13481.182031] lost page write due to I/O error on sdb1
[13481.182036] sd 4:0:0:0: rejecting I/O to offline device
[13481.182039] Buffer I/O error on device sdb1, logical block 1383
[13481.182042] lost page write due to I/O error on sdb1
[13481.182055] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[13481.182059] end_request: I/O error, dev sdb, sector 227952
[13481.182111] usb 2-1: USB disconnect, address 4
[13481.196549] FAT: unable to read inode block for updating (i_pos 7820)
[13481.196585] Buffer I/O error on device sdb1, logical block 583
[13481.196588] lost page write due to I/O error on sdb1
[13481.196594] Buffer I/O error on device sdb1, logical block 487
[13481.196597] lost page write due to I/O error on sdb1
[13481.312734] scsi 4:0:0:0: rejecting I/O to dead device
[13481.380075] usb 2-1: new full speed USB device using ohci_hcd and address 5
[13481.592492] usb 2-1: configuration #1 chosen from 1 choice

---

