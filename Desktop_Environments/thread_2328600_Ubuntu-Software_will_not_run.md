---
title: "Ubuntu-Software will not run"
date: 2016-06-22
forum: Desktop Environments
---

### Post by Pen16 on 2016-06-22
I try to run ubuntu software through terminal but I get this error:   (ubuntu-software:5244): Gs-WARNING **: failed to open plugin /usr/lib/gs-plugins-9/libgs_plugin_xdg_app_reviews.so: /usr/lib/gs-plugins-9/libgs_plugin_xdg_app_reviews.so: cannot open shared object file: No such file or directory      Which means I am missing the libgs_plugin_xdg_app_reviews.so which I confirmed by searching. So I looked online for it and found it bundled in a zip, I unbundled and moved in into the right directory but I still get the same error so I thought that maybe it didn't have the right permissions so I tried to chmod it but it said I can't have a dangling something. When listed in terminal it is the only file that shows up red (which I don't know what that means). Can someone point me in the right direction as to how get this file accepted by the application?

---

### Post by howefield on 2016-06-22
Looks like this bug..

[https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573052](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573052)

---

