---
title: "Auto-Mount NTFS Drive on PCI IDE Controller"
date: 2006-01-10
forum: Desktop Environments
---

### Post by t3ddyg on 2006-01-10
Hi guys,
    I used ubuntuguide to auto-mount the two windows drives i have on my onboard ide controller.  It is working great so far.  I also have two ntfs drives on a pci ide controller.  The controller appears to be detected properly in device manager.  I want to auto-mount those two drives, but i have no clue how to tell what they are called in linux.  My first two drives were on the onboard master ide cable, so i knew they were hda1/hdb1.  But how do i find out what these drives are?  Thanks for your help, sorry if this is really stupid.:confused:

Stealth edit:  The two drives i'm trying to mount are on a pci ide raid controller from newegg:
[SYBA SD-ATA133R]("http://www.newegg.com/Product/Product.asp?Item=N82E16815124001")
They are both attached to the master ide cable.  The controller is detected as a silicon image chipset.

---

### Post by zoiks on 2006-01-11
Does "fdisk -l" (that's an "L") show the drives?  Or do they show up in System|Admin|Disks?  WAG is that they are /dev/hde and /dev/hdf.

---

### Post by t3ddyg on 2006-01-13
[QUOTE=zoiks]Does "fdisk -l" (that's an "L") show the drives?  Or do they show up in System|Admin|Disks?  WAG is that they are /dev/hde and /dev/hdf.[/QUOTE]

fdisk -l didn't show anything at all.  They did show up under System|Admin|Disks, and you were correct - they were hde/hdf.  I used the same guide to automount them, and all is well.  Thanks for your help!

---

