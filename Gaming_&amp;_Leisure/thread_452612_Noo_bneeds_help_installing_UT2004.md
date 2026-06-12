---
title: "Noo bneeds help installing UT2004"
date: 2007-05-23
forum: Gaming &amp; Leisure
---

### Post by knichel on 2007-05-23
I have the CD's for installing UT2004 and found the linux installer.  I can get it to run fine.  The problem is that when It asks for disk 2 I cannot figure out how to get disk 1 out (I tried unmounting it, but it is busy) and even just ejecting it and insterting disk 2, but can never get the installer to read disk 2.

Can someone help me?

--
Mike

---

### Post by MonkeyBoy on 2007-05-23
Have you tried copying the installer onto your pc and running it from there?  Then you should be able to unmount the cds from a seperate terminal window like so:

```
sudo umount /media/cdrom0 (OR WHATEVER YOUR CD DRIVE IS CALLED)
```

---

### Post by Cappy on 2007-05-23
You cannot run the installer from the CD. You must copy the installer to the desktop (or wherever) and run it from there. 
The complete install guide is here:
[http://gaming.gwos.org/e107_plugins/content/content.php?content.56](http://gaming.gwos.org/e107_plugins/content/content.php?content.56)

---

### Post by knichel on 2007-05-23
I did copy the installer to my desktop and run it from there.

---

### Post by knichel on 2007-05-24
Thanks, I got it working.  I was trying to sudo umount /media/cdrom rather than /dev/hdc and now it works.

Mike

---

