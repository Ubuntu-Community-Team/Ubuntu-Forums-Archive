---
title: "Keys broken after uprgrade to 8.10: Right Ctrl, Arrows, Del, Insert, et"
date: 2008-11-23
forum: Desktop Environments
---

### Post by jbuedel on 2008-11-23
After upgrading to 8.10 many of my keys stopped working or invoke different functionality.  I'm assuming my xorg.conf got screwed up somehow but I can't seem to figure it out.

Some specifically broken keys are Right Ctrl (left is fine), Right Alt (now behaving as Enter), arrows (Up behaves as Prnt Scrn, Insert, Delete, Home, End, PgUp, PgDn, and others including all the extra keys (like volume, Mail et).

I am using a usb Microsoft Natural Ergonomic 4000 v1.0 keyboard.  It worked great before upgrading.

Here is the relevant portion of my xorg.conf as I have it now.  I'm pretty sure the keyboard parts are back to the way they were before upgrading

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "screen2" 0 0
    Screen         "screen1" RightOf "screen2"
    Screen	   "AcerScreen2" LeftOf "screen2"
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
 	#Driver			"evdev Managed Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "altwin:meta_win"
EndSection

```

This may be helpful as well.
```

xkb_keymap {
	xkb_keycodes  { include "xfree86+aliases(qwerty)"	};
	xkb_types     { include "complete"	};
	xkb_compat    { include "complete"	};
	xkb_symbols   { include "pc+us"	};
	xkb_geometry  { include "microsoft(natural)"	};
};

```

Thanks for any help.

---

