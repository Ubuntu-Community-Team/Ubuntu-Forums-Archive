---
title: "problem starting live cd ubuntu 8.10"
date: 2008-12-08
forum: Desktop Environments
---

### Post by tsonev on 2008-12-08
I tried to start ubuntu 8.10 on my office computer from  a live cd, but it failed to start grafical environment. I tried "startx" and this is the result:
Primary device is not PCI
(EE)No devices detected

Fatal server error:
No screens found
giving up

xinit: Connection refused (errno 111): unable to connect to x server
xinit: No such process (errno3): server error

Here is the system:

	
Motherboard	
CPU Type	Intel Pentium IIIE, 733 MHz (5.5 x 133)
Motherboard Name	Compaq Professional Workstation AP550
Motherboard Chipset	Intel Carmel i840
System Memory	1280 MB  (PC600 ECC RDRAM)
BIOS Type	Compaq (03/05/99)

	
Display	
Video Adapter	3Dlabs Oxygen GVX1
Video Adapter	3Dlabs Oxygen GVX1
3D Accelerator	3Dlabs Permedia 3
	
Can you give me any idea, what is the reason for the problem. Thank you.

---

### Post by coolethan on 2008-12-09
very strange, did you download the .iso image or is this an official ubuntu disc

---

### Post by tsonev on 2008-12-10
Yes, I did download it. I burned the image disk on another pc, and it was working there. I must check it again.

---

### Post by coolethan on 2008-12-10
i read a thread where a person was having the same issues and what worked for him was to burn the disk .iso again but at the slowest writing speed possible.
[]("http://ubuntuforums.org/showthread.php?t=1006005&highlight=iso")[http://ubuntuforums.org/showthread.php?t=1006005&highlight=iso]("http://ubuntuforums.org/showthread.php?t=1006005&highlight=iso")

---

### Post by tsonev on 2008-12-11
Thank you coolethan, I will try this, but I suppose that there is a problem with the video cart driver.

---

