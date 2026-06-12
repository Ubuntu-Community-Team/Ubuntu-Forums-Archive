---
title: "Low disk space warning"
date: 2009-12-06
forum: Desktop Environments
---

### Post by ExtemeOver on 2009-12-06
Ubuntu 9.10
Hello everyone.
I have a small question - there is a notification window, which pop-ups when there is almost no free space on the hdd. This window provides an option not to show the warning for current hdd. Long ago I chose this option to ignore this hdd.
But now I need to enable the warning for this hdd again. How can I do it?
P.S Sorry for my bad english

---

### Post by SecretCode on 2010-01-06
While trying to solve this for myself I came across your post. And this is the solution:

Open **gconf-editor** (type gconf-editor at the command line), and navigate to the key **/apps/gnome_settings_daemon/plugins/housekeeping/**.

Double-click the **ignore paths** name, and remove the paths you want not to ignore any more.

There are some other useful configuration settings here, like free_percent_notify (default 0.05 meaning notify when space is less than 5%) and free_size_gb_no_notify (default 2 meaning don't notify if the free space is more than 2GB).

---

### Post by shafin on 2010-05-09
> **SecretCode said:**
> While trying to solve this for myself I came across your post. And this is the solution:

Open **gconf-editor** (type gconf-editor at the command line), and navigate to the key **/apps/gnome_settings_daemon/plugins/housekeeping/**.

Double-click the **ignore paths** name, and remove the paths you want not to ignore any more.

There are some other useful configuration settings here, like free_percent_notify (default 0.05 meaning notify when space is less than 5%) and free_size_gb_no_notify (default 2 meaning don't notify if the free space is more than 2GB).
Thanks for the tip.

---

### Post by sidewalkcynic on 2010-05-09
open a terminal and type:

sudo apt-get autoremove

It will identify unneeded kernels that have been replaced with later editions.
When prompted let it remove them, and then

sudo apt-get remove

sudo apt-get autoclean

sudo apt-get clean

---

