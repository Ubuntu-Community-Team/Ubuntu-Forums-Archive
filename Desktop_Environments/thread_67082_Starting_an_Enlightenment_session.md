---
title: "Starting an Enlightenment session"
date: 2005-09-19
forum: Desktop Environments
---

### Post by Jesper Larnaes on 2005-09-19
Hi there,
I've just installed the e16 window manager on Hoary 5.04, which was pretty easy using Synaptic. The problem, however, is this: when I get to the log-on screen I am unable to choose "e16" from the sessions-tab. I've read through some of the other threads on the subject and tried to add a .desktop-file to /usr/share/xsessions. The file contained this:

[Desktop Entry]
Encoding=UTF-8
Name=E16
Comment=This session starts the Enlightenment (e16) window manager
Exec=starte16
Icon=
Type=Application

As far as I could gather from another thread, this should be sufficient. However, even though I after making this file am able to choose "e16" from the sessions-tab, Gnome is still launched.

Any helpful comments as to how I might fix this are much appreciated. Thanks.

/Jesper

---

### Post by JohanL on 2005-09-19
As far as I can remember (I´m on the wrong computer right now, so I cant check) I put in the whole path aftar Exec= when I did this on my box, i.e. Exec=/usr/bin/enlightenment.

---

### Post by Jesper Larnaes on 2005-09-19
Thanks a lot. It worked!! Cheers mate.

/Jesper

---

