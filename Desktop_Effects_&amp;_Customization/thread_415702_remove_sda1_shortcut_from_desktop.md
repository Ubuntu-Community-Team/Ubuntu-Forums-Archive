---
title: "remove sda1 shortcut from desktop"
date: 2007-04-20
forum: Desktop Effects &amp; Customization
---

### Post by granite230 on 2007-04-20
Yesterday I installed Feisty on my laptop. It's now a dual boot (Windows XP / Feisty) and on my desktop is a shortcut to my Windows partition (sda1). I don't like this shortcut on my desktop. Is there a way to get rid of it?

I still want to be able to access it via Places > Computer so unmounting is not an option, right?

---

### Post by lluisanunez on 2007-04-20
Use gconf-editor
Go to Apps >> Nautilus >> Desktop 
Uncheck "show mounted volumes icon" or similar

---

### Post by floke on 2007-04-20
If you uncheck that then you wont be able to see mounted usb's, CDs, DVDs etc.
So have to manually unmount it. From a terminal type

sudo umount /meda/sda1

I have the same problem - trouble is it reappears on next boot. 
I reckon we might have to comment the mount out in the fstab - ie place a '#' in front of the line in the /etc/fstab file that mounts the disk - but haven't yet tried this.

Good luck

* EDIT * Didn't see you didn't want it unmounting - oh well....

---

### Post by aidanr on 2007-04-20
doesn't that also remove things like cd's and usb disks, if you change /etc/fstab to mount the volume somewhere other than /media (eg. /mnt) it shouldn't show up (might need to restart)

at least this worked for me on xubuntu, should be the same for ubuntu


edit:// and for the places > computer thing, just browse to /mnt in nautilus and drag the folder over to places and it'll then show up

---

### Post by Rui Pais on 2007-04-20
> **Steve.K said:**
> If you uncheck that then you wont be able to see mounted usb's, CDs, DVDs etc.
So have to manually unmount it. From a terminal type


No, not a problem. The 'mounted volumes' of gconf-editor refers only to mounted partitions (non removable media). CD, DVDs, pens ans floppys still be appear when mounted.

---

### Post by floke on 2007-04-20
No it doesn't  - and have just double checked.
Apps-Nautilus-Desktop - Volumes Visible - uncheck - there goes my usb - reheck - back again!

---

### Post by granite230 on 2007-04-20
I now changed /etc/fstab. I changed the sda1 part from /media/sda1 to /mnt/sda1. This removed the shortcut on the desktop but also the other one (Places > Computer).

Now when I go to the filesystem I see /media/sda1 exists but is empty. /mnt also exists but is also empty. Where can I find the contents of sda1?

---

### Post by aidanr on 2007-04-20
the folder /mnt/sda1 has to exist to mount to it, so

sudo mkdir /mnt/sda1
sudo chown [username] /mnt/sda1
sudo chgrp [username] /mnt/sda1
sudo mount -a

and to get the places shortcut back again, just drag the folder there from nautilus

---

### Post by granite230 on 2007-04-20
Okay so far everything worked except for one thing: I can't drag anything from the /mnt/sda1 folder to the Places > Computer space. It says: 'Preparing to copy'.

---

### Post by Rui Pais on 2007-04-20
> **granite230 said:**
> I now changed /etc/fstab. I changed the sda1 part from /media/sda1 to /mnt/sda1. This removed the shortcut on the desktop but also the other one (Places > Computer).

Now when I go to the filesystem I see /media/sda1 exists but is empty. /mnt also exists but is also empty. Where can I find the contents of sda1?

The only stuff that appear on Places ->Computer are the ones you mount on /media.

You can do what luisanunez suggested. There is no problem as Steve.K just double checked.

---

### Post by granite230 on 2007-04-20
> **Rui Pais said:**
> The only stuff that appear on Places ->Computer are the ones you mount on /media.

You can do what luisanunez suggested. There is no problem as Steve.K just bouble checked.

Okay I guess I'm finished then. The shortcut is removed from the desktop and I can still access the sda1 partition via /mnt/sda1 so I'm satisfied anyway! Thanx for your help!

---

### Post by aidanr on 2007-04-20
> **granite230 said:**
> Okay so far everything worked except for one thing: I can't drag anything from the /mnt/sda1 folder to the Places > Computer space. It says: 'Preparing to copy'.

like so, i wasn't very clear

---

### Post by granite230 on 2007-04-20
> **aidanr said:**
> like so

That's clever! Didn't know that! Thanks! :)

---

### Post by aidanr on 2007-04-20
no problem :)

---

### Post by Catsworth on 2007-04-30
Hi Guys,

I've made the changes described above, and I still have the icons for those partitions on the desktop.

My understanding was that they would disappear, do I need to reboot for the changes to take effect?

---

### Post by aidanr on 2007-04-30
yes, reboot

---

### Post by tbrothers on 2007-12-16
This worked GREAT for me.  Thanks for the tip!!  
The volume shortcuts have annoyed me long enough.

Just make sure if you're logged in as a user (e.g. terry) that you don't "sudo gconf-editor" or the icons will NOT be removed for user terry.

Use gconf-editor
Go to Apps >> Nautilus >> Desktop
Uncheck "show mounted volumes icon" or similar

No Reboot Necessary

---

### Post by Holleywood on 2008-01-04
> **aidanr said:**
> the folder /mnt/sda1 has to exist to mount to it, so

sudo mkdir /mnt/sda1
sudo chown [username] /mnt/sda1
sudo chgrp [username] /mnt/sda1
sudo mount -a

and to get the places shortcut back again, just drag the folder there from nautilus

Ok, I did that for 3 devices, sda1,2,3. The contents of the ones on the desktop show up in the new directories. I do not understand how to unmount them from /media. If I right click, it tells me I do not have permission. If I try to edit fstab, it tells me I do not have permission. Please help.

---

### Post by Holleywood on 2008-01-04
I forgot to add that I used this command also:

sudo mount /dev/sda1 /media/usb

which I got from another thread, (and substituted the new directory in the place of "/media/usb")

---

