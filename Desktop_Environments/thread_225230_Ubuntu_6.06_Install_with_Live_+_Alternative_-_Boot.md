---
title: "Ubuntu 6.06 Install with Live + Alternative - Boots straight Back into Winxp"
date: 2006-07-29
forum: Desktop Environments
---

### Post by linuxnoob43 on 2006-07-29
Hi,

I've tried many times installing Ubuntu using the live cd onto my sata hd, which already has Winxp on it. My configuration is to leave XP on its NTFS partition, and using free space I created another primary ext3 (for / root, 48gb) and another ext3 for the swap (2gb). All seems fine, however when the live cd starts setting up the partitions and installs, it doesnt ask whether to install GRUB to the MBR...which seems strange, nor does it says it detects Windows XP - it just installs and goes straight to the reboot and remove cd stage. After doing this, the PC just boots straight back into windows - no Grub menu at all.

Ive downloaded the alternative CD and tried doing the same thing, this time setting the Linux / root partition as boot enabled (why does this remove the boot enable from the WinXP ntfs partition?)...the alternative cd detects Winxp and prompts me to say whether I want GRUB to be installed to the MBR. I choose yes, and the same thing happens - boots straight back into Windows.

Can someone please help? Can it be that my MBR is locked, or constantly being overwritten by Windows? This pc is a Mesh, with a hidden recovery partition, could it be that?

I've been at this for 4 days now and still no luck!!! :confused:

BTW, the live and alternative versions ive been using are AMD64.

---

### Post by rowanparker on 2006-07-29
Using the alternate CD, is it possible to install grub to a floppy?

Or, using the recovery mode on the CD. Could you run grub-install?

---

### Post by linuxnoob43 on 2006-07-29
I just tried recoving the previous install, installing grub again to the MBR...still doesn't work!?!?

---

### Post by rowanparker on 2006-07-29
Install grub to a floppy using: (this I think).
```
sudo grub-install fd0
```

---

