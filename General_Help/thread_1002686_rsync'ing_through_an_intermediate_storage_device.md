---
title: "rsync'ing through an intermediate storage device"
date: 2008-12-05
forum: General Help
---

### Post by panfist on 2008-12-05
I am trying to use rsync to synchronize a large collection of files, approximately 1 million files totalling 2TB of space. the amount of data I have to synchronize is too much to send over the internet. 

Ss it possible to rsync through intermediate storage, like from source -> external drive -> destination. I would like rsync to build a file list based on the diff between the source and dest, but then copy to the external drive instead of directly to the destination.

Thank you.

---

### Post by panfist on 2008-12-06
Anybody?

---

### Post by panfist on 2008-12-08
Last bump before I let this die.

---

### Post by p_quarles on 2008-12-08
From the rsync man page:
[quote=man rsync]Usages with just one SRC arg and no DEST arg will list the source files instead of copying.[/quote]
Once you have the file list, you should be able to pipe that information into another command via xargs.

---

