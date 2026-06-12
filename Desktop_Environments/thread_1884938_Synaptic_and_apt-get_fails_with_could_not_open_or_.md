---
title: "Synaptic and apt-get fails with could not open or parse for Maverick"
date: 2011-11-22
forum: Desktop Environments
---

### Post by shumifan50 on 2011-11-22
I run Maverick and was trying to get a new package installed and it fails with 
Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_maverick-updates_universe_binary-i386_Packages (1)
E: The package lists or status file could not be parsed or opened.


Is it no longer supported? or is there something I must do to make it work?

---

### Post by mikewhatever on 2011-11-22
Maverick is supported until the end of April 2012.
I'd say, something is probably wrong with that particular file. Just delete it and then reload the sources.
```
sudo rm /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_maverick-updates_universe_binary-i386_Packages

sudo apt-get update
```

---

### Post by shumifan50 on 2011-11-23
Thanks for that it worked.:D

---

### Post by raja.genupula on 2011-11-23
mark the thread as solved from thread tools

---

