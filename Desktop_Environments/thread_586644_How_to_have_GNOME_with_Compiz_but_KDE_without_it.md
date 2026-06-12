---
title: "How to have GNOME with Compiz but KDE without it?"
date: 2007-10-22
forum: Desktop Environments
---

### Post by dilney on 2007-10-22
I have GNOME and KDE installed.

I like to use GNOME with Compiz, but don't really like the way KDE interacts with Compiz (e.g. multiple desktops don't show correctly, cube has only 1 side).

Is there a way to enable Compiz for GNOME only leaving KDE sessions without Compiz?

Thanks.

---

### Post by happysmileman on 2007-10-22
> **dilney said:**
> I have GNOME and KDE installed.

I like to use GNOME with Compiz, but don't really like the way KDE interacts with Compiz (e.g. multiple desktops don't show correctly, cube has only 1 side).

Is there a way to enable Compiz for GNOME only leaving KDE sessions without Compiz?

Thanks.

Well first of all look in "~/.kde/Autostart" or something like that for a script to start it, it MIGHT be in there.

Secondly you'll have to look for XSessions, these are the scripts that would start up KDE or GNOME after you log in, I'm on Gentoo so don'ty know where they'd be on Ubuntu, since I'm almost certain they're in different places.

Though personally I think it'd make more sence to try get it to work in the settings options, I run KDE and it's all fine, my cube has 4 sides and my desktops all show

---

