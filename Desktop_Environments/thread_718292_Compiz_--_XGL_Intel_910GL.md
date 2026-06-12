---
title: "Compiz -- XGL Intel 910GL"
date: 2008-03-08
forum: Desktop Environments
---

### Post by 3xhacks on 2008-03-08
Having issues with compiz.  Terminal compiz results in 

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2582 (rev 04) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

So i went along and sudo apt-get install xserver-xgl
install goes fine but then i restart X and it freezes after login.  It gets stuck at Orange screen (human background)
so i sudo apt-get remove xserver-xgl and everything goes back to normal
i have an intel 82915G/P/GV/GL/PL/910GL running at 1680x1050 60hz using intel driver
It seems like others have been successful at running compiz on this chip.
Ive also tried to install Aiglx, and it either doesnt work or was not install correctly

thanks

---

