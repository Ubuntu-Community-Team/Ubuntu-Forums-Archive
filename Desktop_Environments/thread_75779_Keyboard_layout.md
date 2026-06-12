---
title: "Keyboard layout"
date: 2005-10-14
forum: Desktop Environments
---

### Post by abominable on 2005-10-14
I can't change my keyboard Layout..
I have gone to kcontrol->Regional&Accesability->Keyboard Layout:

Enable Keyboard layouts
Add Greek

Xkb Options:

Enable xkb options
Alt+shift changes group

Apply

I open kwrite, press alt+shift try to write with greek chars, but still writing with latin chars..

What should I do?

---

### Post by Freddy on 2005-10-14
Don't know if this will work (I choose my layout at install) but you could try to make this in admin mode.
```
kdesu kcontrol
```
/// Freddan

---

### Post by toi_li on 2005-10-30
I edited my kdeglobals file manually, so that it uses Alt+Shift instead of the standard Ctrl+Alt+K:

```
~/.kde/share/config/kdeglobals

Switch to Next Keyboard Layout=Alt+Shift_L


```

---

### Post by grinias on 2005-11-02
See the last post of

[http://ubuntuforums.org/showthread.php?t=81240]("http://ubuntuforums.org/showthread.php?t=81240")

Then you can set the layout as you used to do with kde 3.4.2 and previous versions.

---

