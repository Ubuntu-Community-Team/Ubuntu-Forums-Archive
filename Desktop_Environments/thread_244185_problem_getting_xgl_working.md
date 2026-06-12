---
title: "problem getting xgl working"
date: 2006-08-26
forum: Desktop Environments
---

### Post by ntense on 2006-08-26
im sure your all proabably getting sick of answering and troubleshooting xgl/compiz but heres my problem... so i followed this tutorial here:

[https://help.ubuntu.com/community/CompositeManager/Xgl]("https://help.ubuntu.com/community/CompositeManager/Xgl")

pretty much copy and pasted commands. when it came to choosing how xgl starts up i chose method A. 

now when i log out of my current session and try to start the xgl session i get this error: your session only lasted less than 10 seconds... bla bla bla... then the output was this:



```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "n73n53"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/teknolust:/tmp/.ICE-unix/7311
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(gnome-panel:7380): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(gnome-panel:7380): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and height 24

(gnome-panel:7380): Gtk-WARNING **: Cannot load drag icon from icon name gnome-terminal.png

```

then shoots me back to the login screen... 

ive looked all over the boards for answers or possible links to solutions with no avail... if theres something im missing and you can help me that would be great. im running dapper, everything is up to date and i have an nvidia geforce 5500 gfx card... the drivers i have installed for it are the ones that you get from automatix, i dont know if that makes a difference. but any help would be greatly appreciated.

---

### Post by ntense on 2006-08-26
bump

---

