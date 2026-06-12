---
title: "AAC .ma4 playback"
date: 2006-07-06
forum: Desktop Environments
---

### Post by JPMaximilian on 2006-07-06
I can play aac (.ma4) songs fine with XMMS, but they don't work with Amarok, or Rythmbox, or movie player.  What gives?

---

### Post by FredB on 2006-07-07
Try adding gstreamer plugins from universe and multiverse repositories.

To activate them, to go add / remove in applications menu, and in the dialog box, check both "show..." checkboxes. Click on apply, and after search for gstreamer.

You'll get access to what you need.

Hope I helped ;)

---

### Post by tool462rules on 2006-07-07
Fred that will work for Rhythmbox (Gstreamer) but not on amarok (Xine).

---

### Post by TheMono on 2006-07-07
Also, if I remember rightly, the version of Amarok in the repo's is an older one? 1.4 is the first to properly support AAC/M4A...

---

