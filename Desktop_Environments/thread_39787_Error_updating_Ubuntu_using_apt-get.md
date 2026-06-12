---
title: "Error updating Ubuntu using apt-get"
date: 2005-06-06
forum: Desktop Environments
---

### Post by arunsub on 2005-06-06
I got the following error when i tried to update ubuntu thourgh apt-get upgrade. I tried forcing apt-get, but it didn't work.

Preparing to replace kdelibs-data 4:3.4.0-0ubuntu3.1 (using .../kdelibs-data_4%3a3.4.0-0ubuntu3.2_all.deb) ...
Unpacking replacement kdelibs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.2_all.deb (--unpack):
trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf
Preparing to replace knetworkconf 0.6.1-3ubuntu2 (using .../knetworkconf_0.6.1-3ubuntu4_i386.deb) ...
Unpacking replacement knetworkconf ...
dpkg: error processing /var/cache/apt/archives/knetworkconf_0.6.1-3ubuntu4_i386.deb (--unpack):
trying to overwrite `/usr/share/icons/crystalsvg/22x22/actions/network_connected_lan.png', which is also in package knemo
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
/var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.2_all.deb
/var/cache/apt/archives/knetworkconf_0.6.1-3ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1) 

I couldn't fix the broken packages through Synaptic. Can anyone help?
 ](*,)

---

### Post by xao on 2005-06-06
[QUOTE=arunsub]I got the following error when i tried to update ubuntu thourgh apt-get upgrade. I tried forcing apt-get, but it didn't work.

Preparing to replace kdelibs-data 4:3.4.0-0ubuntu3.1 (using .../kdelibs-data_4%3a3.4.0-0ubuntu3.2_all.deb) ...
Unpacking replacement kdelibs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.2_all.deb (--unpack):
trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf
Preparing to replace knetworkconf 0.6.1-3ubuntu2 (using .../knetworkconf_0.6.1-3ubuntu4_i386.deb) ...
Unpacking replacement knetworkconf ...
dpkg: error processing /var/cache/apt/archives/knetworkconf_0.6.1-3ubuntu4_i386.deb (--unpack):
trying to overwrite `/usr/share/icons/crystalsvg/22x22/actions/network_connected_lan.png', which is also in package knemo
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
/var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.2_all.deb
/var/cache/apt/archives/knetworkconf_0.6.1-3ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1) 

I couldn't fix the broken packages through Synaptic. Can anyone help?
 ](*,)[/QUOTE]




Try running 
sudo apt-get check
to see if everything is playing nicely.

otherwise, running
sudo apt-get clean
may be of some use to clean everything that is cached. That way it will download all new packages.....


xao

---

### Post by NTolerance on 2005-06-06
Try installing the packages that are getting the overwrite errors with 

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/packagename.deb
```

---

### Post by cutOff on 2005-06-06
A quick search gave me this

[http://ubuntuforums.org/archive/index.php/t-25294.html](http://ubuntuforums.org/archive/index.php/t-25294.html)

---

### Post by arunsub on 2005-06-06
I did sudo apt-get check and sudo apt-get clean. I then went and uninstalled Clamav antivirus and it's dependent files. The problem then went away.

---

### Post by connellr on 2005-06-09
I was having the same problem and here is how I finally fixed it (there may be better ways, but this way worked well for me)

1) cd /var/cache/apt/archives
sudo dpkg -i --force-overwrite kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb
** Note: At this point I got a notice that my display manager failed and I was kicked out to console**

2) sudo apt-get remove knetworkconf
** Note: This will uninstall kubuntu-desktop, but we'll fix that later ... your personal settings should be fine (Safe in your home directory) **

3) sudo apt-get remove kdelibs-data
 ** Note: A lot of stuff will get removed with this package ... pretty much all of KDE, but thats ok**

4) sudo apt-get install kubuntu-desktop
** Here we put back all the stuff we got rid of earlier **

5) Either reboot (or you could kill the display manager process and restart it -- for those who dont like restarting).


At this point Synaptic and apt-get didn't complain of any packages that needed to be isntalled and KDE booted without problems too.

---

