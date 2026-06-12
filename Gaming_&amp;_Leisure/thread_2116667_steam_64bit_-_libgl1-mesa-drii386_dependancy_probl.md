---
title: "steam 64bit - libgl1-mesa-dri:i386 dependancy problem"
date: 2013-02-16
forum: Gaming &amp; Leisure
---

### Post by fruitz on 2013-02-16
hello all!

I tried to install steam from software center, since it's available now. I get an error of broken dependencies, and the 'broken' filter on synaptic indicates the broken package is libgl1-mesa-dri:i386.
i tried to install steam with apt-get install -f steam, same error
i tried to run apt-get -f install, same error
funny thing, steam seems to work fine...but the broken dependency blocks all my package activity now. if i try to remove the broken package of course, steam is disinstalled too.

any idea?
thanks!

---

### Post by efflandt on 2013-02-17
Did you try removing **libgl1-mesa-dri:i386** and installing **ia32-libs-multiarch**?  Maybe that would help things cooperate between 64-bit Linux and 32-bit Steam.  I already had ia32-libs-multiarch installed before installing Steam (beta weeks ago), and regular Ubuntu updates still work, along with Steam updating to release version.

---

### Post by fruitz on 2013-02-19
hi,
thanks for your reply.

that package is already installed, but it's called:
[B]ia32-libs-multiarch:i386

[/B] there's no in synaptic
**ia32-libs-multiarch**

---

### Post by Perfect Storm on 2013-02-19
Try removing both of these packages and steam.
Then redownload steam and install.

After that install ia32-libs instead.

```
sudo apt-get install ia32-libs
```

---

### Post by fruitz on 2013-02-20
```
E: /var/cache/apt/archives/libdrm2_2.4.39-0ubuntu1_amd64.deb: trying to overwrite shared '/usr/share/doc/libdrm2/changelog.Debian.gz', which is different from other instances of package libdrm2:amd64
E: /var/cache/apt/archives/libglapi-mesa_9.0-0ubuntu1_amd64.deb: trying to overwrite shared '/usr/share/doc/libglapi-mesa/changelog.Debian.gz', which is different from other instances of package libglapi-mesa:amd64
```

---

### Post by Perfect Storm on 2013-02-20
Sounds like you have installed different packages from non-ubuntu official which makes a mess.
Try with
```
sudo apt-get autoclean &&  sudo apt-get autoremove
sudo apt-get update && sudo apt-get upgrade
```

Then try again.

---

### Post by fruitz on 2013-02-20
```
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libdrm2_2.4.39-0ubuntu1_amd64.deb
 /var/cache/apt/archives/libglapi-mesa_9.0-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Perfect Storm on 2013-02-21
ok, then we need to do it manually.

```
sudo rm /usr/share/doc/libdrm2/changelog.Debian.gz
sudo rm /usr/share/doc/libgl1-mesa-dri/changelog.Debian.gz
sudo rm /usr/share/doc/libgl1-mesa-glx/changelog.Debian.gz
sudo rm /usr/share/doc/libglapi-mesa/changelog.Debian.gz
```

Then:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by fruitz on 2013-02-21
thanks!!! that made the trick!!

---

