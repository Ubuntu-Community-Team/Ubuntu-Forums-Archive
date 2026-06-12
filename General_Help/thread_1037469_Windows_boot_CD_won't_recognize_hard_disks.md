---
title: "Windows boot CD won't recognize hard disks"
date: 2009-01-11
forum: General Help
---

### Post by Feral Rabbits on 2009-01-11
I'm trying to put windows on my computer (Ubuntu being the only OS), and the boot CD says there are no hard disks connected.

How do I install windows?

---

### Post by Slim Odds on 2009-01-11
> **Feral Rabbits said:**
> I'm trying to put windows on my computer (Ubuntu being the only OS), and the boot CD says there are no hard disks connected.

How do I install windows?

If it's a SATA drive, you need a floppy with the drivers.

---

### Post by Feral Rabbits on 2009-01-11
Dang, I don't have one of those.Not even a floppy drive.

---

### Post by balaknair on 2009-01-11
If it's WinXP you're trying to install, it won't recognize SATA drives.

You have 2 options--> 

1) Use a floppy to load the SATA drivers(or if you don't have a floppy, use slipstreaming to get it onto a custom XP install CD
[http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/](http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/) )

2) Disable SATA control in the BIOS(set it to IDE mode), XP should now detect your hard drive. Install XP and after you're done, install the SATA drivers. Yo can now switch the BIOS settings back to SATA mode.

Hope this helps.
All the best.

---

### Post by theozzlives on 2009-01-11
> **balaknair said:**
> If it's WinXP you're trying to install, it won't recognize SATA drives.

You have 2 options--> 

1) Use a floppy to load the SATA drivers(or if you don't have a floppy, use slipstreaming to get it onto a custom XP install CD
[http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/](http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/) )

2) Disable SATA control in the BIOS(set it to IDE mode), XP should now detect your hard drive. Install XP and after you're done, install the SATA drivers. Yo can now switch the BIOS settings back to SATA mode.

Hope this helps.
All the best.

#2 won't work, I just run in ATA mode.

---

### Post by balaknair on 2009-01-11
> **theozzlives said:**
> #2 won't work, I just run in ATA mode.

Not sure I understand what you're saying here.
Do you mean 
a) that disabling the SATA controller in BIOS won't make XP see the drive or 
b) that installing the drivers post-install and then resetting the BIOS to SATA mode won't work?

Getting SATA to work post-install is dependent on the system manufacturer/vendor providing XP drivers for the SATA controller for your particular model, but I'm pretty sure it can be done(I've done a few XP/Ubuntu-as-dual-boot installs on a few laptops, worked fine). 
Terminology and option names vary with the various flavors of BIOS(in some BIOS, it may not allow you to change the SATA settings; in some others, you have to switch 'AHCI Mode' from 'Enhanced' to 'Compatibility'.)

If you can hunt down the XP SATA drivers for your chipset, I think installing them after installing XP should enable you to run in SATA mode. Again, this depends on your hardware(specifically, the vendor providing XP drivers).

---

