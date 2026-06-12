---
title: "Flash drive doesn't show"
date: 2009-06-14
forum: General Help
---

### Post by blazemore on 2009-06-14
I can't do anything with my flash drive in Ubuntu Jaunty.

When I insert it, the light flashes, so it's not totally broken.
It works in Windows, so I know it's an Ubuntu related issue.
It's formatted as FAT32 so it's not some obscure filesystem issue
It doesn't show up in fdisk -l, even with no partitions. It's as if it doesn't exist.

Any ideas?

---

### Post by BZF on 2009-06-14
[SIZE=1][COLOR=Blue]did u make sure to download all the updates and driver updates? cus i had the same problem and that fixed it.[/COLOR][/SIZE]

---

### Post by ddrichardson on 2009-06-14
You don't mention the manufacturer or type of drive - are there any messages from dmesg when you plug it in? Is there a device being built in /dev/sd* when it's inserted?

---

### Post by blazemore on 2009-06-14
Here's the relevent lines from dmesg
```

[40414.155120] usb 1-3: new high speed USB device using ehci_hcd and address 16
[40414.281570] usb 1-3: configuration #1 chosen from 1 choice
[40414.282112] scsi15 : SCSI emulation for USB Mass Storage devices
[40414.282684] usb-storage: device found at 16
[40414.282692] usb-storage: waiting for device to settle before scanning
[40419.283701] scsi 15:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[40419.284139] sd 15:0:0:0: Attached scsi generic sg1 type 0
[40419.531215] sd 15:0:0:0: [sdb] 7839744 512-byte hardware sectors: (4.01 GB/3.73 GiB)
[40419.531983] sd 15:0:0:0: [sdb] Write Protect is off
[40419.531994] sd 15:0:0:0: [sdb] Mode Sense: 23 00 00 00
[40419.532002] sd 15:0:0:0: [sdb] Assuming drive cache: write through
[40419.532737] usb-storage: device scan complete
[40419.536188] sd 15:0:0:0: [sdb] Assuming drive cache: write through
[40419.536198]  sdb: sdb1
[40419.537134] sd 15:0:0:0: [sdb] Attached SCSI removable disk

```

So it's working, but fdisk still shows nothing.

---

### Post by ddrichardson on 2009-06-14
Can you mount it manually?

---

### Post by blazemore on 2009-06-15
No. Like I said, it doesn't even show in fdisk -l.
It's usually at /dev/sdb1, but /dev/sdb doesn't exist

---

### Post by ActiveFrost on 2009-06-15
Have you tried to mount another USB Flash ? Maybe the problem is somewhere else, not in your Ubuntu ( probably in your FLASH ) ?

---

### Post by ddrichardson on 2009-06-15
Does it still mount in Windows? Have you tried another USB stick in Ubuntu (to confirm its not an issue with HAL)?

Given that dmesg is registering everything but that /dev/sdb is not being built then you need to report it as a bug, someone who knows about USB can probably help.

---

### Post by linxuser14 on 2009-06-23
Disregard the following, the flash drive described was a "FrankenFlash". So named cause it was a 4 GiB in a 64 GiB case. 

nix: I also have a Kingston DataTraveler flash stick. Mines a 150. 64 GiB. I've had a time with it beginning with my original post of it on [http://kubuntuforums.net](http://kubuntuforums.net) -> forums -> Hardy -> Hardware Support -> 2 posts 1st was 'Re: 64 GB USB Flash Stick [SOLVED-GIVEN UP]' continued in post 'What the heck?' My 1st post(thread) in 'Re: 64 GB ....' showed what fdisk -l showed on it out of the box. It was weird and I didn't understand it. My 2nd post(thread) shows where I had reformatted it somehow with final format done in windowsXP with fat32format.exe and shows my fdisk -l output afterward with nothing in partition table. ("What the heck?") I've since reformatted it with order of partitions out of order. i.e. fat32 made 1st so its /dev/sdb1 but at end of flash stick with 512MiB unallocated after it. Then a reseirFS /dev/sdb2 at the beginning of it and an ext2 /dev/sdb3 between. I was trying to create a Data_storage visible in windows. It has to be /dev/sdb1 for that. and I used 2.8(+-)GiB before it for partitions for a USB Hardy 8.04 Live with persistence. I had trouble with the system not cleanly unmounting the /dev/sdb2 'casper-rw' and had to filesystem check it between each boot until I finally tried formatting it to reseirFS with Gparted Live 0.4.5.3 CD. I guess reseirFS gets filesystem checked with each mount, so it solved that problem. But my point is that the large size flash stick is weird. And I've found that other than fat32 and maybe ntfs, partitions above the 32GiB area kept giving me unknown partitions. Also the weird out of box fdisk -l output. I don't know if any of this is helpful, but thats my 2+cents worth of info on my Kingston DataTraveler.

---

