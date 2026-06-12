---
title: "xmms Unable to locate loadable module in module_path: &quot;liblighthouseblue.so&quot;"
date: 2006-03-01
forum: Desktop Environments
---

### Post by markymarknz on 2006-03-01
Hi everyone,

I'm not sure what went wrong, I had everything running smoothly and well then I just logged in and tried to start xmms and get the following message:

mark@mark:/etc$ xmms

Gtk-WARNING **: Unable to locate loadable module in module_path: "liblighthouseblue.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "liblighthouseblue.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "liblighthouseblue.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "liblighthouseblue.so",
Segmentation fault

Anyone have any ideas??
I checked and I have that module on my computer at :
/usr/lib/gtk-2.0/2.4.0/engines/liblighthouseblue.so

I'm kinda stumped.

Any help would really be appreciated :)

---

### Post by devaneador on 2007-01-05
Hi, i'm using Xdialog, and it says the same.
I checked too and I have that module on my computer at :
/usr/lib/gtk-2.0/2.4.0/engines/liblighthouseblue.so

---

### Post by Oreo on 2007-01-26
Me too!
Someone please answer!

EDIT: This may have solved my problem: Search in Synaptic for "lighthouse" and install/reinstall both files.
Oreo

---

