---
title: "Keybinding Super+Backspace to be Delete ...Bare install + OpenBox + LXDE"
date: 2023-03-26
forum: Desktop Environments
---

### Post by jamesbrown2 on 2023-03-26
We have a Chromebook that only has a **backspace** key, no **delete**  key.  I would like to tweak it to where either ALT+Backspace,  CTRL+Backspace, or Super+Backspace would **delete**.  I have spent quite a  bit of time configuring config/openbox/lxde-rc.xml to get other things  working, such as Brightness+/-, Volume +/-, Mute, and so forth.  I  imagine there is a way to do so using that config file, but the  documentation does not mention (that I can find) Actions being a "key"  or something like DELETE.  ( [http://openbox.org/wiki/Help:Bindings](http://openbox.org/wiki/Help:Bindings) ).  Perhaps it is more for executing actions than replicating keystrokes....  What should I do?

---

### Post by Holger_Gehrke on 2023-03-26
There is a nice [tutorial on remapping key]("https://ubuntuforums.org/showthread.php?t=2416537") by DuckHook in the tutorial section of this forum. He remaps the insert key to become compose, but this could easily be adapted to the mapping you want to do.

Holger

---

### Post by jamesbrown2 on 2023-03-26
Holger, I do not see his example offering pressing two keys to equal one key.  Plus, the only way I can do this is if I use Compose?  Surely there is a way to make my Super (Super_L, keycode 133) + Backspace (BackSpace, keycode 22) = Delete using the openbox config or some xorg (xmodmap?) setting?

---

### Post by Holger_Gehrke on 2023-03-27
You can give more than one key symbol per key code like so:
```

xmodmap -e 'keycode 22 = BackSpace Delete BackSpace BackSpace'

```
This should assign Backspace to the key itself, Delete to Shift+Key, Backspace to AltGr+Key, Backspace to Shift+AltGr+Key. Doesn't work though. I think Delete and Backspace are special cases and programs check the various modifiers (Shift,Alt,Super ...) themselves; if I run that command, 'shift+Backspace' produces the same thing as 'shift+Delete', which is a '~'.
If I run "xmodmap -e 'keycode 22 = Delete BackSpace BackSpace BackSpace'", I get Backspace acting as Delete and Backspace with shift acting as Backspace.

The logic in the files in /usr/share/X11/xkb/symbols/ is quite similar, you can assign multiple symbols to the same keycode and the assignment are valid for various modifier keys (Shift, Altgr, Super, Hyper, ... No, the latter two are not made up, there are keyboards with those or you can change the modifier map to have some keys act as those).

'xmodmap' has a rather well written manual ('man xmodmap') which explains all the options this tool has. Sadly the documentation of the keyboard mapping files in /usr/share/X11/xkb is not nearly as easy to find.

Holger

---

### Post by jamesbrown2 on 2023-03-27
> **Holger_Gehrke said:**
> You can give more than one key symbol per key code like so:
```

xmodmap -e 'keycode 22 = BackSpace Delete BackSpace BackSpace'

```
...Doesn't work though...That is why I was asking for help:)

---

