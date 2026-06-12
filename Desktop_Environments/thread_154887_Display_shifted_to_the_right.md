---
title: "Display shifted to the right"
date: 2006-04-04
forum: Desktop Environments
---

### Post by shlomy on 2006-04-04
Hi,

I have just installed Ubuntu, and the display is positioned incorrectly, it is slightly shifted to the right so there's a small blank area on the left of the monitor and there's a small area on the right  that goes outside the monitor boundaries. I have an LG Flatron LCD monitor. Any help would be greatly appreciated.

The resolution is correct, 1280x1024. In text mode (e.g. the messages I see when shutting down) the display is positioned correctly.

Thanks,
Shlomy

---

### Post by Phlosten on 2006-04-04
It sounds like something may be not quite right with your X configuration file.
At a terminal prompt run 'sudo dpkg-reconfigure xserver-xorg'.

This will allow you to configure everything for the X server. Pay particular attention to the monitor setup part at the end. You may need to find out particular refresh rates etc for your specific monitor first.

---

### Post by shlomy on 2006-04-04
Thanks for the help. I ran the X configurator again, entered all the information, noticed that it correctly detected the card and the monitor, rebooted - and still, the same. Nothing has changed.

---

