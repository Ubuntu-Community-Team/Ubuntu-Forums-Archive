---
title: "can't install a virus scanner!"
date: 2009-08-20
forum: Desktop Environments
---

### Post by trisie on 2009-08-20
I downloaded the avg virus scanner but every I want to install it I got this message: Only one software management tool is allowed to run at the same time

Please close the other application e.g. 'Update Manager','aptitude' or 'Synaptic' first.

has someone an solution for this problem

greetz,


Trisie

---

### Post by coldReactive on 2009-08-20
System > Administration > System Monitor

and tell me what processes are running when you tried to run AVG's installer.

---

### Post by trisie on 2009-08-20
ok her is the list:
bluetooth-applet
bonobo-activation-server
dbus-deamon
evolution-alarm-notify
evolution-data-server-2.22
evolution-exchange-storage
fast-user-switch-applet
firefox
gconfd-2
gconf-helper
gksu
gnome-keyring-daemon
gnome-panal
gnome-power-manager
gnome-screensaver
gnome-settings-daemon
gnome-vfs-daemon
gnome-volume-manager
gvfsd
gvfsd-burn
gvfsd-trash
gvfsd-fuse-daemon
metacity
nautilus
nm-applet
notification-daemon
pulseaudio
python
seahorse-agent
ssh-agent
tracker-applet
trackerd
trashapplet
update-notifier
x-session-manager

that was it

---

### Post by kanikilu on 2009-08-20
That's probably just showing your processes, if synaptic is open, it will not be running under your account - in fact, notice that "gksu" is listed in your list, so I'd bet that's what it is. Just see if synaptic is open, and close it, and try the AVG installer again. If you can't find it and want to kill it manually, go to the System Monitor, go to the View menu and choose "All processes". You should see synaptic listed now, and you can end the process.

---

