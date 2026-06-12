---
title: "live cd will not run"
date: 2009-01-12
forum: General Help
---

### Post by michaelbenton on 2009-01-12
Back Ground
Dell 830
Intel Core 2 duo
2.49 GHz
3.5 GB Ram

I partitioned 120 GB HDD with gparted from the ubuntu live cd then install ubuntu to free space. (I took live cd out and my kid scratches it under foot.)

I would like to partition external drive but there doesn't seem to be gparted on the install of ubuntu. I try three other live cd's; gparted live cd, xubuntu live cd and the ubuntu live cd. The "loading kernel" stage takes quite a while to load, only to hang graphically on the "loading kernel - 100%" notification.

The drive burned the gparted live cd and reads photo cds to HDD, so I doubt it's the drive, besides, it's only one week old.

---

### Post by redbrain on 2009-01-12
So are you in ubuntu now?

If so you can partition anything after you:

$sudo apt-get install gparted

And you should have it in System->administration ithink

And you can partition another drive.

But do you mean you want to installed Ubuntu now on this 2nd drive? Or did i just mis read? :P

hope this helps

---

### Post by michaelbenton on 2009-01-12
But do you mean you want to installed Ubuntu now on this 2nd drive? Or did i just mis read? :P


Unfortunately I am in my xp because I am at school but I will try your suggestion and get back to you.

I wish to install a medley of OS's including; windows7, edubuntu, fedora9, windowsVista for educational purposes.

Thank you for your comments.

---

### Post by daprofessor on 2009-01-12
I've had this problem before, if it's not a stock disc, then I always had to slow down the write speed.  I know sounds crazy but I forget every time and that's what it ends up being.  (With a new CD-ROM drive)

---

### Post by michaelbenton on 2009-01-12
> **redbrain said:**
> 

$sudo apt-get install gparted

And you should have it in System->administration ithink

And you can partition another drive.


 


Thank you for your code REDBRAIN.  I got exactly what I wanted.


MichaelBenton

---

### Post by michaelbenton on 2009-01-12
> **redbrain said:**
> 

$sudo apt-get install gparted

And you should have it in System->administration ithink

And you can partition another drive.



Okay so I gparted up and I can recognize "My Passport" 250GB Portable HD, only problem is it shows "keys" icon next to the device name.  I cannot resize it, Any ideas?
The file system is FAT32.

Thanks

MichaelBenton

---

### Post by 1packer on 2009-01-12
You need to unmount anything with keys next to it. There should be an option if you right click to unmount the media, otherwise just do it from your places menu.
Edit: My bad, I just checked my partition editor, it's actually called swap-off when you right-click.

---

