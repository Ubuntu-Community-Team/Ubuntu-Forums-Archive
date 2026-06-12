---
title: "removing empathy sets up autoremove to remove almost everything"
date: 2011-03-07
forum: Desktop Environments
---

### Post by Lucradia on 2011-03-07
Basically, after installing **gnome-desktop-environment**, and then removing empathy (as I don't like it, and don't want to see it in my menu, don't want it taking up space, etc) results in all of the below packages queued for autoremove:

```
python-libproxy python-evolution ekiga espeak libevolution libgnome-bluetooth8 gnome-js-common gcalctool telepathy-logger python-gnomedesktop libopal3.6.8 gnome-accessibility gnome-backgrounds libpth20 libfolks0 libbrlapi0.5 gir1.0-json-glib-1.0 gnome-mahjongg telepathy-gabble gnome-search-tool aisleriot gtali baobab libgtkhtml-editor0 gir1.0-gconf-2.0 glchess libgtk-vnc-1.0-0 pkg-config libbrasero-media1 libnet-dbus-perl gtk2-engines hamster-applet genisoimage libkpathsea5 libevdocument3 gnome-games-common esound-clients libsrtp0 gnome-system-log gucharmap libseed0 libdiscid0 gnome-games gir1.0-clutter-gtk-0.10 obexd-client evolution-plugins cheese libtie-ixhash-perl evolution libspectre1 gnobots2 lzma gnome-disk-utility python-pyatspi python-louis liblouis-data gnome-mag libburn4 libpst4 telepathy-haze libtelepathy-logger1 libnm-util1 bogofilter-bdb libtelepathy-farsight0 empathy-common python-speechd libevview3 libcheese-gtk18 libpolkit-gtk-1-0 libestools2.0 gnome-sudoku lightsoff libboost-date-time1.42.0 guile-1.8-libs seahorse xscreensaver-data libgdict-1.0-6 whois libdotconf1.0 gvfs-bin vinagre alsa-oss evolution-common seed telepathy-salut bluez gir1.0-clutter-1.0 evolution-webcal gnibbles libfolks-telepathy0 libgtkhtml-editor-common festlex-cmu gnome-nettool dasher gnome-screenshot libnss-mdns libportaudio2 gir1.0-gdkpixbuf-2.0 gnome-utils libavahi-core7 gconf-editor gnome-accessibility-themes libcryptui0 libgdu-gtk0 libgnome-mag2 libgail-gnome-module gnome-orca libclutter-gtk-0.10-0 python-glade2 telepathy-butterfly gnash-common python-brlapi swell-foop gnome-system-tools bogofilter-common libt1-5 festvox-kallpc16k gnotski deskbar-applet libesd0 liblouis2 libavahi-ui0 python-gtkglext1 dasher-data oss-compat libgtkglext1 gnome-themes-selected gok speech-dispatcher libgtkhtml3.14-19 libtelepathy-glib0 espeak-data libnm-glib2 gnome-bluetooth gnome-user-share gconf-defaults-service at-spi seahorse-plugins libpoppler7 libclutter-1.0-0 evince-common python-telepathy cheese-common libboost-thread1.42.0 wodim sound-juicer vino gir1.0-gstreamer-0.10 libneon27-gnutls gir1.0-gtk-2.0 gir1.0-freedesktop libdjvulibre21 libpoppler-glib5 evince bogofilter iagno desktop-base python-rsvg glines gir1.0-pango-1.0 libspeechd2 esound-common libgail-common libespeak1 nautilus-sendto gnome-utils-common gnome-dictionary dmz-cursor-theme libgnome-speech7 libpt2.6.7 libdaemon0 gtk2-engines-pixbuf gnash gnome-screensaver gnotravex brasero-cdrkit libnl1 gnect avahi-daemon libmission-control-plugins0 brasero-common liboobs-1-5 quadrapassel libatspi1.0-0 libxml-xpath-perl festival libgpgme11 python-farsight libmusicbrainz3-6 python-papyon gstreamer0.10-tools python-wnck brasero festlex-poslex libisofs6 dvd+rw-tools libgsl0ldbl gir1.0-atk-1.0 libdjvulibre-text libavahi-gobject0 system-tools-backends gnome-themes freeglut3 python-crypto libxml-twig-perl swfdec-gnome nautilus-sendto-empathy file-roller telepathy-mission-control-5 gnome-netstatus-applet python-opengl gnomine libaudiofile0
```

---

### Post by Lucradia on 2011-03-09
bumpify

---

### Post by Krytarik on 2011-03-09
OMG, this is great! ;-)  It seems like those are *all* packages of the gnome-desktop-environment. Of course, some of them are clearly associated to Empathy but most of them are not.

Try the following (I can't check it currently, because I don't have autoremovable packages as of now): open Synaptic, filter those packages via the "Status" filter at the left side, click one package and check the available options, may be just "Installation". Then I would try to just remove those packages which are clearly associated to Empathy, at least those with a corresponding name.

---

