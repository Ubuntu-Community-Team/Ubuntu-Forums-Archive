---
title: "need help with frozen desktop"
date: 2008-07-21
forum: Desktop Environments
---

### Post by gway600 on 2008-07-21
Hi --

I'm using Hardy Heron.  Last night I let the update manager install some updates and rebooted the system.  Now, the desktop is frozen.  It goes through the boot process fine, but stalls shortly after it puts up the desktop picture.  No menu bar at the top of the screen, no icons, no ability to right click.  No response from the keyboard, except that I can CTRL+ALT+BACKSPACE into a terminal.

Any help would be greatly appreciated.

---

### Post by smartboyathome on 2008-07-21
Try starting gnome by using control+alt+f1 to get to a terminal, log in, and then type:
```
nano ~/.xinitrc
```
Then add this line to it:
```
exec gnome-session
```
Now push control-x, type y, and push enter. Use
```
sudo /etc/rc.d/gdm stop
```
to stop GDM, control+alt+f7 to switch back to X and kill it if it is up, control+alt+f1 again in case it is already killed, and then use startx to start gnome. If it doesn't load, kill it and see if there are any errors.

---

