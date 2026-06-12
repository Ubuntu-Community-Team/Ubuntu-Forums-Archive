---
title: "Can't see the cd/dvd drive"
date: 2005-10-27
forum: Desktop Environments
---

### Post by blastradius on 2005-10-27
how do i get Konqeuror to see my cd drive.  I can see the floppy but that's all.  It reads ok as i watched a dvd through Kaffeine, but i want to install a game cd i have and can't find the drive.

Thanks

Eric

---

### Post by User_Program on 2005-10-27
In Konqeuror's address bar type 
> /media
There should be a list of drives there.

In kubuntu 5.10 an Icon will also show up on your desktop when media ect is loaded. Right click on that and "open" could help aswell
:)

---

### Post by blastradius on 2005-10-27
The drives are there, (although which is the right one? -cdrom or cdrom0).    
The problem is that if i click the drive it doesn't spin the disk and consequently finds nothing.

Stranger still, my Lord of the Rings dvd displays an icon on the desktop but according to Konqueror there's nothing in the drive! and my Uplink game CD doesn't even display a desktop icon although i know the disc is fine.

Any ideas?

---

### Post by jeremy on 2005-10-27
It is probably the bug that has been reported, [http://bugzilla.ubuntu.com/show_bug.cgi?id=18211](http://bugzilla.ubuntu.com/show_bug.cgi?id=18211)

---

### Post by User_Program on 2005-10-27
Find etc/fstab and look for your cdrom's location.
Mine is hdc. Yours could be somthing else.
In Konqeuror's address bar type
> media:/hdx  x being where your cdrom drive is located.

If there is still a problem.  You may have to create new mount entires the old way and not in media but in mnt.
But see if that works first.
Keep us posted.

---

### Post by blastradius on 2005-10-28
Thanks for your reply.

Mine is hdc as well, unfortunately the media:/hdc command resulted in:-

An error occurred while loading media:/hdc:
The file or folder media:/hdc does not exist

being displayed in Konqueror.

As i said, it is displaying the cdrom + cdrom0 but with nothing in there, even though it spins the drive when i put my cd in!  Seems crazy that i've managed to get my (wifes) Windoze partition mounted and accessible, but can't get my own cd drive working!

Any ideas?

---

### Post by blastradius on 2005-10-28
sorted it!!

I posted the question on linuxquestions.org as well and it turned out i needed to do this:-

sudo mount -t iso9660 /dev/hdc /media/cdrom

It works now, thanks again for your help.

---

### Post by User_Program on 2005-10-28
Glad you got it worked out !



Can one of the mods mark this as solved?

---

