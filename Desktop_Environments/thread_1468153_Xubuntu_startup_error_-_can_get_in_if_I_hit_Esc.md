---
title: "Xubuntu startup error - can get in if I hit Esc"
date: 2010-05-01
forum: Desktop Environments
---

### Post by daboochmeister on 2010-05-01
Hi, using Xubuntu 9.10 on a Dell GX270, 500MB memory, Intel 82865G integrated graphics.

On logging in, I get an Xsession error -- unless I hit Esc, as soon as the initial splash screen (the one with a bundle of mosquitos buzzing around each other) appears.  This is iffy -- I have to time it right. 

The .xsession-errors file produced has the following in it:


```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/startxfce4: X server already running on display :0

** (gnome-screensaver:18048): WARNING **: Failed to get session presence proxy: Could not get owner of name 'org.gnome.SessionManager': no such name

** (xfwm4:18061): WARNING **: Unhandled keyboard shortcut
xfdesktop[18067]: starting up
gnome-screensaver: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
xfce4-settings-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfce4-menu-plugin: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
xfce4-session: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
xfsettingsd: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
xfwm4: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
Thunar: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
xfce4-panel: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
xfce4-places-plugin: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
The application 'xfdesktop' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

```

Any help?  I know the GPU shares main memory ... is there a resource contention or something?

tia!

---

### Post by dino99 on 2010-05-01
try: sudo dpkg --configure -a

---

### Post by daboochmeister on 2010-05-02
No joy.

What's funny is, if I hit Esc right after the Xubuntu mosquito-swirl animated gif (or whatever format) appears, I get in fine -- which makes me think that whatever X resource is the point of contention relates to the animation, maybe?  (is this where xsplash comes into play?)  Is there a simple way to replace that animated gif with something simpler?

Btw, I started with Ubuntu, then installed xubuntu-desktop, if that makes any difference.

Thanks!

---

### Post by daboochmeister on 2010-05-02
While I'd still appreciate any help, I have a temporary fix in place ... I disabled xsplash use during the login by commenting out the call to it in the /etc/gdm/PreSession/Default script.

I don't know if this is valid to report as a bug (and if so, against what -- xsplash, xorg, gdm, intel driver?)

---

