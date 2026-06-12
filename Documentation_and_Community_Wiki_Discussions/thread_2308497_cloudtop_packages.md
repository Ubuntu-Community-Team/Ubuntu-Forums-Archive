---
title: "cloudtop packages"
date: 2016-01-03
forum: Documentation and Community Wiki Discussions
---

### Post by Haplo164 on 2016-01-03
While installing ubuntu server I decided, on a whim to install the ubuntu-mate-cloudtop package. The thing is I can't seem to find out anything about them. When I installed them I was under the impression that they were used for a browser based desktop but I have no idea how to use them. Any info would be appreciated.

---

### Post by ian-weisser on 2016-01-03
It's a metapackage. It contains no software itself, but merely pulls in a bunch of related dependencies.
It is *not* a browser-based desktop, but a reduced MATE-based desktop for terminal servers...though still with alsa, cups, and libreoffice.

```
$ apt-cache show ubuntu-mate-cloudtop 

Package: ubuntu-mate-cloudtop
Priority: optional
Section: universe/metapackages
Installed-Size: 12
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: ubuntu-mate-meta
Version: 1.137
Depends: alsa-base, alsa-utils, anacron, apport, apport-gtk, apport-symptoms, bc, ca-certificates, fonts-dejavu-core, fonts-freefont-ttf, foomatic-db-compressed-ppds, genisoimage, ghostscript-x, hexchat, inputattach, libpam-systemd, libpurple-bin, libreoffice-avmedia-backend-gstreamer, libreoffice-calc, libreoffice-gnome, libreoffice-impress, libreoffice-math, libreoffice-ogltrans, libreoffice-pdfimport, libreoffice-style-human, libreoffice-writer, libsasl2-modules, memtest86+, openprinting-ppds, pidgin, pidgin-libnotify, pidgin-otr, printer-driver-pnm2ppa, rfkill, seahorse, thunderbird, ubuntu-drivers-common, ubuntu-mate-libreoffice-draw-icons, ubuntu-mate-libreoffice-math-icons, unzip, vlc, whoopsie, wireless-tools, wpasupplicant, xkb-data, xorg, zip
Recommends: acpi-support, avahi-daemon, bluez, bluez-cups, cups, cups-bsd, cups-client, cups-filters, fonts-guru, fonts-kacst-one, fonts-khmeros-core, fonts-lao, fonts-lklug-sinhala, fonts-sil-abyssinica, fonts-sil-padauk, fonts-takao-pgothic, fonts-thai-tlwg, fonts-tibetan-machine, hplip, kerneloops-daemon, laptop-detect, libnss-mdns, pcmciautils, policykit-desktop-privileges, printer-driver-brlaser, printer-driver-c2esp, printer-driver-foo2zjs, printer-driver-min12xxw, printer-driver-ptouch, printer-driver-pxljr, printer-driver-sag-gdi, printer-driver-splix, ttf-ancient-fonts-symbola, ttf-indic-fonts-core, ttf-ubuntu-font-family
Filename: pool/universe/u/ubuntu-mate-meta/ubuntu-mate-cloudtop_1.137_amd64.deb
Size: 3078
MD5sum: f98a91b2dd38d5c831fc03353e5d4b1a
SHA1: 1effbb50d7d161fa477b8d2e4132fc8c92a0e489
SHA256: 4944fc5928f355aa7f813519e5ad233c940505ca775a8439882d4088d69300f3
Description-en: Ubuntu MATE - reduced desktop for terminal server deployment
 This package is the Ubuntu MATE desktop environment for cloudtop deployments.
 .
 It is safe to remove this package if some of these packages are not desired.
Description-md5: 8b52b6ede17990fae475077bb557afb7
Homepage: https://launchpad.net/ubuntu-mate/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Task: ubuntu-mate-cloudtop


```

---

### Post by Haplo164 on 2016-01-03
Thanks, that will still be useful for me, but the cloudtop name still throws me off. Much appreciated.

---

