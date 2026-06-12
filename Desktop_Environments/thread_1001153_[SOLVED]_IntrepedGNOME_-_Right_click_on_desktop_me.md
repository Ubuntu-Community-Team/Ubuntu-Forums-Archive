---
title: "[SOLVED] Intreped/GNOME - Right click on desktop menu disappeared!?"
date: 2008-12-03
forum: Desktop Environments
---

### Post by Rubicon421 on 2008-12-03
My right mouse button works fine everywhere else, but the desktop right click menu quit working. The one with create folder, or file, etc.. 

Is there a setting somewhere that might have changed? Would it have anything to do with using xscript instead of GNOME for logging into the session? I tried both earlier and didn't see any difference, but maybe it changed some setting.

---

### Post by Rubicon421 on 2008-12-04
I tried restarting and unplugging the mouse and plugging it back in. And I looked all over for some setting that might have something to do with it. I'm not sure what is going on. Right click works everywhere except in empty spots on the desktop. I have screenlets and avant installed, and right clicking any object from them works fine.

---

### Post by Rubicon421 on 2008-12-04
bump

---

### Post by Rubicon421 on 2008-12-07
More info:

Files/folders saved to desktop are not showing up either.  If I open a file manager and go to the folder for the desktop, the files/folders saved there are actually there but they are not being displayed on the desktop itself.

Also, I have recently started using Avant Window Navigator and Screenlets. Could it be a setting in either of them that is causing this?

---

### Post by Rubicon421 on 2008-12-08
OK, I'm starting to think about reinstalling Ubuntu pretty soon. Does anyone have any ideas of how to fix this? Is there a way to restore settings in the OS without affecting any of the installed programs?

---

### Post by Rubicon421 on 2008-12-08
Well, I don't know what I did but the right click menu is back- but now my screenlets don't work! I logged out of the GNOME session and logged in with the xscript option, then back to GNOME a few times just seeing if there was any difference. Now I have right click menus in both logins but no screenlets in either! The screenlet control settings program is still in the startup and the icon shows up in the panel in both logins but the screenlets them selves won't show up.

---

### Post by Cammy on 2008-12-08
Did you get your files/folders on the desktop to show up?

Sorry, but I've no clue as to what could be going on with the screenlets.

---

### Post by Rubicon421 on 2008-12-08
Sorry, forgot to add that. Yes, the files and folders on the desktop have reappeared. Wish I new why or what made them go away in the first place. Now if I can only get the screenlets back.

---

### Post by Benismyhorse on 2008-12-09
When my Gnome screwed up before I was told to go to terminal and enter:
rm -r /home/USER/.gconf
this will reset ALL your gnome settings e.g. Desktop, Panel, Theme to the Ubuntu defaults but I think this should work in your case.

---

### Post by Benismyhorse on 2008-12-09
I know from locking down ubuntu that the reason you lost right click/Desktop Icons was because there is an option in gconf-editor that disables the nautilus desktop.

---

