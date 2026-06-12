---
title: "Segfault when installing ubuntu-desktop"
date: 2009-08-06
forum: Desktop Environments
---

### Post by fophillips on 2009-08-06
I am trying to install ubuntu-desktop on my 9.04 Ubuntu Server but apt-get segfaulted and told me to run **dpkg --configure -a** when I did I got this output:

```

*Setting up various things successfully...*

Setting up app-install-data-partner (11.9.04.2) ...
Caching application data...
Illegal instruction

Setting up libsensors3 (1:2.10.7-1) ...
.udevdb or .udev presence implies active udev.  Aborting MAKEDEV invocation.

malloc: ../bash/execute_cmd.c:2787: assertion botched
nunits < 30
Aborting...Aborted
dpkg: error processing libsensors3 (--configure):
 subprocess post-installation script returned error exit status 134
Setting up libcanberra0 (0.11-1ubuntu5) ...
Segmentation fault
Segmentation fault
dpkg: error processing libcanberra0 (--configure):
 subprocess post-installation script returned error exit status 139
Setting up poppler-utils (0.10.5-1ubuntu2.2) ...
Setting up python-xapian (1.0.7-3.1ubuntu2) ...
Segmentation fault
dpkg: error processing python-xapian (--configure):
 subprocess post-installation script returned error exit status 139
Setting up libavahi-compat-libdnssd1 (0.6.23-4ubuntu4) ...
zsh: segmentation fault  sudo dpkg --configure -a

```

And then if I try to run dpkg --configure again it just hangs with no output and refuses to be killed even with SIGKILL

---

