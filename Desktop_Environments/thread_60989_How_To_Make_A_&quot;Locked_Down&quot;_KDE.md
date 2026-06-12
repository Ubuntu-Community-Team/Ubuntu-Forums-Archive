---
title: "How To Make A &quot;Locked Down&quot; KDE"
date: 2005-08-30
forum: Desktop Environments
---

### Post by jlacroix on 2005-08-30
Hello Everyone, me again.

We have an Ubuntu PC that guests use, and we want to lock it down to the point where the user can do nothing but browse the internet.

I made a make-shift thing where I removed the KMenu, and only have an icon for firefox, but I can still right-click and get to things I don't want people to get to.

Anyway, it still autoloads Gnome when you start up, which defeats the whole thing easilly. I want it to autoload KDE. It used to ask if you want to set as default, but it doesn't any more. How can I make it autoload KDE, and make it so you cannot boot into any other window manager?

Also, how do I disable the terminal and mouse rightclicking?

Note: My wife uses that computer too, so for her she needs to keep full access.

---

### Post by godzero on 2005-08-30
Sounds like you want kiosk mode.
[http://www.tldp.org/HOWTO/KDE-Kiosk-Mode/](http://www.tldp.org/HOWTO/KDE-Kiosk-Mode/)
[http://extragear.kde.org/apps/kiosktool/](http://extragear.kde.org/apps/kiosktool/)
[http://www.linuxjournal.com/article/7718](http://www.linuxjournal.com/article/7718)
etc,, etc..

About the auto login/kde:
If you're using KDM, there's the config file... you can limit desktop environs in there. GDM must have similar functionality.

---

