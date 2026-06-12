---
title: "Breezy Live CD won't boot"
date: 2006-02-12
forum: Desktop Environments
---

### Post by Barb on 2006-02-12
It was going to take me over thirty six hours to download PC intell Live CD.
Asked a friend to download and burn a disk for me.

My computer BIOS starts boot search sequence as:
CD
Floppy
HD

UBUNTU won't start the boot process from the CD.
I can boot Windows from a CD so the BIOS is seeking in the right manner and the CD drive is functioning off the BIOS.
E Machine 366 MHZ

Windows can't read Linux code so I can't tell what programs are loaded on the CD. This is my second attempt at looking at a Linux program. Knoppx was the first one and that didn't work either.
thanks for suggestions
Barb

---

### Post by heimo on 2006-02-12
Boot to windows, explore the cd and see if you have one or multiple files on it. You should not see only one file (*.iso) on it, but a bunch of files and directories. Is it so?

---

### Post by zxee on 2006-02-12
Since the installer doesn't even start and you state that the bios is setup to boot from a cd there must be either a problem with the disk-can you check it on another computer? Or there is some hardware incompatibility-perhaps you can post your hardware specifics? A clue here is that knoppix didn't work (knoppix has pretty broad hardware recognition)

---

### Post by Barb on 2006-02-12
[QUOTE=heimo]Boot to windows, explore the cd and see if you have one or multiple files on it. You should not see only one file (*.iso) on it, but a bunch of files and directories. Is it so?[/QUOTE]

Only one file "Ubuntu-5.10-license-i386.iso"

My friend still has the download on his HD. He said he would save it until I told him I was able to boot from the CD. What is the solution? We need to burn another CD? The files can't be zipped or they would have to be unzipped to a DVD not CD. If I remember right something was said in PCWorld about some of the files didn't download and the author had to go back a second time to trap them?
thanks
Barb

---

### Post by heimo on 2006-02-12
The cd needs to be burned "from image" (the .iso file). Hopefully this helps:
[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

---

### Post by zxee on 2006-02-12
Also the total size of the live cd is 626.2MB with 718 items-just checked my live cd of 5.10. Just a thought but you can get the installer and live cd from shipit.ubuntu.com.

---

### Post by Barb on 2006-02-12
Thanks to everyone for their helpful hints. My friend nor I have ever burned an ISO disk so it was a learning experience for both of us. Nero has ISO burning capabilities if one understands what the heck that is for.

I figured on a learning curve when I booted Linux. I didn't expect a learning curve before I got the CD to boot.

Thanks to everyone who offered their generous help and support.
always
Barb

---

