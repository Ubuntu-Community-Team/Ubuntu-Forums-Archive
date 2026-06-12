---
title: "Why can't I always see Thumbnails?"
date: 2008-12-17
forum: General Help
---

### Post by the lemming on 2008-12-17
Hello

If I look in my Photo Folder which is inside my Home Folder I can view Thumbnails of my JPEGS.

However if I try to view my JPEGS anywhere else, and especially on my home network I am presented with a generic Icon.  If I want to view the image I have to double click on it to fire up f-spot.

Is there any way that I can always view thumbnails of JPEGS irrespective of where they are stored?

Cheers

---

### Post by hambone79 on 2008-12-17
This is a setting in the Nautilus file manager. I don't have a Ubuntu machine in front of me at the moment, but if you go into the Nautilus settings there are options for setting the maximum file size to thumbmnail. If I remember correctly there are separate settings for local (on your hard drive) and remote (on a network share) files.

Just remember to be careful to set the maximum at a reasonable level, otherwise you could experience speed issues with Nautilus.

---

### Post by SeanHodges on 2008-12-17
> **the lemming said:**
> Hello

If I look in my Photo Folder which is inside my Home Folder I can view Thumbnails of my JPEGS.

However if I try to view my JPEGS anywhere else, and especially on my home network I am presented with a generic Icon.  If I want to view the image I have to double click on it to fire up f-spot.

Is there any way that I can always view thumbnails of JPEGS irrespective of where they are stored?

Cheers
To support hambone79's suggestion:

1) Open the Nautilus file browser (e.g. your Photo folder), and click on Edit -> Preferences.

2) Select the 5th tab ("Preview") and adjust the thumbnail settings. n particular:

- Set the "Show thumbnails" drop-down to "Always".
- Set the "Only for files smaller than" to "10 MB" (or "100 MB" if you have a REALLY fast network connection, and not that many images in a single directory).

---

### Post by the lemming on 2008-12-17
Thanks for the advice chaps, works a treat.

Cheers

---

