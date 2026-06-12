---
title: "Firefox mysteriously takes over for nautilus"
date: 2006-04-20
forum: Desktop Environments
---

### Post by Valhalla on 2006-04-20
So, I did an update this morning and it updated firefox and the firefox gnome-integration packages.  Now, whenever I try to click on of my remote ftp servers under places, it fires up firefox.  This does not occur when I directly click the icon on my desktop or on the bookmark in nautilus.  This is somewhat frustrating as I prefer the old way and I use epiphany. I just keep firefox for its nifty User Agent spoofing extension.  Does anyone know how I can change this back?

---

### Post by Valhalla on 2006-04-20
Well, I figured it out, I fired up the configuration editor and changed

>/
  >desktop
    >gnome
      >url-handlers
        >ftp

to equals /usr/bin/nautilus "%s".  It had misteriously decided it was gonna be mozilla-firefox "%s".  Anyway, if anyone else has this problem, or something like it, theres the answer.

---

