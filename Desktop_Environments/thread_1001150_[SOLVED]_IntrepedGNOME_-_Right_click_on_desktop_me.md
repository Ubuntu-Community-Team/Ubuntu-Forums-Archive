---
title: "[SOLVED] Intreped/GNOME - Right click on desktop menu disappeared!?"
date: 2008-12-03
forum: Desktop Environments
---

### Post by Rubicon421 on 2008-12-03
My right mouse button works fine everywhere else, but the desktop right click menu quit working. The one with create folder, or file, etc.. 

Is there a setting somewhere that might have changed? Would it have anything to do with using xscript instead of GNOME for logging into the session? I tried both earlier and didn't see any difference, but maybe it changed some setting.

---

### Post by ryanhaigh on 2008-12-03
My suspicion would be that you aren't using nautilus to draw the desktop. Im at work so I can't give precise instructions but if you press Alt+F2 and enter the command gconf-editor, the browse to apps>nautilus there should be an option related to drawing the desktop or root window. That option should be enabled.

---

