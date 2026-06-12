---
title: "gnome-screensaver (s) don't work"
date: 2009-08-15
forum: Desktop Environments
---

### Post by mr_jrt on 2009-08-15
I'm trying to set up a photo slideshow for a family PC, but I cannot get the screensavers to work.

I've worked around the silly lack of config options for the dir by editing the .desktop file for the screensaver, and I know these options work fine as I can manually run the screensaver binary:
```
/usr/lib/gnome-screensaver/gnome-screensaver/slideshow --location=/home/allusers/documents/pictures/photos
```..and it appears to pick up the images fine. However, I can't get it to work in the normal use case. :(

When I go to the screensavers config the preview for all gnome-screensavers just stays blank. All xgl screensavers also appear blank. All non-gl xscreensavers appear and preview/run fine.

When I run the gl savers manually they complain about the lack of xgl extensions...which is another issue entirely.

Any ideas?

---

### Post by autonomy on 2009-11-21
Looks like I had to stop compiz from drawing the desktop.

---

