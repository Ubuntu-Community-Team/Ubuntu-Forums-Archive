---
title: "Theme (Icons/Colours) Not Right in vncserver session"
date: 2005-11-10
forum: Desktop Environments
---

### Post by capistrano on 2005-11-10
I have Breezy Badger installed with both the Remote Desktop and vncserver runniung.

The Remote Desktop is perfect with vncviewer, just as if I was sitting at the computer. However, for Remote Desktop I have to leave the PC logged in. 

For this reason I installed vncserver so I could start a separate session.

It's a small point really, but the vnc sessions look a bit odd. Some icons are missing (like the trash can and minimize all windows icons). Also, all window borders are blue instead of the brown colour set in the selected "Human" theme. It looks like the vncserver sessions aren't applying the theme settings correctly.

Initially fonts weren't displaying correctly either but I fixed this by creating the following symbolic link: /usr/X11R6/lib/X11/fonts -> /usr/lib/X11/fonts.

Anyone know why the icons/colours are all askew in the vncserver sessions? And is there any way I can fix it?

Thanks.

---

### Post by Remmelas on 2005-11-10
edit ~/.vnc/xstartup and change
```
x-window-manager &
```
to be
```
gnome-session &
```
that way, vnc will start a true gnome session rather than a scaled back terminal session.  It should be noted however, that the more graphical activity you have, the more data must be transfered.  In other words, a full gnome session will not perform as well as if you just use the vnc4server defaults and start the apps you need from the command line, using them one at a time.

---

### Post by capistrano on 2005-11-10
Thanks for the reply, Remellas, but I've already done that. It is a gnome session, but for some reason it looks like the theme isn't being properly applied. Icons missing and wrong colours).

My .vnc/xstartup file is:
```
#!/bin/sh
xsetroot -solid grey
gnome-session &
```

---

### Post by capistrano on 2005-11-10
I think I now know why this is happenning, but not how to fix it.

It seems that the lost icons/colours problem only happens if the use is already logged onto another session already. I created a new user and logged onto a vncserver session with it and, lo, the icons were back and the correct colours were displayed.

Some files must be locked or something by the first log on.

---

### Post by Kyral on 2005-11-10
Yah logging into multiple GDM sessions with the same user makes thing VERY sketchy

---

