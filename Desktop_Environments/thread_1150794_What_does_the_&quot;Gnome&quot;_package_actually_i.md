---
title: "What does the &quot;Gnome&quot; package actually install?"
date: 2009-05-06
forum: Desktop Environments
---

### Post by mabtifro2 on 2009-05-06
If Ubuntu already uses Gnome, what is the purpose of the Gnome package found in synaptic??

---

### Post by Headbanger2510 on 2009-05-06
It just installs more gnome apps that aren`t installed in ubuntu by default.

---

### Post by mcduck on 2009-05-06
I hsven't tried it myself, but I would assume that it install the default Gnome setup (as opposed to ubuntu-desktop, which installs Ubuntu's own setup for Gnome).

This would mean all Gnome's default apps (like Epiphany for web browser instead of Firefox which Ubuntu uses) and gnome's default themes. Mostly usefull for those people who are using some other desktop or just the CLI interface and want to add the default Gnome instead of Ubuntu's Gnome setup.

As you already have the ubuntu-desktop installed the gnome package will of course not remove anything you already have, so in this case it would just add the things that are part of default gnome setup but not included in Ubuntu's default setup.

---

### Post by glotz on 2009-05-06
```
$ apt-cache show gnome
Package: gnome
Priority: optional
Section: gnome
Installed-Size: 20
Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Architecture: all
Source: meta-gnome2
Version: 1:2.22.2~5
Depends: gnome-desktop-environment (= 1:2.22.2~5), gdm-themes, gnome-themes-extras, gnome-games (>= 1:2.22.2), libpam-gnome-keyring (>= 2.22.2), gstreamer0.10-plugins-ugly (>= 0.10.8), gstreamer0.10-ffmpeg (>= 0.10.4), rhythmbox (>= 0.11.5), synaptic (>= 0.62), system-config-printer (>= 1.0.0), totem-mozilla, swfdec-mozilla, epiphany-extensions, evolution-plugins (>= 2.22.2), evolution-exchange (>= 2.22.2), evolution-webcal (>= 2.21.92), gnome-spell (>= 1.0.4), serpentine, gnome-app-install, transmission-gtk, bluez-gnome, gnome-vfs-obexftp, arj, p7zip, avahi-daemon
Recommends: gnome-games-extra-data (>= 2.22.0), gnome-office (= 1:2.22.2~5), tomboy (>= 0.10.2), update-notifier, empathy | pidgin, gparted, tsclient, network-manager-gnome, hal-cups-utils, gthumb, liferea | blam, menu-xdg, gdebi, hardinfo
Suggests: gnome-dbg, openoffice.org-gnome, openoffice.org-evolution
Conflicts: gnome-cups-manager
Filename: pool/main/m/meta-gnome2/gnome_2.22.2~5_all.deb
Size: 14660
MD5sum: c014b029f9741a69b474fa7d88248993
SHA1: 0f5ded123e9e8cd9371d199e91cc0c9e9f12645d
SHA256: aa62d5553b8445688013b4549c1f25c94f76fb8ef0d24b5fba0d3db3ca90f183
Description: The GNOME Desktop Environment, with extra components
 This is the GNOME Desktop environment, an intuitive and attractive
 desktop, with extra components.
 .
 This package depends on the standard distribution of the GNOME desktop
 environment, plus a complete range of plugins and other applications
 integrating with GNOME and Debian, providing the best possible
 environment to date.
Tag: interface::x11, role::metapackage, special::meta, suite::gnome, uitoolkit::gtk, use::gameplaying
Task: gnome-desktop
```

---

