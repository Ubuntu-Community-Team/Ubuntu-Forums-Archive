---
title: "Stop X"
date: 2009-03-31
forum: General Help
---

### Post by RedSingularity on 2009-03-31
Hey guys can someone tell me how to stop the X server?  I have tried a few things but i cant seem to do it.  I am trying to install nvidia drivers.

---

### Post by clone11 on 2009-03-31
sudo /etc/init.d/gdm stop

I'm pretty sure that's the command

Be sure to push CTR+ALT+f1 before you do that.

---

### Post by damis648 on 2009-03-31
I recommend you do not install nVidia drivers from their site, you will have to reinstall on every kernel update. Any particular reason you need the one from the site?
If you want to continue, close all open applications and then switch to the first virtual terminal and enter the following:
```
sudo /etc/init.d/gdm stop
sudo /path/to/installer
```

---

