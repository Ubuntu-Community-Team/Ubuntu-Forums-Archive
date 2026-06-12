---
title: "installing ati drivers"
date: 2010-08-28
forum: Desktop Environments
---

### Post by foilesr on 2010-08-28
I think that my problem is the installation of the drivers.
I ran the program and it made the package. Now I have to install the package but it tells me it is broken.
I typed :
sudo apt-get -f install
and after (y/n) I got......

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu4_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
 i do not understand what this means any help would be great. thanks

---

### Post by foilesr on 2010-08-28
UPDATE:
i was able to fix the error and install the package, however the instructions say to run a program called "aticonfig --initial" to set it up. the terminal says to me "unknown command.  i went looking for it where it said it would be and it is not there..... now what do i do?

---

### Post by infamous-online on 2010-08-28
On Ubuntu you don't have to install the driver unless your video card isn't on the list, and I am assuming that's the case for you right?

---

