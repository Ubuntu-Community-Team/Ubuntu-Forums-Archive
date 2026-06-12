---
title: "How Do I Use KDE Kicker to Mount My CDROM?"
date: 2007-12-08
forum: Desktop Effects &amp; Customization
---

### Post by fester225 on 2007-12-08
Now that I'm running Gutsy, my CDROM won't mount on startup. When I use 'mount /dev/scd0 /media/cdrom0' , I get get error messages and the thing doesn't work correctly.

When I start Konqueror Home, click on Storage Devices, and then click on the CDRom, it works beautifully until I turn the machine off.

How do I find the script which Konqueror Home uses to mount my CDRom so I can auto-start it using Kicker?

---

### Post by smartboyathome on 2007-12-09
I don't think there is a way to do that. You can try forcing the drive to mount though (mount -f /dev/scd0 /media/cdrom0), but I don't know what the consequences for this are (as I have only done this once).

---

