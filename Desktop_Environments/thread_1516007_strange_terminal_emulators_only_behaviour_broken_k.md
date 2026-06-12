---
title: "strange terminal emulators *only* behaviour: broken key-map?"
date: 2010-06-23
forum: Desktop Environments
---

### Post by badtux2010 on 2010-06-23
hi,

 strangely it seems that *only* my gnome-terminal/xterm stopped to correctly map my keyboard (pc105). Other applications (gedit, openoffice,...) still work correctly.
For example, if I type shift+3, I should get the "£" character but I get "#"+return and "èéàç" keys are no longer working, printing out empty spaces. Same behavior in xterm or other terminals...
I also tried the "fr" layout with the same result: "£" is mapped to "#"+return.

How could I debug the problem? Any suggestion or useful pointers?

_details_
- I'm running ubuntu 8.04.4 LTS
- gnome v.2.22.3
- gnome-terminal 2.22.1
- "locale" output[1]
- "setxkbmap it -print" output[2]


Thank you in advance,
 Simone

[1]
> LANG=it_IT.UTF-8
LC_CTYPE="it_IT.UTF-8"
LC_NUMERIC="it_IT.UTF-8"
LC_TIME="it_IT.UTF-8"
LC_COLLATE="it_IT.UTF-8"
LC_MONETARY="it_IT.UTF-8"
LC_MESSAGES="it_IT.UTF-8"
LC_PAPER="it_IT.UTF-8"
LC_NAME="it_IT.UTF-8"
LC_ADDRESS="it_IT.UTF-8"
LC_TELEPHONE="it_IT.UTF-8"
LC_MEASUREMENT="it_IT.UTF-8"
LC_IDENTIFICATION="it_IT.UTF-8"
LC_ALL=
[2]
> xkb_keymap {
    xkb_keycodes  { include "xfree86+aliases(qwerty)"    };
    xkb_types     { include "complete"    };
    xkb_compat    { include "complete"    };
    xkb_symbols   { include "pc+it+level3(ralt_switch)"    };
    xkb_geometry  { include "pc(pc105)"    };
};


---

