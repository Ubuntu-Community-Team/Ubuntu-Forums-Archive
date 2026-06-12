---
title: "External HD Format?"
date: 2009-03-01
forum: General Help
---

### Post by adlin5000 on 2009-03-01
I have a 250 Gig IDE drive that I have put into a USB enclosure. I'd like to be able to load it up and give it to friends so they can access the files on it. Problem is most of my friends have not made the switch to Linux (despite my prodding). 

So my question is, what format should I make the drive so that both Linux and Windoz can access it?

---

### Post by taurus on 2009-03-01
Either fat32/vfat or ntfs.  Remember, you cannot save files larger than 4GB to fat32/vfat partition/drive.

---

### Post by hyperdude111 on 2009-03-01
> **taurus said:**
> Either fat32/vfat or ntfs.  Remember, you cannot save files larger than 4GB to fat32/vfat partition/drive.

Why is this?

I found out the hard way when i used my 500gb usb FAT32 as the storage space for my virtualbox drive, disappointed to find out that once i added music to it the file strangely corrupted.

---

### Post by mulligan.can on 2009-03-01
Just a limitiaton of the filesystem. It was designed a long time ago when most HDD weren't even 4gb.

Given how much support for ntfs has skyrocketed in recent times I would just format it as that.

You'll be able to access it and so will you friends. Win/Win.

---

### Post by adlin5000 on 2009-03-01
So ntfs allows larger then 4gig files, so what are the drawbacks?

---

### Post by sgosnell on 2009-03-01
You can get fragmentation.  NTFS filesystems have to be defragged every now and then if they slow down due to fragmentation.  It's not a huge problem, and there are defrag tools available in Windows.  Other than that, I don't know of any drawbacks.

---

### Post by adlin5000 on 2009-03-01
Any ntfs defrag tools available for Linux?

---

### Post by mulligan.can on 2009-03-02
Not as far as I am aware. It's not a big issue for a non-system drive though. Just slows down file access.

---

