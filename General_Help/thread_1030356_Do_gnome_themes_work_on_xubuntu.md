---
title: "Do gnome themes work on xubuntu?"
date: 2009-01-04
forum: General Help
---

### Post by rozilla on 2009-01-04
I'm trying to find some nice themes for xubuntu, but all I get is the stuff from xfce-look.org, and I'm not really into those. 
Do gnome themes work on xubuntu 8.04.1?

---

### Post by sub2007 on 2009-01-04
GTK 2.x themes work on Xfce and there are some good ones available. I have trouble getting GNOME .theme files working (I don't know if they are officially supported).

To install a theme in Xfce you need to extract the tar.gz to /home/*username*/.themes (or /usr/share/themes as root if you want it available for all users). Then click Xfce Menu > Settings > User Interface Settings to select the new theme.

---

### Post by Forlong on 2009-01-04
> **rozilla said:**
> I'm trying to find some nice themes for xubuntu, but all I get is the stuff from xfce-look.org, and I'm not really into those. 
Do gnome themes work on xubuntu 8.04.1?
There is no such thing as "gnome themes". You need to differentiate between the window content and the window boarders.

The window content get drawn by GTK+, so there are no GNOME (or Xfce) specific themes for that. GNOME and Xfce are exactly the same here.

What's different between Xfce and GNOME are the window boarders, because those get drawn by the window manager in use.
The default window manager in Xfce is Xfwm and you need specific themes for that.
GNOME's default window manager is Metacity.

It's possible to use Metacity on Xfce though, if you want a specific window boarder.

It's all about choice. :)

---

