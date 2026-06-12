---
title: "Sorting files properly in Banshee."
date: 2006-03-05
forum: Desktop Environments
---

### Post by Morbett on 2006-03-05
I've done some looking around, and I can't find the info I need.   I installed Banshee as an alternative to amaroK and loaded in a library.  In iTunes and amaroK, when you click on the column for artist, it lists the artists in alphabetical order.  The tracks in each album will also automatically be in order.  But in Banshee the tracks are randomly sorted.  I can't figure out how to get them to sort in order.  They are tagged properly for track numbers too.

Hmm...

---

### Post by Morbett on 2006-03-05
I rebooted and everything sorts in order now.  Strange.

---

### Post by RAOF on 2006-03-05
Banshee's sorting currently sucks.  It's one of the things on the dev's todo list :)

If your library is mainly albums (as mine is), and you're building from source, I've hacked together a patch which does proper "Artist->Album->Tracknumber" sorting, via a new "album info" column.  If you're interested, I'll post the patch, or you can find it on the banshee mailing list archives.

---

