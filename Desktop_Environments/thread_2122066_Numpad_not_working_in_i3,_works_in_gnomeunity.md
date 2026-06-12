---
title: "Numpad not working in i3, works in gnome/unity?"
date: 2013-03-04
forum: Desktop Environments
---

### Post by bonuswhore on 2013-03-04
Ubuntu 12.04.02 LTS Precise

In i3 window manager, my keyboard number pad stopped working, regardless of if Numlock was toggled or not.  If I login to gnome or unity, it works properly when numlock is on.  


I was using the 'numlockx' tool, run on startup of i3 to toggle numlock on at login time.  This was working properly for some time, then one day it numpad stopped working in i3.   I disabled the numlockx tool and apt-get removed it, but the problem persisted.  I switched to a usb keyboard and it has the same problem


I run i3, with numlockx as well, on 12.04 on other machines and haven't run into this.    I've googled around and a couple possible fixes I've tried that didn't work:

-disable 'Mouse Keys' in Universal Access.    This was already turned off

-Shift+Numlock, Alt+Shift+Numlock, Ctrl+Shift+Numlock - these just toggle the light on keyboard indicating numlock is being toggled, but the numpad still doesn't work

anyone else run into this or know of another fix I can try?



thanks!

---

### Post by bonuswhore on 2013-03-04
I just tried toggling the Mouse Keys / let keyboard control the mouse in Universal Access to 'On' and then 'Off'.   However, I noticed the numpad was still moving the mouse slowly across the screen, with numlock on or off.   I tried togging it back on and back off again in Universal Access, tried rebooting, apt-get removing i3 and re-installing... still not working.


works fine in gnome/unity.   xev shows the keypresses are being triggerred, but the numbers are not working.  In fact the only key that works is the 'Enter' key on the numpad.

---

### Post by bonuswhore on 2013-03-04
Is there any way to remove the Assistive Technologies completely?   I've tried "apt-get remove at-spi2-core"  but this tries to uninstall ubuntu-desktop and that didn't seem like a good idea?

---

### Post by bonuswhore on 2013-03-05
bump, would love to permanently remove or disable this mousekeys feature

---

### Post by bonuswhore on 2013-03-26
:(

---

### Post by bonuswhore on 2013-03-27
fixed with:

[TABLE]
[TR]
[TD="class: answercell"]     You can permanently disable this incredibly annoying keybinding by editing /usr/share/X11/xkb/compat/complete in superuser mode (ie, gksudo gedit /usr/share/X11/xkb/compat/complete) and commenting out **mousekeys** & **accessx(full)**:
  

[/TD]
[/TR]
[/TABLE]
[http://askubuntu.com/questions/8664/how-to-get-numpad-out-of-mouse-emulation-mode](http://askubuntu.com/questions/8664/how-to-get-numpad-out-of-mouse-emulation-mode)

---

