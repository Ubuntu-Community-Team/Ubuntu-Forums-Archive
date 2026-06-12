---
title: "Media keys on Inspiron 1505"
date: 2007-06-27
forum: Dell  Ubuntu Support
---

### Post by derred on 2007-06-27
Is there any way to make the media keys work outside the Gnome/Metacity window manager. I am experimenting with Ion and KDE and don't know how to make these buttons function, and it's a big issue for me as I tend to have an mp3 playing in the background all the time.

---

### Post by rivasdiaz on 2007-06-27
They generate normal key codes, so you probably can config your desktop to catch this keys globally and do whatever you want. In Gnome they generate the preconfigured key codes for play/pause volume up/down, etc so nothing more is needed. Something similar should be possible in any desktop or even console application.

---

### Post by Paul S on 2007-06-27
In kde, each application has a settings configuration for keyboard shortcuts.  Use this to set the play, fast-forward, stop ,etc for that program.

Also, it can help to create a ~/.hotkeys file with these contents:

paul :~$ cat .hotkeys
keycode 160 = XF86AudioMute
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 162 = XF86AudioPause
keycode 144 = XF86AudioPrev
keycode 153 = XF86AudioNext
keycode 164 = XF86AudioStop

then create an executable script to run on login with the command "xmodmap ~/.hotkeys" in it.  In KDE, you put this in ~/.kde/Autostart/ but I'm not sure where in ion.

HTH

---

