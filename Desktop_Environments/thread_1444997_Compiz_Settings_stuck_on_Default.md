---
title: "Compiz Settings stuck on Default"
date: 2010-04-02
forum: Desktop Environments
---

### Post by Forgotten2191 on 2010-04-02
I recently upgraded my video driver, and I soon found out the Compiz settings for Animations and Animations Add-On had reset themselves to the default settings.  I went to go fix them and it turns out, all of my settings had stayed, they just appear as default settings.  For example, I have the Beam Up animation for opening windows.  The color set is blue, but when the animation is actually activated, it appears white.  How can I get the CompizConfig Settings Manager to respond the way I want it to?

Help or information on this would be greatly appreciated.

---

### Post by adamantoi on 2010-04-02
i think reinstall the compiz will quickly fix that.

---

### Post by Forgotten2191 on 2010-04-02
I tried that.  Didn't really work.  But my settings stuck when I reinstalled, so I think I need to delete the configuration file, but I'm not sure how.  I'm not overly Ubuntu-savvy.

---

### Post by lidex on 2010-04-04
Make sure "compizconfig-backend-gconf" is installed and configure ccsm>preferences to use it, not the flat file.

---

### Post by ronnielsen1 on 2010-04-04
Thanks, I had that problem too.

---

