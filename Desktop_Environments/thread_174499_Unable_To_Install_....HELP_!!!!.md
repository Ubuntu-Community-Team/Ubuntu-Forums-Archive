---
title: "Unable To Install ....HELP !!!!"
date: 2006-05-11
forum: Desktop Environments
---

### Post by Nibiruet on 2006-05-11
**[COLOR="Red"]PROBLEM SOLVED[/COLOR] - thanks for replies.**
Trying to install Ubuntu v5.10 on a P4 system running Win-XP Pro too. Drive has been partitioned for 2nd OS (Linux). On CD boot install runs for a for a few moments and stops after the following messages are displayed and just hangs!

(1) checking if image is initramfs ...... it isn't (no cpio image); looks like an initrd
(2) Freeing limitrd memory: 3963k freed
(3) ACPI: Looking for DSDT in inidrd .... not found
(4) not found!

Any help appreciated.
Thanks

P.S. - Tried Fresh copies of Ubuntu as well as Kubuntu no resolution to problem. Keep getting same message.

---

### Post by safecracker on 2006-05-12
DSDT (Differentiated System Description Table) sits in your BIOS and gives Linux all the info about your computer. It is possible you need to update your BIOS or possibly pass pci=noacpi or linux acpi=off at boot, can't remember which 1 works in Ubuntu off the top of my head.

---

### Post by Nibiruet on 2006-05-12
**[COLOR="Red"]PROBLEM SOLVED[/COLOR] - thanks for replies.**
Ah! finally someone heard my cry for help :) 

Thanks will give it a try. I think BIOS is current if I recall. System is a P4 3.2 GHz 800FSB on an Asuz P4S800D-X mb with 2GB RAM and a 300 GB SATA Maxtor drive with a GeForce 6600 256 Mb 8xAGP card.

I put it together so no support available :(

---

