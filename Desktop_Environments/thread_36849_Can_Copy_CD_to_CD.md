---
title: "Can Copy CD to CD"
date: 2005-05-24
forum: Desktop Environments
---

### Post by stevenyu on 2005-05-24
I am currently having issue of copy CD to CD in Ubuntu, I have tried Gnome Baker, K3B, and the command line use dd to create image and use cdrdao for burnning, all three of them failed at the start for reading the DATA CD.

I remember I can copy CD to CD in Debian and Mandriva without any issues, but I can get it to work under Ubuntu???

The only thing I can do at the moment is burning backup data from HD to CD.  :???:

---

### Post by RastaMahata on 2005-05-24
[QUOTE=stevenyu]I am currently having issue of copy CD to CD in Ubuntu, I have tried Gnome Baker, K3B, and the command line use dd to create image and use cdrdao for burnning, all three of them failed at the start for reading the DATA CD.

I remember I can copy CD to CD in Debian and Mandriva without any issues, but I can get it to work under Ubuntu???

The only thing I can do at the moment is burning backup data from HD to CD.  :???:[/QUOTE]
 have you tried graveman yet? :)

sudo apt-get install graveman

I think it's in the universe repos (or multiverse, i dont remember)

---

### Post by stevenyu on 2005-05-25
Just did, still the same error!!!

I think it has something to do with Ubuntu not doing the unmount when system need to read the raw data image from the CD

---

