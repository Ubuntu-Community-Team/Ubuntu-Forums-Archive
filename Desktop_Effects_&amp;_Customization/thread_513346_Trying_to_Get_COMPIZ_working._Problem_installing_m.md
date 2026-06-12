---
title: "Trying to Get COMPIZ working. Problem installing missing compiz-decorate"
date: 2007-07-30
forum: Desktop Effects &amp; Customization
---

### Post by dubayou on 2007-07-30
it doesnt want to install decorate for some reason... can i get some help on this

this is the result of ```
sudo aptitude -f install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf
```

> dubayou@ubuntu:~$ sudo aptitude -f install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  file libfreetype6 libmagic1 libpng12-0 linux-image-generic 
  linux-restricted-modules-common linux-restricted-modules-generic 
The following packages have been kept back:
  app-install-data app-install-data-commercial apport apport-gtk bind9-host 
  capplets-data compiz-core compiz-plugins dnsutils evolution-data-server 
  evolution-data-server-common firefox firefox-gnome-support gimp gimp-data 
  gimp-python gnome-app-install gnome-control-center gnome-panel 
  gnome-panel-data hwdb-client-common hwdb-client-gnome iptables 
  language-pack-en libbind9-0 libcamel1.2-10 libcurl3 libdecoration0 
  libdns22 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 
  libedataserver1.2-9 libedataserverui1.2-8 libegroupwise1.2-13 
  libexchange-storage1.2-3 libexif12 libgimp2.0 libgnome-window-settings1 
  libisc11 libisccc0 libisccfg1 libkrb53 liblwres9 libmagick9 libmetacity0 
  libnspr4 libnss3 libpanel-applet2-0 libslab0 libsmbclient linux-generic 
  linux-headers-generic metacity metacity-common openoffice.org 
  openoffice.org-base openoffice.org-calc openoffice.org-common 
  openoffice.org-core openoffice.org-draw openoffice.org-evolution 
  openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-java-common openoffice.org-math 
  openoffice.org-style-human openoffice.org-writer python python-apport 
  python-gdbm python-minimal python-problem-report python-uno python2.5 
  python2.5-minimal rdesktop samba-common smbclient ttf-opensymbol tzdata 
  unattended-upgrades update-manager update-manager-core vim-common 
  vim-tiny xscreensaver-data xscreensaver-gl 
The following NEW packages will be installed:
  compiz-fusion-plugins-unofficial 
The following packages will be upgraded:
  compiz-gnome 
1 packages upgraded, 1 newly installed, 0 to remove and 98 not upgraded.
Need to get 0B/308kB of archives. After unpacking 1855kB will be used.
Do you want to continue? [Y/n/?] 
Writing extended state information... Done
(Reading database ... 90198 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.1+git20070728~3v1ubuntu1_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070728~3v1ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Unpacking compiz-fusion-plugins-unofficial (from .../compiz-fusion-plugins-unofficial_0.0.1+git20070729~3v1ubuntu0_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-fusion-plugins-unofficial_0.0.1+git20070729~3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libkeybinding.so', which is also in package compiz-plugins
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070728~3v1ubuntu1_i386.deb
 /var/cache/apt/archives/compiz-fusion-plugins-unofficial_0.0.1+git20070729~3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of compiz:
 compiz depends on compiz-decorator; however:
  Package compiz-decorator is not installed.
dpkg: error processing compiz (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 compiz


---

### Post by psyopper on 2007-07-30
Did you try ```
sudo aptitude install compiz-decorator
```

-f *should* try to fix the dependencies, but part of that depends on how the package was built.

Which repo are you installing Compiz-Fusion from?

---

### Post by Espreon on 2007-07-30
Or do this (Emerald has succeeded the Compiz-Decorator)

```
sudo apt-get install emerald emerald-themes libemeraldengine0
```

---

### Post by dubayou on 2007-07-30
just tried both with these results
> dubayou@ubuntu:~$ sudo apt-get install emerald emerald-themes libemeraldengine0
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator
  compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
dubayou@ubuntu:~$ sudo apt-get -f install emerald emerald-themes libemeraldengine0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator
  compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
dubayou@ubuntu:~$ sudo apt-get -f install emerald emerald-themes libemeraldengine0


---

### Post by Espreon on 2007-07-30
Give up, and remove Compiz-Decorator and try to install Emerald Again. or download the .debs and do this:

```
sudo dpkg --install (drag and drop emerald .debs here)
```

Link to .debs:

[http://3v1n0.tuxfamily.org/dists/feisty/eyecandy/index.html](http://3v1n0.tuxfamily.org/dists/feisty/eyecandy/index.html)

Download the Emerald,Emerald Themes and the libemeraldengine0 .debs

---

### Post by psyopper on 2007-07-30
By the way... use aptitude instead of apt-get. 

Aptitude is a newer and updated revision of apt-get that is far more feature rich - among other things it will automatically load the dependencies and you won't get that whole section about missing dependencies and using apt-get -f

---

