---
title: "can I make XFCE default on netbook remix?"
date: 2010-01-04
forum: Desktop Environments
---

### Post by linuxhippy on 2010-01-04
can I make XFCE default on netbook remix?  I just bought a netbook with a fresh install of Ubuntu 9.10 netbook remix and am used to the snappy desktop of XFCE...can I use this on a netbook?

---

### Post by kerry_s on 2010-01-04
of course, just change it at the login menu.

---

### Post by linuxhippy on 2010-01-05
that's what I was hoping...I'm just using the live version off usb and it's slow on a big desktop pc.  So does the netbook remix of Ubuntu use the same repos as Ubuntu or do I need to use stripped down versions of programs I want?

---

### Post by kerry_s on 2010-01-05
same repos its still all ubuntu.

---

### Post by snowpine on 2010-01-05
This will give you the Xfce desktop:

```
sudo apt-get install xubuntu-desktop
```

Then, you can log out and choose Xfce from the login screen.

If the computer is brand new to you, you might consider a fresh reinstall of Xubuntu. That way, you won't have all the Netbook Remix stuff taking up space on your hard drive. (Obviously if you have a big hard drive, you don't need to worry about it... my netbook only has 8gb so I try to keep it lean and mean.)

(edit) the only "catch" is if the current OS is factory pre-installed with special drivers... then you might not want to do a fresh reinstall. Which netbook is it?

---

### Post by linuxhippy on 2010-01-05
It's a 160 GB System 76 netbook (Intel Atom).  I got it off ebay-it's a little over 4 months old.  The guy selling it said he just did a fresh install of ubuntu 9.10 netbook remix by wiping the drive and doing a live usb install from the downloadable iso file.  I want to make several partitions on it so that I can install xubuntu next to it and see which I like better.

---

### Post by snowpine on 2010-01-05
> **linuxhippy said:**
> I want to make several partitions on it so that I can install xubuntu next to it and see which I like better.

Waste of hard drive space. Netbook Remix and Xfce are simply two different desktop environments over the same core system. You can switch between them from the login screen; separate partitions are not necessary. With a 160gb hard drive, no worries. :)

---

### Post by linuxhippy on 2010-01-05
that makes sense-the desktop remix is just another GUI.  I'll just add XFCE to that and all should be good.  The netbook should come by UPS tomorrow.  I'm just making plans :)

Thanks for the help!

---

