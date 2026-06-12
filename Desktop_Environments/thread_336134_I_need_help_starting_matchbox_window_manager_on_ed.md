---
title: "I need help starting matchbox window manager on edgy"
date: 2007-01-11
forum: Desktop Environments
---

### Post by jbus on 2007-01-11
I installed matchbox window manager and all its dependencies with synaptic. I'd like to run it for testing purposes, but it wasn't added to my GDM session list. Is there a way to add it to the session list?

---

### Post by rcoconnell on 2007-03-16
No help, but I have the same problem.

---

### Post by rcoconnell on 2007-03-17
I thought I should be more specific.  I've installed xubuntu edgy, and all of the matchbox packages.  gdm doesn't, however, offer me a matchbox session -- of course, I figured it would.  Digging around a bit, there seems to be a file

/usr/share/xsessions/xfce4.desktop

which is referenced in 

/etc/X11/gdm-cdd.conf

I figure there should be a similar matchbox.desktop, and reference in gdm-cdd.conf, but I don't really know how these work.  Can anybody provide some guidance?  The matchbox documentation only says what to do with .xinitrc.

-ross

---

### Post by rcoconnell on 2007-03-17
I ended up making a file /usr/share/xsessions/matchbox.desktop , and edited it so it read:

[Desktop Entry]
Encoding=UTF-8
Name=Matchbox Session
Exec=matchbox-session
Icon=
Type=Application

---

