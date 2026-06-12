---
title: "Entering Desktop very slowly and program launching slowly"
date: 2007-07-28
forum: Desktop Environments
---

### Post by lzhonsailing on 2007-07-28
Hello.
    After I used Ubuntu Feisty for a little while, I found that when I input the username and passwd and then enter the Desktop, it takes a long time (30s or more) to show the icons on the desktop and the panal. And when I run a program such as opening nautilus to view the file list, it is still very slow. However,  the program is running fast after launching. 
    This is the .xsession-errors below, could you help me find the problem? I am not familiar to the errors reports. Thank you very much!
--------------------------------------

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "xh"
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=zh_CN.
Start IM through /home/xh/.xinput.d/zh_CN linked to /etc/X11/xinit/xinput.d/fcitx.
SESSION_MANAGER=local/xh-ubuntu:/tmp/.ICE-unix/4737

** (gnome-session:4737): WARNING **: Host name lookup failure on localhost.
Initializing gnome-mount extension

** (nautilus:4811): WARNING **: Can not caclulate _NET_NUMBER_OF_DESKTOPS

** (nautilus:4811): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:4811): WARNING **: Can not get _NET_WORKAREA

** (nautilus:4811): WARNING **: Can not determine workarea, guessing at layout
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is not supported by direct rendering context, trying indirect rendering context instead
inotify_add_watch: No such file or directory

** (GNOME Control Center:4937): WARNING **: 
error raised: [libslab_get_gconf_value: error getting /desktop/gnome/applications/main-menu/lock-down/user_modifiable_apps]


(GNOME Control Center:4937): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

** (GNOME Control Center:4937): WARNING **: 
error raised: [load_xbel_store: couldn't load bookmark file [(null)]
]

---

