---
title: "Gnome-session error while loaded shared libraries ace"
date: 2007-05-28
forum: Desktop Environments
---

### Post by quinuclidine on 2007-05-28
Hi, i have this problem: when, in my ubuntu, i start gnome at login (gdm is ok) i receive this error:

gnome-session: error while loading shared libraries: ace: cannot open shared object file: No such file or directory, i can't enter by gnome or gnome failsafe...

i have installed libace library, but the error remains

now i have changed my desktop in xubuntu and i have the same error with application like gedit or evolution... 

but i would return to gnome, please give me some helps
thanks

quinuclidine

---

### Post by quinuclidine on 2007-05-30
to a better explain of my problem i copy here my .Xsession-errors file:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "nko"
/etc/gdm/Xsession: Beginning session setup...
<stdin>:0: warning: Unknown encoding: it_IT.UTF-8@euro
    Setting IM through im-switch for locale=it_IT.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/startxfce4: X server already running on display :0
** Message: This build doesn't include support for XF86Misc extension
** Message: Querying Xkb extension
** Message: Xkb extension found
[...]
** Message: Querying Xkb extension
** Message: Xkb extension found

** (xfce4-session:9816): WARNING **: 
[...]
gnome-volume-manager: error while loading shared libraries: ace: cannot open shared object file: No such file or directory
update-notifier: error while loading shared libraries: ace: cannot open shared object file: No such file or directory
gnome-power-manager: error while loading shared libraries: ace: cannot open shared object file: No such file or directory
modinfo: could not open /lib/modules/2.6.20-15-generic/volatile/nvidia_legacy.ko: No such file or directory
modinfo: could not open /lib/modules/2.6.20-15-generic/volatile/nvidia.ko: No such file or directory
modinfo: could not open /lib/modules/2.6.20-15-generic/volatile/nvidia.ko: No such file or directory
xscreensaver: 14:21:23: 0: unrecognised ClientMessage "_NET_ACTIVE_WINDOW" received
xscreensaver: 14:21:23: 0: for window 0x1a00003 (mousepad / Mousepad)
LoadPlugin: failed to initialize shared library /usr/lib/totem/libtotem-basic-plugin.so [ace: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /usr/lib/totem/libtotem-gmp-plugin.so [ace: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /usr/lib/totem/libtotem-mully-plugin.so [ace: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /usr/lib/totem/libtotem-narrowspace-plugin.so [ace: cannot open shared object file: No such file or directory]
xscreensaver: 14:23:09: 0: unrecognised ClientMessage "_NET_ACTIVE_WINDOW" received
xscreensaver: 14:23:09: 0: for window 0x1000003 (Thunar / Thunar)
xscreensaver: 14:23:25: 0: unrecognised ClientMessage "_NET_ACTIVE_WINDOW" received
xscreensaver: 14:23:25: 0: for window 0x1000003 (Thunar / Thunar)

please help me... i must restore my ubuntu gnome desktop!!!

---

