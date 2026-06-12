---
title: "Adding a keyboard shortcut to Gnome's File Chooser"
date: 2011-02-23
forum: Desktop Environments
---

### Post by ankle on 2011-02-23
I'd like to add a keyboard shortcut to the Gnome File Chooser: "Ctrl-D" to switch to the Desktop folder (as "Apple-D" does in OS X). I haven't found a way to do this, yet. 

Will it require changes to the source code, or is there possibly another way to add this in Gnome?

---

### Post by Copper Bezel on 2011-02-23
Switch to the desktop folder? Do you mean to minimize all windows to show the desktop, or to load a file manager to the desktop folder?

Either way, you'll be setting this in Compiz Config Settings Manager, most likely, unless you're running without desktop effects, in which case you would use Keyboard Shortcuts from the Preferences menu. You don't want to use Ctrl+D for this, because it's used for many applications. I suggest Super+D.

If you want to create a show desktop shortcut through Compiz, you can find it in CCSM under "General Options" in the "Keyboard Shortcuts" tab. If you're not using desktop effects, navigate to Preferences - > Keyboard Shortcuts. Either way, the action is called "Show Desktop." You can just select it and press the key binding you want.

If you want to load the desktop folder in Nautilus, you'll have to create a custom action:

nautilus /home/yourusername/Desktop

and assign it to a key binding, again either in CCSM through the "Commands" plugin or, if you're not using Compiz desktop effects, in Preferences - > Keyboard Shortcuts in the Main Menu.

---

### Post by kidwm on 2011-03-19
But I tried Alt + D, this shortcut is working!

---

### Post by ankle on 2011-04-27
Alt+D works!

---

