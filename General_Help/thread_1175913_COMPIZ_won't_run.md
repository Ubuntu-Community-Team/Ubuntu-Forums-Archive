---
title: "COMPIZ won't run"
date: 2009-06-01
forum: General Help
---

### Post by FFGANDALF on 2009-06-01
I noticed my desktop effects didn't work after updating to 9.04, after trying various things(reinstalling the nvidia drivers, reinstalling compiz,etc.) I tried running compiz from a terminal and get the following output:

         Checking for Xgl: not present. 
         xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
         Detected PCI ID for VGA: 
         Checking for texture_from_pixmap: not present. 
         Trying again with indirect rendering:
         Checking for texture_from_pixmap: not present. 
         aborting and using fallback: xterm 
         no xterm found, exiting

this is when I use sudo compiz,
when I try just compiz I get:

         xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
         Detected PCI ID for VGA: 
         Checking for texture_from_pixmap: not present. 
         Trying again with indirect rendering:
         Checking for texture_from_pixmap: not present. 
         aborting and using fallback: /usr/bin/metacity


and then compiz hangs, after I use crtl+z to stop compiz I can no longer access menus, or click on currently open windows, the only thing that continues to function is the pointer.

---

