---
title: "Compiz/XGL logs out immediately"
date: 2006-08-09
forum: Desktop Environments
---

### Post by StayPuft on 2006-08-09
As soon as I log into my XGL session, I can see my desktop and then it immediately logs me out. It's been a while since I logged into XGL so I can't really pinpoint an update or dist-upgrade that may have caused the problem. I have included my .xsession-errors log file below. Thanks for any help.

[HTML]/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "bkozan"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/staypuft:/tmp/.ICE-unix/7073

(gnome-panel:7142): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(gnome-panel:7142): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
Failed to load gnome-fs-desktop: Icon not found
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(gnome-panel:7142): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -15 and height 24
gnome-window-decorator: no process killed
compiz.real: No composite extension
CalDAV Eplugin starting up ...

(evolution-2.6:7170): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.6:7170): e-utils-WARNING **: Plugin 'Bogofilter junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'

(evolution-2.6:7170): camel-WARNING **: camel_exception_get_id called with NULL parameter.
LoadPlugin: failed to initialize shared library /usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so [/usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so: undefined symbol: XtCalloc]
LoadPlugin: failed to initialize shared library /usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so [/usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so: undefined symbol: XtCalloc][/HTML]

---

