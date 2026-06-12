---
title: "xfce login-crash"
date: 2007-09-15
forum: Desktop Environments
---

### Post by bkf3rreus on 2007-09-15
Xfce wont work anymore..

I was doing stuff in xorg.conf (for other reasons (fixed, i think..)) before and now Xfce crashes immediately on logging in. Logging in to failsafe mode (KDM) and then starting xfce4-session, seems to work fine, and i get to see these error-messages..

:(

```
###@###:~$ xfce4-session
** Message: This build doesn't include support for XF86Misc extension
** Message: Querying Xkb extension
** Message: Xkb extension found
Error:            Can't find file "pc105" for symbols include
                  Exiting
                  Abandoning symbols file "(null)"
[1189887546,000,xklavier_config_xkb.c:xkl_config_get_keyboard/]         
Could not load xkbcomp output as XKM file, got 127 (asked 127)
** Message: Querying Xkb extension
** Message: Xkb extension found
QPainter::setPen: Will be reset by begin()
kbuildsycoca running...
QPainter::setPen: Will be reset by begin()

(xfce4-panel:10997): libxfcegui4-WARNING **: ICE I/O Error

(xfce4-panel:10997): libxfcegui4-WARNING **: Disconnected from session 
manager.

(xfdesktop:10990): libxfcegui4-WARNING **: ICE I/O Error

(xfdesktop:10990): libxfcegui4-WARNING **: Disconnected from session 
manager.
####@####:~$ ICE default IO error handler doing an exit(), pid = 
11000, errno = 0
DCOP aborting (delayed) call from 'anonymous-10998' to 'kwalletmanager'
ERROR: Communication problem with kwalletmanager, it probably crashed.

```

---

### Post by bkf3rreus on 2007-09-16
could anyone tell me which information i need to acquire?

---

### Post by ryno519 on 2007-09-16
Did you make a backup of the configuration file?

---

### Post by bkf3rreus on 2007-09-16
i'm not really sure if this one is older than this problem, i can't remember. it's about a month old..

the old one, the parts i've changed (but i have been running dpkg-reconfigure xserver-xorg)
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection
```

new one
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"dellusbmm"
	Option		"XkbLayout"	"pc105"
	Option		"XkbVariant"	"se"
EndSection
```

---

