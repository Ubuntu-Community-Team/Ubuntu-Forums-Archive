---
title: "Evolution doesn't work"
date: 2007-10-21
forum: Desktop Environments
---

### Post by hanzotutu on 2007-10-21
Suddenly, Evolution in my Ubuntu 7.04 doesn't work. I tried to launch it from command line, I got some segmentation fault.

$ evolution

(evolution-2.10:6773): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(evolution-2.10:6773): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(evolution-2.10:6773): e-data-server-CRITICAL **: e_source_group_peek_base_uri: assertion `E_IS_SOURCE_GROUP (group)' failed
Segmentation fault (core dumped)


Any idea how to fix it? Thanks.

---

### Post by frecon on 2007-10-24
I have the same problem. I installed 7.10 gutsty gibbon but it didn't work properly so I did a clean install of 7.04 instead. I have a separate partition with /home in it. My output is slightly different:

(evolution-2.10:21296): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(evolution-2.10:21296): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(evolution-2.10:21296): e-data-server-CRITICAL **: e_source_group_peek_base_uri: assertion `E_IS_SOURCE_GROUP (group)' failed

Any ideas?

---

### Post by stueyboy on 2007-10-24
I did exactly the same as frecon and have exactly the same errors. Something to do with installing evolution on 7.10 then reverting back to 7.04? I also have a seperate home partition with my mail files on it etc.

---

### Post by stueyboy on 2007-10-24
Just a quick update, I found this thread

[http://ubuntuforums.org/showthread.php?t=547465](http://ubuntuforums.org/showthread.php?t=547465)

I'm off to try it and will report back ASAP

---

### Post by stueyboy on 2007-10-24
OK following the above thread has worked. I had to make a backup of my .evolution folder then delete the original as well as deleting the .gconf/apps/evolution folder. I then had to set up my profile in evolution and import the files I needed from my backup folder

Hope that helps

---

