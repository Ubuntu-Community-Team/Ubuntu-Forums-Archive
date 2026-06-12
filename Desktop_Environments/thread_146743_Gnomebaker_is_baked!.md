---
title: "Gnomebaker is baked!"
date: 2006-03-18
forum: Desktop Environments
---

### Post by John Jason Jordan on 2006-03-18
<Crossposted to AMD-64 support>
OS: Ubuntu-64 Breezy

Grrr.

So I'm trying to burn this ISO image of Ubuntu-32 Breezy Install CD for a computer group meeting tomorrow. I open Gnomebaker, which I've never used before, but it appears pretty straightforward. I start the process and a few seconds later Gnomebaker just disappears.

So I open a terminal and launch it from the command line. I repeat the process. And this time when it disappears the terminal says "Segmentation fault."

OK, screw it. I knew Gnomebaker wasn't going to work the minute I launched it. The menus and buttons were simple to understand and it was just too easy to use. This is, after all, Linux, right?

So after I toss Gnomebaker in the bin, what do y'all suggest I replace it with?

Or does someone have an idea what might be wrong?

---

### Post by eyebrowman92 on 2006-03-18
try k3b

---

### Post by virgule on 2006-03-18
You can use the terminal. Replace **?** with appropriate figures. For me, speed=8 (for 8x) and dev= is /dev/sr0. It is advised to use a lower-than-maximum speed for ISO burns. I found my device with dmesg.
```

]# sudo cdrecord -speed=? -v -pad -eject dev=/dev/??? file.iso

```

```

]# dmesg | grep CD
(...)
Attached scsi CD-ROM **sr0** at scsi0, channel 0, id 6, lun 0

```

As for what might be wrong I suspect 64 bit is not quite there yet. Just a guess tho ;)

---

### Post by taurus on 2006-03-18
Not sure what but lately, it seems like everybody is having problems with Gnomebaker!!!  I've never used that and don't intend to because k3b has everything that I need...  So, give k3b a try.  And yes, even though it's a KDE app, it will run in Gnome!  Otherwise, Graveman is another option.

---

### Post by John Jason Jordan on 2006-03-19
[QUOTE=taurus]Not sure what but lately, it seems like everybody is having problems with Gnomebaker!!!  I've never used that and don't intend to because k3b has everything that I need...  So, give k3b a try.  And yes, even though it's a KDE app, it will run in Gnome!  Otherwise, Graveman is another option.[/QUOTE]
Thanks to all for the suggestion. K3b is now installed and working fine. I also tried X-CD-Roast but couldn't get it configured. To hell with all of them. K3b rules!

I jsut hope it's not another one of those KDE apps that screw up your login -- you know "your last session lasted less than 10 seconds ..."

---

### Post by taurus on 2006-03-19
k3b is just an app so it will not screw your login screen or session.  :)

---

