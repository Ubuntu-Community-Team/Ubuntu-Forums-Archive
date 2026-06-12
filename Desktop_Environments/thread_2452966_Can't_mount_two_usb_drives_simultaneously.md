---
title: "Can't mount two usb drives simultaneously"
date: 2020-10-31
forum: Desktop Environments
---

### Post by lou6 on 2020-10-31
I use WD Element usb drives (formatted as ntfs) for backup and general file storage.  This morning I tried to copy some files from one to the other (which I have been doing for years) and found that Xubuntu 20.04.1 will mount the first drive but not the second drive.  It does not matter which order I attempt to mount them - the system will not allow them both to be mounted. Any solutions/suggestions will be very welcome.

Thanks.

EDIT:  I also tried other usb ports - they will allow mounting another device (like a mouse) but will not accept a usb drive.

---

### Post by TheFu on 2020-10-31
That the partition that won't open used on Windows?  Could Windows have left the file system open?  I think that's been the Windows default unless you disable it since Win8.  If so, reconnect it to Windows and have that OS properly close the file system.

[https://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](https://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)
But that's just a guess.  There could be all sorts of other reasons too, but those are mainly due to hardware problems - cables, power supply, ports.

---

### Post by lou6 on 2020-10-31
No, Windows is not involved - my system is not dual-boot.  I have been using these WD Element drives (I have three) since Xubuntu 12.04 LTS and have never had problems until now.  I can mount and use any of these drives by themselves but can't mount any two simultaneously.  As mentioned above, I have also tried other ports with the same result - any one drive will mount properly but no two will mount.\\

Thanks for responding.

---

### Post by TheFu on 2020-10-31
Please post the exact mount command being used.

What do the system logs show when each is connected?  I'd use **dmesg -w** to see that.

If you don't have Windows, why use NTFS?

---

### Post by lou6 on 2020-10-31
I don't use a command to mount the drive(s) - I plug them into a usb port and xubuntu automounts them.

I'll use the command you suggested and post the results.

I use NTFS because many of my friends and family use Windows and I occasionally share files with them.  I also have a laptop running Windows 7 and have compatibility there as well. I have been using it since 2012 - never a problem until right now.

EDIT:  the results of dmesg -w result in MANY pages of text.  I'm not sure I should post that much here.  The last mount seems to start about here:

[31867.583899] usb 1-1.2: new high-speed USB device number 25 using ehci-pci
[31867.773837] usb 1-1.2: New USB device found, idVendor=1058, idProduct=2621, bcdDevice=10.26
[31867.773842] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[31867.773844] usb 1-1.2: Product: Elements 2621
[31867.773847] usb 1-1.2: Manufacturer: Western Digital
[31867.773849] usb 1-1.2: SerialNumber: 575834314132393333585A37
[31867.774519] usb-storage 1-1.2:1.0: USB Mass Storage device detected
[31867.774979] scsi host6: usb-storage 1-1.2:1.0
[31868.781141] scsi 6:0:0:0: Direct-Access     WD       Elements 2621    1026 PQ: 0 ANSI: 6
[31868.782311] sd 6:0:0:0: Attached scsi generic sg2 type 0
[31868.785990] sd 6:0:0:0: [sdb] Spinning up disk...
[31869.803965] ...ready
[31871.852740] sd 6:0:0:0: [sdb] 3906963456 512-byte logical blocks: (2.00 TB/1.82 TiB)
[31871.853769] sd 6:0:0:0: [sdb] Write Protect is off
[31871.853774] sd 6:0:0:0: [sdb] Mode Sense: 47 00 10 08
[31871.854829] sd 6:0:0:0: [sdb] No Caching mode page found
[31871.854835] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[31871.902482]  sdb: sdb1
[31871.905583] sd 6:0:0:0: [sdb] Attached SCSI disk

This was a successful mount.  Next I tried to mount a second usb:

[33122.008113] usb 4-1: new SuperSpeed Gen 1 USB device number 43 using xhci_hcd
[33127.240303] usb 4-1: device descriptor read/8, error -110
[33127.348152] usb 4-1: new SuperSpeed Gen 1 USB device number 43 using xhci_hcd
[33127.672243] usb 4-1: new SuperSpeed Gen 1 USB device number 44 using xhci_hcd
[33132.872344] usb 4-1: device descriptor read/8, error -110
[33132.980273] usb 4-1: new SuperSpeed Gen 1 USB device number 44 using xhci_hcd
[33133.108357] usb usb4-port1: attempt power cycle
[33135.072408] usb 4-1: new SuperSpeed Gen 1 USB device number 46 using xhci_hcd
[33140.296528] usb 4-1: device descriptor read/8, error -110
[33140.404437] usb 4-1: new SuperSpeed Gen 1 USB device number 46 using xhci_hcd
[33145.672677] usb 4-1: device descriptor read/8, error -110
[33145.984641] usb 4-1: new SuperSpeed Gen 1 USB device number 47 using xhci_hcd
[33151.048746] usb 4-1: device descriptor read/8, error -110
[33151.156632] usb 4-1: new SuperSpeed Gen 1 USB device number 47 using xhci_hcd
[33151.284720] usb usb4-port1: attempt power cycle
[33151.728768] usb 4-1: new SuperSpeed Gen 1 USB device number 48 using xhci_hcd
[33156.936864] usb 4-1: device descriptor read/8, error -110
[33157.044805] usb 4-1: new SuperSpeed Gen 1 USB device number 48 using xhci_hcd
[33162.313005] usb 4-1: device descriptor read/8, error -110
[33162.625003] usb 4-1: new SuperSpeed Gen 1 USB device number 49 using xhci_hcd
[33167.689121] usb 4-1: device descriptor read/8, error -110
[33167.796994] usb 4-1: new SuperSpeed Gen 1 USB device number 49 using xhci_hcd
[33173.065219] usb 4-1: device descriptor read/8, error -110
[33173.181346] usb usb4-port1: unable to enumerate USB device

---

### Post by TheFu on 2020-10-31
A few thoughts. May not be helpful at all.

[LIST]
[*] HDDs wear out. A 6 yr old USB HDD is on borrowed time. Please ensure you have excellent backups.
[*] are you certain that it doesn't matter which port and which drive is connected first?
[*] are both drives externally powered or do they both use USB power only? If they are USB-powered only, try using a front USB-port and a rear USB port to spread the power draw out. Use the direct power for the HDD, not the USB power.
[*] Try using all USB3 and all USB2 ports as well
[*] Boot from the last known kernel that worked.
[/LIST]

```
 [33151.284720] usb usb4-port1: **attempt power cycle**
[33167.796994] usb 4-1: new SuperSpeed Gen 1 USB device number 49 using xhci_hcd
[33173.065219] usb 4-1: device descriptor read/8, error -110
```
No mount will work when that error happens. Have you googled that error?
[https://bbs.archlinux.org/viewtopic.php?id=198460](https://bbs.archlinux.org/viewtopic.php?id=198460) came up with a few options. There's a BIOS setting about "Turbo Mode" - they are guessing that a Linux kernel update and that BIOS setting could be interacting.    Seems power related.

More about the power: [https://www.linuxquestions.org/questions/debian-26/usb-error-110-a-4175600294/](https://www.linuxquestions.org/questions/debian-26/usb-error-110-a-4175600294/)  Something about fully powering down the system and fully powering down all external devices. They claim this solved it.

If a Windows machine had the problem device connected, it could have left the file system open. Linux won't mount those. It is to protect the data.

---

### Post by lou6 on 2020-10-31
Thank you for trying to be helpful.  Everything you have suggested has validity except for the fact that all my usual activities were working flawlessly on a daily basis on Xubuntu 18.04 - but then I installed 20.04 and many, many things went south. Maybe the way to approach this is to ask "what's up with 20.04?" rather than "what's this guy doing wrong?".

 It's just too hard for me to believe that all my hardware wore out (actually, all my USB's are not eight years old - there have been replacements along the way).  I haven't used any of these devices on my Windows system in weeks (long before the current problems began) and when I do connect a USB on the Windows box I make sure to unmount it and anyway, my devices DO connect - just not two at the same time. 

I can find ways to work around this latest 20.04 problem but I'm getting really tired of having to make my established activities conform to the latest Ubuntu release.  I'll go along a bit longer but truthfully?  I'm about one more oddity from reinstalling Xubuntu 18.04 and running it 'till it won't run anymore.

Thank you for trying to help. but I genuinely believe that the problem does not lie with my equipment or my occasional need to connect two USB's at the same time.

---

### Post by TheFu on 2020-10-31
If you boot from an 18.04 "Try Xbuntu" flash drive, does everything work as expected?
A few other questions were made. Did you try those? Results?

BTW, I'm on 16.04 still and will probably skip 18.04 completely for all my systems.  I've had some 20.04 issues, but those are inside VMs, so no direct hardware access. Still have a few months before a decision must be made.

I really think the power is related based on that error.

---

### Post by C.S.Cameron on 2020-11-01
If the USB's were ever used to make boot drives they might both have the same UUID. You can check this using Disks and create a new UUID using GParted. Using two USB's that have duplicate UUID's can cause similar problems.

---

### Post by lou6 on 2020-11-01
Good thought but no - they were never used for anything other than backup using rsync (actually Grsync but same difference).

---

### Post by lou6 on 2020-11-01
I've about decided to go back to 18.04.  I have an 18.04.3 version and an 18.04.5 version.  Can someone tell me what the differences are.  I'm hoping the .5 version has all the latest 18.04 revisions...

Thank you for your help.

---

### Post by TheFu on 2020-11-01
18.04.5 has kernel support.  18.04.3 does not have kernel support.  

[https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)  scroll down about 60% of the page to get the detailed view of which releases have support for how long. 18.04.3 support ended in 2019.

There isn't much choice. 18.04.5.

Can't say that I blame you, assuming 18.04 ends the issue.

---

### Post by lou6 on 2020-11-01
I'm almost ashamed to admit this, but starting today I can (again) mount multiple usb drives.  I've done absolutely nothing to the system since yesterday.  This is truly embarrassing  - I assure you that I'm not mentally ill or subject to hallucinations of any kind.

Please accept my thanks for trying to help and my apologies for wasting your time.  I'll be marking this as closed.

---

### Post by TheFu on 2020-11-01
Not even a full power cycle? 

Thanks for posting. Hope it stays working. I don't feel like this was a waste of time. I've seen all sorts of issues with USB connections. Switched most over to eSATA to make those problems stop.

---

### Post by lou6 on 2021-04-11
Eventually I solved this problem by swapping cables on my WD Elements drive(s).  One cable was bad but the problem appeared to be random because the computer I was using at the time ha a mix of usb2/usb3 ports.  The bad cable would work in the usb2 port but not in the usb3.  Needless to say, I acquired new cables...

Updating this several months later for the benefit of anyone who might have a similar problem...

---

