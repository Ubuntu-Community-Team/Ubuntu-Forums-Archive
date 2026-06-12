---
title: "Gnomebaker, CD/DVD Creator"
date: 2006-10-08
forum: Desktop Environments
---

### Post by ales on 2006-10-08
Hello,

my problem is simple (to solve it, is not simple for me) :)   CD/DVD Creator always starts to create an image file - I don't undestand why, when it can write directly from the directory where the files are. But this is not the worst, worst problem is that after creating an image it starts to write the cd/dvd but directly it writes - without any writing - that it is finalizing the cd/dvd. Finally such the CD/DVD has burned the file structure and browsing it shows, that files are burned, but they are not there it's just the fille system - the files u can't play copy ...
I installed gnomebaker and it has the same problem - gnomebaker starts on the fly from drive to write - it writes in the dialog input/output error and starts to finalize the dvd. It writes about 1/4 of dvd and stops.

In windows there is no problem with the CD-R RW device. 

If u can help me please do so. :) THX

In attachement is the screenshot of dialog.
Ales

---

### Post by ales on 2006-10-08
Well what I found by browsing the forum is that I checked the dvd r drive it shows me tha there are only read persmission. Is this causing the problem?

If yes could you write me the command for terminal how to change it forever.


Ales

---

### Post by Kateikyoushi on 2006-10-08
Is the mount point owned by you ?

Right click on /media/cdrom and can check in properties.

---

### Post by ales on 2006-10-08
> **Kateikyoushi said:**
> Is the mount point owned by you ?

Right click on /media/cdrom and can check in properties.

This is how ot looks looks like the root is the owner.

---

### Post by Kateikyoushi on 2006-10-08
Seems no one has write persmission to the folder.
This should set write permissions for root,

```
sudo chmod 755 /media/cdrom
```

---

### Post by ales on 2006-10-08
> **Kateikyoushi said:**
> Seems no one has write persmission to the folder.
This should set write permissions for root,

```
sudo chmod 755 /media/cdrom
```

Thanks for code but something is wrong cause i did the command but when i look at properties of cdrom the owner is UNKNOWN. Don't know why. I added the picture. The writing of cd goes only a few seconds - see the second picture - and then it stops writing and starts finishing the cd.

Thanks for your time.

---

