---
title: "USB external drive goes to sleep too early"
date: 2009-06-16
forum: General Help
---

### Post by U242 on 2009-06-16
Hi,

It's rather a general unix question

My external usb hard drive goes to sleep after 5 minutes or so. I'd like to be able to set spindown timeout myself. I tried the hdparm with -S parameter to set the standby (spindown) timeout but this doesn't work. Well I can create a cron job with "fdisk -l" to not let the hard drive go to sleep at all but I still want this parameter to be configurable. Any ideas?

ps (There is no bios setting I can adjust)

Thank you

---

### Post by sedawk on 2009-06-16
You can also try hdparm's -B and you can monitor the
status of the drive with "-C" to learn about the real status of the
hard disk.

I wonder if the timeout is controlled by the USB chipset, not
the hard disk itself, e.g. the USB chipset has a (hard coded)
timeout you cannot change with hdparm. Especially extern hard
disks without any power switch seem to have some enhanced
features (not "spin-up" until the USB cable is connected to a PC).

---

### Post by niteshifter on 2009-06-16
Hi,

The only sure-fire way I know of to change the internal timer on external USB drives is to use the vendor supplied tool - on a Windows box. This is more trouble than it's worth especially if the drive isn't FAT32 or NTFS.

The cron jobbed fdisk is a very popular solution :)

---

### Post by flux242 on 2009-06-16
> **niteshifter said:**
> 
The cron jobbed fdisk is a very popular solution :)

oh really? I figured it out just experimenting with my HD103SI I bought recently ;)

Well - find some vendor supplied utility was the first thing I did. Didn't succeed. At least this one h**p://www.samsung.com/global/business/hdd/support/utilities/Support_HUTIL.html is not a big help here.

Ok, seems like I should write a script that observes network activities and stops calling fdisk after some time of inactivity (say 60 minutes). (I have a file server on a router running debian)

---

### Post by flux242 on 2009-06-16
> **flux242 said:**
> oh really? 


oh heck! I forgot that I already have an account here and registered another one - U242. And now Firefox logged me in automatically with my old account!

---

