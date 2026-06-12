---
title: "XDM Problem"
date: 2005-05-11
forum: Desktop Environments
---

### Post by Ronbo on 2005-05-11
I have just done a minimal stall of Ubuntu, the server install.  I then apt-get xfce4, xserver-xorg, x-window-system-core,xdm and xterm.  After all was installed I typed startx and XFCE4 started right up.  However when I reboot the XDM login screen comes up and after I type in my login and password the screen blanks (like it's trying to start XFCE) and goes right back to the login.  I have tried several time in case I typed my password wrong to no avail.  I can't even get out of the XDM login screen to a terminal.  Anyone have any ideas?  Help would be greatly appreciated.

---

### Post by bcrowell on 2005-05-11
[QUOTE=Ronbo]I have just done a minimal stall of Ubuntu, the server install.  I then apt-get xfce4, xserver-xorg, x-window-system-core,xdm and xterm.  After all was installed I typed startx and XFCE4 started right up.  However when I reboot the XDM login screen comes up and after I type in my login and password the screen blanks (like it's trying to start XFCE) and goes right back to the login.  I have tried several time in case I typed my password wrong to no avail.  I can't even get out of the XDM login screen to a terminal.  Anyone have any ideas?  Help would be greatly appreciated.[/QUOTE]

Control-alt-F6 should get you to a plain-text terminal, and control-alt-F7 should get you back to X. Do you have a .xsession file in your home directory? You could also look at the relevant long files.

---

