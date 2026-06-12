---
title: "Lost the logoff pop-up window, need some help..."
date: 2008-03-22
forum: Desktop Environments
---

### Post by Keyper7 on 2008-03-22
Hi,

I recently had to recompile the gnome-panel package to fix a small bug. Everything went smoothly, except for one thing: I've lost the Ubuntu logoff pop up window (the one that shows when you click on top-right button in the desktop, with shutdown, restart, hibernate, etc. buttons). It's been replaced with two different popups, "Exit" (switch user and logoff) and "Shutdown" (restart, hibernate, etc.).

As far as I know, this is the original Gnome design, so what I lost is the Ubuntu personalization (another evidence of this is that I've lost the "about ubuntu" button). Quite strange, considering apt-get source applies all ubuntu patches automatically.

Any help on how can I fix this? Installing the original gnome-panel package had no effect.

Thanks,
-Keyper7

---

### Post by Keyper7 on 2008-03-23
*bump* nothing?

---

### Post by Patb on 2008-03-25
Keyper, I think the command which starts that popup window is:
```
gnome-session-save --kill
```
Test it first from a terminal.  If it's okay, you could try a sort of bandaid repair (which I recall doing myself in similar circumstances) by binding the relevant key or menu item or panel icon to that command.  

Cannot tell you anything about the "About Ubuntu" button, sorry.  

Good luck, Pat

---

