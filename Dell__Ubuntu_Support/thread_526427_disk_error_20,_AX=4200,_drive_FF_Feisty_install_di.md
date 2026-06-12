---
title: "disk error 20, AX=4200, drive FF Feisty install disk freezes at Start or Install"
date: 2007-08-15
forum: Dell  Ubuntu Support
---

### Post by CompTechGirl on 2007-08-15
Hi all,

I have been using Ubuntu Breezy Badger for my apache webserver for over a year, tried to do updates and well it seems they don't exist. So, I decided to backup my stuff and start fresh with Feisty Fawn, Breezy Badger installed for me no problems at all.

I downloaded Feisty Fawn 3 times, the first time it only partially downloaded, the second 2 times it was a full download, I checked the ms5sum and they both show the correct checksum. I burnt the first download onto a CD-RW disk and half the time it wouldn't boot at all.

So, I went and bought some cd-r disks, incase that was the problem, re-downloaded feisty fawn and tried again. This disk boots everytime. The memtest runs and says no problems. But, when I select test the cd, or "start or install Ubuntu" It just freezes. This is on my dell pc:

Specs:
dell optiplex 
P3, 600 MHz
256 RAM
30 GB maxtor hdd - I tested this with maxtor test - it passed both quick and advanced, then I zeroed the drive.
onboard video

I also tried this boot cd on my P2 machine that has 392 MB ram and on that pc it gave me the error message I have in the title
"I/O error reading boot CD (there is a reboot button)"
Disk error 20, AX=4200; drive FF

Thanks in advance for any help.

---

### Post by ridgeland on 2007-08-16
Did you check the md5sum on the CD that you created?
I use:
$ md5sum /dev/scd0
depends on how the CD gets mounted in Breezy.

---

### Post by CompTechGirl on 2007-08-17
Hey, 

I had to re-burn the cd-r, as it turned out that my first 2 iso's got corrupted during the burn process, I checked the md5 checksums for the ISOs after downloading, and they showed to be ok. I burned it to CD, then used "check the integrity of the CD" and sadly 2 CDs were wasted - both failed the integrity test. But, 3rd times a charm. The third cd passed the integrity test. I triple booted my work computer xp, vista and ubuntu.
I then tried to install on my old dell optiplex and it just wasn't working.

This is how I got feisty fawn installed. I ended up moving my hard drive to another computer, that was faster and much more upgraded. Installed it, then moved the hard drive back to my old machine and I am using it now.

Thanks again for your help.

---

