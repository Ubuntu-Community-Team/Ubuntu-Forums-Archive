---
title: "Shutdown and restart buttons gone"
date: 2006-09-12
forum: Desktop Environments
---

### Post by aleska on 2006-09-12
Not sure whether I have a problem, or this is expected behavior.  But, I've noticed that the graphical button to logout in gnome, which normally allows you to logout, lock screen, switch user, shutdown restart and hibernate, is missing the shutdown and restart options.  Now it only allows me to logout, lock screen, switch users, or hibernate.
I can shutdown from command line, but curious why they are missing as graphical options.  I do have shared folders (NFS) for this machine mounted on other pcs on my network.  Would that be the reason?
Any insight would be greatly appreciated.

---

### Post by Cable on 2006-09-12
Are you using XGL/Compiz?  It happens if you use that.

---

### Post by aleska on 2006-09-12
Actually I did have Compiz installed.  I uninstalled it though becasue it broke with a recent update for me.Is there a way I can configure or change it back now that compiz is gone?

---

### Post by CapnCook on 2006-09-12
That happened to am also. I had forgotten that I had to edit /etc/gdm/gdm.conf-custom and remove 

0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb
flexible=true

from the file. After I did that everything started working fine again.
Hope that helps.

---

