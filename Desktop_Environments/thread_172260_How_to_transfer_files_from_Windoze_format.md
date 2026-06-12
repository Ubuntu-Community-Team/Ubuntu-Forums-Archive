---
title: "How to transfer files from Windoze format?"
date: 2006-05-08
forum: Desktop Environments
---

### Post by Odyssey1942 on 2006-05-08
Back for lesson #2 :) 

The office computer that I put Ubuntu on is a new computer replacing an XP unit that went pear-shaped.

Happily, Open Office, browser and email all working OK, but now time to try to get all the files (mostly .txt , .doc , and .mp3 files from the Windoze format HDD to the new puter.

Being a bit dim-witted, I cheerfully made a CD with the files and popped it into the Ubuntu puter CD drive. It did not want to know. :confused: 

I (now) assume that there is a format issue, so how do I get the files onto the new computer? Hopefully there is a download for Ubuntu to allow it to recognize and read the CD?  :idea: 

There are way too many for a USB drive and the two computers are at totally different locations, though both are internet connected. I am a bit intimidated by ftp, so if anyone is going to suggest this, I will need a lot of handholding.

TIA

---

### Post by dickohead on 2006-05-08
You did the right thing by placing the files on CD, however, did you check that the files made it there successfully after burning? Check that first and then try this:

If there is a CD-ROM icon on the desktop, right click on it and choose "mount volume" or "mount".

If there is no icon you can try and type the following in a terminal:
sudo mount /media/cdrom
or
sudo mount /media/cdrom1
or
sudo mount /media/cdrom0

If none of those work maybe there is a problem with the disc or your CD drive?

---

### Post by Odyssey1942 on 2006-05-08
There is no CD drive icon on the desktop, but I wouldn't mind having one if someone can give me guidance on how to do this.

Here is a snapshot of what happened when I entered the commands you suggested

robert@ubuntu:~$ sudo mount /media/cdrom
Password:
mount: No medium found
robert@ubuntu:~$ sudo mount /media/cdrom1
mount: can't find /media/cdrom1 in /etc/fstab or /etc/mtab
robert@ubuntu:~$ sudo mount /media/cdrom0
mount: No medium found

This appears to me to indicate that cdrom1 is the correct designator for the CD drive, but it still cannot read the disk.

I have a feeling that I am at fault. I used Win XP to drag and drop onto the CD, but perhaps it needs to be "closed" somehow. If so, I'll go back to the other puter and figure out how to do that. 

Or is there something else I should try while at the Ubuntu puter? What do you think?

---

### Post by Jungingen on 2006-05-08
maybe it can help - try to mount to /media/cdrom correct device:
$sudo mount /dev/hdx /media/cdrom

"hdx" is there your cdrom drive connected - primary master - hda, slave - hdb, secondary master - hdc and finaly secondary slave - hdd

---

### Post by cyracks on 2006-05-08
You can find out what is your cdrom drive by typing.

$dmesg |grep hd
or
$cat /etc/fstab| grep /media/cdrom

and no /media/cdrom1 is not you cdrom drive.
(mount: **can't find** /media/cdrom1 in /etc/fstab or /etc/mtab)

---

### Post by ComplexNumber on 2006-05-08
> There is no CD drive icon on the desktop, but I wouldn't mind having one if someone can give me guidance on how to do this. the icon only appears after you've inserted the cd into the drive and its become mounted.
> 

I have a feeling that I am at fault. I used Win XP to drag and drop onto the CD, but perhaps it needs to be "closed" somehow. If so, I'll go back to the other puter and figure out how to do that. if you haven't made the cd multisession when you first burnt it in XP, it needs to be finalised. if its not finalised, then there will appear to be nothing on the disk....and thats probably why it can't be read.

---

