---
title: "Ubuntu 8.10. gdm won't start."
date: 2009-02-09
forum: General Help
---

### Post by kthread on 2009-02-09
Hi all.

Maybe this has been asked before, but here goes:

GDM (xserver) won't load. I turn the computer on, and the spinning cursor comes up - and stays there. Nothing happens after that.

If I bring up a command line with ctrl-alt-F2 and run 

dpkg-reconfigure xserver-xorg or
dpkg-reconfigure gdm 

  .. and reboot, that doesn't help. Still the same thing.

Any suggestions?

Thanks in advance for your help.

---

### Post by tzulberti on 2009-02-10
It doesn't seem to be an error of configuration in the xorg file.
Try to watch the Xorg log file (/var/log/Xorg.0.log).

Also, if you change the xorg file there is no need to restart the pc. In the graphic session user Control+Alt+Backspace.
Go to a console, and write: "sudo /etc/init.d/gdm stop"
To start it again, then write: "sudo /etc/init.d/gdm start"

---

