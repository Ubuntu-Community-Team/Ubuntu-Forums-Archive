---
title: "XFCE -&gt; keyboard language selector"
date: 2005-02-04
forum: Desktop Environments
---

### Post by Jad on 2005-02-04
Greetings Ubunters
I've just installed XFCE, Any idea how to add a language selector botton, or How to set a shortcut for changing keyboard language ?
I mainly write in English/arabic

Thank you in Advance.

---

### Post by lerio on 2005-02-10
I have the same problem. after i upgraded to hoary (and using xorg) the kayboard layout changed to en-us and now there-s no way to revert back to italian layout.

hope you guys can help

---

### Post by Jad on 2005-02-10
Hope to find a way to add multi language, I use arabic,english and sometimes russian.

---

### Post by cargo on 2005-03-23
So, did anybody find a solution how to have multiple input languages?
I'm permanently getting an error message:
> 
Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of <b>xprop -root | grep XKB</b>
- The result of <b>gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd</b>

bored fighting...  :-|

---

### Post by Jad on 2005-03-23
No
Back to gnome!

---

### Post by istoyanov on 2005-03-24
I use multiple input languages under Xfce4 by appropriately modifying /etc/X11/XF86Config-4.

Or you may take a look at [http://xfce-goodies.berlios.de/](http://xfce-goodies.berlios.de/) and search for xfce4-xkb-plugin.

Cheers!

---

### Post by Jad on 2005-03-24
already installed but I cant find it, and I cant find out how to add Arabic language input.

---

### Post by majed on 2006-06-18
Check this out.. hope it works for you :)

[http://ubuntuforums.org/showthread.php?t=82213](http://ubuntuforums.org/showthread.php?t=82213)

Majed

---

