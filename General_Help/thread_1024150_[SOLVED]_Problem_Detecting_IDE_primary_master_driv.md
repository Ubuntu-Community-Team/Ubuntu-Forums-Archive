---
title: "[SOLVED] Problem Detecting IDE primary master drive"
date: 2008-12-28
forum: General Help
---

### Post by spencer1105 on 2008-12-28
I recently got an older computer and decided to try out ubuntu. The computer previously had windows98 installed. I installed ubuntu using the CD downloaded from the website, it finished installing just fine, but when i try to boot, it gets stuck with the following message:
Problem detecting IDE primary master [Press F4 to skip...]

or something along those lines. Pressing F4 does nothing. I have changed just about every option I can think that would have an affect in the BIOS and it still gets stuck there. If I tell the computer that there is no primary master IDE drive, then it goes through the others (primary slave, secondary master, secondary slave) just fine and will still boot from the ubuntu CD. Any suggestions on how to fix this problem? Thanks for the help.

---

### Post by Schlandower on 2008-12-28
Hi, could you supply some details on the hardware you are using, not just the machine model and make but if possible what cpu, chipset, and other details from within.

Some of the info is available from the bios when the machine boots, the rest you will need to actually open the case and take a look.
Also what hard drives are you using, is your cdrom / dvdrom a sata unit.
Do you have a usb extention card on the machine?
If you are using a sata extension card what chipset does it use?

---

### Post by spencer1105 on 2008-12-28
Well, I did this kind of backwards, I was tired of looking at the BIOS, so i took it apart first. Any idea which of the things I will need to look at on the parts themselves? I do know that the motherboard is an intel motherboard. The drives are not connected throught SATA, forgive my ignorance, but the drives are connected with a series of many wires all attached together (SCSI I believe). If possible i would rather not remove any of the drives, as that would require taking apart almost the entire thing. The processor is a pentium iii 450MHz, and it has 512MB of RAM. 
The odd thing, or at least I thought so, was that booting from the ubuntu disk, the machine was able to detect the harddrive, and all of the installed files were there for ubuntu. Perhaps I am misunderstanding exactly what it means by saying that there is no primary master IDE, but I would think that if the harddrive were set to that, it would not be able to detect the harddrive.

I'm going to try to find all the information I need from inside the case before I hook the computer up again. Thanks

---

### Post by cariboo on 2008-12-28
I would suggest reseating the ribbon cables to the hard drive and cdrom. The ribbon cables mean that you are using IDE drives, the chances of the drives being scsi are slim to none. One other thing to check is to make sure the jumpers are in the correct position. As jumper settings on hard drives are all different, I would suggest going to the hard drives manufactutuers web site and doing a search for the user manual or installation guide for the drive.

Jim

---

### Post by spencer1105 on 2008-12-28
The only thing is that when I was able to boot from the ubuntu CD, the hard drive was visible within the OS, and it said that the drive was SCSI. By reseating the ribbon cables, do you just mean to make sure that there is a good connection?

---

### Post by spencer1105 on 2008-12-28
So, the harddrive is a seagate harddrive, the page for the harddrive says the following:
"Types that have been identified are:
     a 528MB limitation (CHS[1024x16x63]x512 = 528,482,304)
     a 2.113GB or 4095 cylinder limitation 
     a 3.262GB or 6322 cylinder limitation 
     a 4.22GB  or 8192 cylinder limitation
     a 8.45GB  Standard INT13 limitation (CHS[1024x256x63]x512)
     a 33.8GB or 66,060,287 LBAs limitation
and, if exceeded, may cause the system to hang during boot, 
capacity reduction or it can truncate or wrap the cylinders when 
auto-detect options set in the CMOS."

and also the following:
"On drives less than 33.8GB, Limit Capacity jumper sets the default 
cylinder translation to 4092 to solve issues with certain BIOS that 
only auto-detect. Total available sectors are still at full capacity 
as reported via Identify Drive data words 52 - 61. On drives greater
than 33.8GB, Limit Capacity jumper changes total available sectors
as reported via Identify Drive data words 60-61 to 33.8GB. The ATA 
Read Native Max and Set Max commands may be used to reset the true 
full capacity. Third party partitioning software may be needed to 
achieve full capacity when using this option jumper."

Sorry about the large blocks of text, but it appears that possibly since the computer is so old (bought in 1999) that maybe it can't handle having such a large hard drive. However, these instructions aren't quite clear to me, does anyone think this may be the problem, and can you clear up the instructions for correcting this problem? Looking at the installation guide for the drive it looks like there are two pairs of pins that would need jumpers. One makes the drive master, and the other limits the capacity. I will go check if these jumpers are on the drive, but is it possible the drive would have worked before if they were not?

It still seems odd that installing a new OS would cause problems like this since I would think all this information would be stored in the BIOS and the system worked fine before. Thanks again.

---

### Post by spencer1105 on 2008-12-28
I checked the jumpers on the drive, and the drive is enabled as a master drive. The pins to limit the capacity also have a jumper on them. Is it possible that the fact that the capacity limiting pins have a jumper could be causing the problem? That doesn't make much sense, but neither does the rest of this.

---

### Post by spencer1105 on 2008-12-29
Just wanted to let you all know that I got it working. There were arguments with the jumpers and the wiring on the IDE cable. The jumper on the hard drive was set for it to be the master, but the position on the cable was such that it should have been the slave. I removed the IDE cable from the ZIP drive, and now the hard drive is the only drive on that cable, in the master position. My advice to anyone else that has this problem is to check the jumpers and the cables. Another thing I found when researching this problem is that the hard drive I had needed to be limited in size in order for the older motherboard to detect it. Though I doubt most will have this problem anymore.

Thanks for the help everyone.

---

