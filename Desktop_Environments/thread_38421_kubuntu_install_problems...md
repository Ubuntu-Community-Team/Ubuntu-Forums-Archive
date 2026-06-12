---
title: "kubuntu install problems.."
date: 2005-05-31
forum: Desktop Environments
---

### Post by toddncl on 2005-05-31
I have ubuntu installed and running fine, however when i try to install kubuntu-desktop i get the following:

john@ubuntu:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
kubuntu-desktop is already the newest version.
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies:
  k3b: Depends: kdelibs-data (>= 4:3.3.99) but it is not going to be installed
  kdelibs4: Depends: kdelibs-data (>= 4:3.3.0) but it is not going to be install ed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a s olution).

For some reason it seems to have installed kubuntu but when i tried to boot into it there were no programs listed in the menu and konqueror could not browse my system.

is there a way for me to completley remove kubuntu and its dependancies and start again? or will i just get the same errors next time i try to install it?

thanks for any help.

---

### Post by Mez on 2005-05-31
```
sudo apt-get install --reinstall acpi-support acpid amarok anacron apmd arts bc bicyclerepair bogofilter cdparanoia cdrecord cupsys cupsys-bsd cupsys-client cupsys-driver-gimpprint dbus-1-utils dbus-qt-1 dc diveintopython doc-base doc-debian dvd+rw-tools fetchmail foomatic-db foomatic-db-engine foomatic-db-gimp-print foomatic-db-hpijs foomatic-filters foomatic-filters-ppds fortune-mod gs-esp hal irssi-text k3b kaffeine kdeadmin kdebase kdegraphics kdemultimedia kdenetwork kdepim kdeutils kdm knetworkconf konq-plugins konserve konversation kscreensaver kubuntu-default-settings kynaptic lftp libglut3 libsasl2-modules lsb mkisofs openoffice.org openoffice.org-kde pmount pnm2ppa powermanagement-interface powernowd procmail python-adns python-apt python-cddb python-clientcookie python-crypto python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools python-epydoc python-eunuchs python-examples python-gadfly python-gd python-gdbm python-gdchart python-genetic python-geoip python-gnupginterface python-gst python-htmlgen python-htmltmpl python-id3lib python-imaging python-imaging-sane python-jabber python-kjbuckets python-ldap python-musicbrainz python-mysqldb python-netcdf python-newt python-numarray python-numeric python-opengl python-osd python-pam python-parted python-pexpect python-pgsql python-pisock python-pqueue python-pyao python-pylibacl python-pyopenssl python-pyorbit python-pyvorbis python-pyxattr python-reportlab python-simpletal python-soappy python-sqlite python-stats python-syck python-twisted python-unit python-xdg python-xmpp python2.4-dbus python2.4-dictclient python2.4-librdf python2.4-libxml2 python2.4-libxslt1 python2.4-pycurl python2.4-samba readahead screen slocate smbclient ttf-arabeyes ttf-arphic-bkai00mp ttf-arphic-bsmi00lp ttf-arphic-gbsn00lp ttf-arphic-gkai00mp ttf-baekmuk ttf-bitstream-vera ttf-freefont ttf-indic-fonts ttf-kochi-gothic ttf-kochi-mincho ttf-malayalam-fonts ubuntu-quickguide unzip wvdial x-ttcidfont-conf x-window-system-core xlibmesa-gl xorg-driver-synaptics xterm zip
```

I'd suggest installing gnome first so you can get into a web browser and copy and paste that rather than having to type it all out

```
sudo apt-get install ubuntu-desktop
```

---

