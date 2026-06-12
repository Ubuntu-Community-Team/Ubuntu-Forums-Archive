---
title: "Help me get my gnome back!!!"
date: 2011-03-08
forum: Desktop Environments
---

### Post by wtj104 on 2011-03-08
Ubuntu 10.04
Installed updates and rebooted the other day.  Everything is fine to the login page.  After I enter my password, a blank default ubuntu desktop wallpaper is shown with a moveable mouse cursor, but nothing else.  If left alone, the screensaver will kick on eventually.  Same thing after unlocking from the screensaver.

This happens in both gnome and failsafe gnome.  I can login to xterm, and I can also ctrl+alt+F1 from the blank desktop to get a CLI.  I can also access it via SSH.  Other background tasks seem to be working as well (MythTV, etc.)

Some things I tried to no avail (not necessarily in this order)
1. rm -rf .gnome .gnome2 .gconf .gconfd .metacity
2. login as different users (same problem)
3. create a new user (same problem)
4. apt-get install --reinstall ubuntu-desktop
5. apg-get remove --purge gnome-desktop-environment
   apt-get install gnome-desktop-environment
6. apt-get remove compiz, apt-get remove compiz-core
7. dpkg --configure -a
8. apt-get install ubuntu-desktop
9. apt-get -f install

Finally i installed kubuntu-desktop just to get a working desktop environment.  KDE works fine.

Where do I go from here to troubleshoot?

---

### Post by neoroses on 2011-03-08
this is just a quick thought as i encounterd somthing similar. When you get to the login screen click the ubuntu logo (if your are on 10.04 or higher) and the text that says somthing like your user name or the session and it will change to ubuntu-desktop or gnome. then try logging in....it may be nothing to do with it as it may be a more serious problem. But give it ago.

---

### Post by kellemes on 2011-03-08
Have you tried restarting the gnome-panel?
```
gnome-panel &
```

---

### Post by wtj104 on 2011-03-08
> **neoroses said:**
> this is just a quick thought as i encounterd somthing similar. When you get to the login screen click the ubuntu logo (if your are on 10.04 or higher) and the text that says somthing like your user name or the session and it will change to ubuntu-desktop or gnome. then try logging in....it may be nothing to do with it as it may be a more serious problem. But give it ago.

Clicking on the hostname under the ubuntu logo cycles between the hostname and the version #.  Logging in while in either state results in the same problem.

---

### Post by wtj104 on 2011-03-08
> **kellemes said:**
> Have you tried restarting the gnome-panel?
```
gnome-panel &
```

Command is accepted and provides the new process id.  No effect on the gnome environment however.

---

### Post by garvinrick4 on 2011-03-08
These 3 are all installed:
```
rick@rick-HP:~$ aptitude show xorg
Package: xorg                            
State: installed
Automatically installed: no
Version: 1:7.6~3ubuntu11
Priority: optional
Section: x11
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Uncompressed Size: 45.1 k
Depends: xserver-xorg, libgl1-mesa-glx | libgl1, libgl1-mesa-dri, libglu1-mesa,
         xfonts-base (>= 1:1.0.0-1), x11-apps, x11-session-utils, x11-utils,
         x11-xfs-utils, x11-xkb-utils, x11-xserver-utils, xauth, xinit,
         xfonts-utils, xkb-data, xorg-docs-core, xterm | x-terminal-emulator,
         x11-common, xinput
Recommends: xfonts-scalable (>= 1:1.0.0-1)
Suggests: xorg-docs, xfonts-100dpi (>= 1:1.0.0-1), xfonts-75dpi (>= 1:1.0.0-1)
Provides: x-window-system, x-window-system-core
Description: X.Org X Window System
 This metapackage provides the components for a standalone workstation running
 the X Window System.  It provides the X libraries, an X server, a set of fonts,
 and a group of basic X clients and utilities. 
 
 Higher level metapackages, such as those for desktop environments, can depend
 on this package and simplify their dependencies. 
 
 It should be noted that a package providing x-window-manager should also be
 installed to ensure a comfortable X experience.

rick@rick-HP:~$ aptitude show gdm
Package: gdm                             
State: installed
Automatically installed: no
Version: 2.32.0-0ubuntu9
Priority: optional
Section: gnome
Maintainer: Sebastien Bacher <seb128@ubuntu.com>
Uncompressed Size: 2,462 k
Depends: libc6 (>= 2.4), libcairo2 (>= 1.2.4), libcanberra-gtk0 (>= 0.4),
         libcanberra0 (>= 0.2), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>=
         0.88), libfontconfig1 (>= 2.8.0), libgconf2-4 (>= 2.31.1),
         libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.24.0), libgtk2.0-0
         (>= 2.23.90-0ubuntu4), libpam0g (>= 0.99.7.1), libpango1.0-0 (>=
         1.14.0), libpolkit-gobject-1-0 (>= 0.94), libupower-glib1 (>= 0.9.0),
         libwrap0 (>= 7.6-4~), libx11-6, libxau6, libxdmcp6, libxklavier16 (>=
         5.0), debconf (>= 0.5) | debconf-2.0, gconf2 (>= 2.28.1-2),
         upstart-job, adduser, libpam-modules (>= 0.72-1), libpam-runtime (>=
         0.76-13.1), gnome-session-bin, kbd | console-tools, udev (>= 149-2)
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

rick@rick-HP:~$ aptitude show ubuntu-desktop
Package: ubuntu-desktop                  
State: installed
Automatically installed: no
Version: 1.217
Priority: optional
Section: metapackages
Maintainer: Matt Zimmerman <mdz@ubuntu.com>
Uncompressed Size: 61.4 k
Depends: alacarte, alsa-base, alsa-utils, anacron, baobab, bc, ca-certificates,
         checkbox-gtk, cups, cups-bsd, cups-client, dc, desktop-file-utils,
         doc-base, eog, evince, file-roller, foomatic-db-compressed-ppds,
         foomatic-filters, gcalctool, gconf-editor, gdm, gedit, genisoimage,
         ghostscript-x, gnome-about, gnome-applets, gnome-control-center,
         gnome-icon-theme, gnome-media, gnome-menus, gnome-nettool, gnome-panel,
         gnome-power-manager, gnome-screenshot, gnome-search-tool,
         gnome-session, gnome-session-canberra, gnome-system-log,
         gnome-system-monitor, gnome-system-tools, gnome-terminal,
         gnome-themes-selected, gnome-themes-ubuntu, gstreamer0.10-alsa,
         gstreamer0.10-plugins-base-apps, gstreamer0.10-pulseaudio,
         gtk2-engines, gtk2-engines-pixbuf, gucharmap, indicator-applet-session,
         inputattach, language-selector-gnome, launchpad-integration, lftp,
         libgd2-xpm, libpam-ck-connector, libsasl2-modules, libsdl1.2debian,
         libsdl1.2debian-pulseaudio, libxp6, metacity, nautilus,
         nautilus-sendto, notify-osd, nvidia-common, openprinting-ppds, pnm2ppa,
         pulseaudio, pulseaudio-esound-compat, rarian-compat,
         screensaver-default-images, seahorse, smbclient, software-center,
         software-properties-gtk, ssh-askpass-gnome, synaptic,
         system-config-printer-gnome, ttf-dejavu-core, ttf-freefont,
         ubuntu-artwork, ubuntu-extras-keyring, ubuntu-sounds, unity, unzip,
         update-manager, update-notifier, wireless-tools, wpasupplicant,
         x-ttcidfont-conf, xdg-user-dirs, xdg-user-dirs-gtk, xkb-data, xorg,
         xscreensaver-data, xscreensaver-gl, xterm, yelp, zenity, zip
Recommends: acpi-support, aisleriot, app-install-data-partner, apport-gtk,
            avahi-autoipd, avahi-daemon, banshee,
            banshee-extension-ubuntuonemusicstore, bluez, bluez-alsa,
            bluez-cups, bluez-gstreamer, branding-ubuntu, brasero, brltty,
            brltty-x11, compiz, computer-janitor-gtk, empathy, espeak,
            evolution, evolution-exchange, evolution-indicator,
            evolution-plugins, evolution-webcal, example-content, firefox,
            firefox-gnome-support, foo2zjs, gbrainy, gcc, gdm-guest-session,
            ginn, gnome-accessibility-themes, gnome-bluetooth,
            gnome-codec-install, gnome-disk-utility, gnome-mag, gnome-mahjongg,
            gnome-orca, gnome-screensaver, gnome-sudoku, gnome-user-guide,
            gnomine, gvfs-fuse, hplip, ibus, ibus-gtk, ibus-pinyin,
            ibus-pinyin-db-android, ibus-table, im-switch, indicator-messages,
            jockey-gtk, kerneloops-daemon, laptop-detect, libgail-gnome-module,
            libnss-mdns, libpam-gnome-keyring, libreoffice-calc,
            libreoffice-gnome, libreoffice-help-en-us, libreoffice-impress,
            libreoffice-math, libreoffice-style-human, libreoffice-writer,
            libwmf0.2-7-gtk, linux-headers-generic, make, min12xxw, mousetweaks,
            nautilus-share, network-manager-gnome, network-manager-pptp,
            network-manager-pptp-gnome, onboard, pcmciautils, pitivi,
            plymouth-theme-ubuntu-logo, policykit-desktop-privileges,
            pulseaudio-module-bluetooth, pulseaudio-module-gconf,
            pulseaudio-module-x11, pxljr, shotwell, simple-scan,
            speech-dispatcher, splix, telepathy-idle, tomboy, totem,
            totem-mozilla, transmission-gtk, tsclient, ttf-indic-fonts-core,
            ttf-kacst-one, ttf-khmeros-core, ttf-lao, ttf-liberation,
            ttf-punjabi-fonts, ttf-takao-pgothic, ttf-thai-tlwg,
            ttf-ubuntu-font-family, ttf-unfonts-core, ttf-wqy-microhei, ubufox,
            ubuntu-docs, ubuntuone-client-gnome, usb-creator-gtk, vinagre, vino,
            xcursor-themes, xdg-utils
Description: The Ubuntu desktop system
 This package depends on all of the packages in the Ubuntu desktop system 
 
 It is also used to help ensure proper upgrades, so it is recommended that it
 not be removed.

rick@rick-HP:~$ 

```

---

### Post by wtj104 on 2011-03-08
> **garvinrick4 said:**
> These 3 are all installed:

They appear to be installed:
```
bill@desktop:~$ aptitude show xorg
Package: xorg
State: installed
Automatically installed: no
Version: 1:7.5+5ubuntu1
Priority: optional
Section: x11
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Uncompressed Size: 36.9k
Depends: xserver-xorg, libgl1-mesa-glx | libgl1, libgl1-mesa-dri, libglu1-mesa,
         xfonts-base (>= 1:1.0.0-1), xfonts-100dpi (>= 1:1.0.0-1), xfonts-75dpi
         (>= 1:1.0.0-1), x11-apps, x11-session-utils, x11-utils, x11-xfs-utils,
         x11-xkb-utils, x11-xserver-utils, xauth, xinit, xfonts-utils, xkb-data,
         xorg-docs-core, xterm | x-terminal-emulator, x11-common, xinput
Recommends: xfonts-scalable (>= 1:1.0.0-1)
Suggests: xorg-docs
Provides: x-window-system, x-window-system-core
Description: X.Org X Window System
 This metapackage provides the components for a standalone workstation running
 the X Window System.  It provides the X libraries, an X server, a set of fonts,
 and a group of basic X clients and utilities. 
 
 Higher level metapackages, such as those for desktop environments, can depend
 on this package and simplify their dependencies. 
 
 It should be noted that a package providing x-window-manager should also be
 installed to ensure a comfortable X experience.

bill@desktop:~$ aptitude show gdm
Package: gdm
State: installed
Automatically installed: no
Version: 2.30.2.is.2.30.0-0ubuntu5
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

bill@desktop:~$ aptitude show ubuntu-desktop
Package: ubuntu-desktop
State: installed
Automatically installed: no
Version: 1.197
Priority: optional
Section: metapackages
Maintainer: Matt Zimmerman <mdz@ubuntu.com>
Uncompressed Size: 61.4k
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

bill@desktop:~$ aptitude show ubuntu-desktop
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

bill@desktop:~$ 


```

---

### Post by Krytarik on 2011-03-08
Do you get a terminal in there, when you press Cltr+Alt+t ?

If so, try those commands:
```
killall gnome-panel
killall nautilus
```

---

### Post by wtj104 on 2011-03-08
> **Krytarik said:**
> Do you get a terminal in there, when you press Cltr+Alt+t ?

If so, try those commands:
```
killall gnome-panel
killall nautilus
```

No terminal with ctrl+alt+t from my blank gnome thing.

The only things that I know I can do is wait for a screensaver, move the mouse pointer around, ctrl+alt+F1 for a CLI, or get back to the login screen by restarting gdm (either from the CLI or via ssh).

---

### Post by wtj104 on 2011-03-08
Would I be able to completely wipe out any remnants of gnome, perhaps using this:
[http://www.psychocats.net/ubuntu/purekdelucid](http://www.psychocats.net/ubuntu/purekdelucid)

and then ```
sudo apt-get install ubuntu-desktop
``` to reinstall gnome?

---

### Post by Krytarik on 2011-03-08
Sure, try it, but of course spare the last command in the line!

**EDIT:** And I would also use "purge" instead of "remove".

---

### Post by neoroses on 2011-03-09
> **wtj104 said:**
> Clicking on the hostname under the ubuntu logo cycles between the hostname and the version #.  Logging in while in either state results in the same problem.

Yea fair enough lol. :(

---

### Post by wtj104 on 2011-03-10
> **Krytarik said:**
> Sure, try it, but of course spare the last command in the line!

**EDIT:** And I would also use "purge" instead of "remove".

Well, kinda wussed out on trying that...  I installed xubuntu-desktop instead.  That works fine as well and is a lot more like gnome than KDE, so I'm somewhat happy for the moment.  

I still have no idea what is going on with the gnome sessions though.  FWIW lots of gnome stuff works fine in xfce (nautilus, gnome terminal, etc).

---

### Post by Krytarik on 2011-03-10
Sure, XFCE is cool, I also have it installed. I really don't like KDE, I used at my first install of a Linux distro, Redhat or Fedora, some eight years ago. At the next version of Fedora it had an issue with the mouse cursor, so I dropped it in favor of Gnome. I saw it again some years later when I installed Suse at a try-out-machine at work, and I again didn't like it. I can't even specifically say what it is, it simply feels kind of un-linux-like if that makes sense.

---

