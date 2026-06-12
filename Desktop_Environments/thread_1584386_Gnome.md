---
title: "Gnome?"
date: 2010-09-29
forum: Desktop Environments
---

### Post by TNT1 on 2010-09-29
I was in software center just now, and I see "The GNOME desktop environment" is not installed... So... what am I using then? How do I find out?

---

### Post by garvinrick4 on 2010-09-29
aptitude show (package name)

rick@rick-laptop:~$ aptitude show gdm
Package: gdm
State: installed
Automatically installed: no
Version: 2.30.2.is.2.30.0-0ubuntu4
Priority: optional
Section: gnome
Maintainer: Sebastien Bacher <seb128@ubuntu.com>
Uncompressed Size: 8,032k
Depends: libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.29.3), libattr1 (>=
         2.4.41-1), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6
         (>= 2.4), libcairo2 (>= 1.2.4), libcanberra-gtk0 (>= 0.4), libcanberra0
         (>= 0.2), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78),
         libdevkit-power-gobject1 (>= 1:0.9.1), libfontconfig1 (>= 2.8.0),
         libfreetype6 (>= 2.2.1), libgconf2-4 (>= 2.27.0), libglib2.0-0 (>=
         2.23.5), libgnome2-0 (>= 2.17.3), libgnomecanvas2-0 (>= 2.11.1),
         libgtk2.0-0 (>= 2.16.0), liborbit2 (>= 1:2.14.10), libpam0g (>=
         0.99.7.1), libpanel-applet2-0 (>= 2.26.0), libpango1.0-0 (>= 1.14.0),
         libpolkit-gobject-1-0 (>= 0.94), libpopt0 (>= 1.15), libselinux1 (>=
         1.32), libwrap0 (>= 7.6-4~), libx11-6 (>= 0), libxau6, libxdmcp6,
         libxklavier16 (>= 5.0), libxml2 (>= 2.6.27), zlib1g (>= 1:1.1.4),
         debconf (>= 0.5) | debconf-2.0, gconf2 (>= 2.10.1-2), upstart-job,
         adduser, libpam-modules (>= 0.72-1), libpam-runtime (>= 0.76-13.1),
         gnome-session-bin, kbd | console-tools, udev (>= 149-2)
Recommends: xserver-xorg, metacity | x-window-manager, gnome-settings-daemon |
            xfconf
Suggests: locales, uswsusp, libpam-gnome-keyring, gnome-power-manager,
          gnome-orca, gok, gnome-mag
Conflicts: fast-user-switch-applet, gdm-snapshot, libxklavier15 (<
           4.0-0ubuntu2), xsplash (< 0.8)
Breaks: usplash
Replaces: fast-user-switch-applet, gdm-snapshot
Provides: x-display-manager
Description: GNOME Display Manager
 gdm provides the equivalent of a "login:" prompt for X displays- it pops up a
 login window and starts an X session. 
 
 It provides all the functionality of xdm, including XDMCP support for managing
 remote displays. 
 
 The greeting window is written using the GNOME libraries and hence looks like a
 GNOME application- even to the extent of supporting themes! By default, the
 greeter is run as an unprivileged user for security.

rick@rick-laptop:~$

---

### Post by TNT1 on 2010-09-29
Ok, I get: 
```
Package: gdm
State: installed
Automatically installed: no
Version: 2.30.2.is.2.30.0-0ubuntu3
Priority: optional
Section: gnome
Maintainer: Sebastien Bacher <seb128@ubuntu.com>
Uncompressed Size: 7,848k
Depends: libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.29.3), libattr1 (>=
         2.4.41-1), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6
         (>= 2.4), libcairo2 (>= 1.2.4), libcanberra-gtk0 (>= 0.4), libcanberra0
         (>= 0.2), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78),
         libdevkit-power-gobject1 (>= 1:0.9.1), libfontconfig1 (>= 2.8.0),
         libfreetype6 (>= 2.2.1), libgconf2-4 (>= 2.27.0), libglib2.0-0 (>=
         2.23.5), libgnome2-0 (>= 2.17.3), libgnomecanvas2-0 (>= 2.11.1),
         libgtk2.0-0 (>= 2.16.0), liborbit2 (>= 1:2.14.10), libpam0g (>=
         0.99.7.1), libpanel-applet2-0 (>= 2.26.0), libpango1.0-0 (>= 1.14.0),
         libpolkit-gobject-1-0 (>= 0.94), libpopt0 (>= 1.15), libselinux1 (>=
         1.32), libwrap0 (>= 7.6-4~), libx11-6 (>= 0), libxau6, libxdmcp6,
         libxklavier16 (>= 5.0), libxml2 (>= 2.6.27), zlib1g (>= 1:1.1.4),
         debconf (>= 0.5) | debconf-2.0, gconf2 (>= 2.10.1-2), upstart-job,
         adduser, libpam-modules (>= 0.72-1), libpam-runtime (>= 0.76-13.1),
         gnome-session-bin, kbd | console-tools, udev (>= 149-2)
Recommends: xserver-xorg, metacity | x-window-manager, gnome-settings-daemon |
            xfconf
Suggests: locales, uswsusp, libpam-gnome-keyring, gnome-power-manager,
          gnome-orca, gok, gnome-mag
Conflicts: fast-user-switch-applet, gdm-snapshot, libxklavier15 (<
           4.0-0ubuntu2), xsplash (< 0.8)
Breaks: usplash
Replaces: fast-user-switch-applet, gdm-snapshot
Provides: x-display-manager
Description: GNOME Display Manager
 gdm provides the equivalent of a "login:" prompt for X displays- it pops up a
 login window and starts an X session. 
 
 It provides all the functionality of xdm, including XDMCP support for managing
 remote displays. 
 
 The greeting window is written using the GNOME libraries and hence looks like a
 GNOME application- even to the extent of supporting themes! By default, the
 greeter is run as an unprivileged user for security.
```

So what's the thing in software center then? And why is my gdm smaller than yours, and why is yours for ubuntu4 and I'm only at ubuntu3?

---

### Post by garvinrick4 on 2010-09-29
find the true linux name of package and then run it. The package name is. I think I see what your looking at. Is it a Debian testing repository package. The package is not in my selections.```

sudo dpkg --get-selections > installedsoftware 
```
this will give you a text file of all your packages in true linux names in Home directory.

---

### Post by garvinrick4 on 2010-10-01
```
rick@rick-laptop:~$ aptitude show ubuntu-desktop
Package: ubuntu-desktop
State: installed
Automatically installed: no
Version: 1.197
Priority: optional
Section: metapackages
Maintainer: Matt Zimmerman <mdz@ubuntu.com>
Uncompressed Size: 61.4k
Depends: alacarte, alsa-base, alsa-utils, anacron, bc, ca-certificates,
         checkbox-gtk, cups, cups-bsd, cups-client, dc, desktop-file-utils,
         doc-base, eog, evince, file-roller, foomatic-db, foomatic-db-engine,
         foomatic-filters, gcalctool, gconf-editor, gdebi, gdm, gedit,
         genisoimage, ghostscript-x, gnome-about, gnome-applets,
         gnome-control-center, gnome-icon-theme, gnome-media, gnome-menus,
         gnome-nettool, gnome-panel, gnome-power-manager, gnome-session,
         gnome-session-canberra, gnome-system-monitor, gnome-system-tools,
         gnome-terminal, gnome-themes-selected, gnome-themes-ubuntu,
         gnome-utils, gstreamer0.10-alsa, gstreamer0.10-plugins-base-apps,
         gstreamer0.10-pulseaudio, gtk2-engines, gtk2-engines-pixbuf, gucharmap,
         indicator-applet-session, inputattach, language-selector,
         launchpad-integration, lftp, libgd2-xpm, libgl1-mesa-glx,
         libgnome2-perl, libpam-ck-connector, libsasl2-modules, libsdl1.2debian,
         libsdl1.2debian-pulseaudio, libxp6, metacity, nautilus,
         nautilus-sendto, notify-osd, openprinting-ppds, pnm2ppa, pulseaudio,
         pulseaudio-esound-compat, rarian-compat, screen,
         screensaver-default-images, seahorse, smbclient, software-center,
         software-properties-gtk, ssh-askpass-gnome, synaptic,
         system-config-printer-gnome, ttf-dejavu-core, ttf-freefont,
         ubuntu-artwork, ubuntu-sounds, unzip, update-manager, update-notifier,
         wireless-tools, wpasupplicant, x-ttcidfont-conf, xdg-user-dirs,
         xdg-user-dirs-gtk, xkb-data, xorg, xscreensaver-data, xscreensaver-gl,
         xterm, yelp, zenity, zip
Recommends: acpi-support, aisleriot, app-install-data-partner, apport-gtk,
            avahi-autoipd, avahi-daemon, bluez, bluez-alsa, bluez-cups,
            bluez-gstreamer, bogofilter, branding-ubuntu, brasero, brltty,
            brltty-x11, cdparanoia, compiz, computer-janitor-gtk, dvd+rw-tools,
            empathy, espeak, evolution, evolution-couchdb, evolution-exchange,
            evolution-indicator, evolution-plugins, evolution-webcal,
            example-content, f-spot, firefox, firefox-gnome-support, foo2zjs,
            gbrainy, gcc, gdm-guest-session, gnome-accessibility-themes,
            gnome-bluetooth, gnome-codec-install, gnome-disk-utility, gnome-mag,
            gnome-mahjongg, gnome-orca, gnome-screensaver, gnome-sudoku,
            gnome-user-guide, gnomine, gvfs-fuse, hplip, ibus, ibus-gtk,
            ibus-m17n, ibus-table, im-switch, indicator-messages, jockey-gtk,
            kerneloops-daemon, laptop-detect, libgail-gnome-module,
            libgl1-mesa-dri, libnss-mdns, libpam-gnome-keyring, libwmf0.2-7-gtk,
            linux-headers-generic, make, min12xxw, mousetweaks, nautilus-share,
            network-manager-gnome, network-manager-pptp,
            network-manager-pptp-gnome, onboard, openoffice.org-calc,
            openoffice.org-gnome, openoffice.org-help-en-us,
            openoffice.org-impress, openoffice.org-math,
            openoffice.org-style-human, openoffice.org-writer, pcmciautils,
            pitivi, plymouth-theme-ubuntu-logo, plymouth-x11,
            pm-utils-powersave-policy, policykit-desktop-privileges,
            pulseaudio-module-bluetooth, pulseaudio-module-gconf,
            pulseaudio-module-x11, pxljr, quadrapassel, rhythmbox,
            rhythmbox-ubuntuone-music-store, simple-scan, speech-dispatcher,
            splix, telepathy-idle, tomboy, totem, totem-mozilla,
            transmission-gtk, tsclient, ttf-indic-fonts-core, ttf-kacst-one,
            ttf-khmeros-core, ttf-lao, ttf-liberation, ttf-punjabi-fonts,
            ttf-takao-pgothic, ttf-thai-tlwg, ttf-unfonts-core,
            ttf-wqy-microhei, ubufox, ubuntu-docs, ubuntuone-client-gnome,
            usb-creator-gtk, vinagre, vino, wodim, xcursor-themes, xdg-utils
Description: The Ubuntu desktop system
 This package depends on all of the packages in the Ubuntu desktop system 
 
 It is also used to help ensure proper upgrades, so it is recommended that it
 not be removed.

rick@rick-laptop:~$ aptitude show gnome
Package: gnome
State: not installed
Version: 1:2.28+1ubuntu3
Priority: optional
Section: universe/gnome
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 57.3k
Depends: gnome-desktop-environment (>= 1:2.28+1ubuntu3), gdm-themes | gdm (>=
         2.26), gnome-themes-extras, gnome-games (>= 1:2.28),
         libpam-gnome-keyring (>= 2.28), gstreamer0.10-plugins-ugly (>=
         0.10.12), gstreamer0.10-ffmpeg (>= 0.10.9), rhythmbox (>= 0.12.5) |
         banshee (>= 1.5), synaptic (>= 0.62), system-config-printer-gnome (>=
         1.0.0), totem-mozilla, swfdec-mozilla, epiphany-extensions,
         gedit-plugins, evolution-plugins (>= 2.28), evolution-exchange (>=
         2.28) | evolution-mapi (>= 0.28), evolution-webcal (>= 2.28),
         software-center | gnome-app-install, transmission-gtk, arj,
         avahi-daemon, tomboy (>= 1.0) | gnote
Recommends: gnome-games-extra-data (>= 2.28), network-manager-gnome (>= 0.7),
            gnome-office (= 1:2.28+1ubuntu3), update-notifier, gparted, grdc,
            gthumb, liferea | evolution-rss | blam, menu-xdg, gdebi, hardinfo
Suggests: gnome-dbg, openoffice.org-gnome, openoffice.org-evolution
Conflicts: gnome-cups-manager
Description: The GNOME Desktop Environment, with extra components
 This is the GNOME Desktop environment, an intuitive and attractive desktop,
 with extra components. 
 
 This package depends on the standard distribution of the GNOME desktop
 environment, plus a complete range of plugins and other applications
 integrating with GNOME and Debian, providing the best possible environment to
 date.

rick@rick-laptop:~$ 

```

---

### Post by mcduck on 2010-10-01
> **TNT1 said:**
> I was in software center just now, and I see "The GNOME desktop environment" is not installed... So... what am I using then? How do I find out?

That actually makes sense, as Ubuntu isn't really using the default setup of Gnome.

Most likely that package would give you everything that's included on default Gnome desktop, as opposed to what the default Ubuntu desktop includes.

For example Gnome uses Epiphany as it's browser instead of Firefox that's included on Ubuntu desktop, and Abiword & Gnumeric as opposed to OpenOffice.

---

### Post by TNT1 on 2010-10-04
> **mcduck said:**
> That actually makes sense, as Ubuntu isn't really using the default setup of Gnome.

Most likely that package would give you everything that's included on default Gnome desktop, as opposed to what the default Ubuntu desktop includes.

For example Gnome uses Epiphany as it's browser instead of Firefox that's included on Ubuntu desktop, and Abiword & Gnumeric as opposed to OpenOffice.

Ah, right. I am new to Gnome, and didn't realise this. Thanks.

---

### Post by TNT1 on 2010-10-04
So is there any reason/benefit to install this enhanced version of Gnome from SC?

---

### Post by 3Miro on 2010-10-04
There are a number of packages that are considered "meta" packages. They don't install anything on their own, but rather they pull a whole bunch of dependencies. For many of those, you can just remove them afterwards. If you try to install the package, it will probably have no effect on your system or whatsoever.

---

