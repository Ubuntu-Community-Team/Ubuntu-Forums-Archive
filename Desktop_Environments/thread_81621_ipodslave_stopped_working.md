---
title: "ipodslave stopped working"
date: 2005-10-24
forum: Desktop Environments
---

### Post by ltmon on 2005-10-24
Hi there,

My ipodslave (i.e. "ipod:/" in konqueror) has suddenly stopped working.

I can confirm that my ipod is mounted rw at /mnt/ipod, and everything else looks the same as it did before.

Every time I load up "ipod:/", I get the message:

"Could not load ipodslave"

I've tried removing and reinstalling the ipodslave package.

Any ideas on how to fix this?

L.

---

### Post by Takis on 2005-10-25
I'm totally guessing here, but could this possibly be related to the media:/ bug...?
[http://ubuntuforums.org/showthread.php?t=79204](http://ubuntuforums.org/showthread.php?t=79204)
They have a stopgap solution, downgrading, but I don't know if that'll help.

---

### Post by ltmon on 2005-10-25
I doubt it, because I never got that bug (having been using KDE 3.5 the whole time).

I ended up fixing this by installing ipodslave from source.  It's a newer version with better playlist support anyway... so I'm happy :)

L.

---

