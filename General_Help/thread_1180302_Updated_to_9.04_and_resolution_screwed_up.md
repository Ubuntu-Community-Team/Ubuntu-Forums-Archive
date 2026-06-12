---
title: "Updated to 9.04 and resolution screwed up"
date: 2009-06-06
forum: General Help
---

### Post by duker on 2009-06-06
I just updated to Ubuntu 9.04 today and now when I open a window, the edges of the window (especially the top) are off the page, and there is no sign of the window in the taskbar at the bottom. So I can't move windows around or close them etc.
Any suggestions?
I have tried changing the screen res. but that doesn't work.  Actually, I think I don't even have title bars on the windows.
When I clicked on the desktop icon on the bottom right, I got some message about some error, or no windows manager was running.  Sorry this is vague, but I can't get back to that message, as the current firefox window takes up the entire screen.
thanks

---

### Post by duker on 2009-06-06
After restarting I got the message again when I clicked on the desktop button.  here it is....

Your window manager does not support the show desktop button, or you are not running a window manager.

---

### Post by JCoster on 2009-06-06
Sounds like you have a problem with Compiz.  Try to disable desktop effects and then uninstall your graphics drivers with Synaptic.  

Restart, and then enable Desktop Effects again and it should install new drivers.

If this does not work, then attempt to install proprietary drivers from your graphics vendor's website.

---

### Post by kvarley on 2009-06-06
You may need to use a different graphics driver.

Use EnvyNG if you can to change driver.

---

### Post by duker on 2009-06-07
JCoster, Thanks.
I discoverd that compitz wasn't completely installed, so I installed compitz-gnome which fixed the problem. Later when I changed the visual effects it also updated the drivers.

thanks again for your help!

---

