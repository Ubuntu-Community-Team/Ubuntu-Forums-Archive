---
title: "Fluxbox graphics too &quot;big&quot;!"
date: 2007-01-16
forum: Desktop Environments
---

### Post by DrSnuggles on 2007-01-16
Hello,

I have a problem with an Ubuntu-serverinstall w/ Fluxbox. Everything works fine, except from the graphics being too "big"! The resolution is fine (1024x768 on my laptop monitor) but everything else is too big. It's hard to explain, but heres a screenshot:

[http://www.inn.se/upload/privat/screenshot.jpg](http://www.inn.se/upload/privat/screenshot.jpg)

Hot can I solve this problem?

---

### Post by hikaricore on 2007-01-16
That's actually pretty standard for 1024x768, try another theme maybe?  I find the theme called Twice very useable at low resolutions like the one you're using.

---

### Post by DrSnuggles on 2007-01-16
I had a Dapper install w/ Fluxbox on the same computer and just made a fresh install (edgy). I hadn't made any changes to the theme on the old setup, and it was much smaller. I've tried Twice, but in my opinion it's still too big!

---

### Post by hikaricore on 2007-01-16
Are you sure it was in 1024x768 mode previously?  There's no other reason I can imagine that would cause this.

---

### Post by DrSnuggles on 2007-01-16
Yepp, the monitor is only capable of 1024x768.

I can't imagine a reason either.

Another interesting thing...:
Setup 1: Edgy server i386 install, apt-get install xubuntu-desktop fluxbox
Setup 2: Edgy server i386 install, apt-get install x-window-system-core aterm gksu fluxbox

Setup 1 gives me the "correct" size.
Setup 2 gives me this big crap. The problem is that I don't want to have XFCE installed when I only use Fluxbox :)

---

### Post by Pobega on 2007-01-16
Then don't install xubuntu-desktop; Also, I've noticed that some themes seem too large in Fluxbox, but I think it's all theme dependant. Try to find one that works for you.

---

### Post by DrSnuggles on 2007-01-16
But... When I have xubuntu-desktop installed it all looks fine. When I don't have it installed, it's too big!

---

### Post by Pobega on 2007-01-16
Well, when I downloaded 915resolution my widescreen resolution began working, maybe you need a package like that?

> pobega@ackbar:~$ aptitude show xubuntu-desktop 
Package: xubuntu-desktop
New: yes
State: not installed
Version: 2.23
Priority: optional
Section: metapackages
Maintainer: Jani Monoses <jani@ubuntu.com>
Uncompressed Size: 36.9k
Depends: abiword, abiword-plugins, acpi, acpi-support, acpid, anacron, apmd,
         apport-gtk, avahi-daemon, bc, cdparanoia, cdrecord, cupsys, cupsys-bsd,
         cupsys-client, cupsys-driver-gutenprint, dbus-1-utils, dc, doc-base,
         dvd+rw-tools, evince-gtk | evince, firefox, foo2zjs, foomatic-db,
         foomatic-db-engine, foomatic-db-hpijs, foomatic-filters, gaim,
         gcalctool-gtk | gcalctool, gdebi, gdm, gimp, gimp-print,
         gnome-app-install, gnumeric-gtk | gnumeric, gqview, gs-esp,
         gtk2-engines-ubuntulooks, gtk2-engines-xfce, gxine, hal, hotkey-setup,
         landscape-client, language-selector, lftp, libgl1-mesa-glx,
         libglib2.0-data, libglut3, libgoffice-gtk-0-3, libjpeg-progs,
         libpam-foreground, libsasl2-modules, libstdc++5, libxp6, min12xxw,
         mkisofs, mousepad, mozilla-thunderbird, onboard, orage, pnm2ppa,
         powermanagement-interface, python-exo, readahead, screen, scrollkeeper,
         slocate, smbclient, synaptic, system-config-printer, tango-icon-theme,
         tango-icon-theme-common, thunar, thunar-archive-plugin,
         thunar-media-tags-plugin, ttf-bitstream-vera, ttf-dejavu, ttf-freefont,
         ubuntu-artwork, unzip, update-manager, usplash, vim-runtime, wvdial,
         x-ttcidfont-conf, xarchiver, xfburn, xfce4-appfinder,
         xfce4-battery-plugin, xfce4-clipman-plugin, xfce4-cpugraph-plugin,
         xfce4-dict-plugin, xfce4-fsguard-plugin, xfce4-mailwatch-plugin,
         xfce4-mcs-plugins, xfce4-mixer-alsa, xfce4-mount-plugin,
         xfce4-netload-plugin, xfce4-notes-plugin, xfce4-panel,
         xfce4-quicklauncher-plugin, xfce4-screenshooter-plugin, xfce4-session,
         xfce4-smartbookmark-plugin, xfce4-systemload-plugin, xfce4-taskmanager,
         xfce4-terminal, xfce4-utils, xfce4-verve-plugin, xfce4-weather-plugin,
         xfce4-xkb-plugin, xfdesktop4, xfprint4, xfwm4, xfwm4-themes,
         xkeyboard-config, xorg, xscreensaver, xscreensaver-data,
         xscreensaver-gl, xterm, xubuntu-artwork-usplash,
         xubuntu-default-settings, xubuntu-docs, xubuntu-system-tools |
         gnome-system-tools, zip
Recommends: example-content, gcc, gnome-accessibility-themes, hplip,
            linux-headers-generic, make, powernowd, scim, scim-anthy,
            scim-chewing, scim-gtk2-immodule, scim-hangul, scim-pinyin,
            ttf-arabeyes, ttf-arphic-ukai, ttf-arphic-uming, ttf-baekmuk,
            ttf-gentium, ttf-indic-fonts, ttf-kochi-gothic, ttf-kochi-mincho,
            ttf-lao, ttf-malayalam-fonts, ttf-mgopen, ttf-thai-tlwg,
            xcursor-themes
Description: Xubuntu desktop system
 This package depends on all of the packages in the Xubuntu desktop system 
 
 It is safe to remove this package if some of the desktop system packages are
 not desired.

Maybe something in it's dependencies are making it look better? Try installing some packages individually and see what happens.

---

### Post by kerry_s on 2007-01-16
Maybe try manually setting the DPI to something like 75 x75. On mine i edit my /etc/X11/xorg.conf, but i use 100 X 100. Here's how it looks->

Section "Monitor"
	Identifier	"A70"
	Option		"DPMS"
        Option   	"UseEdidDpi"   "FALSE"
        Option   	"DPI"   "100 x 100"
EndSection

---

