---
title: "Screen resolution"
date: 2006-03-16
forum: Desktop Environments
---

### Post by terranz on 2006-03-16
Help

Since installing Nvidia drivers I no longer have access to resolutions higher than 1024x768

---

### Post by klahjn on 2006-03-16
[QUOTE=terranz]Help

Since installing Nvidia drivers I no longer have access to resolutions higher than 1024x768[/QUOTE]

This may help.  open a terminal and type sudo gedit /etc/X11/xorg.conf
after you enter your password then you should see a window with your xorg.conf inside it.
Locate the section where it shows your resolutions, "under monitor i believe"
be sure that the information you provide there is accurate according to the mfr
Make sure the Horiz Freq & Vertical Freq are set correctly.
Then save the file and close.
Reboot.  Hopefully that will fix your problem.

btw....i take gratitude in the form of $$........haha j/k

---

### Post by Blairboy on 2006-03-16
Another way would be to run "sudo dpkg-reconfigure xserver-xorg"  and just follow the steps through.  Just make sure you enable the resolutions that you want.

---

