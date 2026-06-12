---
title: "Problems with Terminal"
date: 2010-01-13
forum: Desktop Environments
---

### Post by BelovedAngel on 2010-01-13
When I open Terminal, all I can see is the background of the active program or desktop.
My settings is default, thereby I mean one color.

Can't see anything, no menu, no text or anything...

Why is it like this?

---

### Post by tpjk on 2010-01-13
welcome to the forums.

> When I open Terminal, all I can see is the background of the active program or desktop.
Can't see anything, no menu, no text or anything...

does that mean that the terminal doesn't come up at all when you try to open it? or do you at least get the title bar or something?

> My settings is default, thereby I mean one color.

which settings are you referring to?

---

### Post by Kevbert on 2010-01-13
I'm assuming that you're accessing Applications-Accessories-Terminal. You should get the attached display.
If you don't then it may be worth trying to re-install gnome-terminal via System-Administration-Synaptic Package Manager. Just search for terminal and then select gnome-terminal.

---

### Post by howefield on 2010-01-13
You could also try pressing the Alt + F2 keys to bring up a run box into which type 

```
gconf-editor
``` 

Then navigate to apps > gnome-terminal > profiles > Default and if there isn't a check against "default_show_menubar, put one there.

Next terminal you open should have a menu bar from which you can select Edit > Profile Preferences and alter background/foreground colours to suit.

You could do it in gconf-editor as well, but probably simpler from the menu bar options once you can see them.

---

