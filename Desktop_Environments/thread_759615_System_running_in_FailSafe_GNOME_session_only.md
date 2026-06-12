---
title: "System running in FailSafe GNOME session only"
date: 2008-04-19
forum: Desktop Environments
---

### Post by toprasad on 2008-04-19
Hi,

I am new to Ubuntu..

I executed some of commands at command prompt..

I forgot the things wht i did. 

After restarting i am not able to logining in to normal mode. only thru failsafe gnome sessoonly..

i checked the xsession error file..

The contents are like this...

*******************************************************************************

(process:5433): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:5437): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Checking for nVidia: not present.
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama

Fatal server error:
no screens found
rm: cannot remove `/tmp/.X1-lock': No such file or directory
xmodmap:  unable to open display ':1'

(x-session-manager:5430): Gtk-WARNING **: cannot open display:

*********************************************************************

Any help, would be helpful.....

---

