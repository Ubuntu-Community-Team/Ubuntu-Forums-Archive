---
title: "Error in removing VirtualBox(and updating ubuntu)"
date: 2009-01-26
forum: General Help
---

### Post by Schok on 2009-01-26
This error came out when i tried to uninstall virtualbox thru the terminal..

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package virtualbox-ose is not installed, so not removed
Package virtualbox-ose-source is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up swapd (0.2-10.1) ...
invoke-rc.d: initscript swapd, action "start" failed.
dpkg: error processing swapd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 swapd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Sometimes a swapd error would happen even when i update. can anyone help?

---

### Post by mb_webguy on 2009-01-26
Try running the following commands in the terminal:
```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by Schok on 2009-01-26
gomez@MAHA617:~$ sudo dpkg --configure -a
[sudo] password for gomez: 
Setting up swapd (0.2-10.1) ...
invoke-rc.d: initscript swapd, action "start" failed.
dpkg: error processing swapd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 swapd


same thing?

---

### Post by Schok on 2009-01-26
Solved..i removed swapd..btw y isnt "solved" under the thread tools anymore?

---

