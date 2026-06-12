---
title: "Shutdown permissions"
date: 2006-09-07
forum: Desktop Environments
---

### Post by Mr_Person on 2006-09-07
I run an ubuntu server that people can VNC into.  One of my users runs XFCE4 as their window manager and one day discovered that he could shutdown the server by just clicking the "shutdown" button from the XFCE logout menu.

I was pretty surprised that worked because no regular users have permission to issue any shutdown commands either from the command line or using GDM.  After some research, I think HAL is to blame.  As far as I can tell, XFCE sends a command to HAL via D-Bus, and it then executes /usr/share/hal/scripts/hal-system-power-shutdown.  Since hald-runner (which I'm assuming is responsible for executing HAL scripts) runs as root, it's able to issue shutdown commands without any problems.

This is a pretty big problem for me.  I can't have just any user issuing shutdown commands on a shared server.  It's also worrying that HAL will execute scripts on behalf of any user as root.  Is there any way to restrict what kinds of things HAL will do for users or at least keep it from running scripts as root?

Thanks!

---

### Post by mssever on 2006-09-07
It sounds to me like you've found a bug. You should probably report it on Launchpad. In the meanwhile, you could break the files that HAL uses to shutdown. I'd do something like:
```
cd /usr/share/hal/scripts
sudo chmod 000 *power* # be sure to write down the original permissions in case you need to restore them
``` Of course, this might break the legitimate graphical shutdown commands; but you can still do ```
sudo reboot
#or
sudo poweroff
``` if you need to.

EDIT: HAL might behave more like sudo than a true root program. In other words, it might only have authority to execute certain comands as root.

---

### Post by Mr_Person on 2006-09-07
The fix you suggested did work.  I went ahead and reported this issue on Launchpad: [http://launchpad.net/bugs/59397](http://launchpad.net/bugs/59397)

Thanks!

---

