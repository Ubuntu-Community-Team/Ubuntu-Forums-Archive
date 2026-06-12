---
title: "Default Desktop"
date: 2006-04-12
forum: Desktop Environments
---

### Post by Geffers on 2006-04-12
I initially installed Kubuntu and using the package manager have also installed Gnome desktop as an alternative.

On my log on screen I have the option to start either K or Gnome but it initially boots up with a K background and when I shut down I see the command that k-display (I think I've got that correct) is shutting down.

How can I alter it to Gnome as default rather than K.

I am hoping this may help with a problem I have with ndis GTK which keeps telling me gnome GTK bindings have failed and to check my Gnome installation.

Geffers

---

### Post by apjone on 2006-04-12
if you login using a different session it should ask you "Do you want to use this session as the defualt seesion!.

---

### Post by aysiu on 2006-04-12
I don't know if this'll fix the splash issue, but you can do ```
sudo gedit /etc/X11/default-display-manager
``` and change /usr/bin/kdm to /usr/sbin/gdm

---

### Post by Ubuntuud on 2006-04-12
EDIT: My post made no sence, sorry.

---

