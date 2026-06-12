---
title: "System Not Found on Dell Mini9"
date: 2009-09-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by AJFMini9 on 2009-09-04
When I start up I keep getting:

PXE-E61: Media test failure, check cable
PXE-MOF: Exiting PXE ROM
Operating System not found
I tried to reinstall Ubuntu but I keep getting the same message when it starts up

Dell insists it's a software problem. Now I'm really in limbo because whenever I call Dell, my call gets sent to a machine that tells me to visit this website. 

What could be the problem?

---

### Post by ugm6hr on 2009-09-04
Can you enter the BIOS?

Can you select to boot from USB device?

From memory, I get a similar message when I reset with Ctrl-Alt-PrtScrn R-E-I-S-U-B; never worked out why.

---

### Post by AJFMini9 on 2009-09-04
> **ugm6hr said:**
> Can you enter the BIOS?

Can you select to boot from USB device?

From memory, I get a similar message when I reset with Ctrl-Alt-PrtScrn R-E-I-S-U-B; never worked out why.

I can enter BIOS and boot from a USB device.

---

### Post by ugm6hr on 2009-09-04
> **AJFMini9 said:**
> I can enter BIOS and boot from a USB device.

Have you tried installing 9.04 NBR from a LiveUSB?

---

### Post by AJFMini9 on 2009-09-04
> **ugm6hr said:**
> Have you tried installing 9.04 NBR from a LiveUSB?I don't know what a LiveUSB is but I did try using an external drive with the UBUNTU 8.04+LTS Recovery disc that came with the computer.It goes through the entire download procedure, restarts then I get the same message when it reboots.

---

### Post by ugm6hr on 2009-09-04
Assuming you have actually reinstalled it properly, it sounds like you have a problem with the SSD MBR (i.e. "Hard Disk" master boot record).

Although. I would anticipate this getting errors at the install time.  Hence, try installing 9.04 NBR using a USB (>1GB) flash drive.  Just download and install as per instructions on the ubuntu.com homepage.

---

### Post by AJFMini9 on 2009-09-05
I did try to install OSX using a thumb drive ( I have OSX running on 2 other Mini9's without ant problems at all) and when I try to format the hard drive, it comes up with a failed to format error. I'll try what you said though.

---

