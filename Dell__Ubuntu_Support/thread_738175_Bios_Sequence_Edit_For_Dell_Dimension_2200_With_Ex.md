---
title: "Bios Sequence Edit For Dell Dimension 2200 With External Hard Drive In USB Port?"
date: 2008-03-28
forum: Dell  Ubuntu Support
---

### Post by Breandean on 2008-03-28
I am beginning to put Ubuntu 7.10 on my EHD, so far I am checking and altering my BIOS in my Dell Dimesnion 2200. I checked it, after tring to alter the boot sequence, but it did not detect my EHD, although so far there are only documents on my EHD.

How shall I adjust the boot sequence to put the USB EHD after the CD ROM before the IHD?

---

### Post by Koolgecko91 on 2008-03-28
I wouldnt mess with thw BIOS. If you mess them up you will brick your motherboard.

---

### Post by virtuallinux on 2008-03-29
Ok, as for bricking your motherboard, it might be tricky on some higher end systems, but on a Dimension 2200, you should be ok.

As for the boot sequence, if the only thing on the EHD is documents, and no Operating System, then there's not a boot loader for the BIOS to detect.  You should probably set the boot sequence in this order:

1 CD-ROM
2 USB device
3 Internal Hard disk

To install on the EHD, boot to the CD, and then select the EHD when it asks you to set up partitions.  I realize these instructions may seem a little vague, so ask for clarification if needed.

---

### Post by Breandean on 2008-03-29
So the USB EHD is primary or secondary, and is it called diskette?

I think I may already have it right, I understand what you writing, there is no boot loader otherwise it would detect it with the present updated BIOS sequence.

---

### Post by virtuallinux on 2008-03-29
Well, I've never actually installed to an external drive before, but I would imagine that the installer sees it as the secondary drive.  Assuming you've only got one internal drive, the installer will probably see it as "sdb". I hope that answer's your question. You may want to use the manual method for setting up partitions, as it will give you more control over what goes where.

---

### Post by Hexagrapher666 on 2008-05-16
> **Breandean said:**
> How shall I adjust the boot sequence to put the USB EHD after the CD ROM before the IHD?

Some BIOSes will simply not recognize a USB device as a bootable device.   Unfortunately, I believe that such is the case with the BIOS in a Dell Dimension 2200.  There are ways to get around this BIOS limitation though.  One way would be to [_create a bootstrap CD_]("https://help.ubuntu.com/community/BootFromUSB") and boot from it, which would then detect your external USB hard-drive and boot into the Ubuntu OS that you had previously installed on that USB drive.

---

