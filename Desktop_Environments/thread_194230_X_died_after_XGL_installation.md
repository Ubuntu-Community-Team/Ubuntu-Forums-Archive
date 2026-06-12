---
title: "X died after XGL installation"
date: 2006-06-11
forum: Desktop Environments
---

### Post by fargoth on 2006-06-11
i followed this post:
[http://www.ubuntuforums.org/showthread.php?t=131267&highlight=compiz](http://www.ubuntuforums.org/showthread.php?t=131267&highlight=compiz)

(done everything except booting before writing xmodmap... thoughy ctrl-alt-bckspc is enough... oh and didn't do the ```
nvidia-kernel-common
``` i use the latest linux-i686 kernel).

now i reboot, and get the blue screen:
could'nt load RGB_DB 'usr/share/X11/rgb'
and the ususal stuff that shows when X is misconfigured....

ive restored a backup of xorg.conf - didn't change anything
iv'e tried ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
that didn't work either....

any ideas?

---

### Post by fargoth on 2006-06-11
heh, me and my stupied mistakes.... the card was set to "nv" - changed it to "nvidia" and now its all fine....

---

