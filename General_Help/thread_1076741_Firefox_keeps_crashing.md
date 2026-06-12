---
title: "Firefox keeps crashing"
date: 2009-02-21
forum: General Help
---

### Post by Shiloh Hawkesworth on 2009-02-21
My Firefox keeps randomly crashing. Streaming media seems to trigger it, but it's not consistent. For example sometimes Utube crashes it and sometime a site like alltel.com will crash it.

When it crashes it just closes and I have to reopen Firefox and restore session and it works. 

Any ideas how I can fix this?

---

### Post by Shiloh Hawkesworth on 2009-02-21
If I run firefox from the terminal here is what I get:

shiloh@chondro:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
GCJ PLUGIN: thread 0x805e8f8: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x805e8f8: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x805e8f8: NP_GetValue
GCJ PLUGIN: thread 0x805e8f8: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x805e8f8: NP_GetValue return
GCJ PLUGIN: thread 0x805e8f8: NP_GetValue
GCJ PLUGIN: thread 0x805e8f8: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x805e8f8: NP_GetValue return

(firefox:30106): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:30106): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:30106): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

---

### Post by Shiloh Hawkesworth on 2009-02-21
This seem to have solved my own problem:


wget [http://launchpadlibrarian.net/131551...pport_i386.deb](http://launchpadlibrarian.net/131551...pport_i386.deb)
sudo dpkg -i flashplugin-nonfree_9.0.115.0ubuntu6~nolibflashsupport_i386.de b
sudo apt-get remove libflashsupport

---

