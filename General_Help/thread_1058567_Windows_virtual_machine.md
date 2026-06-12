---
title: "Windows virtual machine"
date: 2009-02-03
forum: General Help
---

### Post by Fata_ku on 2009-02-03
I was wandering if there was a way to boot a windows virtual machine directly from a mounted filesystem. I've been looking around and all I find are VirtualBox-type emulators that use a virtual hard drive. I noticed that QEmu could boot DSlinux with it's filesystem directly on the usb-drive, but I can't seem to get the same result with it's linux version.

I suspect there is a reason for this (risk of corrupting the filesystem?)...
Can anyone shed any light on this?

---

### Post by lykwydchykyn on 2009-02-03
Qemu can do it, but there are problems.  
 - With windows, if you try to boot to significantly different hardware (and the virtualized hw is very different from your real hw), it will probably blue screen and die; if it manages to boot, it will probably be de-activated and need reactivation.  You can usually fix this by booting to the windows install disc and doing a "repair install", but then you'll blue screen when switching back to the real hardware.
 - With Linux, I've had issues with the UUID of the partition not being right.  It has a better chance of working than Windows, since it autodetects hardware on every startup and doesn't require activation; but sometimes locating the correct partition can be a problem switching from real to virtual.

keep in mind qemu only emulates IDE drives, so if your real drive is SATA, it's going to create problems in any OS.

---

### Post by Fata_ku on 2009-02-03
Well, the hard-ware should not be too much of a problem - i'd be running an already-installed windows partition. I'd just have to make sure the hw emulation settings are as close as possible to my current PC, i guess?

Also, I just can't seem to find the settings to boot off a folder. nigh-everything requires me to create a VDI.

---

### Post by lykwydchykyn on 2009-02-03
> **Fata_ku said:**
> Well, the hard-ware should not be too much of a problem - i'd be running an already-installed windows partition. I'd just have to make sure the hw emulation settings are as close as possible to my current PC, i guess?

The hardware that matters can't typically be set.  If you've seen an emulator that lets you specify the exact CPU and Motherboard to emulate, you've seen one I've not seen.  And that's the problem:  Windows loads at INSTALL time one of several HALs (Hardware Abstraction layers) depending on your processor configuration.  The boot configuration is also very dependent on the type of drive you use (SATA vs IDE).  If this stuff changes -- BLUE SCREEN.  

If this is a one-way transition (you aren't wanting to ever boot back, or you intend to make a copy of the partition), than you can run a repair install and fix this stuff.  But if you intend to bounce back and forth between real and virtual, it isn't going to work.
> 
Also, I just can't seem to find the settings to boot off a folder. nigh-everything requires me to create a VDI.

I don't know about using folders, I don't think that's possible, but you can boot from a physical device (e.g. /dev/sdb).  How a windows install will react to being booted in qemu (not sure it will work if the windows and linux partitions share a drive) is another question, but I have used qemu many times to access a raw disk or partition, e.g.:
```

sudo qemu -hda /dev/sdb

```

You need to use sudo, BTW, to access the drives directly like that.

---

