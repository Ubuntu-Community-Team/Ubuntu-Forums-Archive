---
title: "aptitude wants to remove a lot of packages"
date: 2005-12-27
forum: Desktop Environments
---

### Post by wheelchair_2 on 2005-12-27
For some reason for the past few weeks any time I run aptitude install I get this:

```
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
The following packages are unused and will be REMOVED:
  libgmp3c2 libgmpxx3
The following packages will be automatically REMOVED:
  celestia-gnome etherape ethereal ethereal-common gcombust gtkpod kismet
  linux-686 seahorse vlc wxvlc
The following packages will be REMOVED:
  abiword-common abiword-gnome ant apache2 apache2-common
  apache2-mpm-prefork apache2-utils ark celestia-gnome chbg etherape
  ethereal ethereal-common gcombust gdeskcal gnome-themes-extras gparted
  gtk2-engines-spherecrystal gtkpod imlib-base junit kdelibs-bin
  kdelibs-data kdelibs4c2 kismet liba52-0.7.4 libant1.6-java
  libapache2-mod-php4 libapr0 libart2 libarts1c2 libaspell15c2 libcairo1
  libenchant1c2 libgdk-pixbuf2 libglib1.2 libglibmm-2.4-1c2 libglitz1
  libgpgme11 libgtk1.2 libgtk1.2-common libgtkmm-2.4-1c2 libid3tag0
  libjsch-java liblua50 liblualib50 libmad0 libmodplug0c2 libmpeg2-4
  libnetpbm10 libopenexr2c2 libpcap0.7 libpcre3 libpixman1 libpng10-0
  libqt3-mt libsigc++-2.0-0c2 libungif4g libwxgtk2.4-1 libzzip-0-12
  linux-686 linux-image-2.6.12-6-686 linux-image-686 menu-xdg netpbm
  openssl php4-common samba seahorse ssl-cert ubuntu-calendar
  ubuntu-calendar-march vlc wxvlc xmms
0 packages upgraded, 0 newly installed, 77 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 271MB will be freed.
Do you want to continue? [Y/n/?] n
Abort.

```

I've replaced my sources.list with the recommended one here, and I've done just about every purge and clean option in aptitude. Why does it want to remove so many things? I need most of those! For example:

I use the 686 kernel
I use Apache/PHP
I use samba
I use abiword
I use VLC

Most importantly, those things actually work! Does anyone have a clue why it would be trying to remove all of these packages?

---

### Post by sciurus on 2005-12-27
Try sudo apt-get install ubuntu-desktop and see ig that reduces the number of packages it wants to remove.

---

### Post by wheelchair_2 on 2005-12-28
[QUOTE=sciurus]Try sudo apt-get install ubuntu-desktop and see ig that reduces the number of packages it wants to remove.[/QUOTE]

Didn't work. It still wants to remove everything. I even did a reinstall of the ubuntu-desktop package in Synaptic, same issue.

I tried removing some packages I could do without to see if one of them would fix it, and none did. Now I get this:

```
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
The following packages will be automatically REMOVED:
  linux-686
The following packages will be REMOVED:
  abiword-common abiword-gnome ant apache2 apache2-common
  apache2-mpm-prefork apache2-utils ark chbg gdeskcal gnome-themes-extras
  gparted gtk2-engines-spherecrystal imlib-base junit kdelibs-bin
  kdelibs-data kdelibs4c2 liba52-0.7.4 libant1.6-java libapache2-mod-php4
  libapr0 libart2 libarts1c2 libaspell15c2 libcairo1 libenchant1c2
  libgdk-pixbuf2 libglib1.2 libglibmm-2.4-1c2 libglitz1 libgpgme11
  libgtk1.2 libgtk1.2-common libgtkmm-2.4-1c2 libid3tag0 libjsch-java
  liblua50 liblualib50 libmad0 libmodplug0c2 libmpeg2-4 libnetpbm10
  libopenexr2c2 libpcap0.7 libpcre3 libpixman1 libpng10-0 libqt3-mt
  libsigc++-2.0-0c2 libungif4g libwxgtk2.4-1 libzzip-0-12 linux-686
  linux-headers-2.6.12-10 linux-headers-2.6.12-10-686 linux-headers-686
  linux-image-686 menu-xdg netpbm openssl php4-common samba ssl-cert
  ubuntu-calendar ubuntu-calendar-march xmms
0 packages upgraded, 0 newly installed, 67 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 232MB will be freed.
Do you want to continue? [Y/n/?]

```

In other words...the same thing. Any other ideas?

---

### Post by wheelchair_2 on 2005-12-28
Scratch that... I fixed it and am not sure why it worked. I ran aptitude and pressed G. It brought up the list of apps to remove, then selected Package>Keep. It decided to keep them.

I'm really wondering why it happened in the first place, but I suppose as long as it's fixed, I'm ok.

Thanks for your help, I appreciate the reply.

---

