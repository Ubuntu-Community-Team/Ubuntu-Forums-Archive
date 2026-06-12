---
title: "PNG not a valid file type ?!?!?!?!?"
date: 2010-05-20
forum: Desktop Environments
---

### Post by Cremator on 2010-05-20
Last night I was backing up data to my external drive and found that .png image files were throwing errors with the message warning that the <filename>.png was not a valid file type.

This happened on 50 odd images that were generated IN linux and existed nowhere else. I need these files moved to the external drive.

Does any method exist to get around this problem?

---

### Post by TenPlus1 on 2010-05-20
It seems strange that simply copying your .png files would throw up this error but generally when I have a file that the system doesn't recognize I'll right-click, select open with and chose (inyour case) the image viewer and click as default action...

---

### Post by maedox on 2010-05-20
Did this error occur on copy, or when opening the files after they were copied?
How do you backup the files? Did you try rsync? (rsync -avS /from/here/ /to/here/)

---

### Post by Cremator on 2010-05-20
Backing up.... From "Pictures" folder to External Hard drive (USB type)

Files were  being copied and not being opened.

Files ARE valid images as I use view them ok, they show up as ICONs no issue and they were made in GIMP.

TBH its not the first time this has happened, it has happened with other file types too like mp3's for example.

I have also noticed something odd about the filing system. It would appear that Ubuntu thinks my 20GB boot drive is 30GB. Fact that the drive has stickers stating as much, I wonder if a bug exists as I have also had some problems when backing up to DVD large files where it appears that the most I can fit on a 4.7 DVD is 4.1 Gig.


SO

Could this be down to the file system?

---

