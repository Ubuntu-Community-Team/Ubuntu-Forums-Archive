---
title: "64 bit ubuntu"
date: 2011-03-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by C1377 on 2011-03-30
The Dell Ubuntu 10.04 iso is 32bit with the Netbook Interface

I have  upgraded  Ubuntu 10.10 64bit and I would like to install the netbook interface.

Does anyone know how?

---

### Post by garvinrick4 on 2011-03-30
```
sudo apt-get install unity
``````
sudo apt-get install ubuntu-netbook
```rick@rick-HP-G71-Notebook-PC:~$ aptitude show unity
```

Package: unity                           
State: installed
Automatically installed: no
Version: 0.2.46-0ubuntu5
Priority: optional
Section: gnome
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 594k
Depends: libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.29.3), libbamf0 (>=
         0.2.20), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6
         (>= 2.2.5), libcairo2 (>= 1.2.4), libclutk-0.3-0 (>= 0.3.6),
         libclutter-1.0-0 (>= 1.2.12-0ubuntu3) | libclutter-eglx-es20-1.0-0 (>=
         1.2.12-0ubuntu3) | libclutter-eglx-es11-1.0-0 (>= 1.2.12-0ubuntu3),
         libclutter-gtk-0.10-0 (>= 0.10.2), libdbus-1-3 (>= 1.0.2),
         libdbus-glib-1-2 (>= 0.78), libdbusmenu-glib1 (>= 0.3.12), libdee-1.0-0
         (>= 0.1.0), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.2.1),
         libgconf2-4 (>= 2.31.1), libgdk-pixbuf2.0-0 (>= 2.21.6), libgee2 (>=
         0.5.2), libglib2.0-0 (>= 2.22.2-0ubuntu1wncksync3),
         libgnome-desktop-2-17 (>= 1:2.29.92), libgnome2-0 (>= 2.17.3),
         libgnomecanvas2-0 (>= 2.11.1), libgnomeui-0 (>= 2.22.0), libgnomevfs2-0
         (>= 1:2.17.90), libgtk2.0-0 (>= 2.18.0), libice6 (>= 1:1.0.0),
         libindicator1, libjson-glib-1.0-0, liborbit2 (>= 1:2.14.10),
         libpango1.0-0 (>= 1.14.0), libpng12-0 (>= 1.2.13-4), libpopt0 (>=
         1.16), libsm6, libstartup-notification0 (>= 0.10), libunique-1.0-0 (>=
         1.0.0), libunity-misc0 (>= 0.1.0), libunity0 (>= 0.2.30),
         libutouch-grail1 (>= 1.0.4), libwnck22 (>= 1:2.22), libx11-6,
         libxcb-atom1 (>= 0.3.6), libxcb-event1 (>= 0.3.6), libxcb-icccm1 (>=
         0.3.6), libxcb-property1 (>= 0.3.6), libxcb1, gconf2 (>= 2.28.1-2),
         mutter (>= 2.31.5), unity-asset-pool (>= 0.8.18)
Recommends: unity-place-applications, unity-place-files, indicator-appmenu,
            indicator-application, indicator-sound, indicator-datetime,
            indicator-messages, indicator-me, indicator-session,
            ubuntu-netbook-default-settings
Conflicts: netbook-launcher (< 1:2.1.18-0ubuntu2)
Replaces: netbook-launcher (< 1:2.1.18-0ubuntu2)
Provides: indicator-renderer, netbook-launcher
Description: Unity Interface for Ubuntu Netbook Edition
 Unity is a graphical interface designed for Ubuntu Netbook Edition
Homepage: [https://launchpad.net/unity](https://launchpad.net/unity)
``````

rick@rick-HP-G71-Notebook-PC:~$ aptitude show netbook
E: Unable to locate package netbook      
rick@rick-HP-G71-Notebook-PC:~$ aptitude show ubuntu-netbook
Package: ubuntu-netbook                  
State: installed
Automatically installed: no
Version: 2.035
Priority: optional
Section: metapackages
Maintainer: Ubuntu Desktop Developers <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 61.4k
Depends: alacarte, alsa-base, alsa-utils, anacron, bc, ca-certificates,
         checkbox-gtk, consolekit, cups, cups-bsd, cups-client,
         cups-driver-gutenprint, dc, desktop-file-utils, doc-base, eog, evince,
         file-roller, foomatic-db-compressed-ppds, foomatic-filters, gcalctool,
         gconf-editor, gdm, gedit, genisoimage, ghostscript-x, gnome-about,
         gnome-applets, gnome-control-center, gnome-media, gnome-menus,
         gnome-nettool, gnome-panel, gnome-power-manager, gnome-session,
         gnome-session-canberra, gnome-system-monitor, gnome-system-tools,
         gnome-terminal, gnome-themes-selected, gnome-themes-ubuntu,
         gnome-utils, gstreamer0.10-alsa, gstreamer0.10-plugins-base-apps,
         gstreamer0.10-pulseaudio, gtk2-engines, gtk2-engines-pixbuf, gucharmap,
         humanity-icon-theme, indicator-applet-session, inputattach,
         language-selector, launchpad-integration, lftp, libgd2-xpm,
         libgnome2-perl, libpam-ck-connector, libsasl2-modules, libxp6,
         nautilus, nautilus-sendto, notify-osd, openprinting-ppds,
         plymouth-theme-ubuntu-logo, pnm2ppa, pulseaudio,
         pulseaudio-esound-compat, rarian-compat, screen,
         screensaver-default-images, seahorse, smbclient, software-center,
         software-properties-gtk, ssh-askpass-gnome, synaptic,
         system-config-printer-gnome, ttf-dejavu-core, ttf-freefont,
         ubuntu-artwork, ubuntu-extras-keyring, ubuntu-netbook-default-settings,
         ubuntu-sounds, unity, unzip, update-manager, update-notifier,
         wireless-tools, wpasupplicant, x-ttcidfont-conf, xdg-user-dirs,
         xdg-user-dirs-gtk, xkb-data, xorg, xscreensaver-data, xterm, yelp,
         zenity, zip
Recommends: acpi-support, aisleriot, app-install-data-partner, apport-gtk,
            avahi-autoipd, avahi-daemon, bluez, bluez-alsa, bluez-cups,
            bluez-gstreamer, branding-ubuntu, brltty, brltty-x11, cheese,
            computer-janitor-gtk, empathy, espeak, evolution,
            evolution-exchange, evolution-indicator, evolution-plugins,
            evolution-webcal, example-content, firefox, firefox-gnome-support,
            foo2zjs, gdm-guest-session, gnome-accessibility-themes,
            gnome-bluetooth, gnome-codec-install, gnome-disk-utility, gnome-mag,
            gnome-mahjongg, gnome-orca, gnome-screensaver, gnome-sudoku,
            gnome-user-guide, gvfs-fuse, gwibber, hplip, ibus, ibus-gtk,
            ibus-pinyin, ibus-pinyin-db-android, ibus-table, im-switch,
            indicator-appmenu, indicator-datetime, indicator-messages,
            jockey-gtk, kerneloops-daemon, laptop-detect, libnss-mdns,
            libpam-gnome-keyring, libunity-misc0, linux-headers-generic,
            min12xxw, mousetweaks, nautilus-share, network-manager-gnome,
            onboard, openoffice.org-calc, openoffice.org-gnome,
            openoffice.org-help-en-us, openoffice.org-impress,
            openoffice.org-style-human, openoffice.org-writer, pcmciautils,
            policykit-desktop-privileges, pulseaudio-module-bluetooth,
            pulseaudio-module-gconf, pulseaudio-module-x11, pxljr, quadrapassel,
            rhythmbox, rhythmbox-ubuntuone-music-store, shotwell, simple-scan,
            speech-dispatcher, splix, telepathy-idle, tomboy, totem,
            totem-mozilla, transmission-gtk, ttf-indic-fonts-core,
            ttf-kacst-one, ttf-khmeros-core, ttf-lao, ttf-liberation,
            ttf-punjabi-fonts, ttf-takao-pgothic, ttf-thai-tlwg,
            ttf-ubuntu-font-family, ttf-unfonts-core, ttf-wqy-microhei, ubufox,
            ubuntu-docs, ubuntuone-client-gnome, usb-creator-gtk,
            xcursor-themes, xdg-utils
Description: The Ubuntu Netbook system
 This package depends on all of the packages in the Ubuntu Netbook system 
 
 It is also used to help ensure proper upgrades, so it is recommended that it
 not be removed.

rick@rick-HP-G71-Notebook-PC:~$ 

```You install Netbook version you get desktop with it.
You install Desktop version you only get Desktop:
Link below for installing packages:
[http://ubuntuguide.org/wiki/Ubuntu:Maverick](http://ubuntuguide.org/wiki/Ubuntu:Maverick)

---

