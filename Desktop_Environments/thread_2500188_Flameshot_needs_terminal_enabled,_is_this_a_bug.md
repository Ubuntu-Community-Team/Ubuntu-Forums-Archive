---
title: "Flameshot needs terminal enabled, is this a bug?"
date: 2024-08-25
forum: Desktop Environments
---

### Post by IRQsRFun on 2024-08-25
On Ubuntu 24.04 (mostly default),

I am trying to use a snip-it like tool called flameshot.  It seems to work fine from the terminal.

Out of the box, the configure action work fine.  (right mouse click on the icon).
However, I could not get this to work until I
1) copied the file org.flameshot.Flameshot.desktop from /usr/share/applications to /home/kevin/.local/share/applications
2) change the state of the terminal property from false to true
3) reboot

Right click on flameshot->Take Screenshot now works.  I did not work before I made the change to terminal.

Perhaps someone could help with determining if this a bug with Flameshot (the app) or could it bne related to recent Wayland or Gnome changes?  

Obviously, having the terminal disabled is highly desirable.

---

### Post by currentshaft on 2024-08-26
Why is having the terminal disabled highly desirable? It is not obvious to me.

---

