---
title: "I buggered my xorg.conf..."
date: 2005-07-23
forum: Desktop Environments
---

### Post by Sachmojo on 2005-07-23
Hey guys, 

Before i explain, let me say that i know i should have backed up the xorg.conf before messing with it, but it was late, i was getting pretty cocky, and i was really wanting to get my ATI drivers working. I also have subsequently learned that using fglrx-config to make a new xorg.conf is unnecessary and unsafe, but what's done is done and i want to avoid reinstallation.

This is the error message i get a soon as  i log in to gnome:

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

The weird thing is that even though i recieve that message, i don't notice any problems while actually using the desktop. I can only assume that XKB refers to my keyboard set-up, but hell, i have no idea how to fix it aside from running fglrx-config again and trying different settings.

Can anyone help me?

Thanks in advance.

---

### Post by Who on 2005-07-23
Well, there are a couple of likely options
you may have success using dexconf, which (and I only read the man page very briefly today to determine I didn't need it) writes xorg.conf based on your debconf settings - which sounds like it may 'reset' xorg.conf. Probably best to read the manual firsst cos I am really rather sketchy on this
The second thing you could try is xorgcfg, which is a graphical tool to help you configure your x server
Finally, failing that, there is the text based xorgconf which ouught to do the trick, but at great length.

Just in case it helps, here is the keyboard stuff from my /etc/X11/xorg.conf file
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Hope that helps

and remember sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_BACKUP :P

Who

---

