---
title: "Get Gnome EDesktop Back From xfce"
date: 2010-05-16
forum: Desktop Environments
---

### Post by gwm on 2010-05-16
Please can someone help me to restore the normal Gnome Desktop.

While trying to get my task bar's quit button back and under time pressure, I didn't read the instructions carefully and changed my desktop to Xubuntu.
I've become accustomed to Gnome and the programs it offers and I really don't want to have to face another set of learning curves right now.

I'm running 64bit version 10.4.

---

### Post by XubuRoxMySox on 2010-05-16
Did you add Xfce or Xubuntu-desktop to an existing Ubuntu? Or are you using Xubuntu?

Open Synaptic Package Manager and see if **xubuntu-desktop** is installed. If you are using Ubuntu, you can simply uninstall it. Or if you'd rather keep it (and I recommend it - Xfce is awesome),

Then go to **Menu** (or right-click anywhere on the desktop) **> System > Login Screen**. Unlock it (by clicking on **Unlock** and entering your computer's root password). Now choose Gnome as your **default Session**. You can even have it automatically log you in if you like.

Enjoy,
Robin

---

### Post by gwm on 2010-05-16
Thanks Robin. Right click didn't give those kind of options but the **Applications>System>Login Screen** did. I am about to reboot and see what happens.

By the way, what I have seems to be Xubuntu but the options differentiate between that and is Xfce. What is the difference?

Thank you once again.

---

### Post by XubuRoxMySox on 2010-05-16
> **gwm said:**
> ... what I have seems to be Xubuntu but the options differentiate between that and is Xfce. What is the difference?

**Xfce** is the *desktop environment*. Like Gnome, KDE, LXDE, and E17 it is used in many different Linux distributions. You can install Xfce-4 in Ubuntu to experience the pure Xfce desktop.

**Xubuntu-desktop** is the Xubuntu developers' *implementation* of the Xfce desktop environment. It is not "pure" Xfce, but a metapackage of chosen settings and applications used in the Xubuntu distribution.

The same goes for Gnome (the desktop environment) and ubuntu-desktop (Canonical's implementation of Gnome with Ubuntu's default settings, applications, etc); and with KDE/kubuntu-desktop and LXDE/Lubuntu-desktop.

So for the "pure" LXDE experience without the entire Lubuntu suite of settings and applications, you can install LXDE from Synaptic and simply choose that for your *Session* when you log in. If you have room on your hard drive, you can install them all and try them out! 

When you have time to explore, of course. At login (unless you have enabled automatic login), you can click on Options > Session and choose any one you have installed! Gnome, KDE, Xfce (my favorite - took me a year of trying them all out to choose one), LXDE, etc.

Happy to help,
Robin

---

### Post by gwm on 2010-05-17
Thank you Robin,
That was a very useful and informative response.

---

### Post by XubuRoxMySox on 2010-05-17
You forgot to say if it worked after you rebooted, lol. But I assume from the SOLVED tag that it did. 

Happy to have helped,
Robin

---

