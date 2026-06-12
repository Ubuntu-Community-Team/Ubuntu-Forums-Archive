---
title: "Screen resolution trouble"
date: 2009-02-10
forum: General Help
---

### Post by titan2020 on 2009-02-10
Hello,

I tried connecting my toshiba satellite a205 - s4607 laptop to my tv through the s-video output. When I changed the screen resolution i lost the task bars on my display. Can someone please help me get them back. I'm new to linux so the more details the better.

Thank you,

---

### Post by jonlemur on 2009-02-11
If you haven't customised your /etc/X11/xorg.conf file, I would recommend running ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and restarting the x-server with Ctrl+Alt+Backspace.  If you can't get the terminal open because of the taskbars being gone, you can switch to another terminal (don't remember what they're called) with Ctrl+Alt+F1 (and switch back with Ctrl+Alt+F7).  If you have to switch to the other terminal like that, either switch back to the graphical one and restart the x-server or just restart the computer (sudo reboot).

EDIT:
This is if you are wanting to get your computer where it was before you had the TV plugged in.  If you're still wanting to use the TV, we can try to help with that.

---

### Post by titan2020 on 2009-02-11
That's what i was looking for. Thank you.

---

