---
title: "Booting to Terminal Screen only"
date: 2005-04-21
forum: Desktop Environments
---

### Post by Spud on 2005-04-21
[FONT=Tahoma]I did the update thing online with success, then attempted to install Menu Editor and Azureus. All of a sudden I loose the top and bottom bars on my destop and basically cant do anything. So after rebooting the PC I'm stuck at the DOS looking screen wondering where the ubuntu desktop got to.

Can this Linux noob get back in with a command or something?[/FONT]

---

### Post by dataw0lf on 2005-04-21
Try checking your virtual terminals (Ctrl + Alt + 1 through 7), just in case.  At the command line, you can start X with a 'startx'.

---

### Post by Alexander Kirillov on 2005-04-21
[QUOTE=Spud][FONT=Tahoma]I did the update thing online with success, then attempted to install Menu Editor and Azureus. All of a sudden I loose the top and bottom bars on my destop and basically cant do anything. So after rebooting the PC I'm stuck at the DOS looking screen wondering where the ubuntu desktop got to.

Can this Linux noob get back in with a command or something?[/FONT][/QUOTE]
Assuming you still have gnome running (but no panels), try 
Alt-F2 - it will give you command prompt. Entering there "gnome-terminal' will give you terminal. After this, try running command gnome-panel to see if it gives you back your panel.

---

