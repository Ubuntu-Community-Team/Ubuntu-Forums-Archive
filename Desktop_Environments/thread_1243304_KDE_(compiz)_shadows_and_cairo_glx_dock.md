---
title: "KDE (compiz) shadows and cairo glx dock"
date: 2009-08-18
forum: Desktop Environments
---

### Post by x-shaney-x on 2009-08-18
Although I'm using gnome I do use a fair few KDE apps also.
I recently installed cairo dock and have found that when running it as glx-dock I lose all the menu shadows (compiz) on KDE apps, when I revert to the no OpenGL cairo dock the shadows come back.

Anything I can do about it as I would prefer to use the OpenGL version.

---

### Post by fabounet on 2009-08-18
I think it is relative to the Qt/opengl bug.
it affects Qt-based application, like VLC of Smplayer.
it's a know bug for 6 months now, and Qt guys don't care ...
but there is a workaround for that, you can find it easily I guess.

---

### Post by x-shaney-x on 2009-08-18
Not that easily (for me), since I can't find any workarounds.
Most of the info I can find relating to QT/OpenGL bugs is related to compiz crashing.
It never crashes for me, just doesn't show the shadows on kde menus (transperency is normal).

---

### Post by fabounet on 2009-08-19
it's not a crash, it's a visual bug inside Qt.
search for "export XLIB_SKIP_ARGB_VISUALS=1 "

---

### Post by x-shaney-x on 2009-08-19
Ahh that old workaround (seem to remember using it to fix flash problems some while ago).

So I can easily add the line to bashrc or something but is it likely to have any negative effects on anything else?

---

### Post by fabounet on 2009-08-20
you can add it to your .bashrc, but then think of modifying the launcher of Compiz and Cairo-Dock, which both need OpenGL.
you can write :
unset XLIB_SKIP_ARGB_VISUALS && cairo-dock
for instance

---

### Post by x-shaney-x on 2009-08-20
Thanks, most helpful :)

---

