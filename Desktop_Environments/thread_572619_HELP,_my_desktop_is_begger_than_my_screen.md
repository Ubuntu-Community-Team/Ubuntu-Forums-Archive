---
title: "HELP, my desktop is begger than my screen"
date: 2007-10-10
forum: Desktop Environments
---

### Post by freeulster on 2007-10-10
I don't know what happened. I installed the updates for 7.10 and restarted. Now my desktop in too big for my monitor. I don't know how to resize it. The resolution is at 1792x1344. i usually run 1280 but it won't change, it keeps coming back to 1792. HELP, I hate this.

---

### Post by taurus on 2007-10-10
At the GUI login screen, press <Ctrl><Alt>F2 and log in with your user name and password.  Then, edit /etc/X11/xorg.conf and change the resolutions (near the end) back to whatever you want to use.

```
sudo nano -Bw /etc/X11/xorg.conf
```
<Ctrl>o to save and <Ctrl>x to exit.  Then, press <Alt>F7 to get back to GUI login screen.  Now, press <Ctrl><Alt>Backspace to restart X again.

---

