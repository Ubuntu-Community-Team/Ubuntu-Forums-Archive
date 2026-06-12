---
title: "[SOLVED] GTK Theme looks bad"
date: 2008-06-30
forum: Desktop Environments
---

### Post by doorknob60 on 2008-06-30
Well, I'm using LXDE and I need a good matching GTK theme. I found this theme: [http://www.xfce-look.org/content/show.php/Wii-Black?content=45829](http://www.xfce-look.org/content/show.php/Wii-Black?content=45829), but when I install it it looks like this:

[img]http://img373.imageshack.us/img373/3662/screeniedw8.png[/img]

Any ideas? I'm assuming it needs a GTK engine, but I wouldn't know what to get...I have clearlooks and murrine already BTW, and probably more.

---

### Post by phoenix_abhi on 2008-06-30
This may not be the right place to ask, but ur desk compelling me to do so.
What is LXDE ? Is it compatable with Gnome ? What is the advantage ?

---

### Post by doorknob60 on 2008-06-30
[http://lxde.org/](http://lxde.org/)

> Introduction
LXDE is a new project aimed to provide a new desktop environment which is lightweight and fast.  It's not designed to be powerful and bloated, but to be usable and slim enough, and keep the resource usage low.  Different from other desktop environments, we don't tightly integrate every component.  Instead, we tried to make all components independent, and each of them can be used independently with few dependencies.
Features

    * Lightweight, runs with reasonable memory usage
    * Fast, rund well even on older machines produced in 1999
    * Good-looking, gtk+ 2 internationalized user interface
    * Easy-to-use, the user interface is simple, but usable enough
    * Desktop independent (suprise! Every component can be used without LXDE)
    * Standard compliant, follows the specs on freedesktop.org
    * Suitable for old machines

Components

    * PCManFM: The ultimate fast and robust file manager. It provides tabbed-browsing and desktop icons with low system resource usage
    * LXPanel: Feature-rich yet user-friendly desktop panel providing most crucial functions you expect from a desktop panel. Configuration is done through GUI
    * LXSession / LXSession_Lite: Standard-compliant X11 session manager with shutdown/reboot/suspend supports via HAL and gdm (LXSession Lite is a stripped-down lightweight version without X11 session management support, and it's more stable)
    * LXAppearance: LXAppearance is a new feature-rich GTK+ theme switcher able to change GTK+ themes, icon themes, and fonts used by applications
    * Openbox: Lightweight, standard-compliant, and highly-configurable window manager (This is not developed by us, but we use it as our default window manager). This can be replaced by any other window manager like icewm, fluxbox, metacity, ...etc.
    * GPicView: A very simple, fast, and lightweight image viewer featuring immediate startup.
    * Leafpad: Lightweight and simple text editor(This is not developed by us, but we suggest using this as default text editor).
    * LXTerminal:Desktop-independent VTE-based terminal emulator for LXDE without any unnecessary dependency (All instances share the same process to reduce memory usage)
    * XArchiver: Lightweight, fast, and desktop-independent gtk+-based file archiver (This is not developed by us, but we suggest using this as default archiver).
    * LXNM (still under development): Lightweight network connection helper daemon for LXDE supporting wireless connections (Linux-only)


It's fast on my craptop with 192 RAM and 400 Mhz processor :) The advantage is that it uses much less RAM. What do you mean when you ask if it's Gnome compatible? It's compatible with all the apps you currently use, and the themes, although I'm obviously having problems (Gnome has never touched this computer though, so I bet it would have the same problem o if Gnome was installed it would work better).

---

### Post by phoenix_abhi on 2008-06-30
I have Hardy x64 now (Ubuntu). My doubt was, is this LXDE same like installing KDE or Xfce in Default Ubuntu. After installing LXDE can I go back to Gnome from Starup option ? Is there any conflict. (I experienced some when I used KDE 4.0 on Ubuntu)

---

### Post by doorknob60 on 2008-06-30
Solved it by reading the comments and running this:
```
sudo aptitude install gtk2-engines-pixbuf
```

I knew I needed a GTK engine, just didn't know which one :-P Now it looks sweeet :D

> **phoenix_abhi said:**
> I have Hardy x64 now (Ubuntu). My doubt was, is this LXDE same like installing KDE or Xfce in Default Ubuntu. After installing LXDE can I go back to Gnome from Starup option ? Is there any conflict. (I experienced some when I used KDE 4.0 on Ubuntu)

Yeah it's just like installing KDE, Xfce, or another WM. It doesn't install much, I doubt it would conflict with Gnome. If so, you could always remove it. (No matter what the wiki says, use aptitude for easy uninstallation instead of apt-get, I'll have to edit that soon)

---

