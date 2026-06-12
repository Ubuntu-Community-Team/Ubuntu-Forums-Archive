---
title: "Dapper, XGL help please"
date: 2006-09-05
forum: Desktop Environments
---

### Post by Green_Star on 2006-09-05
Hi 

I am running Dapper on AMD64 processor with 32bit version Dapper. I have  	 SAPPHIRE 100143L Radeon X1300PRO 256MB GDDR2 PCI Express x16 Video Card. I am getting following error, any idea?

> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "suma"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/sumkir:/tmp/.ICE-unix/5131
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-1000/socket
This socket already exists indicating esd is already running.
Exiting...
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-1000/socket
This socket already exists indicating esd is already running.
Exiting...
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
compiz: No composite extension

(gnome-panel:5205): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(gnome-panel:5205): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and height 24

Thanks in advance

---

### Post by Green_Star on 2006-09-07
Never mind, it worked after couple hours of research.

---

