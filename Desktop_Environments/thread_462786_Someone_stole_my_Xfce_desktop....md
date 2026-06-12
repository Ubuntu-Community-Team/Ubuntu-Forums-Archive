---
title: "Someone stole my Xfce desktop..."
date: 2007-06-03
forum: Desktop Environments
---

### Post by BroadArrow on 2007-06-03
After noticing that my wallpaper was gone, I opened the Desktop Preferences utility and found that everything was shaded out and the "Allow Xfce to manage the desktop" checkbox was clear. Checking the box brings up a dialog which says:

> To ensure that Xfce does not manage your desktop the next time you start Xfce, please be sure to save your session when logging out. If you are not using the Xfce session manager (xfce4-session), you will need to manually edit your ~/.config/xfce4/initrc file. Details are available in the documentation provided on [http://xfce.org/](http://xfce.org/)

However, the problem is then temporarily fixed *for the current session*. However, my desktop gets stolen again after logging out.

I encountered this on another machine that I switched from Ubuntu to Xubuntu and found that removing some of the Gnome packages fixed the problem. (I can't remember which packages now.) However, this machine has never had Gnome on it so I can't think how any Gnome session manager or window manager would ever have thought it had a right to mess around with my desktop.

Any ideas about what specifically is causing this and how to prevent it reoccuring?

Many thanks in advance to anyone who figures this out...

---

### Post by majed on 2007-06-03
did u save your session?

try to go to the session manager in XFCE and check the save session checkbox and also disable gnome services on startup..

this link can help you: [http://www.xfce.org/documentation/4.2/manuals/xfce4-session?lang=eu]("http://www.xfce.org/documentation/4.2/manuals/xfce4-session?lang=eu")

Good luck!

Majed

---

### Post by BroadArrow on 2007-06-03
> **majed said:**
> try to go to the session manager in XFCE and check the save session checkbox and also disable gnome services on startup.

Thanks. Are the Gnome services on startup needed by anything?

I wonder if something I install requires a package that changes that setting?

---

### Post by majed on 2007-06-03
> **BroadArrow said:**
> Thanks. Are the Gnome services on startup needed by anything?

I wonder if something I install requires a package that changes that setting?

If you don't know why or if you need it, then most probably you don't.

Disable it and if you figure out you need it, then you can always enable it from the same place.

I am just hoping this would work but really don't know.. I have it disabled myself.

---

### Post by BroadArrow on 2007-06-23
> **majed said:**
> If you don't know why or if you need it, then most probably you don't.

Disable it and if you figure out you need it, then you can always enable it from the same place.

I am just hoping this would work but really don't know.. I have it disabled myself.

Disabling it seems to have worked. Thanks.

---

