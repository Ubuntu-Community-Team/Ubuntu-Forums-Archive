---
title: "Freeing up Memory"
date: 2009-05-25
forum: General Help
---

### Post by MechWarrior001 on 2009-05-25
Which of these programs can I kill and disable from starting up in the first place without ruining my system?

mixer_applet2
update-notifier
multiload-applet-2
fast-user-switch-applet
notification-daemon
nm-applet
xfce-mcs-manager
trashapplet
gconfd-2
gnome-power-manager
evolution-alarm-notify
evolution-exchange-storage
evolution-data-server-2.24
gnome-screensaver
bonobo-activation-server
ssh-agent
dbus-daemon
gvfs-hal-volume-monitor
gvfs-gphoto2-volume-monitor
gvfs-fuse-daemon
gvfsd-trash
gnome-keyring-daemon
gvfsd
dbus-launch
gam_server
sh

---

### Post by Steelmourne on 2009-05-25
Evolution alarm if you don't want notifications of new mail. Most of the others are necessary and don't take up much memory. How much memory do you have? Ubuntu isn't that resource hungry.

---

### Post by kerry_s on 2009-05-26
are you using gnome? i see xfce in there.

you should look in system> preferences> session, there you just uncheck them.

---

### Post by kpkeerthi on 2009-05-26
Yes. Turn them off from System -> Preferences -> Startup applications.

Also look in System -> Admin -> Services. I have bluetooth and CUPS disabled as I have no need for them.

---

### Post by sreekanth555 on 2009-05-26
You must be very careful whiling stopping those.Some of them are really needed to
start up with your system.Please contact your system admin.

---

### Post by MechWarrior001 on 2009-05-26
> **sreekanth555 said:**
> You must be very careful whiling stopping those.Some of them are really needed to
start up with your system.Please contact your system admin.

I am my system admin.

> **Steelmourne said:**
> Evolution alarm if you don't want notifications of new mail. Most of the others are necessary and don't take up much memory. How much memory do you have? Ubuntu isn't that resource hungry.

384MB SDRAM,
AMD Athlon 1.2gHz 462 Socket 
Nvidia 7800 GS AGP_8x 256MB GDDR3

vm.swappiness = 10

> **kerry_s said:**
> are you using gnome? i see xfce in there.

you should look in system> preferences> session, there you just uncheck them.

I am running Ubuntu 8.10 with a Synaptic Installation of Xfce4. I just simply have gnome-panel running because it's configured the way I want it, but I wonder if there's a way to make xfce-panel use the config & layout files for all your icons & applets that gnome-panel has set.

---

### Post by kerry_s on 2009-05-26
i get back to you.

---

### Post by kerry_s on 2009-05-26
sorry had to switch computers so i could look.

for /etc/sysctl.conf use this:

```

vm.overcommit_memory = 1
vm.overcommit_ratio = 95
vm.dirty_ratio = 5
vm.swappiness = 1

```

that will use most of your ram before it uses swap.

> I just simply have gnome-panel running because it's configured the way I want it, but I wonder if there's a way to make xfce-panel use the config & layout files for all your icons & applets that gnome-panel has set.

not sure what you means, you can do icons just like gnome-panel.
for gnome-applets you need " xfce4-xfapplet-plugin " and just add it to the panel and select what gnome applet you want, i'm using the sensors-applet.

once you get rid of that gnome stuff things should drop down.

---

