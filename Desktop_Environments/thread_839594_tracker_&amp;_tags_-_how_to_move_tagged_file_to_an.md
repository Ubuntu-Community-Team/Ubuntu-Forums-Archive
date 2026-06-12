---
title: "tracker &amp; tags - how to move tagged file to another PC ?"
date: 2008-06-24
forum: Desktop Environments
---

### Post by rafalr on 2008-06-24
Hi,

the objective is to tag a bunch of ca 1'000 files on a Windoze run PC and move that bunch of files to an Ubuntu 8.04 run PC with tags not lost (visible for tracker).

As far as I know no windows based programm can produce tags that will "travel together with files" and be readable for tracker.

I arrived to a point that I produced a Live Ubuntu Hardy CD that has been optimised to contain all tracker-related packages plus a Paperbox GUI application (a deb package from launchpad.net)that is quite smart for easy making tags.

I can launch the live CD, can tag all files on local HD, but whenever I close the application/system and re-start the PC (using the Live CD) the tags are "forgotten". 

I then discovered that the indexing/tagging information is stored in /home/user/.cache/tracker and /home/user/.local/share/tracker catalogues. So after tagging done you need to copy those two catalogues on a USB and after you launch Live Cd again you first re-setup tracker and copy both catalogues from USB back to /home/user/... locations. Then all the tags are preserved and visible for tracker.

This is as far as I have gone - it seems that copying the tagged files to USB (done in many smart ways incl tracker tracking both the HD and USB) always looses tags. Also, if I first copy the files to USB and then tagg theme there - it is as far as I can go, because during the next restart (or actually after plugging the USB with tagged files to my Ubuntu PC) I always see that the tags are not maintained (even with /cache and .local directories backed up on USB and copied back to /home).

Do anyone know mechanics of tracker sufficiently to explain how to achieve this: moving/copying tagged files from one PC to another PC still maintaining the tags ?

all hints appreciated,
kuna

---

### Post by rafalr on 2008-07-02
anyone ?

---

### Post by life-on-mars on 2009-08-23
```
tracker-tag -l *file*
```

A script using tracker-tag that dumps all tags of a file into a variable and reassigns them after copying should do the trick.

If all file-names are unique, you could also create a database that updates the tags automatically whenever files are moved. Possibly tracker's own tag database could be used to rewrite the tags.

---

