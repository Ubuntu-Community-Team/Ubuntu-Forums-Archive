---
title: "Help! - Screensaver logs me out"
date: 2006-08-28
forum: Desktop Environments
---

### Post by max_croft on 2006-08-28
I've done a fresh install of Ubuntu and just intalled the AMD64-K8 kernel with the latest nvidia drivers. Everything is working fine. Because it's a fresh install, I decided to change the screensaver to something I liked. It opened up fine with a list of screensavers, I clicked on 'flurry', the screen when black and the monitor clicked as if changing resolutions, the screen came back up again and I saw the login prompt -- Weird, OK, that was probably just one of those one off things; so I try it again. As soon as I go System -> Preferences -> Screensaver .. the window doesn't even pop up this time. The monitor goes black, makes the resolution change click and then dumps me back out to the login prompt again.

Any ideas on what's going on and how I can fix it?

---

### Post by Sam on 2006-08-28
Delete the ~/.xscreensaver file (make backup first).

---

### Post by max_croft on 2006-08-28
Fixed! Thanks for that -- :)

---

