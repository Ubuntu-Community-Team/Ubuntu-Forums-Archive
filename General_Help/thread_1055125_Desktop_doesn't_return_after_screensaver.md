---
title: "Desktop doesn't return after screensaver"
date: 2009-01-30
forum: General Help
---

### Post by jcross on 2009-01-30
I just installed Desktop Version 8.10.  When the desktop goes into screensaver, and comes back out later my desktop is gone.  The wallpaper is there, but the icons are gone and I have to power down the desktop to get things back to the way they were.

Any ideas?

---

### Post by cmnorton on 2009-01-30
Before you power down the next time, try two things:

Either use a left-mouse click, or press CTRL+ALT+F1 and then press CTRL+ALT+F7.

My problem is slightly different. I cannot get the screen saver to stop. 

You can also look in your logs:

sudo tail /var/log/messages
sudo tail /var/log/syslog
dmesg | less

If it keeps happening, look around in Ubuntu launchpad for a similar sounding bug, or enter a new bug report.

---

