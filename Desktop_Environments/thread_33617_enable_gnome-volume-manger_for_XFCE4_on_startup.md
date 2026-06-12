---
title: "enable gnome-volume-manger for XFCE4 on startup"
date: 2005-05-11
forum: Desktop Environments
---

### Post by mrbass on 2005-05-11
With GNOME installed and XFCE 4.2.1 many wish to have cd and dvds automounted.  Some say to start gnome-volume-manager manually.  Best way is to:

Click **setup | Sessions and Startup | Advanced tab **
and check **Launch Gnome services on startup**
Logout and login again...voila DVDs automount.

---

### Post by harryc on 2005-05-11
In the interest of keeping a 'light' install of XFCE4 here, the next logical question would be; If you enable 'Gnome services on startup', what other services are started beside gnome-volume-manager ?. I took a slightly different approach based on a thread I saw here. I just started gnome-volume-manager from a terminal, then saved the session options on exit. It's been starting on its' own ever since.

---

### Post by mrbass on 2005-05-11
nautilus-cd-burner/mapping-daemon
gnome-pty-helper
gnome-keyring

I believe just those three above....so memory and speed wise it's a non issue.

gnome-vfs-daemon  (I believe this is started if you start gnome-volume-manager manually)

---

