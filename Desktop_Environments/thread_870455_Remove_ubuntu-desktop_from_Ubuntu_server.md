---
title: "Remove ubuntu-desktop from Ubuntu server"
date: 2008-07-25
forum: Desktop Environments
---

### Post by brucehohl on 2008-07-25
After installing ubuntu 6.06 server I used "apt-get install ubuntu-desktop" to install the Gnome desktop. 

I now want to remove all the packages from ubuntu-desktop metapackage to return to a 'server' install.

Will the following work?:
# aptitude remove <all_dependent_packages>


Where I remove <all_dependent_package listed here:

$ aptitude show ubuntu-desktop
Package: ubuntu-desktop
State: installed
Automatically installed: no
Version: 0.120
Priority: optional
Section: base
Maintainer: Matt Zimmerman <mdz@ubuntu.com>
Uncompressed Size: 41.0k

Depends: acpi, acpi-support, acpid, alacarte, anacron, apmd, bc, bicyclerepair, bluez-cups, bluez-pcmcia-support, bluez-pin, bluez-utils, brltty, brltty-x11, bug-buddy, cdparanoia, cdrecord, contact-lookup-applet, cupsys, cupsys-bsd, cupsys-client, cupsys-driver-gutenprint, dbus-1-utils, dc, deskbar-applet, desktop-file-utils, diveintopython, doc-base, doc-debian, dvd+rw-tools, ekiga, eog, esound, evince,  evolution, evolution-exchange, evolution-plugins, evolution-webcal, example-content, file-roller, firefox, firefox-gnome-support, foo2zjs,  foomatic-db, foomatic-db-engine, foomatic-db-gutenprint, foomatic-db-hpijs, foomatic-filters, foomatic-filters-ppds, fortune-mod, gaim, gamin, gcalctool, gconf-editor, gdebi, gdm, gedit, gimp, gimp-print, gimp-python, gnome-about, gnome-accessibility-themes, gnome-app-install, gnome-applets, gnome-btdownload, gnome-control-center, gnome-cups-manager, gnome-games, gnome-icon-theme, gnome-mag, gnome-media, gnome-menus, gnome-netstatus-applet, gnome-nettool, gnome-panel, gnome-pilot-conduits, gnome-power-manager, gnome-screensaver, gnome-session, gnome-spell, gnome-system-monitor, gnome-system-tools, gnome-terminal, gnome-themes, gnome-utils, gnome-volume-manager, gnome2-user-guide, gnopernicus, gok, gs-esp, gstreamer0.10-alsa, gstreamer0.10-esd,  gstreamer0.10-plugins-base-apps, gthumb, gtk2-engines-clearlooks, gtk2-engines-industrial, gtk2-engines-mist, gtk2-engines-smooth, gucharmap, hal, hal-device-manager, hotkey-setup, hplip, hplip-ppds, hwdb-client, irssi, landscape-client, language-selector, lftp, libesd-alsa0, libgl1-mesa, libglib2.0-data, libglut3, libgnome2-perl,  libgnomevfs2-bin, libgnomevfs2-extra, libpam-foreground, libpt-plugins-v4l, libpt-plugins-v4l2, librsvg2-common, libsasl2-modules, libstdc++5, libxp6, metacity, min12xxw, mkisofs, nautilus, nautilus-cd-burner, nautilus-sendto, notification-daemon, openoffice.org, openoffice.org-evolution, openoffice.org-gnome, pnm2ppa, powermanagement-interface, powernowd, python-adns, python-apt, python-cddb, python-clientcookie, python-crypto, python-egenix-mxproxy, python-egenix-mxstack, python-egenix-mxtexttools, python-egenix-mxtools, python-epydoc, python-eunuchs, python-examples, python-gadfly, python-gd, python-gdbm, python-genetic, python-geoip, python-glade2, python-gnome2, python-gnupginterface, python-gst0.10, python-gtk2, python-htmlgen, python-htmltmpl, python-id3lib, python-imaging, python-imaging-sane, python-jabber, python-kjbuckets, python-ldap, python-mysqldb, python-netcdf, python-newt, python-numeric, python-pam, python-parted, python-pexpect, python-pgsql, python-pisock, python-pqueue, python-pyao, python-pylibacl, python-pyopenssl, python-pyorbit, python-pyvorbis, python-pyxattr, python-reportlab, python-simpletal, python-soappy, python-sqlite, python-stats, python-syck, python-unit, python-xdg, python-xmpp, python2.4-dbus,  python2.4-dictclient, python2.4-librdf, python2.4-libxml2, python2.4-libxslt1, python2.4-pycurl, readahead, rhythmbox, rss-glx, scim, scim-gtk2-immodule, screen, screensaver-default-images, scrollkeeper, serpentine, slocate, smbclient, sound-juicer, ssh-askpass-gnome, synaptic, tangerine-icon-theme, tango-icon-theme, tango-icon-theme-common, totem, tsclient, ttf-arabeyes, ttf-arphic-ukai, ttf-arphic-uming, ttf-baekmuk, ttf-bitstream-vera, ttf-dejavu, ttf-freefont, ttf-gentium, ttf-indic-fonts, ttf-kochi-gothic, ttf-kochi-mincho, ttf-lao, ttf-malayalam-fonts, ttf-mgopen, ttf-thai-tlwg, ubuntu-artwork, ubuntu-docs, ubuntu-sounds, unzip, update-notifier, usplash, vino, wvdial, x-ttcidfont-conf, x-window-system-core, xcursor-themes, xkeyboard-config, xsane, xscreensaver-data, xscreensaver-gl, xserver-xorg-input-synaptics, xterm, xvncviewer, yelp, zenity, zip 

Description: The Ubuntu desktop system 
This package depends on all of the packages in the Ubuntu desktop system 
It is safe to remove this package if some of the desktop system packages are not desired.  However, it is recommended that you keep it installed, because it is used to carry out certain upgrade transitions (such as adding new packages to the system).

---

### Post by EXCiD3 on 2008-07-25
I think it should be safe to remove that, its just going to remove any graphical applications and revert you back to the standard terminal interface for ubuntu server instead. you should be fine.

---

### Post by foxmajik on 2010-04-25
> **brucehohl said:**
> After installing ubuntu 6.06 server I used "apt-get install ubuntu-desktop" to install the Gnome desktop. 

I now want to remove all the packages from ubuntu-desktop metapackage to return to a 'server' install.

Will the following work?:
# aptitude remove <all_dependent_packages>


Use tasksel to re-purpose your computer.

```
$ sudo tasksel
```

Use the space bar to uncheck Ubuntu Desktop and check Basic Server.

Then press Enter to go ahead.

Removing the desktop packages and installing the server packages may take several minutes.

---

### Post by Perfect Storm on 2011-11-19
Necromancing, please start a new thread.



Thread closed.

---

