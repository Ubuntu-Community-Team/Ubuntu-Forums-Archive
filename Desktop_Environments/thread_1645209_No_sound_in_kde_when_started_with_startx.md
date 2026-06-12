---
title: "No sound in kde when started with startx"
date: 2010-12-14
forum: Desktop Environments
---

### Post by arj1singh on 2010-12-14
I recently installed KDE in my ubuntu 10.10. To access KDE, I want to use
startx /usr/bin/startkde
But using it disables sound in KDE (Sound is working fine in GNOME). It doesn't sound for anything like login sound, totem, mplayer or any other player. But when I press Alt+Ctrl+F1 to change to virtual console, the playback resumes from where it was in time and when coming back Alt+Ctrl+F7 and the time in totem (or any other player) doesn't move. While log out also it doesn't play logout sound and doesn't logout, so I have to press Ctrl+Alt+F1 so that logout sound play then it exits.](*,)

When starting KDE by kdm or gdm, the sound works normally. But I don't want to login again using kdm or gdm and not to use root user to start kdm or gdm.

I don't know what is the difference between when KDE is started by startx or by kdm/gdm where the same user login in kdm/gdm as that for startx and how linux is managing I/O.

Help me please.:(

---

### Post by arj1singh on 2010-12-14
Edited ~/.xinitrc
exec /usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session /usr/bin/startkde

And then ran
startx

This fixed the problem ;)

---

