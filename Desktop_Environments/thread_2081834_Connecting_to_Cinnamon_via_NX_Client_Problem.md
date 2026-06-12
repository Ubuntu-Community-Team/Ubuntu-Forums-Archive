---
title: "Connecting to Cinnamon via NX Client Problem"
date: 2012-11-07
forum: Desktop Environments
---

### Post by twistydoerofthings on 2012-11-07
I hope this is the right section to post this, if not please move it to the proper section.

I have been attempting to get Cinnamon working on my Ubuntu Server (12.04, Kernel 3.5.2-linode45). I can connect and view Unity fine, just don't prefer using it. I have Mate installed and can connect to that just fine. When I connect and execute [FONT=Courier New]gnome-session-cinnamon2d[/FONT], I get a an error sometimes and no icons or toolbars.

The error I see is:

Error activiating XKB configuration.

Here are the results from the suggested commands:
[FONT=Courier New]
root@TuckVPS:~# xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xfree86", "pc102", "en_US", "", ""
_XKB_RULES_NAMES(STRING) = "xfree86", "pc102", "en_US", "", ""

root@TuckVPS:~# gsettings get org.gnome.libgnomekbd.keyboard model
''
root@TuckVPS:~# gsettings get org.gnome.libgnomekbd.keyboard layouts
['aa']
root@TuckVPS:~# gsettings get org.gnome.libgnomekbd.keyboard options
@as [][/FONT]

Here is some extra details:

[FONT=Courier New]root@TuckVPS:/# setxkbmap -query
rules:      xfree86
model:      pc102
layout:     en_US
root@TuckVPS:/# setxkbmap -print
xkb_keymap {
    xkb_keycodes  { include "xfree86+aliases(qwerty)"    };
    xkb_types     { include "complete"    };
    xkb_compat    { include "complete"    };
    xkb_symbols   { include "pc+latin"    };
    xkb_geometry  { include "pc(pc102)"    };
};[/FONT]

Been banging away at everything I can find to correct it, yet I seem to not find much current information. I have added the following to my xorg.conf:

[FONT=Courier New]Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option  "XkbRules"      "xfree86"
        Option  "XkbModel"      "pc102"
        Option  "XkbLayout"     "en_US"
EndSection
[/FONT]
Any help or insight would be great. Thanks!

---

