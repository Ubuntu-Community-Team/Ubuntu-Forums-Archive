---
title: "Unknown USB 'device' under /media"
date: 2009-02-22
forum: General Help
---

### Post by warped0ne on 2009-02-22
I was looking to free up some space on my secondary drive when I noticed I have a drive labeled **USB\040HDD** under **/media**.

[IMG]http://home.mchsi.com/~tk1/usb040hdd.png[/IMG]

I have no idea where this came from, but everytime I remove something from my computer, it get's larger and it's eating up about 30GB of hard disk space right now.

The only USB devices I have plugged into my computer right now are a Logitech webcam and a 4 port USB hub, neither of which have any internal storage, let alone 30GB.

My primary hard disk is &#8776; 75GB; 71.5GB for '/' and a 3 as a Swap.

My secondary hard disk is &#8776; 56GB, mounted at '/media/disk'.

Gparted does not show any further partitions.

I would like to delete this, however, I want to know if it's safe or how to create a recovery disk so I can back in without losing the bulk of my data.

Help please.

---

### Post by hansdown on 2009-02-22
Hi warped0ne.

If you double click the file, you can see what is inside.

---

### Post by cariboo on 2009-02-22
You should also be able to right-click on the device and unmount it.

Jim

---

### Post by warped0ne on 2009-02-22
Yah, sorry, I forgot to include a snapshot of the folders contents.

[IMG]http://home.mchsi.com/~tk1/usb040hdd-2.png[/IMG]

It appears to be a huge Live CD or another installation of Ubuntu, but I have no idea where it came from.

---

### Post by warped0ne on 2009-02-22
> **cariboo907 said:**
> You should also be able to right-click on the device and unmount it.

Jim
Nope, no 'unmount volume' option when I right click on this drive.

---

### Post by hansdown on 2009-02-22
It looks like a wubi install from usb thumbdrive.

---

### Post by warped0ne on 2009-02-22
> **hansdown said:**
> It looks like a wubi install from usb thumbdrive.

Isn't the 'wubi install' the Ubuntu in Windows installation?

---

### Post by hansdown on 2009-02-23
Yes.

What does the```
 read me
``` file say when you double click it?

---

### Post by warped0ne on 2009-02-23
The **README.diskdefines** file says I do not have permissions to open that file when I double click it.  However, when I open it through Terminal and Gedit, it's a blank page.

---

### Post by warped0ne on 2009-02-23
Ok, quick update. I'm not worried about the size of this folder anymore, now I'm worried that I cannot remove it.  I just ran

> sudo rm -rf /media/USB\040HDD

and the file is still there.

---

### Post by warped0ne on 2009-02-23
> **warped0ne said:**
> Ok, quick update. I'm not worried about the size of this folder anymore, now I'm worried that I cannot remove it.  I just ran

sudo rm -rf /media/USB\040HDD

and the file is still there.

I just did it again, and now the folder is gone.  The only thing I did differently was drag the folder into the terminal rather than type out it's location.  I haven't restarted yet, but everything seems to be ok.

---

### Post by warped0ne on 2009-02-23
I think this folder came from when I used *System > Adminstration > Create a USB Startup Disk* to create a bootable SD card for my EeePC.  What I'm not sure of is how that folder ended up on my hard drive when I have never asked that program to leave anything on the hard drive and always copy directly to the SD card only. 

Anyway, the folders gone, computer is running fine.  Thank you for anyone who responded.

---

