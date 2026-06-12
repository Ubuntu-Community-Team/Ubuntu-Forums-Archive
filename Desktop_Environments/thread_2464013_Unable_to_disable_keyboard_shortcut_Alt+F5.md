---
title: "Unable to disable keyboard shortcut Alt+F5"
date: 2021-06-23
forum: Desktop Environments
---

### Post by mberg2007 on 2021-06-23
Hello,

The built in keyboard shortcut Alt+F5 toggles a window into "non-full-screen" mode. It also conflicts with Eclipse which does the same, rather than activate an Eclipse function assigned to that hotkey.

I've been to the Gnome settings panel, in the Keyboard Shortcuts area. Alt+F5 is _not assigned to anything_ and hasn't been assigned to anything for months. I've lived with this for some time but now I'm hoping to get an answer to why Alt+F5 is still being picked up by Gnome/Ubuntu.

Anyone know how I can disable Alt+F5 in Ubuntu/Gnome?

-Michael

$ uname -a
Linux michael-Latitude-5511 5.11.0-18-generic #19-Ubuntu SMP Fri May 7 14:22:03 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 21.04
Release:	21.04
Codename:	hirsute

$ wmctrl -m
Name: GNOME Shell
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF

---

### Post by coffeecat on 2021-06-23
Support, not chat.

*Thread moved to **Desktop Environments**.*

---

### Post by mberg2007 on 2021-06-25
Apologies for posting in the wrong forum - thanks for relocating, @coffeecat :-)

Anyway - to answer my own question, Alt+F5 is apparently a sort of "native binding" that doesn't show up in the keyboard shortcuts settings in the Gnome settings panel. It can't be disabled, except with a command:

[FONT=courier new]$ [/FONT][FONT=var(--ff-mono)][FONT=courier new]gsettings set org.gnome.desktop.wm.keybindings unmaximize "[]"[/FONT]

I used this, and it worked. Alt+F5 can now be used in Eclipse.

And I also learned another reason why Ubuntu will never be successful on the desktop.

[/FONT]

---

### Post by tea for one on 2021-06-25
> **mberg2007 said:**
> And I also learned another reason why Ubuntu will never be successful on the desktop.

Unnecessary jibe.

There is another keyboard shortcut to [COLOR="#0000FF"]unmaximise[/COLOR] a window: Super + Down Arrow.
Did you re-configure that one also?

By the way, have you installed [COLOR="#0000FF"]gnome-tweaks[/COLOR]?
It gives the user access to a plethora of keyboard settings.

---

