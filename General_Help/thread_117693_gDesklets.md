---
title: "gDesklets"
date: 2006-01-15
forum: General Help
---

### Post by Ubuntuud on 2006-01-15
Hi, my desklets are black... Not completely, just the background. What could be the problem? Is it Ubuntu?

---

### Post by jonny_boy27 on 2006-01-15
what is the background set to on the individual desklets?

---

### Post by Ubuntuud on 2006-01-15
Some of them are black, but some of them are white. But not just the background is black, also a large border around the desklet.

---

### Post by jasay on 2006-01-15
Try right clicking on the gdesklets icon in the notifcation area and selecting configuration.  Then unclick translucency.  Not sure why, but his has worked for many people.

---

### Post by pbb on 2006-01-15
I've had this also. It seems to be caused by all desklets defaulting to the non-existent "gfx/bg.png" background.
After I restarted my computer, all the black backgrounds were changed into the default desktop background, even though their background property still pointed to the non-existent background file.

---

### Post by Ubuntuud on 2006-01-16
It worked, thanks. But I still have an other problem, they disappear when I restart. Is there a way to make them to load themselfs during startup?

---

### Post by sunny_nwho on 2006-01-16
system--->preferences--->sessions-->startup programs  select ADD and type gdesklets it iwll start from ur next boot or logon

---

