---
title: "Can't change keyboard layouts in DWM window manager"
date: 2022-02-06
forum: Desktop Environments
---

### Post by undefinednone on 2022-02-06
[SIZE=3]**What I did:**[/SIZE]
I installed DWM from and wanted to add a German keyboard layout to the default US one so that I could switch between the two.

To do this I ran this command:

```
localectl --no-convert set-x11-keymap us,de pc105 , grp:win_space_toggle,compose:ralt
```

As I read [here]("https://wiki.archlinux.org/title/Xorg/Keyboard_configuration#Using_localectl") in the Arch Wiki you can permanently change the keyboard layout with localectl.
After that I restarted my computer.

[SIZE=3]**The problem:**[/SIZE]
In the lightdm display manager both keyboard layouts worked fine but in DWM I could only use the US keymap.

[SIZE=3]**More information:**[/SIZE]
After the reboot I gathered the following information.

This is the output of ```
setxkbmap -print -verbose 10
``` which only shows the US layout:

```

Setting verbose level to 10
locale is C
Trying to load rules file ./rules/evdev...
Trying to load rules file /usr/share/X11/xkb/rules/evdev...
Success.
Applied rules from evdev:
rules:      evdev
model:      pc105
layout:     us
options:    grp:win_space_toggle,compose:ralt
Trying to build keymap using the following components:
keycodes:   evdev+aliases(qwerty)
types:      complete
compat:     complete
symbols:    pc+us+inet(evdev)+group(win_space_toggle)+compose(ralt)
geometry:   pc(pc105)
xkb_keymap {
        xkb_keycodes  { include "evdev+aliases(qwerty)" };
        xkb_types     { include "complete"      };
        xkb_compat    { include "complete"      };
        xkb_symbols   { include "pc+us+inet(evdev)+group(win_space_toggle)+compose(ralt)"     };
        xkb_geometry  { include "pc(pc105)"     };
};

```

However, the output of ```
localectl
``` showed both layouts:

```

   System Locale: LANG=en_US.UTF-8
       ...
       VC Keymap: n/a
      X11 Layout: us,de
       X11 Model: pc105
     X11 Variant: ,
     X11 Options: grp:win_space_toggle,compose:ralt

```

[B][SIZE=3]How I tried to resolve this:
[/SIZE][/B][SIZE=2]I also manually put these settings in both ```
/etc/default/keyboard
``` and ```
/etc/X11/xorg.conf.d/00-keyboard.conf
``` with the same result.
Finally I also changed the settings in Gnome which I still have installed in the graphical settings editor.

[/SIZE][SIZE=2]It looks like this happens only on Ubuntu since I did the same on Arch Linux and it worked there.

[/SIZE]Could you please help me how I can finally get my keyboard configured how I want it in DWM

---

### Post by GhX6GZMB on 2022-02-06
You need to add/install the keyboard layout first.

---

### Post by undefinednone on 2022-02-07
Thanks for the short answer.
I now installed the necessary language packages with ```
sudo gnome-language-selector
``` and it worked.

---

### Post by undefinednone on 2022-02-09
> **undefinednone said:**
> I now installed the necessary language packages with ```
sudo gnome-language-selector
``` and it worked.

EDIT: this only works on my PC. But on my laptop the problem persists.
Could you tell me how else I could solve this issue?

---

### Post by GhX6GZMB on 2022-02-09
There shouldn't be any difference.

---

