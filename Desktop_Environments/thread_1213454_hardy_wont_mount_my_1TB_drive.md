---
title: "hardy wont mount my 1TB drive"
date: 2009-07-14
forum: Desktop Environments
---

### Post by randywilharm on 2009-07-14
In Applications/Computer it is recognized - or at least listed-
as an SCSI drive. but I can't do anything with it.

 It's a Western Digital SATA internal hard drive. Western is notorious for
ignoring LINUX so they don't help much.
If anyone can point me to a tutorial, or better yet some code I
can enter in the terminal please tell me.

---

### Post by Dave_Connor on 2009-07-14
Try "dmesg" and see if Ubuntu picks up on the device.
If it reports back something then you can go to /media and create a directory with "sudo mkdir yourdirectory" and then enter your password and then access the drive with "sudo mount /dev/sdx /media/yourdirectory" and then you should be able to see the files on your drive.

---

### Post by randywilharm on 2009-07-17
> **Dave_Connor said:**
> Try "dmesg" and see if Ubuntu picks up on the device.
If it reports back something then you can go to /media and create a directory with "sudo mkdir yourdirectory" and then enter your password and then access the drive with "sudo mount /dev/sdx /media/yourdirectory" and then you should be able to see the files on your drive.
Hey thanks a lot-- I got it in! I used gksudo nautilus and 
got the permissions straght, too.
It's just those cheap (maybe) Western drives that Best Buy
is selling cheap these days. 
It's the "green" model and I got a cheap power supply so
things balance out nice.
The damn thing works great and will transfer data
at 55mB/s drive-to-drive.

Thanks again, and have a good one..

---

### Post by Dave_Connor on 2009-07-17
Your welcome, glad to help a fellow linux user out. :)

---

