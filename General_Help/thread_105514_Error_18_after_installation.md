---
title: "Error 18 after installation"
date: 2005-12-18
forum: General Help
---

### Post by Masteroc on 2005-12-18
Hi,

This is my first time installing Ubuntu and i am using the Install disc that i got in the mail from Ubuntu. I did a regular install on 160gb HD that previously had slackware installed on it. I chose the option to erase everything and install ubuntu, and everyting went fine. It all installed and then it ejected the cd and said to restart the machine, which i did. When it restarts, it comes up with:

GRUB loading, please wait...
Error 18

What could be happening?!?!

P.S. i do not have any other os dual booting or anyting.

---

### Post by duminas on 2005-12-18
> 18 : Selected cylinder exceeds maximum supported by BIOS. This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).
Is the primary partition (the one marked as active) at the start of the drive? If not, try moving it there.

---

