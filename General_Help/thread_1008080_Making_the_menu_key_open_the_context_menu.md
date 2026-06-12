---
title: "Making the menu key open the context menu"
date: 2008-12-11
forum: General Help
---

### Post by dirkhaim on 2008-12-11
How can I make the menu key on my keyboard open the context menu for the current window (like in Windows). I think it was working like this in 8.04, but since I installed 8.10, it stopped working.

Any idea?

Thanks

---

### Post by eBoxNet on 2008-12-11
try : 
System->Preference->Keyboard Shortcut-->

---

### Post by dirkhaim on 2008-12-11
Already tried that, couldn't find it there

---

### Post by prshah on 2008-12-11
> **dirkhaim said:**
> How can I make the menu key on my keyboard open the context menu for the current window (like in Windows)

I assume you mean the panel menu and not the context menu (right click menu). In this case, System-Preferences-Keyboard Shortcuts-Desktop-"Show the Panel Menu"

---

### Post by dirkhaim on 2008-12-11
Nope. I mean the context menu which is evoked by a right click with the mouse. On Windows you can evoke it using the menu key on the keyboard (which is totally different key that the Windows/Start key carrying the Microsoft logo).

---

### Post by nielz on 2008-12-11
Seems to work "by default" for me in 8.10. I just tried it in ff, gedit and thunderbird.

Perhaps you can try taking a look in: *System->Preferences->Keyboard->Layouts->Other options*? There's a Alt/Win key behavoir option in there. For me it's set to "Default"

---

### Post by prshah on 2008-12-11
> **dirkhaim said:**
> Nope. I mean the context menu which is evoked by a right click with the mouse.

The "regular" context menu key (right of space bar) works fine; there is no need to assign it to a shortcut.

You can also have a context menu popup by pressing [s]Ctrl+F10.[/s]

Does the "context menu" key not work for you on your keyboard?

EDIT: Oops, I mean SHIFT+F10, not CTRL+F10.

---

### Post by dirkhaim on 2008-12-11
Nope, didn't find anything there.

However, I have a new insight to donate:
The menu-key is actually mapped to the Undo command instead of opening the context menu. How weird is that for you?

---

### Post by dirkhaim on 2008-12-11
CTRL+F10 works fine
The dedicated context menu key actually does Undo, which is totally wrong

---

