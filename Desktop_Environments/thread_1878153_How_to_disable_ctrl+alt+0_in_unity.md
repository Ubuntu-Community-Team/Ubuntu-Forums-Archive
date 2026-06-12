---
title: "How to disable ctrl+alt+0 in unity"
date: 2011-11-09
forum: Desktop Environments
---

### Post by bestron on 2011-11-09
I use Blender frequently, and there's a shortcut that sets the camera to current view that's control+alt+numpad0, which is a maximize command in unity.
I tried it when the blender window is maximized and in fullscreen mode but not working.
How can I disable that in unity?

---

### Post by Paddy Landau on 2011-11-09
That key-combination doesn't maximise my windows (I have 11.04 - which version do you have?).

That key-combination will be set somewhere in either your keyboard shortcuts or your Compiz settings. If you can find it, you can reset it.

First look in Keyboard Shortcuts:


[LIST]
[*]Open Keyboard Shortcuts.
[*]Scroll down to Window Management.
[*]Scroll down to Maximise Window.
[*]Look on the right; what key-combination does it have? To disable it, click it and press Backspace. To set it, click it and press the required combination.
[/LIST]

If you didn't find it there, look in CompizConfig Settings Manager. If it is not installed, open Ubuntu Software Centre, search for *ccsm* (Advanced Desktop Effects Settings) and install it.


[LIST]
[*]Open CompizConfig Settings Manager.
[*]Warning: If you fiddle with the settings, you run the risk of disabling your Unity desktop (it can be repaired), so unless you know what you're doing, just follow these instructions.
[*]Select General (on the left) and then General Options (on the right).
[*]Select the Key Bindings tab.
[*]Look for *Maximise Window*.
[*]What key-combination does it have? To disable, click the button on its right and clear Enabled.
[/LIST]

If you didn't find it there, you may have to press Back (on the bottom left) and explore the various other settings until you find it. The settings are vast, so you may have to search a while. Remember that any plug-in not checked will have no effect, so you need look only at those that are checked.

Good luck.

---

### Post by bestron on 2011-11-09
I have Ubuntu 11.10, and I've searched in keyboard shortcuts and in ccsm (including unity plugin and window management), I've also searched in metacity under apps in the gconf editor but couldn't find what I wanted

---

### Post by Paddy Landau on 2011-11-09
I'm sorry; this has me stumped. I do not know any other place where keyboard shortcuts are held.

---

### Post by coffeecat on 2011-11-09
I get the same ctrl+alt+0 = maximise the focused window in my 11.10 installation. A couple of links:

[http://www.webscopia.com/2011/10/unity-basics-and-keyboard-shortcuts-in-ubuntu-11-10-oneiric-ocelot/#Window_Placement-7](http://www.webscopia.com/2011/10/unity-basics-and-keyboard-shortcuts-in-ubuntu-11-10-oneiric-ocelot/#Window_Placement-7)

[http://askubuntu.com/questions/28086/what-are-unitys-keyboard-and-mouse-shortcuts](http://askubuntu.com/questions/28086/what-are-unitys-keyboard-and-mouse-shortcuts)

Scroll down to Windows Placement in the second link. What I can't find is how - indeed if - you can disable this key combination.

Slightly OT - the alt+ctrl+5 shortcut is useful. Press it repeatedly and it will cycle through several windows widths.

---

### Post by cyclam on 2012-01-27
For future Blender users, the setting is in CompizConfig Settings Manager > Window Management > Grid.

Click on the '<Control><Alt>KP0' button and uncheck 'enabled'

---

