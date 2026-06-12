---
title: "Firebox Browser Occupies Entire Screen"
date: 2009-01-28
forum: General Help
---

### Post by igneousquill on 2009-01-28
For the past few weeks a problem has kept coming up with my Mozilla Firefox (on Ubuntu 8.10).  For no apparent reason the window occupies the entire screen, with no way to minimize or close without going into file.  The last few times it happened I fiddled with it until, again for no apparent reason, it cleared up. 

I can't seem to move the window and I can't find any setting to fix this.  Does anyone know what this is?

---

### Post by druellan on 2009-01-28
Try this:
Start Firefox and push F11 key, this will get back the title bar.
To avoid Firefox to open up on fullscreen again, push the restore button (the contrary to maximize), shrink the window a little, close and open up Firefox and then maximize the window again.

That should work.

---

### Post by igneousquill on 2009-01-28
That got it.  Thanks!

---

### Post by druellan on 2009-01-29
You're welcome :)

---

### Post by -kg- on 2009-01-29
> **igneousquill said:**
> That got it.  Thanks!

It probably won't for long.  :)

You need to assure that you have compiz-settings manager installed.  Go to System/Administration/Synaptics Package Manager, launch Synpatics, then do a search for "compiz" (without the quotes).  One of the entries will be "compizconfig-settings." Make sure this is installed.  If it's not, install it and accept the other things (which are dependencies).

Once you have insured you have compiz manager installed, go to System/Preferences and launch "Advanced Desktop Effects Settings."  Under "Utilities" click on "Workarounds."  At the very top of the screen you will see "Legacy Full Screen Support."  _Uncheck_ that box, and Firefox will never open that way again.

Until I found this out, I went round and round with Firefox, pressing F11 twice only for Firefox to do the same thing again a little later.  This solved it permanently.

---

