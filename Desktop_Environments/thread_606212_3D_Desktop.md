---
title: "3D Desktop"
date: 2007-11-07
forum: Desktop Environments
---

### Post by kbless7 on 2007-11-07
So I'm trying to follow the following thread ([http://ubuntuforums.org/showthread.php?t=100169](http://ubuntuforums.org/showthread.php?t=100169)) on how to do the 3d desktop, but I don't know how to enable the repositories and 3D support. Any help is much appreciated.

-Matt

---

### Post by Happy_Man on 2007-11-07
No offense, but that guide is really old and should be moved to the "outdated" section. The Compiz Fusion window manager included with Gutsy should be able to this. All you have to do is install the package 'compizconfig-settings-manager', and then enable the Desktop Cube and Rotate Cube plugins.

---

### Post by kbless7 on 2007-11-07
Ok that works great. New question: I want to be able to go in the cube mode without having my mouse attached to use the middle mouse button. Does anyone know how to program a hotkey like the windows button to do this action?

-Matt

---

### Post by 3rdalbum on 2007-11-07
I believe Compiz by default sets up the cube to use Control-Alt-Leftclick to activate rotate mode too.

---

### Post by Othyz on 2007-11-10
Where do I find or put *'compizconfig-settings-manager'* ? I tried CLI but got bad command message. Looked in apps, places and system, no joy.

...and yes I'm a noob...

---

### Post by kbless7 on 2007-11-10
you open up a terminal and type "sudo apt-get install compizconfig-settings-manager" if i remember correctly

---

### Post by Jose Catre-Vandis on 2007-11-10
Then once installed, you type ccsm at a terminal or go through the menu to:

Menu>System>Preferences>Advanced Desktop Effects Settings

---

### Post by Othyz on 2007-11-10
Got it to that point, but no cool cube effect like [here]("http://www.youtube.com/watch?v=CcnLyYbnV18").  Is there something else I need to add?

---

### Post by Othyz on 2007-11-10
... or rather a setting I'm over looking?

---

### Post by kbless7 on 2007-11-10
you have to click the mouse wheel to get the cube like that. otherwise you do crtl-alt-arrows to navigate the desktops. windows-E also does a pane view of the desktops. be sure to increase the number of desktops in general options

---

### Post by Othyz on 2007-11-10
Thanks! that works... now how do  get it to stay where I put it.  Let's say I want it to stay on the corner looking at 3 sides of the cube.  Is that an option or does it snap to flat when wheel released?

---

