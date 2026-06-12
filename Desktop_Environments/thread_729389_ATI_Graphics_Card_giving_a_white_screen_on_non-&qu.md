---
title: "ATI Graphics Card giving a white screen on non-&quot;failsafe Gnome&quot; login"
date: 2008-03-19
forum: Desktop Environments
---

### Post by (4M)Stephen on 2008-03-19
here's one for you... my graphics card (x1600 pro) worked fine on gusty a while ago... but now I have the same issue on gusty and hardy... (8.3 driver)

I install the driver as always... using wiki.cchtml.com
I do all that and the aticonfig --initial step and the aticonfig --overlay-type=Xv commands...

when I CTRL + ALT + Backspace, it restarts the xserver, and then my monitor says it's out of frequency... I solved this issue (blind into terminal alt + F2 xterm then command line sudo update-rc.d -f gdm remove then sudo aticonfig --resolution=1280x1024)

NOW when I log in regular gnome I get a white screen... first the normal brown then it turns white, I can see my mouse, but nothing else... then I CTRL + ALT + Backspace back to the login screen and log into the failsafe... this is the only way I can currently use ubuntu... does anyone know what I can do to stop this, tell me anything you want... I'll upload it...

---

### Post by (4M)Stephen on 2008-03-28
I found it easier to write down commands and execute them in a terminal log-in...

when I hear the chime to log in I would ctrl+alt+F2 into a terminal log in...

still this should be fixed... I need to take it to launchpad, but it's an ATI error isn't it?

---

