---
title: "can t install compiz !!!!!!!"
date: 2009-02-20
forum: Desktop Environments
---

### Post by henness on 2009-02-20
can any one help pleaseeeeeeee!
when i try to install compiz config manager from terminat and synaptic gives me all kind of errors! here s a list maybe someone can tell me what to do:
henness@henness-desktop:~$  sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  compizconfig-settings-manager
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/609kB of archives.
After this operation, 4022kB of additional disk space will be used.
(Reading database ... 114509 files and directories currently installed.)
Unpacking compizconfig-settings-manager (from .../compizconfig-settings-manager_0.7.4-0ubuntu2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/compizconfig-settings-manager_0.7.4-0ubuntu2_all.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compizconfig-settings-manager_0.7.4-0ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by taurus on 2009-02-20
Looks like a bad download.  First, clean out your cache from a terminal

Applications -> Accessories -> Terminal
```
sudo apt-get clean
```
and then go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and change to another server.  Then, click Reload and try to install that app again.

---

