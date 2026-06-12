---
title: "package management problem"
date: 2006-08-31
forum: Desktop Environments
---

### Post by dark_myself on 2006-08-31
I was updating my Ubuntu when X crashed and I couldn't get it to start again so I ran the following command: 

sudo reboot

When it was back on X had no problems but now no package manager is working. I tried to run dpkg --configure -a but it shows this error:

sudo dpkg --configure -a
dpkg: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory

Please help.

---

### Post by az on 2006-08-31
Try 

sudo dpkg --clear-avail

and the sudo apt-get update...

---

### Post by dark_myself on 2006-08-31
It doesn't work tried it all ready, but I've fixed everything by renaming a status-old file (dated 2 hours before the reboot) into status.

---

