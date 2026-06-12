---
title: "Image my hard drive to a larger one and be alright?"
date: 2008-12-20
forum: General Help
---

### Post by Elchbulle on 2008-12-20
Currently I have a 160 GB drive showing up as /sda, a 320 gb drive as /sdb

I want to image my 160 gb drive to a new 320 gb drive and get rid of the 160...  

I have Acronis drive image, and have imaged drives many times in the past, but I just want to make sure that it will work ahead of time.  Will it copy all necessary boot items and whatnot?  Then when it boots into ubuntu I will just partition the extra space and mount it somewhere like /space ?

Currently my /etc/fstab is set to assign mount points via UUID, I'm guessing this may cause problems as obviously the drive UUID is going to change.  Should I change it to /dev/sda1 and /dev/sdb1 before I image?


Thanks for any and all help!

Tim :confused:

---

### Post by cdtech on 2008-12-20
Your correct in assuming your UUID's would change. Using /dev/sda ect.. would correct this.

---

### Post by Elchbulle on 2008-12-20
Thanks for the quick reply, I like your avatar! 

Quick question then, if somehow the /sda and /sdb part were to be switched by the drive changing could I somehow still fix that after it attempted to boot the first time?

Obviously I would change /etc/fstab first to the ones I would think they would be assigned to (the primary being /sda  but I have seen it switch around in the past... if yo know what I mean.


Thanks again!

---

### Post by cdtech on 2008-12-20
Sure, you could just use the live cd to find your drives, using the sudo fdisk -l command then edit the file while in live cd. You could even get the UUID's while your in there.

Thanks for the flowers. :)

---

### Post by Elchbulle on 2008-12-20
Awesome!  So I take it the live cd is the boot cd correct?  It has some sort of maintenance mode option when you boot it?

Thanks much for all this help

T

---

### Post by Elchbulle on 2008-12-20
Or maybe it's the gparted live cd in your signature!  I am checking that out right now.

Thanks!
T

---

### Post by cdtech on 2008-12-20
There are both. The live cd allows you to boot into a normal GUI environment, then you can mount your drives as you would with a normal install.

---

