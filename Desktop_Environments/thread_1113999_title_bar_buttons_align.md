---
title: "title bar buttons align"
date: 2009-04-02
forum: Desktop Environments
---

### Post by ramsesdm on 2009-04-02
Hi, some days ago I installed the Mac4Lin theme running an script, it put my title bar buttons (close, maximize, minimize) on the left corner of the window. Yesterday I uninstalled the theme and my buttons are still on the left side and I wanna them in the right corner. How can I change my buttons align?

---

### Post by Giblet5 on 2009-04-02
Mac4Lin left artifacts, eh...

You have tried choosing a different theme via
System/Preferences/Appearance
right?

---

### Post by ramsesdm on 2009-04-02
> **Giblet5 said:**
> Mac4Lin left artifacts, eh...

You have tried choosing a different theme via
System/Preferences/Appearance
right?

Yes and no changes

---

### Post by Giblet5 on 2009-04-02
You can try poking around in metacity's (gnome window manager/decorator) configuration with gconf-editor, but I see nothing that controls the button positions.

You can always install Emerald if you're using Compiz-fusion. Emerald lets you load themes or visually edit them...

You should also contact the Mac4Lin author and tell them about this, as I'm sure they would want to know. They'll also be the best person to help fix it.

---

### Post by zhocchao on 2009-04-02
the key in gconf is:

/apps/metacity/general/button_layout

As i have no window buttons i can't tell you how to arrange it, but ":" is the separator left/right i think

---

### Post by Giblet5 on 2009-04-02
Found it.

Bring up gconf-editor.
Go to Apps/metacity/general
You want the "button_layout" to be:
menu:minimize,maximize,close

The effect is instantaneous.

---

### Post by ramsesdm on 2009-04-02
> **Giblet5 said:**
> Found it.

Bring up gconf-editor.
Go to Apps/metacity/general
You want the "button_layout" to be:
menu:minimize,maximize,close

The effect is instantaneous.

it works!!!!! thanks

---

### Post by JoaoMachado on 2010-03-09
Uh....THANK YOU 
This was driving me nuts!

:D

---

