---
title: "Update to 9.04 caused audio to be half volume?"
date: 2009-12-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bigkahuna on 2009-12-08
My wife has an Inspiron 1545 (also called a "15n") that came with Ubuntu 8.10.  About a week ago she did something to the audio driver (while setting up the scanner) which apparently messed up the audio driver(s).  I posted here for help and the advice was to upgrade to 9.04, which I did yesterday.  Doing so got the audio to work, but now the volume level is roughly half what it used to be.  I checked all the volume controls and they are all at 100%.  I also verified that the hardware volume controls (through the F keys) were also at 100%, but it's still about half what it used to be.  Any ideas?

---

### Post by bigkahuna on 2009-12-08
Found the fix:  open the Terminal and run "alsamixer".  One of the settings is at 70% by default.

---

