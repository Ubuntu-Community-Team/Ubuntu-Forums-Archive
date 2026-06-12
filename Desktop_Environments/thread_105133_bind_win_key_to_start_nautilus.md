---
title: "bind win key to start nautilus"
date: 2005-12-17
forum: Desktop Environments
---

### Post by rdx1968 on 2005-12-17
Hello - Is there anybody who knows how to bind the windows key to start nautilus. I want to start it like Explorer in Windows - when I type win+E
I used Configuration editor to edit keybinding_commands for metacity and now I don't know how to bind the win key ... any ideas ? 10x in advance!

---

### Post by endersshadow on 2005-12-17
You can't do Win (or, as Linux calls it, Super_L or Super_R)+E because Super_X is treated as a unique key and cannot be part of a key combonation.  I've set my Nautilus as Ctrl+Alt+E.

Also, to edit keybindings, go to System>Preferences>Keyboard Shortcuts.  Much easier than via gconf.

---

### Post by aysiu on 2005-12-17
This can be done in KDE. I'm not sure how to do it in Gnome.

---

### Post by endersshadow on 2005-12-17
[QUOTE=aysiu]This can be done in KDE. I'm not sure how to do it in Gnome.[/QUOTE]

It's not possible in Gnome using Metacity (default) or even xfwm4...I've tried :-|

---

### Post by rdx1968 on 2005-12-18
Hmm .. I don't think so. It is possible ...
I can bind right win key, but I want the left one. Right now it's work fine when I hit right win + e. 
I don't know how to map the left win - to be modifier. Here is the output from xmodmap:
xmodmap:  up to 3 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Alt_L (0x7d),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3
mod4        Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  ISO_Level3_Shift (0x7c)

Im using <mod4>e to open nautilus. That's mean Super_L or Hyper_L and e.
I can't understand why it's work with right win key !?!
I tried to get the keycode on the left win and remap it with xmodmap - but unsuccesfully. Here is the output from xev when I type left win.

FocusOut event, serial 29, synthetic NO, window 0x2600001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 29, synthetic NO, window 0x2600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

There is no keycode for the key - why !?! The result from typing the right win:

KeyRelease event, serial 29, synthetic NO, window 0x2600001,
    root 0x115, subw 0x0, time 848194, (666,143), root:(671,216),
    state 0x40, keycode 116 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes:

You can see - it's with keycode 116 , but which one is the code on the left win. Maybe the problem is in my xorg.conf and in my keyboard driver .. maybe not - I don't know. Any ideas - how to get it works with left win and e ?
10x in advance ;)

---

### Post by kosmic on 2005-12-18
Yes it is possible, the win key is called Super_L, and if you go to the Gnome argh registry you can associate this key with nautilus :)
 
 
Also in a terminal use Xev to see the code of the key you want to use.
 
 
EDIT: ups I've only managed to get the left win key to work, never the right one :( sorry

---

