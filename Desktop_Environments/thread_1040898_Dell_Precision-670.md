---
title: "Dell Precision-670?"
date: 2009-01-16
forum: Desktop Environments
---

### Post by Peager on 2009-01-16
Has anyone successfully installed Ubuntu on a Precision-670?  64 bit?  Perc 320 SCSII Raid 10?  Dual monitors?

Many thanks in advance.

Paul

---

### Post by adamlau on 2009-01-16
No, but I have installed Xubuntu/Ubuntu on a number of older Precision Workstations (32/64 SCSI) with excellent results. MP-BIOS bugs here and there, but nothing outstanding otherwise.

---

### Post by JGraupman on 2009-01-19
I have attempted to install Ubuntu 8.04.1 on a Precision 670 station and ran into problems. I have successfully installed Ubuntu on my laptop and as a virtual machine before that to experiment, so I've worked through the normal process successfully.

This time though it's a retired Precision 670 server that I thought I would turn into a web forum server.  The install though doesn't even really begin.  After I choose to install from the menu it doesn't enter into the normal install GUI.  Instead something called BusyBox v.1.1.3, the repeating error is

ata2.oo: status: {DRDY}
ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
ata2.00: cmd c800:08:00:00:00/00:00:00:00:00/e0 tag ) dma 4096 1

and then it repeats again, and again, until I choose to reboot.

I am attempting to install onto a PATA drive, and I do have 2 SATA drives separately in raid 0 for storage.  The drives are newer though and were working fine as a win2003 server which still boots fine once I remove the install disc.  My thought was to install Ubuntu in a dual boot configuration for my forum server and leave the windows 2003 server in place in case our new web server had any problems.

This particular computer does have 2  Intel Xeon processors so perhaps that's an issue?  

Thank you for any thoughts and suggestions anyone may have.

---

### Post by adamlau on 2009-01-19
Issue is likely not related to the Xeons as I have Xubuntu 8.10 on a 1600SC with two Xeons running two U160 Cheetahs without issue. Appears to be more an issue with the PATA, or controller. What happens when you disable the RAID controller and install to the PATA from there?

---

### Post by JGraupman on 2009-01-19
Thanks,  it is the raid card that is causing the problems.  I removed it and the install completed successfully.

Now however the problem is if I put the raid card back into the computer Ubuntu will not boot at all.  Take the card out and I can get to the login screen fine.

Looks like the manufacturer has linux drivers so guess I'll try that next.

Besides this issue, everything else seems to be working great.

---

### Post by foxmajik on 2010-01-07
I am using Karmic 64 bit on a Dell Precision 670 Workstation.

I had already installed Jaunty and upgraded it to Karmic on my previous box which also had an Intel motherboard.

When I got the 670 I just took the hard drive out of my old machine and put it into the 670.

Everything worked perfectly the first time.

The only problem I've experienced is that the LPC47M534 sensors are not supported by lm-sensors, so I cannot read the temperatures for the system.

**EDIT 4-16-2010:**  It should be noted that on Karmic and Lucid, the installer will not boot fully if there is more than one display connected.  This also happens when installing Windows 7.

Also, the hardware thermal sensors on the 670 are not supported due to a lack of documentation on the thermal monitor chip in the 670.

---

