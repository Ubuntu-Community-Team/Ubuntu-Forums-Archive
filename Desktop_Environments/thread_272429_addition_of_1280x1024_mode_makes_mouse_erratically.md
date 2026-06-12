---
title: "addition of 1280x1024 mode makes mouse erratically uncontrollable"
date: 2006-10-06
forum: Desktop Environments
---

### Post by skyemoor on 2006-10-06
I added the following to my xorg.conf file so that I could use a 1280x1024 flat screen monitor with my Latitude C810.  

SubSection "Display"
   Depth 24
   Modes "1280x1024" "1600x1200"
EndSubSection

Now the screen is shrunken (not lower resolution) and the mouse is uncontrollably erratic, making it impossible to select anything.  How can I gain control of my computer again to restore my xorg.conf?  Are there hotkeys to get out of gdm?

---

### Post by drummer on 2006-10-06
Ctrl-Alt-F1 (or any F key 1 - 6) will drop you to a terminal. Then once you've fixed up your stuff, Ctrl-Alt-F7 will get you back to X. You'll need a Ctrl-Alt-Backspace in X to restart it too.

---

