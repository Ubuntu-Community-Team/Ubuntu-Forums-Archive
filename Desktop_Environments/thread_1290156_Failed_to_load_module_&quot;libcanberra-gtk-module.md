---
title: "Failed to load module &quot;libcanberra-gtk-module.so&quot;"
date: 2009-10-13
forum: Desktop Environments
---

### Post by OrangeVixen on 2009-10-13
I've been having this problem whenever I run any GTK (gtk-1) app:

Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Reading the archives, help, and other posts... reinstalling the canberra packages did not help. I'm wondering if anyone knows of any more recent soltion?

I'm using Ubuntu 9.04.

---

### Post by OrangeVixen on 2009-10-14
Bump, anyone with this problem ever got it fixed?

---

### Post by lebe0024 on 2009-10-23
I am also having this problem and it is annoying.  Any gtk app started from the command line produces this error.  I don't have canberra installed, nor do I want it installed.  But something is trying to initialize it.  I removed all my gtk rc files/directories in my home directory, and there's nothing under /etc/gtk*.

---

### Post by lebe0024 on 2009-10-23
SOLVED.  Something along the way set my GTK_MODULES environment variable to include the canberra gtk module.  I simply unset this environment variable.  It was probably some theme I downloaded and installed.  I don't know much about gtk themes.

---

### Post by OrangeVixen on 2009-10-25
Super!!

*Almost* solved, we need a permanent way to unset it.

Where do I unset the environment GTK_MODULE?

The only bashrc is in $HOME/.bashrc, is there somewhere else I should unset this in Ubuntu 9.04?

---

### Post by wd5gnr on 2009-11-27
Have a look in /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules

You can make the file nonreadable (sudo chmod 000 52libcan* ) or edit it to suit.

---

### Post by blueyed on 2011-10-11
You might rather want to uninstall the "libcanberra-gtk-module" package instead (which ships this file according to "dpkg -S X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules").

It's still a workaround though and the real bug is something more like [https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/872172](https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/872172) .

---

