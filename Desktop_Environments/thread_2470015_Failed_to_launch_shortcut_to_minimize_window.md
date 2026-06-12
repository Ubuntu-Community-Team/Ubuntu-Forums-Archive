---
title: "Failed to launch shortcut to minimize window"
date: 2021-12-17
forum: Desktop Environments
---

### Post by xadder on 2021-12-17
I'm trying to set up a keyboard shortcut to minimize a window. Using Settings manager I've associated Ctrl+Alt+h to hide_window_tab, but pressing this key combo gives me the error message:

! Failed  to launch shortcut "<Primary><Alt>h"
Failed to execute child process "hide_window_tab" (No such file or directory)

I had earlier tried Super+h, but some reading suggested that the Super key was problematic. Now it seems that any combination is problematic.

I'm using xubuntu 21.10.
Thanks

---

### Post by schragge on 2021-12-17
It's **hide_window_[COLOR=green]key[/COLOR]**, not **hide_window_[COLOR=red]tab[/COLOR]**.
```
[COLOR=green]$[/COLOR] xfconf-query -lvc xfce4-keyboard-shortcuts|grep hide_window[COLOR=green]
/xfwm4/custom/<Alt>F9                      hide_window_key
/xfwm4/default/<Alt>F9                     hide_window_key[/COLOR]
```

---

### Post by xadder on 2021-12-17
Thanks. Actually, when testing this I found another menu that let me associated "Hide window" Ctrl_Alt-h, but just now I can't find this menu. The Settings/keyboard/Applicaton Shortcuts isn't showing my new shortcut (which does work!). There must be two ways to configure such things?

---

### Post by schragge on 2021-12-17
From [XFCE FAQ]("https://docs.xfce.org/faq#is_it_possible_to_change_the_default_shortcut_keys"):
> **Is it possible to change the default shortcut keys?**

Yes, of course. Keyboard shortcuts are defined in two locations. The  shortcuts to handle the window manager are defined in the Settings  Manager > Window Manager Settings > Keyboard. The [FONT=monospace]Default[/FONT] theme can not be changed; but, when you add a theme you can change that the theme you just added.

     More global keyboard shortcuts, like volume adjustments, can be found in  Settings Manager > Keyboard Preferences > Shortcuts. Again, you  need to add a new theme before you can start customizing it.

---

### Post by xadder on 2021-12-19
OK, thanks again. It is a bit confusing with two systems to define shortcuts for hiding windows, but all works now. I'll mark this as solved.

---

