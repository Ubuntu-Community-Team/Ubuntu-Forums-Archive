---
title: "ubuntu server 7.10 GUI problem"
date: 2007-11-01
forum: Desktop Environments
---

### Post by sp00kii on 2007-11-01
Hi,

i installed ubuntu 7.10 server and i installed with apt-get xinit, but unfortunately fails to start.
i have also tried installing kde with sudo apt-get install ubuntu-desktop.

When i type in startx i get the following error:

xauth: creating new authority file /home/username/.serverauth.4064
xauth: /home/username.Xauthority not writable, changes will be ignored
xauth: error in locking authority file /home/username/.Xauthority
xauth: error in locking authority file /home/username/.Xauthority
xauth: error in locking authority file /home/username/.Xauthority

X: cannot stat /etc/X11/X (no such file or directory) aborting giving up.
xinit: connection refused (errno 111): unable to connect to X server

Now, when i type the command xinit it says:
X: cannot stat /etc/X11/X (no such file or directory) aborting, server error.

How can i install kde or gnome?

Any ideas about those error messages?

thanks in advance.

---

### Post by kerry_s on 2007-11-01
you need to install X before you install a DE or WM.
**sudo apt-get install xorg**

---

