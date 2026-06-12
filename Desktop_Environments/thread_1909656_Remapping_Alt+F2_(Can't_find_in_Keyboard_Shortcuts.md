---
title: "Remapping Alt+F2 (Can't find in Keyboard Shortcuts)"
date: 2012-01-15
forum: Desktop Environments
---

### Post by Lemons on 2012-01-15
Hello everyone.

My problem starts with running a game in wine. That works perfectly, minus the fact I need to use Alt+F1-F8 a bit. I remapped all the I could find in the Keyboard window to Alt+Super+F_, but cannot find where to change the Run Command shortcut (Alt+F2). Is this hidden somewhere else? I googled it and it said it should be in there, under Desktop, but I have no Desktop category. Can I change this, or is there another workaround for this?

Running Ubuntu 11.10 64bit, any help would much appreciated!

---

### Post by Krytarik on 2012-01-15
So, since you don't know where to find that setting, but apparently have a working Alt+F2 Run Dialog, you definitely aren't running Gnome Shell. :P

And if you are running one of the default Gnome Fallback sessions, or Unity 2D, you can't change that key-combination, afaik.

But if you are running the regular Unity, or any other session with Compiz (not available by default), install "CompizConfig Settings Manager", if you haven't already, and change both of these settings, though I don't know if the first one is affecting Unity, or if they both are interrelated:

[LIST]
[*]"Gnome Compatibility -> General -> Run Dialog"
[*]"Ubuntu Unity Plugin -> Behaviour -> Key to execute a command"
[/LIST]
Hope that helps.

---

### Post by Lemons on 2012-01-15
Installing the CompizConfig Settings Manager and going to the Ubuntu Unity Plugin settintgs did the trick. Thanks for the help!

---

