---
title: "CUPS will not load at startup"
date: 2005-11-30
forum: Desktop Environments
---

### Post by chrisndebb on 2005-11-30
When I startup or restart, CUPS will not load. But if I go to Synaptic and uninstall cupsys and reinstall it, I'm then able to print. But before I do this when I go to Administration>Printing, I get the error "The CUPS server could not be contacted."
I notice when I startup or restart (Ubuntu 5.10) I don't notice the "CUPS" module loading up.   Any suggestions?
Chris

---

### Post by Xian on 2005-11-30
Try making sure it is in the default runlevel:

$ sudo update-rc.d cupsys default

Or, you can install bum and have a nice GUI to manage that daemon.

$ sudo apt-get install bum
$ sudo bum

---

### Post by chrisndebb on 2005-12-01
Tried your first suggestion and still won't work at startup and bum is not available with apt-get. Thanks anyway.    Chris

---

