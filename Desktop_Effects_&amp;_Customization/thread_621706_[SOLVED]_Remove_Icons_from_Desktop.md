---
title: "[SOLVED] Remove Icons from Desktop"
date: 2007-11-24
forum: Desktop Effects &amp; Customization
---

### Post by Sam Plamondon on 2007-11-24
I have been customizing my desktop for a while, but there is one small problem that I do not know how to get rid of.  On my desktop there are four icons:  "DellUtility", "MEDIADIRECT", "OS", and "RECOVERY".  These represent partitions associated with Windows Vista and my Dell computer's utilities, and I do not want them on my desktop.  How would I remove the icons from my desktop, without damaging or removing the partitions?

---

### Post by zvacet on 2007-11-24
```
gconf-editor
```

**apps<nautilus<desktop>unchek volumes visible**

---

### Post by Forlong on 2007-11-24
If you still want to keep the nice effect that you get an icon when inserting a CD/DVD or add an USB stick, you can mount the partitions to another path than /media (e.g. /mnt - I'm doing that myself).

---

### Post by Sam Plamondon on 2007-11-25
Thank you, it worked perfectly.

---

### Post by hebetude on 2008-01-23
Originally nothing appeared on my desktop, now after updates today and a reboot I have all my volumes appearing on the desktop.  I moved the automagical mount to the /mnt folder, but nautilus still grabs it.  The other partition is mounted at /backup, this is quite annoying ><.

I'd rather not nuke the volume setting, since it is indeed quite handy.  It's a bit stupid that it doesn't limit itself to either the /media folder or usb/cdrom devices

---

