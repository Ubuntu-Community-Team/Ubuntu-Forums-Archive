---
title: "Command to modify gnome window movement key?"
date: 2009-05-09
forum: Desktop Environments
---

### Post by fermulator on 2009-05-09
In gnome-window-properties, we can set:

"Movement Key'
 - To move a window, press-and-hold this key then grab the window:
   * Control
   * Alt
   * Super (or "Windows logo")

Is there a way to script this in the command line?

(For an example case, I have a script to launch games in WINE, and some games having the ALT key to move windows can be inhibiting to the game...)

Thanks!

---

### Post by kerry_s on 2009-05-09
that's only for the mouse and you have to hold it to work, unlike the alt+f7.
how could it possibly effect a game in wine, that's most likely set to use windows shortcuts and has no idea its running on linux?

---

### Post by fermulator on 2009-05-09
> **kerry_s said:**
> that's only for the mouse and you have to hold it to work, unlike the alt+f7.
how could it possibly effect a game in wine, that's most likely set to use windows shortcuts and has no idea its running on linux?

Um, I can't really explain the 'internal reasons' why, but it does.

I run wine in "Virtual Desktop" mode (Not fullscreen) so it jives better with my dual screen setup.  That might be a contributing factor.

Example: Warcraft III, I use Alt+G to ping quickly.  If "Alt" is assigned to "window move", it stutters the game for half a second and it's pretty bad during intense moments ;-0

---

### Post by fermulator on 2009-05-16
"bump"

---

### Post by fermulator on 2009-05-27
Perhaps this is a better question:

The "Windows Preferences" dialogue window has to modify SOMETHING to make the change from CTRL/ALT/SUPER.  How can we figure out which file it changes?  (whether it be an actual file, or something in the gconf editor)

---

### Post by PizzAp on 2010-06-21
In case the google leads anyone else to this thread...

The window movement key can be changed with gconftool-2:

```
gconftool-2 -s --type string /apps/metacity/general/mouse_button_modifier "<Meta>"
```

However with gnome 2.30 the setting is not activated after login. I guess the is another bug in the control-center regarding keys. You have to restart metacity to make it work:

```
metacity --replace &
```

---

