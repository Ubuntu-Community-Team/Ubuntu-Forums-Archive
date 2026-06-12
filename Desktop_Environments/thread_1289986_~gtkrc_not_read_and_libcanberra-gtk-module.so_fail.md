---
title: "~/gtkrc not read? and libcanberra-gtk-module.so failed to load"
date: 2009-10-13
forum: Desktop Environments
---

### Post by OrangeVixen on 2009-10-13
I've been looking through the archives and I can't find a fix for this problem.

(there are actually two problems here).

First, it dosen't sem that my ~/.gtkrc (GTK-1) file in $HOME/.gtkrc is being read. The global /etc/gtk/gtkrc is read, appearently. I tried rename the ~/.gtkrc to ~/.gtkrc.mine but that did not work either. Does anyone know what might the problem be?

Next problem, running any gtk-1 program/application produces the output stderr error message:

Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

Could that be the cause? and yes I read the archives, someone mentioned about creating a symlink in /usr/lib to it in /usr/lib/gtk-2.0/modules but hen I do that every gtk app crashes on startup. Without the symlink I don't get the crash but just the error message.

I'm using Ubuntu 9.04.

---

### Post by VCoolio on 2009-10-13
My file is called ~/.gtkrc-2.0. You could give that a try.

Do you have libcanberra-gtk-module installed? I had a problem once with annoying sound effects when using a different window manager. I uninstalled libcanberra-gtk-module, but that gave me these same error messages, so I reinstalled it and solved the problem otherwise (removed something like  52libcanberra-gtk-module_add-to-gtk-modules in /etc/rc?.d).

---

### Post by OrangeVixen on 2009-10-13
The ~/gtk-2.0 is for GTK 2, not GTK (they're totally different animals) I''m just not sure why $HOME/.gtkrc is not being read while /etc/gtk/gtkrc is read.

I also tried reinstalling the libcanberra-gtk-module packages, but it did not work. I also have another error now whenever I run any GTK app:

Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",


The GTK app still runs, but I''m worried about the warnings.

Anyone have any idea what is causing these GTK warnings?

---

### Post by OrangeVixen on 2009-10-13
Bump: anyone familiar with these two problems?

I've been reading about the second problem all night in the archives but none of the suggestions I've tried work yet.

---

