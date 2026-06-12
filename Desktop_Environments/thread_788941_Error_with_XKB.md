---
title: "Error with XKB"
date: 2008-05-10
forum: Desktop Environments
---

### Post by kabads on 2008-05-10
Whenever I boot Ubuntu 8.04 I get the following pop-up: 

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

The output from those commands are:
adam@home:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc102", "GB", "UK", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc102", "GB", "UK", ""
adam@home:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [uk]
 model = pc102
 options = [grp	grp:alts_toggle]
 overrideSettings = true

The only noticeable problem with this is that I cannot get to a terminal (without X running) by pressing the usual ctrl-alt-f1 combination. 

Any ideas of a fix?

---

### Post by Motorhead Kaze on 2008-06-27
I have the same error!  But this problem is disabling my Japanese keyboard, which is seriously f-ed up since I use Japanese in my job!

Can someone offer a fix for this?

---

### Post by Motorhead Kaze on 2008-06-27
This is what I just did:

Type this into a terminal
```
 gksudo gedit /etc/X11/xorg.conf

``` to access your xorg.conf and go to the section called, 
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	
EndSection

```
I had all these **Options** right after "driver 'kbd'" and I deleted all of those options. Then I did ctrl+alt+bksp, then went to system/preferences/keyboard and reset my keyboard to the way I want it (Japanese keyboard, 106keys).  Now my keyboard is back to normal.

---

