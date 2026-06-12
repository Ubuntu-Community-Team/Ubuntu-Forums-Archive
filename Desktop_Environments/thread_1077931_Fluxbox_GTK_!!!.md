---
title: "Fluxbox GTK !!!"
date: 2009-02-22
forum: Desktop Environments
---

### Post by xX-Felipao-Xx on 2009-02-22
Hi, I'm having a problem, and it is that when I log into my session, it loads OK, but if I want to "enable" the GTK appearance of the windows and stuff, I need to open the Gnome GTK Appearance daemon everytime I log in.

Is there a way to avoid doing this and get GTK started itself?

PS: The idea is not to put the daemon into the startup list, because I'll need to close everytime I log in ...

Thanks in advanceee

Cheers!!!!!!!:D

---

### Post by Anzan on 2009-02-25
Yes. install  gtk-chtheme and start it from CLI or put it in your root menu.

---

### Post by m_duck on 2009-02-25
Or you could install lxappearance, which achieves basically the same thing. Down to personal preference really.

---

### Post by xX-Felipao-Xx on 2009-02-25
Solved some days ago -you guys remembered me to announce it, sorry- by adding the line "gnome-settings-daemon" (without the quotes) to ~/.fluxbox/startup

---

### Post by kerry_s on 2009-02-25
> **xX-Felipao-Xx said:**
> Solved some days ago -you guys remembered me to announce it, sorry- by adding the line "gnome-settings-daemon" (without the quotes) to ~/.fluxbox/startup

gnome settings daemon, is run in the background, that's a extra program you don't need running, you get the same effect using lxappearance and nothing runs in the background using up resources.

---

### Post by xX-Felipao-Xx on 2009-02-26
Ohhh, so I'm gonna try lxappearance and then, I'll post my experience.

Thanks !

---

