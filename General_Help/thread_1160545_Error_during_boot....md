---
title: "Error during boot..."
date: 2009-05-15
forum: General Help
---

### Post by mjpatey on 2009-05-15
Hello, group-

I installed Ubuntu Studio (64-bit edition) on a free partition, and when I first boot, I have the usual Ubuntu issue (on my hardware) of displaying the wrong resolution for my monitor.  I click on the "hardware drivers" tray icon when it appears, and select the nVidia driver (version 180).  Up comes the dialog box wich should be showing progress of the driver download/install, but the dialog is blank.  Eventually, the system hangs (I lose mouse and keyboard control).

When I reboot, the boot sequence takes a left turn at some point, and I get this:

> Boot from (hd0,0) ext4 1be86f7b-a630-4773-aa5d-b38bf5535538

Starting up...

[0.113778] ACPI: Aborted because invalid compressed format (err=1)
[3.328847] RAMDISK: Ran out of compressed data
[3.328896] invalid compressed format (err=1)
[3.349372] Kernel panic - not syncing: VFS: Unable to mount root FS on unknown-block(0,0)This outcome is consistent every time.  I actually went over and over this until finally deciding something must have gone wrong during the install, and I wiped the partition and reinstalled.  Same problem!  I've also tried it with and without installing updates prior to the driver install.

I just Googled a bit regarding Ubuntu Studio and ext4 (the filesystem I chose during installation both times).  Some are saying ext4 is not a good idea with Ubuntu Studio... could that be my issue?  Thanks for any light you can shed on this!

-Mark

---

