---
title: "gconf-editor won't execute changes"
date: 2010-02-04
forum: Desktop Environments
---

### Post by xpacker on 2010-02-04
Hello--

I'm trying to get rid of the default Home and Trash icons on my desktop in Jaunty/Eeebuntu 3.0.  I unclicked them in the gconf-editor (Apps>Nautilus>Desktop).  However, the icons are still on my desktop.

I've checked and unchecked them, and also checked and unchecked the Computer and Network icons.  There is no change whatsoever.  Gconf-editor records the changes, but it won't execute them.

I'd be grateful for any help!

---

### Post by Psumi on 2010-02-05
Did you accidentally use gk/sudo gconf-editor instead of just gconf-editor? or did a password screen come up when launching gconf-editor?

if so, you're editing the root's desktop, not yours.

---

### Post by xpacker on 2010-02-07
Yes, that was the problem!  Everything's fine now -- thanks, Psumi!

---

