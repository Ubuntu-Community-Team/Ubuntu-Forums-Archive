---
title: "XFCE - panel transparency value"
date: 2007-05-06
forum: Desktop Environments
---

### Post by tompot on 2007-05-06
I've found it in xfce documentation:

"Please, note that transparency only works with an X server that supports the Composite extension, like XOrg >= 6.8.0 and the composite extension has been enabled in the configuration file and the window manager supports it (e.g. xfwm4 has to be compiled with --enable-compositor).

By default the panel will be transparent unless the autohide option has been set. When the mouse moves over the panel, the transparency will be temporarily removed.

You can create the file <basedir>/xfce4/transparency if you want to change the transparency value for the panel (or the iconbox). Create the file and add a line with the format panel=<value>, where value is a number between 0 and 100. Setting it to 0 effectively turns transparency off.

For example, a transparency file may look like this:

panel=25
iconbox=0"

But not everything is clear for me in this guide: firstly I don't know what kind of file should it be? I've created txt file but it doesn't work. And secondly should panel and composite function be off when editing or creating this file.

---

### Post by aidanr on 2007-05-06
you can go to the settings manager -> window manager tweaks and enable compositing there, and in the settings manager -> panel, set the transparency

---

### Post by tompot on 2007-05-06
Thanks for an advice. I couldn't find this option for the first time because compositing was turned off.

---

### Post by `GooZ´ on 2008-04-13
> **aidanr said:**
> you can go to the settings manager -> window manager tweaks and enable compositing there, and in the settings manager -> panel, set the transparency
Thanks :)

---

