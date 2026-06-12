---
title: "Dependcy"
date: 2006-01-11
forum: General Help
---

### Post by awakatanka on 2006-01-11
I don't get the dependcy thing, i'm looking in my package list what i have installed and want to uninstall things that i don't use.

example : Fortune-mod , its a prg that makes furtune coockies, something that i don't use its under games in kpackage. 

Depends on : 

libc6 (>= 2.3.4-1), librecode0 (>= 3.6), fortunes-min | fortune-cookie-db

ok i want to uninstall now it says that its going to uninstall :

Fortune-mod
Fortune-min
**kubuntu-desktop** why?

Why it wants to uninstall my kubuntu-desktop?

Its a stupid little prg nobody use but it wan't to messing up my whole desktop.

Can't it just uninstall those 2 stupid files and leave my desktop alone?

Plz someone let me understand that depency hell.

There more packages that want to uninstall more then there own prg.

edit :
Cleaned out some words now i'm calmed down ;)

---

### Post by Thirsteh on 2006-01-11
Calm down. Kubuntu-desktop is a "dummy" package which only purpose it to install all the packages that come with Kubuntu with it -- Removing it will have no impact on your system whatsoever. It simply wants to remove that package because it was the one that brought "Fortune" into your system. You can safely click yes.

By the way, Fortune isn't stupid, it's rather brilliant actually ;).

Minor update: Unless you're running out of disk space, there's no reason whatsoever to remove applications like fortune in Linux. They don't slow down your computer or do anything else that windows tends to do. There's no reason whatsoever to remove fortune, it's like 500kb tops? Yes, of course, if they discover a major security flaw that allows anyone to gain superuser access to your computer through the fortune cookie, but somehow I doubt that.

---

### Post by awakatanka on 2006-01-11
[QUOTE=Thirsteh]Calm down. Kubuntu-desktop is a "dummy" package which only purpose it to install all the packages that come with Kubuntu with it -- Removing it will have no impact on your system whatsoever. It simply wants to remove that package because it was the one that brought "Fortune" into your system. You can safely click yes.

By the way, Fortune isn't stupid, it's rather brilliant actually ;).

Minor update: Unless you're running out of disk space, there's no reason whatsoever to remove applications like fortune in Linux. They don't slow down your computer or do anything else that windows tends to do. There's no reason whatsoever to remove fortune, it's like 500kb tops? Yes, of course, if they discover a major security flaw that allows anyone to gain superuser access to your computer through the fortune cookie, but somehow I doubt that.[/QUOTE]
I'm no running out of space, but if i look at the files it going to uninstall it has all desktop files in it. i'm sure it will uninstall the desktop.

I just want the prg that i don't use not installed,even if it doesn't slow down my pc. I just like a clean system with only the prg i need ;)

```

summary
Kubuntu desktop system
version
0.55
status
install ok installed
group
base
size
36000
description
This package depends on all of the packages in the Kubuntu desktop system . It is safe to remove this package if some of the desktop system packages are not desired.
architecture
i386
depends
acpi, acpi-support, acpid, adept, akode, akregator, amarok, anacron, apmd, ark, arts, bc, bicyclerepair, bluez-cups, bluez-pcmcia-support, bluez-utils, bogofilter, cdparanoia, cdrecord, cupsys, cupsys-bsd, cupsys-client, cupsys-driver-gimpprint, dbus, dc, diveintopython, doc-base, doc-debian, dvd+rw-tools, fetchmail, foomatic-db, foomatic-db-engine, foomatic-db-gimp-print, foomatic-db-hpijs, foomatic-filters, foomatic-filters-ppds, fortune-mod, gs-esp, gstreamer0.8-alsa, gstreamer0.8-audiofile, gstreamer0.8-cdparanoia, gstreamer0.8-dv, gstreamer0.8-dvd, gstreamer0.8-flac, gstreamer0.8-gsm, gstreamer0.8-hermes, gstreamer0.8-jpeg, gstreamer0.8-misc, gstreamer0.8-musepack, gstreamer0.8-oss, gstreamer0.8-plugin-apps, gstreamer0.8-sdl, gstreamer0.8-speex, gstreamer0.8-theora, gstreamer0.8-vorbis, gstreamer0.8-x, gtk2-engines-gtk-qt, gwenview, hal, hotkey-setup, hplip-base, hplip-ppds, irssi-text, ivman, k3b, kaddressbook, kaffeine-gstreamer, kamera, karm, katapult, kate, kaudiocreator, kcontrol, kcron, 
priority
optional
maintainer
Andreas Mueller <amu@ubuntu.com>
source
kubuntu-meta
, readahead, screen, slocate, smbclient, speedcrunch, ttf-arabeyes, ttf-arphic-bkai00mp, ttf-arphic-bsmi00lp, ttf-arphic-gbsn00lp, ttf-arphic-gkai00mp, ttf-baekmuk, ttf-bitstream-vera, ttf-dejavu, ttf-freefont, ttf-indic-fonts, ttf-kochi-gothic, ttf-kochi-mincho, ttf-malayalam-fonts, ttf-mgopen, unzip, usplash, vorbis-tools, wvdial, x-ttcidfont-conf, x-window-system-core, xkeyboard-config, xorg-driver-synaptics, xterm, zip
readahead, screen, slocate, smbclient, speedcrunch, ttf-arabeyes, ttf-arphic-bkai00mp, ttf-arphic-bsmi00lp, ttf-arphic-gbsn00lp, ttf-arphic-gkai00mp, ttf-baekmuk, ttf-bitstream-vera, ttf-dejavu, ttf-freefont, ttf-indic-fonts, ttf-kochi-gothic, ttf-kochi-mincho, ttf-malayalam-fonts, ttf-mgopen, unzip, usplash, vorbis-tools, wvdial, x-ttcidfont-conf, x-window-system-core, xkeyboard-config, xorg-driver-synaptics, xterm, zip
de-guidance, kde-systemsettings, kdeadmin-kfile-plugins, kdebase-kio-plugins, kdebluetooth, kdegraphics-kfile-plugins, kdemultimedia-kappfinder-data, kdemultimedia-kfile-plugins, kdemultimedia-kio-plugins, kdenetwork-filesharing, kdenetwork-kfile-plugins, kdepasswd, kdepim-kio-plugins, kdepim-wizards, kdeprint, kdesktop, kdm, kfind, kghostview, khelpcenter, kicker, kio-apt, kio-locate, klaptopdaemon, klipper, kmail, kmenuedit, kmilo, kmix, knetworkconf, knotes, konq-plugins, konqueror, konqueror-nsplugins, konserve, konsole, kontact, konversation, kooka, kopete, korganizer, kpdf, kpf, kppp, krdc, krfb, krita, kscd, kscreensaver, ksmserver, ksnapshot, ksplash, ksvg, ksysguard, ksystemlog, kubuntu-artwork-usplash, kubuntu-default-settings, kubuntu-docs, kubuntu-konqueror-shortcuts, kuser, kwalletmanager, kwifimanager, kwin, lftp, libgl1-mesa, libglut3, libgstreamer-plugins0.8-0, libgstreamer0.8-0, libsasl2-modules, libxp6, mkisofs, openoffice.org2, openoffice.org2-kde, pmount, pnm2ppa, powermanagement-interfa
e-guidance, kde-systemsettings, kdeadmin-kfile-plugins, kdebase-kio-plugins, kdebluetooth, kdegraphics-kfile-plugins, kdemultimedia-kappfinder-data, kdemultimedia-kfile-plugins, kdemultimedia-kio-plugins, kdenetwork-filesharing, kdenetwork-kfile-plugins, kdepasswd, kdepim-kio-plugins, kdepim-wizards, kdeprint, kdesktop, kdm, kfind, kghostview, khelpcenter, kicker, kio-apt, kio-locate, klaptopdaemon, klipper, kmail, kmenuedit, kmilo, kmix, knetworkconf, knotes, konq-plugins, konqueror, konqueror-nsplugins, konserve, konsole, kontact, konversation, kooka, kopete, korganizer, kpdf, kpf, kppp, krdc, krfb, krita, kscd, kscreensaver, ksmserver, ksnapshot, ksplash, ksvg, ksysguard, ksystemlog, kubuntu-artwork-usplash, kubuntu-default-settings, kubuntu-docs, kubuntu-konqueror-shortcuts, kuser, kwalletmanager, kwifimanager, kwin, lftp, libgl1-mesa, libglut3, libgstreamer-plugins0.8-0, libgstreamer0.8-0, libsasl2-modules, libxp6, mkisofs, openoffice.org2, openoffice.org2-kde, pmount, pnm2ppa, powermanagement-interfa


```I did it before with a other file that also selected the kubuntu-desktop and i had to reinstall the os again.

---

### Post by newuser111 on 2006-01-12
kubuntu-desktop in itself isnt anything important, it just selects all the kde packages selected by the ubuntu team

but you should be able to see what synaptic wants to uninstall if it has selected a lot of KDE apps, then yes it will mess your OS up, if its just removing kubuntu-desktop by itself it cannot ruin your OS

---

