---
title: "Relation between desktops and windows managers ?"
date: 2006-06-12
forum: Desktop Environments
---

### Post by Vilius on 2006-06-12
Hi, I'm newbie. 
However, I thought that graphical user interface in Linux consist of server software (X-server) and some client 'desktop' (like gnome). But now I heard about some 'window manager' ( metacity and etc.)
Could someone explain me shortly what is relation between desktop (gnome, kde) and window managers( metacity, fluxbor ), what different functions they accomplish ?

---

### Post by Ramses de Norre on 2006-06-12
Gnome and KDE are called desktop environments and consist out of a window manager and a lot of apps. A window manager only, like fluxbox for example, is just the window manager (takes care of how windows look and behave) but doesn't include any apps of their own. So you can for example install ubuntu desktop and then fluxbox and use fluxbox as window manager with all gnome apps.

---

### Post by Vilius on 2006-06-12
So what default window manager uses ubuntu 6.06 ?
I found this info:
"The GNOME (pronounced "Gah-NOME") project's aim is to build a complete, user-friendly desktop based entirely on free software. It is not a window manager, and in fact has to be run in conjunction with a window manager. "

---

### Post by Ramses de Norre on 2006-06-12
Gnome is the default desktop environment, and gnome comes with a window manager, called metacity. Gnome is in fact metacity + a lot of apps.
It is possible to use another window manager if you like to, you then use something else instead of metacity but you still have acces to all installed apps.

---

### Post by Vilius on 2006-06-12
As I undestood, window manager(metacity) controls how all GUI looks, not gnome ?
I mean shape of buttons, and etc ?

---

### Post by Ramses de Norre on 2006-06-12
Uhm it's not that simple, the window manager draws windows, window borders, taskbars, desktop etc, some of this (desktop, taskbars) can also be drawn by independent apps (nautilus, gdesklets), the window manager is also responsible for the behaviour of windows, how you resize them, how to maximize/minimize them and so on.

The contents of a window however has nothing to do with the window manager, but is drawn independent of that. My apps in fluxbox look the same inside the window as in gnome, but they have different borders.

I'll attach a screenshot I just took of nautilus in fluxbox, the look of nautilus can be configured the same in gnome, but the titlebar and my taskbar and so one are typically fluxbox.

I hope you understand a bit =)

---

