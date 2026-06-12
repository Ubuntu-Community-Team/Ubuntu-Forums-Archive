---
title: "Changing window manager in gnome"
date: 2006-02-20
forum: Desktop Environments
---

### Post by FIONEX on 2006-02-20
Hey,

I'm a new Ubuntu user (returning to the linux scene since 3 years - surprised to see so much change).  The point is, I like window maker and I want to try running it ontop of gnome.  I have window maker installed but right now, I'm having to shut down metacity and start up wmaker manually.  How do I do things properly?

Thanks in advance.

---

### Post by RAOF on 2006-02-20
You could add "wmaker --replace" to your gnome session using the session manager (System->Preferences->Sessions).  That should start it up on each login, and if wmaker supports the freedesktop.org window-manager standard, it'll replace metacity (Gnome's wm).

---

### Post by FIONEX on 2006-02-20
I've tried typing that in a terminal but it gives me an error.  I remember a place where you could select the window manager you want to use.  I can't find it :S.

---

### Post by RAOF on 2006-02-20
[QUOTE=FIONEX]I've tried typing that in a terminal but it gives me an error.  I remember a place where you could select the window manager you want to use.  I can't find it :S.[/QUOTE]
If there was once a place, it's long gone from Ubuntu ;)

You could check out poofyhairguy's [Knome guide]("http://www.ubuntuforums.org/showthread.php?t=115974") - that replaces metacity with kwin.  If you just do the steps which involve gnome-session, you should be able to strip out metacity and add "wmaker" to your session in the same way as kwin gets added.

---

### Post by FIONEX on 2006-02-21
I just wanted to say thx for helping me out.  I managed to get wmaker working with gnome.

I still have a small problem where the windows appear in my task tray AND as docked windows.  For some reason, checking off "Disable miniwindows.  For use with KDE/Gnome." isn't doing anything :S.  Any ideas?

---

