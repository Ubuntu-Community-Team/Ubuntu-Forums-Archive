---
title: "Can't type at GDM (xorg error?)"
date: 2006-01-15
forum: Desktop Environments
---

### Post by durand on 2006-01-15
I don't know whether this is the right forum to post this problem as i don't use Ubuntu Forums much but i am such a n00b so here goes:
When i started breezy yesterday, i tried typing my username into gdm but as soon as i started typing, x restarted. I tried typing again, but it did the same thing. I restarted breezy about 3 times but no change... This seems to be caused by the letter and number keys only. Symbols, enter, backspace and other "power keys" work. :confused: I used ctrl+alt+f1 to access the terminal, logged in as root and tried starting x by using ```
$rm /tmp/.X0.lock
$startx
``` and x did start but as soon as i tried typing something into gedit, as a test, nautilus restarted. I can't access the gnome-term, kde-term, gaim, or opera. I have managed to run firefox and aMSN and both work properly, i can even type in them. The other problem i noticed is that i can't move windows around using metacity but it works when i use enlightenment. This whole set of problems were not there the day before yesterday, and as i didn't make any changes in any config or install any software, i can't see what the problem is. :( I also tried looking at the config of /etc/X11/xorg.conf on the live cd and compared it to my installed version and there is not much difference. When i ran startx from the terminal i got a few errors. Something like no symbols found. I don't want to reinstall ubuntu becasue i have already had to do it 4 times...don't ask why!:rolleyes: So any ideas? I'll try to post what the error actually said once i find out how to get back to the terminal. crtl+alt+f1 doesn't work...

---

### Post by cb951303 on 2006-01-15
it has something to do with your keyboard layout.
try "nano -w /etc/X11/xorg.conf" in console and then change the keyboard layout to EN
maybe it helps

---

### Post by durand on 2006-01-15
Thanks for the very quick reply:p but unfortunately, it didn't do anything. I have found what the error says. It is not word for word as i had to write it down then type it here.
```
Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":No symbols found
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":No symbols found
The XKEYBOARD keymap compiler (xkbcomp) reports:
>Error: Key<META> added to map for multiple modifiers
>Using Mod4, ignoreing Mod1
>Warning: Tyoe "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols.
>Ignoring extra symbols

Errors from xkbcomp are not fatal to the X server.
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Waiting for X server to shutdown.

```

---

### Post by durand on 2006-01-19
it doesn't matter anymore...I fixed it by re-installing ubuntu

---

