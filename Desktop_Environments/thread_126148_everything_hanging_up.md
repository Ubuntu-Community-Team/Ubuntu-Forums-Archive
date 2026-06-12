---
title: "everything hanging up"
date: 2006-02-05
forum: Desktop Environments
---

### Post by umbrAtrorum on 2006-02-05
hi!

i just installed ubuntu 5.10 for the second time on my laptop (hp pavilion zd7000), the only things i did manually after the regular installation was to set up the ndiswrapper-drivers for my broadcom-wlan and sudo apt-get installing the nvidia drivers. now, when i try to start the terminal, the window opens without scrollbars and freezes. after shutting it down several times i receive the following error message:

Window with title "Terminal" is not responding. This window belongs to application gnome-terminal (PID=8160, hostname=localhost).

didn't seem too informative to me, so i started the gnome-terminal from a sudo xterm, which delivers new error messages:

(gnome-terminal:8788): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) !=NULL' failed

(gnome-terminal:8788): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) !=NULL' failed

can anyone help?! an almost identical error message shows up when trying to start gdmsetup. i'd be very grateful for advice

jaspeR

---

### Post by umbrAtrorum on 2006-02-06
little addition: I additionally installed the kde environment. the problem only occurs in kde, NOT in gnome. nevertheless the question remains: why can't i maintain both desktop environments? 

jaspeR

---

