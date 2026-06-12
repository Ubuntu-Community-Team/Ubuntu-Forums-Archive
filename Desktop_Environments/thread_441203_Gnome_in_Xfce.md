---
title: "Gnome in Xfce"
date: 2007-05-12
forum: Desktop Environments
---

### Post by h0bbe on 2007-05-12
There is a couple of Gnome applications and libraries installed i Xubuntu as default. Is there a  point in removing them to get a faster system?

Is there a good way to tell a gnome-app from a gtk-app?

/ h0bbe

---

### Post by aysiu on 2007-05-12
If you want your system to run faster, remove any extra services. An application being installed (but not in use) won't slow down your system. Are you running any Gnome-related services (gnome-settings-daemon, gnome-keyring-manager, etc.)?

---

### Post by h0bbe on 2007-05-12
gnome-volume-manager is the only gnome-related in my taskmanager (or atleast the only task with gnome in the name) can you change that to something else?

How about libraries? When installing from synaptic sometimes the application I'm installing needs a gnome library. Will that drain my system too?

Thanks for your answers aysiu :-)

---

### Post by aysiu on 2007-05-12
Xfce has its own volume manager: *thunar-volman-plugin*

I'd use that instead.

I'm no library expert, but I'd say the more libraries you load with a program, the slower it'll be. If you install an application but don't run it, I don't see the harm.

---

### Post by h0bbe on 2007-05-14
I've now installed *thunar-volman-plugin*, but how do I change to it from *gnome-volume-manager*?

---

### Post by aysiu on 2007-05-14
Well, you can uninstall *gnome-volume-manager* and then configure the Thunar volume manager in the Thunar preferences.

---

