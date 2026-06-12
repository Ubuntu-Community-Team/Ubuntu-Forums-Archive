---
title: "keyboard indicator"
date: 2006-02-19
forum: Desktop Environments
---

### Post by xinelo on 2006-02-19
Hi, 

The "keyboard indicator" in my Gnome panel does not work. I've added arabic as a new language in the "layout" section, but I can't swap between the two languages. I've tried several options in the Layout Options > Group Shift/Lock Behavior, with no success. I can only use what seems the default one (spanish, in a spanish keyboard).

To sum up, I can't swap between Spanish and Arabic, nor can I type in Arabic by any other means. I don't know whether this problem might be related to an unresolved issue about not being able to use the keys for characters other than 0-9 and a-z (no "at", no "dollar sign", no "ñ", no "ç", etc.). 

I could also be related to my arabic.xkb file... 

The questions are: 
- Does anyone know how to solve this problem? OR
- Does anyone know about another similar program for Linux which works properly (I mean, an alternative to the "keyboard indicator"?

Oh, btw, every time I click on any option of this utility,there appears a message twice which only says "error", on the upper left corner of the screen. 

Thanks a lot. xinelo

---

### Post by xinelo on 2006-02-19
this might be related. I've installed the language pack for arabic through the language selector, so I can have a Gnome interface in arabic. I restart and there it goes. 

however, I get a message window with the following message: 

[COLOR="Blue"]Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd[/COLOR]

this is not new, it happens with any other language, but I thought it could help.

---

