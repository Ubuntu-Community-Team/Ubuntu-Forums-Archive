---
title: "Error with DockBarX"
date: 2011-06-09
forum: Desktop Environments
---

### Post by antoniu86 on 2011-06-09
Hello,

I just installed dockbarx and had an error. It says that the package is broken. When I start Ubuntu Software Center i get a message that i have to repair the package catalog. When i go to the terminal and execute the "apt-get -f install" i get this error:


antoniu@antoniu-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  dockmanager
The following NEW packages will be installed:
  dockmanager
0 upgraded, 1 newly installed, 0 to remove and 34 not upgraded.
1 not fully installed or removed.
Need to get 0 B/84.6 kB of archives.
After this operation, 434 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 208300 files and directories currently installed.)
Unpacking dockmanager (from .../dockmanager_0.1.0-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/dockmanager_0.1.0-0ubuntu1_i386.deb (--unpack):
 trying to overwrite '/usr/share/dockmanager/data/skype_away.svg', which is also in package faenza-icon-theme 0.9-ubuntu3
Errors were encountered while processing:
 /var/cache/apt/archives/dockmanager_0.1.0-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Can anyone help me? pls :D

PS: I am using Ubuntu 11.04 with Unity 3D interface

---

### Post by M7S on 2011-06-09
It's an error in the faenza package (it writes files where it shouldn't). This should fix it.

```
sudo dpkg -i --force-all /var/cache/apt/archives/dockmanager_0.1.0-0ubuntu1_i386.deb
sudo apt-get install -f
```

---

### Post by antoniu86 on 2011-06-09
Thanks ! It worked :D

---

