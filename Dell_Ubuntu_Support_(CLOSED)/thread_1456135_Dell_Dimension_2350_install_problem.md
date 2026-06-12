---
title: "Dell Dimension 2350 install problem"
date: 2010-04-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by JDylantx on 2010-04-16
Ok, I bought this computer from my aunt and its great it has 1g of ram a Intel Pentium 4 processor and a nividi 8400 graphic card, and its super quick. But i was trying to install & preview ubuntu and i got a message saying unable to find a matrix containing a live file system. And i considered using a usb to install ubuntu but that's not a option because i can not find a floppy disk any where, and i don't have a diagnostics disk so i cant use that method ether. PLEASE HELP

---

### Post by Kai Summers on 2010-04-17
Dell's BIOS will allow you to boot from USB just unpack and write the ISO download to a USB stick and it should work fine. All you will have to do is go into the BIOS and set the boot order so that it will try the USB before the HDD it will usually be set to be the last in the boot order, so just change it to first.

With regards to the CD/DVD that you are currently trying to boot from, did you check to see if the hash code matched up to check that the download was not corrupted.

Hope that Helps!

---

### Post by JDylantx on 2010-04-17
OK Ive tried that but the problem is my bios is revision A01 and there is a update but to do that i need a floppy disk or a diagnostics disk. But i cant do that because i cant find ether of them.

---

### Post by asteidl on 2010-04-23
I just had the same problem with my 2350, while trying to install 9.1.  My rig has the P4, with 750 RAM, GeForce 8400GS, DVDr, CDrw, 3.5" floppy, 2x 40GB HDD's.  I ended up pulling the GPU to get it to install.  Unfortunately, upon reinstalling GPU after install, I cracked the pcb of the gpu.  So, I'm back to onboard graphics, and after updating everything but GRUB (another story), working fine.  Not sure why I pulled the graphics card, but it worked for me, so might be worth a try.

EDIT:  you can get hte BIOS update here:  [http://support.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R58200&SystemID=DIM_PNT_CEL_2350&os=WW1&osl=en&deviceid=308&devlib=0&typecnt=1&vercnt=3&formatcnt=2&fileid=70067](http://support.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R58200&SystemID=DIM_PNT_CEL_2350&os=WW1&osl=en&deviceid=308&devlib=0&typecnt=1&vercnt=3&formatcnt=2&fileid=70067)

---

