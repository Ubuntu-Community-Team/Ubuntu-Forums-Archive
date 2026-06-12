---
title: "KDE From Gnome Desktop Install"
date: 2007-04-11
forum: Desktop Environments
---

### Post by Holzster on 2007-04-11
Hello

This I think will be an easy one..

I have Ubuntu (Gnome) I want to install the KDE desktop but I do not want the KDE theme that you get when you use 'apt-get install kde-desktop'  what is the pakage called where you just get the desktop that you can choose at the log on screen while keeping the gnome theme.

thanks

---

### Post by panicbyte on 2007-04-11
try:
sudo apt-get install kubuntu-desktop

WARNING! It basically turns everything into kubuntu including the boot splash screen

---

### Post by panicbyte on 2007-04-11
however gnome will still be available

---

### Post by Holzster on 2007-04-11
thats what I was trying to ask - maybe I said it badly

I want to keep the Gnome theme  I just want KDE thats why I do not want to kde-desktop install

any ideas?

---

### Post by aysiu on 2007-04-11
Installing KDE in any of its forms (kdebase, kde-core, kubuntu-desktop, kde) will not get rid of Gnome.

When you install KDE, you'll be asked if you want GDM or KDM to be your default display manager--it sounds to me as if you'll want to answer *GDM* (that's the login screen manager).

---

### Post by y0ssarian on 2007-04-12
Do you mean you want to keep the gnome login screen theme? If you do, I don't know how to change to login from KDE, but just boot into GNOME and choose login from the System menu at the top. I'm not at my home computer right now, so I don't know the exact name, but if you are unable to find this, let me know.

---

### Post by y0ssarian on 2007-04-12
Sorry for the double post but do you know if when you boot, you're launching kdm or gdm? This may also be your problem.

---

