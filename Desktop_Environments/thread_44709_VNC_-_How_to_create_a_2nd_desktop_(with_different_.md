---
title: "VNC - How to create a 2nd desktop (with different resolution)?"
date: 2005-06-27
forum: Desktop Environments
---

### Post by unzari on 2005-06-27
Can somebody tell me how to create a second desktop with a different screen resolution to be accessed by 'vncviewer'?

I have set up PalmVNC on my Sonly Clié device.  This works great, but the desktop is too large.  I want to have a second one which corresponds to the resolution of the Clié (resolution is 480 x 320).

Many thanks...

---

### Post by crashtest on 2005-06-27
[QUOTE=unzari]Can somebody tell me how to create a second desktop with a different screen resolution to be accessed by 'vncviewer'?

I have set up PalmVNC on my Sonly Clié device.  This works great, but the desktop is too large.  I want to have a second one which corresponds to the resolution of the Clié (resolution is 480 x 320).

Many thanks...[/QUOTE]

Try 'vncserver --geometry 480x320'  Don't expect to see a full gnome or kde desktop unless you specify that in  ~/.vnc/xstartup.  The display that is created will be <hostname>:1 and <hostname>:2 for the next one, and so on. 

This assumes you have already installed vncserver: 'sudo apt-get install vncserver'  The first time you run vncserver, you will be prompted to create a password.  I'm not aware of a way to do want you want using the built-in server System -> Preferences -> Remote Desktop, which shares your desktop:0.  There may well be a way to do it with this...  Anyone?

---

