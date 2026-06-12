---
title: "Hard Drive Problem"
date: 2006-01-30
forum: Desktop Environments
---

### Post by josh34 on 2006-01-30
I have an old computer, and since it won't boot from CD, I pulled out the hard drive and put it in my good computer to install Ubuntu. The install went fine and I put the hard drive back in the old computer. When I start to old computer is says "DRIVE NOT READY, insert boot diskette in A:, press any key when ready." How do I get it to boot Ubuntu?

---

### Post by olddog55 on 2006-01-30
How old is the computer?  Did the new install boot properly on the installation system?

If it was bootable on the installation system, it would appear that the BIOS is attempting to boot off a floppy.  

Get into the BIOS and check that the hard drive is set to boot before the floppy.  

Method is manufacturer dependant, but is typically via F1 ( or ESC or F10 or .. ) during the power-on boot-up sequence.

---

### Post by josh34 on 2006-01-30
It booted fine on the good system. The old computer is set to boot from C: and then A:.

---

### Post by dcstar on 2006-01-31
[QUOTE=josh34]I have an old computer, and since it won't boot from CD, I pulled out the hard drive and put it in my good computer to install Ubuntu. The install went fine and I put the hard drive back in the old computer. When I start to old computer is says "DRIVE NOT READY, insert boot diskette in A:, press any key when ready." How do I get it to boot Ubuntu?[/QUOTE]
You probably won't.

Using the disk in the new PC probably resulted in the hard disk being used in a way the old PC cannot understand, so now the old PC does not see the boot sector.

The Ubuntu install is also probably now configured for the hardware on the new PC, and it is doubtful it will even load on the old one (if you do get past the first hurdle).

Try searching the forum for info on a floppy install of Ubuntu.

---

