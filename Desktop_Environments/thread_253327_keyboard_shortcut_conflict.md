---
title: "keyboard shortcut conflict"
date: 2006-09-08
forum: Desktop Environments
---

### Post by mority on 2006-09-08
I am using and loving the gnome-terminal feature to switch tabs with the keyboard shortcut ALT+n (ALT+1 for first tab and so on).

Unfortunately the keyboard shortcut ALT+3 is already taken for "paste cocntent of clipboard" on my system. I don't need this "paste" shortcut but I want to be able to switch to the third tab in my gnome-terminal with ALT+3 so I want to make this shortcut free but don't know how.

I looked at System -> Preferences -> Keyboard Shortcuts but didn't find it there...

This is a small but for me very annoying issue, so I would very much appreciate any help :)

---

### Post by tuxinvader on 2006-09-08
It works fine on my system. I can only suggest you run gconf-editor and search for paste.

You should see a key in /apps/gnome-terminal/keybindings/paste mine is set to "<CTRL> <SHIFT> V". Perhaps yours is "<ALT> 3"?

HTH :confused:

---

### Post by mority on 2006-09-08
> **tuxinvader said:**
> It works fine on my system. I can only suggest you run gconf-editor and search for paste.

You should see a key in /apps/gnome-terminal/keybindings/paste mine is set to "<CTRL> <SHIFT> V". Perhaps yours is "<ALT> 3"?

HTH :confused:

That did the trick!
I have absolutely no idea why but <ALT> 3 really was set to 'paste'. I removed the binding in gconf-editor as you said and it works again as I am used to it.

I never used gconf-editor before so I did not thought of looking there for a solution but if I have a similar problem in the future I will do so.

You helped me a lot, thanks! :)

---

