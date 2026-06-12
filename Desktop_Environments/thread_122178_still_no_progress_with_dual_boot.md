---
title: "still no progress with dual boot"
date: 2006-01-26
forum: Desktop Environments
---

### Post by helmet on 2006-01-26
so i've looked everywhere and nothing has fixed this.

i have kubuntu installed to an 80gig sata, with windows on 2x160 gig sata in raid 0. grub is installed to the 80 gig so when i press F8 at boot to get the mobo's boot menu, i can select the 80 gig and it tries to boot. initially it just doesn't work at all, but i change in grub the

```
root (hd2,0)
```

line to read

```
root (hd0,0)
```

and it starts with the splash screen and gets to mounting /dev or whatever the second thing on the list is, and gives me an error about unrecognized device or something. so even though it can install to sdc1, it won't recognize sdc1 as being able to mount and whatnot. what is going on!

---

### Post by aysiu on 2006-01-27
Try [reinstalling Grub to the MBR](http://ubuntuforums.org/showthread.php?t=24113).

---

### Post by helmet on 2006-01-27
even if i wanted to i couldn't. windows is on the raid so if i try to install it to the mbr, it just messes everything up and i have to use fixmbr to get windows to boot. i want to have grub on the 80 with kubuntu, but it just won't recognize something, or it recognizes it as something different

argh...

---

### Post by GnuSense on 2006-01-28
helmet, what does the Windows stanza in your /boot/grub/menu.lst look like?

Here is what my stanza looks like, booting Windows off /dev/hdb:

> title           Windohs 
        map (hd0) (hd1) # Tell the 1st hard drive to pretend to be the 2nd
        map (hd1) (hd0) # Tell the 2nd hard drive to pretend to be the 1st
        root (hd1,0) # Tell GRUB Windows is on /dev/hdb1 
        savedefault
        makeactive # Sets the partition to active
        chainloader     +1  # Tells GRUB to load the Windows bootloader when done


Grub and LILO don't like booting Windows that is on other hard drives than the MBR, I've found.  Those "map" lines seem to help me.  I'm not sure how you'd use them with a S-ATA RAID array.

---

