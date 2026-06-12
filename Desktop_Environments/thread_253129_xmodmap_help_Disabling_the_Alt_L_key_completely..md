---
title: "xmodmap help: Disabling the Alt_L key completely."
date: 2006-09-07
forum: Desktop Environments
---

### Post by Sak on 2006-09-07
Hey all,

I'm trying to modify my keyboard layout using xmodmap.  Specifically I'm trying to get rid of the Alt_L key.  I'm using an Apple keyboard, and since Control_L and Alt_L are right next to one another I keep inadvertently killing the xserver.  What I'm trying to do is replace the Left Apple (command) key with the Alt_L key.  Here's my .xmodmaprc file so far:

```
remove mod1 = Alt_L
keycode 64 = Meta_L
keycode 115 = Alt_L
add mod1 = Alt_L
```

At this point I've left the Meta_L keycode setting for emacs, but I'm not set on it.  The problem that I'm having is that the left Alt key still functions, even though my output looks like this:

```
sak@demian:~$ xmodmap -pm
xmodmap:  up to 3 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x73),  Alt_L (0x7d),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3
mod4        Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  ISO_Level3_Shift (0x7c)
```

... and...

```
sak@demian:~$ xmodmap -pke | grep Alt
keycode 113 = Alt_R Meta_R
keycode 115 = Alt_L
keycode 125 = NoSymbol Alt_L
```

Keycode 115 is the Apple (command) key on the keyboard, and it works fine as an Alt key with these settings.  But then so does the left Alt key as well.  Any suggestions on how I can completely disable the left Alt key so that the Apple (command) key can take over the responsibility?

---

