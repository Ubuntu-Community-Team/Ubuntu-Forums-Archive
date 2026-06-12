---
title: "How can evolution mail be disabled?"
date: 2009-06-06
forum: Desktop Environments
---

### Post by callahanp on 2009-06-06
Ubuntu installs evolution-mail as the default e-mail client 

I tried to remove it using synaptic but although evolution is listed as groupware client with e-mail and office stuff, removing it would appear to remove more than just evolution:  it also would remove  gnome-desktop-environment*  



cat /etc/issue
Ubuntu 9.04 \n \l
[PHP][/PHP]
uname -a
Linux hostname 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux


$ sudo apt-get remove --purge evolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  menu-xdg desktop-base planner gthumb python-renderpm
  gstreamer0.10-plugins-ugly libdiscid0 cheese libots0 gnome-network-admin
  hardinfo gthumb-data gparted gnome-office libaiksaurusgtk-1.2-0c2a
  abiword-common abiword abiword-plugin-mathview latex-xft-fonts
  libaiksaurus-1.2-0c2a python-lxml swfdec-gnome python-reportlab-accel
  libsoup2.2-8 dasher libloudmouth1-0 link-grammar-dictionaries-en p7zip
  gnome-themes-extras gdm-themes abiword-help python-numpy arj
  gstreamer0.10-ffmpeg gnome-volume-manager libaiksaurus-1.2-data
  python-4suite-doc gnome-backgrounds dasher-data xfce4-icon-theme gok
  libgdome2-0 abiword-plugin-grammar libwmf-bin libswfdec-0.8-0
  python-uniconvertor imagemagick-doc liferea libgdome2-cpp-smart0c2a
  libsidplay1 swfdec-mozilla gnome-core gtk2-engines-xfce python-4suite-xml
  imagemagick liblink-grammar4 libgtkmathview0c2a gnome-accessibility inkscape
  python-reportlab serpentine sound-juicer libmusicbrainz3-6 gnome-vfs-obexftp
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  evolution* evolution-exchange* evolution-indicator* evolution-plugins*
  gnome-desktop-environment*
0 upgraded, 0 newly installed, 5 to remove and 6 not upgraded.
After this operation, 10.9MB disk space will be freed.
Do you want to continue [Y/n]? ^C

---

### Post by aysiu on 2009-06-08
It's okay to remove *gnome-desktop-environment*

It's just a pointer to all the packages included in a default Gnome installation. If you remove one of those packages, you remove the pointer.

---

### Post by ugm6hr on 2009-06-08
I would also recommend ensuring that evolution-data-server-common and evolution-data-server remain, since they appear to form part of the Gnome panel.

The rest of evolution can be safely removed (as far as I know).

---

