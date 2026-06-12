---
title: "GNOME wouldn't start - splash screen not showing"
date: 2006-09-08
forum: Desktop Environments
---

### Post by lukaszd on 2006-09-08
Hello all,

My problem appeared surprisingly after installing the linux-686 package (though it's also relevant when I switch to the older, 386-compiled kernel). I put my login and password into the gdm welcoming screen and all I get is the window manager - blank screen and a mouse pointer.

Now, if I log into a console, set DISPLAY and run nautilus, my desktop icons will show up. If I run gnome-panel, I'll get it, too. A visit to System->Preferences->Fonts will apply my current theme. All in all, the system can be made functional by hand but something definitely breaks the automatic startup.

I wonder if anybody could point me to any config/startup files I might have a look into. Let me add that I've tried renaming .gnome* directories (to no effect) and that .Xsession-errors doesn't offer any explanation.

TIA,
Lukasz

---

### Post by linux_newbie on 2006-09-08
I have a similar problem. This is something wrong with the Gnome login screen. The current workaround that I use is, set the default Display Manager to KDM and then on the login screen, select session as Gnome after which it works fine.

If any can tell us what is wrong, it would be higly appreciated

---

### Post by bruno2 on 2006-09-08
Well, I have a similar problem as well. I first tried to install standard ubuntu but it hanged on installation. I then tried Kubuntu and no problem with it. However, when I install gnome (using KDM as session manager) it happens again the same, it apparently starts loading but it ends up in a blank screen (it shows the ubuntu background theme but nothing else) and the mouse pointer. ???

---

### Post by lukaszd on 2006-09-14
Gosh, this was simple.. somehow I must have accidentally removed gnome-session - I reinstalled it and everything's fine again..

---

