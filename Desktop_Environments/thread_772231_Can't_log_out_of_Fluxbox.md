---
title: "Can't log out of Fluxbox"
date: 2008-04-28
forum: Desktop Environments
---

### Post by blippy on 2008-04-28
I installed Hardy Kubuntu on an iMac, but I figured I'd try out the Fluxbox WM after doing apt-get install fluxbox.

Fluxbox runs fine, and I can switch virtual consoles when it's running. When I try to exit Fluxbox (via the exit menu item or by Ctl-Alt-Backspace), all the windows, including the slit, disappears, and I'm left with just the background. I don't get back to kdm, nor can I switch virtual consoles. The only thing I've been able to do is hit Ctl-Alt-Del to reboot the machine.

Sounds like I should be reporting a bug; but I wanted to ask about it here first.

---

### Post by blippy on 2008-04-28
Actually, I switched back to using KDE as my Window Manager, although Fluxbox is still installed. When I log out of a KDE session, the screen goes black. I am not taken back to kdm.

---

### Post by chaanakya_chiraag on 2010-01-22
Fluxbox's "Exit" menu item exits out of Fluxbox, not the actual session.  I'm not exactly sure how to actually log out of a Fluxbox session.  I just shutdown or suspend my laptop.

---

### Post by Euboon2 on 2010-11-06
Control-Alt-Backspace seems to have been disabled in newer OS update.  The "exit" from Debian menu is handy. I would open up "/etc/X11/fluxbox/fluxbox-menu" and copy some useful items to my personalized fluxbox menu file.

---

### Post by chaanakya_chiraag on 2010-11-07
You can reenable it by (in GNOME) going to System->Preferences->Keyboard Layout and hitting modify and then expanding the "Key Sequence to Kill the X Server" thingy and then enabling Ctrl-Alt-Backspace! :)

---

