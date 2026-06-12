---
title: "Enemy Territory after Breezy upgrade"
date: 2005-10-16
forum: Gaming &amp; Leisure
---

### Post by McLoud on 2005-10-16
I did the upgrade to Breezy, now ET stopped seeing the difference between the 5 on main keyboard and the 5 in the numeric keypad (KP_5), no matter how I use numlock (I don't think it would made a difference anyway). I have made sure I used different bindings for both keys, but looks like the keycodes may be messed somehow. This is how the keyboard is configured:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us_intl"
EndSection

This is the output from xev after pressing/releasing KP_5:

KeyPress event, serial 29, synthetic NO, window 0x2c00001,
    root 0x116, subw 0x0, time 20429644, (500,436), root:(503,457),
    state 0x0, keycode 84 (keysym 0xffb5, KP_5), same_screen YES,
    XLookupString gives 1 bytes: (35) "5"
    XmbLookupString gives 1 bytes: (35) "5"
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x2c00001,
    root 0x116, subw 0x0, time 20429726, (500,436), root:(503,457),
    state 0x0, keycode 84 (keysym 0xffb5, KP_5), same_screen YES,
    XLookupString gives 1 bytes: (35) "5"

---

### Post by seethru on 2005-10-16
it's kind of weird that X is even starting with you using the "keyboard" driver since it was changed to "kbd". Try making that change and see if that makes a difference.

Also try setting the layout to just "us"

---

### Post by McLoud on 2005-10-16
kdb didn't worked, but using setxkbmap us worked, thanks :) 
Now, I just need to figure out what to pass to setxkbmap to return to the prior layout, can you help me with that? I tryed passing us_intl to it but it reports an error when loading the keyboard description and didn't worked. setxkbmap -print return this:

mcloud@Sanctuary:~$ setxkbmap -print -v 10
Setting verbose level to 10
locale is C
Applied rules from xorg:
model:      pc104
layout:     us_intl
Trying to build keymap using the following components:
keycodes:   xfree86+aliases(qwerty)
types:      complete
compat:     complete
symbols:    pc(pc104)+us_intl
geometry:   pc(pc104)
xkb_keymap {
        xkb_keycodes  { include "xfree86+aliases(qwerty)"       };
        xkb_types     { include "complete"      };
        xkb_compat    { include "complete"      };
        xkb_symbols   { include "pc(pc104)+us_intl"     };
        xkb_geometry  { include "pc(pc104)"     };
};

I may provide more info if needed, since looks like a but in xorg, I have a very updated hoary system before the upgrade and it worked perfectly :???:

---

### Post by McLoud on 2005-11-03
Well, i got some hardware problems and screwed up my HD, then I did a clean Breezy install, and somehow selected the layout wrong during install. After that, I used the gnome language panel to configure the keyboard, and now it works without needing the workaround. This is how it is reported:

mcloud@Sanctuary:~$ setxkbmap -print -v 10
Setting verbose level to 10
locale is C
Applied rules from xorg:
model:      pc104
layout:     us,us
variant:    ,alt-intl
options:    grp:alts_toggle
Trying to build keymap using the following components:
keycodes:   xfree86+aliases(qwerty)
types:      complete
compat:     complete
symbols:    pc(pc104)+us+us(alt-intl):2+group(alts_toggle)
geometry:   pc(pc104)
xkb_keymap {
        xkb_keycodes  { include "xfree86+aliases(qwerty)"       };
        xkb_types     { include "complete"      };
        xkb_compat    { include "complete"      };
        xkb_symbols   { include "pc(pc104)+us+us(alt-intl):2+group(alts_toggle)};
        xkb_geometry  { include "pc(pc104)"     };
};

To configure that from command line, just use: setxkbmap us alt-intl
Now im reading to try to set that on xorg.conf so it works for all users ;)

---

