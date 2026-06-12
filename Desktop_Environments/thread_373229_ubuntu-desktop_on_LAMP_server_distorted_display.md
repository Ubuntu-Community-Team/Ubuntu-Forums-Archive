---
title: "ubuntu-desktop on LAMP server: distorted display"
date: 2007-03-01
forum: Desktop Environments
---

### Post by honiball on 2007-03-01
I installed ubuntu-desktop on my newly installed LAMP server (6.06).  When I rebooted, the new desktop (Gnome?) loaded.  However, when the logon screen loaded the display became distorted, as if the display frequency is wrong.

How do I change the display frequency for the opening logon screen?  I can logon, but can't see enough detail to go and change the settings in Linux.  Is there another way of changing the display settings (e.g. in non-graphics mode)?

---

### Post by honiball on 2007-03-02
I fixed it myself.... (with help from a different thread posted in this forum).

In terminal mode, I ran the command....
sudo dpkg -reconfigure xserver-xorg
...and selected all the defaults, except for the screen resolution where I chose 800x600, and then rebooted.

Problem solved :)

---

