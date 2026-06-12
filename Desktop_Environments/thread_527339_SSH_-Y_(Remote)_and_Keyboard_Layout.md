---
title: "SSH -Y (Remote) and Keyboard Layout"
date: 2007-08-16
forum: Desktop Environments
---

### Post by superuser2 on 2007-08-16
After fumbling with NX for a day and a half, I've decided to just use SSH -Y to remote control my soon-to-be-headless Ubuntu machine from my Mac with X11 installed. Now, this works almost perfectly, except for the keyboard layout. Text comes out completely jumbled (as in caps lock acts as spacebar), and when I try to change it to "US Macintosh", an error pops up on the display that's actually plugged into the ubuntu machine (screenshot:)

[[IMG]http://img69.imageshack.us/img69/7048/screenshotgnomesettingser2.th.png[/IMG]](http://img69.imageshack.us/my.php?image=screenshotgnomesettingser2.png)

The keylayout never changes.

As per the instructions in the dialog box:

[B]The result of xprop -root | grep XKB
[/B]```
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "us", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "us", "", ""

```

[B]The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

[/B]```

 layouts = [us,us-mac]
 model = 
 options = [grp grp:alts_toggle]
 overrideSettings = true

```

Please help! I can't behead my server until I can type on it...

I'm open to another remote access solution but VNC is too slow. If someone can help me get NX working that's good too but I think SSH -Y will be the easiest. I don't want to use SSH -X because I want my desktop, not just one app. Running gnome-session from there ignores my themeing and preferences and stuff and also isn't what I want.

This is Mac OS 10.4 controlling Ubuntu 7.04

---

### Post by superuser2 on 2007-08-19
^^bump

It works in Xfce and KDE, is there any way to make it work in GNOME?

---

