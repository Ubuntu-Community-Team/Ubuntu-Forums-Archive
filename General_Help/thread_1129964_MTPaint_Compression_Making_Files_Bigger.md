---
title: "MTPaint Compression Making Files Bigger"
date: 2009-04-19
forum: General Help
---

### Post by Mark76 on 2009-04-19
:o

Take a look at the screenshot

---

### Post by Mark76 on 2009-04-19
El bumpo

---

### Post by wjaguar on 2009-04-20
Check the PNG compression level ("Preferences/Files", or in the "Save as" window). Your file appears to be uncompressed (level 0).

---

### Post by Mark76 on 2009-04-20
Hmm. It appears it's not the compression to blame. Something happens when I scale them down from 1280 x 1024 to 1024 x 819 that makes them bigger.

---

### Post by wjaguar on 2009-04-20
> **Mark76 said:**
> Hmm. It appears it's not the compression to blame. Something happens when I scale them down from 1280 x 1024 to 1024 x 819 that makes them bigger.
Given that nothing like that had ever happened to anyone, and that the filesize matches one for an uncompressed file (not perfectly, but 2521694 and 2521712 are quite close), disabled compression is the obvious suspect.

If PNG compression setting is at nonzero value (set it to 9 if it isn't already, to be sure) and the problem still persists, then it could be a libpng bug, or a zlib bug - these things are very rare, but they do happen - or the resized image really had become incompressible. It is impossible to determine what happened from a screenshot showing the two filesizes.
You can test what happens when re-saving the original file unchanged, when scaling it to a different size than 1024x819, and when scaling a different file to 1024x819; and from the results of that, it would be possible to better understand the problem.

---

### Post by wjaguar on 2009-05-03
Most likely, this problem was caused by PNG compression level spinbutton stuck at 0, which in turn was caused by a bug in GTK+ 2.16 - promised to be fixed in GTK+ 2.16.2: [http://bugzilla.gnome.org/show_bug.cgi?id=581190](http://bugzilla.gnome.org/show_bug.cgi?id=581190)

---

