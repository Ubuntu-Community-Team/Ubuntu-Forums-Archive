---
title: "Command to change number of Virtual Desktops?"
date: 2012-07-26
forum: Desktop Environments
---

### Post by mikeym on 2012-07-26
Hi,

I'm just wondering if anyone has a command to change the number of virtual desktops under LXDE (with openbox)?

I would like to set up a pair of keyboard shortcuts to add and remove desktops. 2 is normally enough, but sometimes launching something like gimp which really needs one on its own, it would be nice to add some extras.

---

### Post by TheFu on 2012-07-26
Most people setup the largest number of virtual desktops they want and ignore the extras.  I suspect that changing the number requires a restart of X-session which will kill all your currently running X/Windows programs - anything in a window.  

I found the Openbox Configuration Manager has a place to specify the number of virtual desktops.  "ObConf" is the program. It appears you can run with different config files to be used.  Mine for LXDE are in ~/.config/openbox/lxde-rc.xml.  Basically, I'd make one that I like, copy it to a new filename, then use the GUI to make the changes that I like for more desktops, save and make a copy of that too.  Now just pass in **obconf** the conf file to be used by your script.

'man obconf'  to learn more.

Please mark this thread as [solved] when done.

---

