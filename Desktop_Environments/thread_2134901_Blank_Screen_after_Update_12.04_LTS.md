---
title: "Blank Screen after Update 12.04 LTS"
date: 2013-04-12
forum: Desktop Environments
---

### Post by TrevP on 2013-04-12
I just downloaded the latest updates to Xubuntu 12.04 LTS and I get a blank screen and the monitor goes into standby mode. The problem seems to be with the latest kernel update (3.2.0.40). I tried recovery mode and found no apparent problems and on selecting "resume", the system did start, but with the wrong screen resolution. However, on restarting the system, it went back to a blank screen and standby mode.

I have temporarily fixed the problem by reconfiguring Grub to default to booting the previous kernel (3.2.0.39) which works perfectly. I was wondering if anyone else has encountered problems with kernel version 3.2.0.40?

PS - I'm running the 64 bit version of Xubuntu and I'm using the Nouveau open source drivers on an Nvidia 7600 GPU.

---

### Post by Dannox on 2013-04-12
I've been experiencing the same issue after an update to ubuntu 12.04 LTS. Kernel version 3.2.0.39 boots fine from the grub menu, but the new kernel only works in recovery mode at the wrong resolution. My graphics card is an ATI Radeon HD3450 and I'm running the 32bit version.

---

### Post by TrevP on 2013-04-12
It looks like it may be a problem with how the system interacts with the monitor rather than a graphics driver or video card problem (because you seem to be getting the same issues with a different graphics card and operating system). My monitor is a Packard Bell MW19H-AAAD.

---

### Post by Dannox on 2013-04-12
It'd make sense. I'm running it through an RCA Scenium tv in 1024x768 on hdmi stretched to widescreen by the tv. Also- the login screen has the edges chopped off and also when you drop to terminal.

---

### Post by mediajunkie on 2013-04-17
HI,
I've been running 12.04 from day1 it was out. and other than configuration issues here and there, I had no problems. 
But after the last upgrade to kernel version 3.2.0.40 I've had all kind of problems. 

[LIST]
[*]Blank screen at boot (33% of the time) - system completely frozen Only Ctrl. Alt. Prtscr. R E I S I U B can restart the system (or pulling the battery) 
[*]Weird BAD LUN (0,1) ..... error (might not be related but it started after update.
[*]several programs freeze the system (ex. shift prt sc) screen shot... but when selecting the zone, it freezes completely. 
[*]at unexpected moments the system will just freeze.  (running very unstable)  
[*] ....
[/LIST]

Selecting 3.2.0.37 kernel in Grub menu, makes all those problems go away, except of course the kernel modules I had compiled for 3.2.0.40 won't run. .... grrrrrr

So what now?   Upgrading to 13.04 when it is released? .... Would rather stay on LTS version for my production machine, but need fix quick though....
anybody have ideas?

---

### Post by Dannox on 2013-04-21
Made some changes. First, I got a new monitor, an acer h274hl lcd. Still using hdmi. Second, I've reinstalled 12.04.2 lts. It came default with kernel 3.5.0-23 generic. This boots fine, but after the first update it updated to some other one. The updated kernel is 3.5.0-27. This gives me a black screen and my monitor goes into power save. It has to be something in the first huge amount of updates after install.Don't know how to copy them to text so I uploaded screenshots of the update history. You using hdmi mediajunkie? and what graphics card?
edit: also been getting screen tearing in fullscreen flash videos shortly after this problem appeared
edit2: included var/log/apt/history and the results of  cat /var/log/dpkg.log | grep "\ install\ "
```

Start-Date: 2013-02-13  22:07:47
Commandline: apt-get --yes install ubuntu-keyring
Upgrade: ubuntu-keyring:i386 (2011.11.21, 2011.11.21.1)
End-Date: 2013-02-13  22:07:47

Start-Date: 2013-02-13  22:07:50
Commandline: apt-get --yes upgrade
Upgrade: dmsetup:i386 (1.02.48-4ubuntu7, 1.02.48-4ubuntu7.1), libnih-dbus1:i386 (1.0.3-4ubuntu9, 1.0.3-4ubuntu9.1), libc-bin:i386 (2.15-0ubuntu10, 2.15-0ubuntu10.3), vim-common:i386 (7.3.429-2ubuntu2, 7.3.429-2ubuntu2.1), base-files:i386 (6.5ubuntu6, 6.5ubuntu6.5), libplymouth2:i386 (0.8.2-2ubuntu30, 0.8.2-2ubuntu31), libapt-pkg4.12:i386 (0.8.16~exp12ubuntu10, 0.8.16~exp12ubuntu10.7), libdbus-1-3:i386 (1.4.18-1ubuntu1, 1.4.18-1ubuntu1.3), libdrm-intel1:i386 (2.4.32-1ubuntu1, 2.4.39-0ubuntu0.1), perl-base:i386 (5.14.2-6ubuntu2, 5.14.2-6ubuntu2.2), libsqlite3-0:i386 (3.7.9-2ubuntu1, 3.7.9-2ubuntu1.1), initramfs-tools-bin:i386 (0.99ubuntu13, 0.99ubuntu13.1), login:i386 (4.1.4.2+svn3283-3ubuntu5, 4.1.4.2+svn3283-3ubuntu5.1), python2.7:i386 (2.7.3-0ubuntu3, 2.7.3-0ubuntu3.1), libexpat1:i386 (2.0.1-7.2ubuntu1, 2.0.1-7.2ubuntu1.1), libdevmapper1.02.1:i386 (1.02.48-4ubuntu7, 1.02.48-4ubuntu7.1), libpciaccess0:i386 (0.12.902-1, 0.12.902-1ubuntu0.1), isc-dhcp-client:i386 (4.1.ESV-R4-0ubuntu5, 4.1.ESV-R4-0ubuntu5.6), apt-utils:i386 (0.8.16~exp12ubuntu10, 0.8.16~exp12ubuntu10.7), initramfs-tools:i386 (0.99ubuntu13, 0.99ubuntu13.1), vim-tiny:i386 (7.3.429-2ubuntu2, 7.3.429-2ubuntu2.1), xkb-data:i386 (2.5-1ubuntu1, 2.5-1ubuntu1.3), python2.7-minimal:i386 (2.7.3-0ubuntu3, 2.7.3-0ubuntu3.1), coreutils:i386 (8.13-3ubuntu3, 8.13-3ubuntu3.2), udev:i386 (175-0ubuntu9, 175-0ubuntu9.2), passwd:i386 (4.1.4.2+svn3283-3ubuntu5, 4.1.4.2+svn3283-3ubuntu5.1), apt:i386 (0.8.16~exp12ubuntu10, 0.8.16~exp12ubuntu10.7), libdrm2:i386 (2.4.32-1ubuntu1, 2.4.39-0ubuntu0.1), sudo:i386 (1.8.3p1-1ubuntu3, 1.8.3p1-1ubuntu3.3), libdrm-nouveau1a:i386 (2.4.32-1ubuntu1, 2.4.39-0ubuntu0.1), cron:i386 (3.0pl1-120ubuntu3, 3.0pl1-120ubuntu4), dpkg:i386 (1.16.1.2ubuntu7, 1.16.1.2ubuntu7.1), ubuntu-minimal:i386 (1.267, 1.267.1), multiarch-support:i386 (2.15-0ubuntu10, 2.15-0ubuntu10.3), isc-dhcp-common:i386 (4.1.ESV-R4-0ubuntu5, 4.1.ESV-R4-0ubuntu5.6), lsb-base:i386 (4.0-0ubuntu20, 4.0-0ubuntu20.2), libdrm-radeon1:i386 (2.4.32-1ubuntu1, 2.4.39-0ubuntu0.1), libudev0:i386 (175-0ubuntu9, 175-0ubuntu9.2), sysvinit-utils:i386 (2.88dsf-13.10ubuntu11, 2.88dsf-13.10ubuntu11.1), libglib2.0-0:i386 (2.32.1-0ubuntu2, 2.32.3-0ubuntu1), tzdata:i386 (2012b-1, 2012e-0ubuntu0.12.04.1), gpgv:i386 (1.4.11-3ubuntu2, 1.4.11-3ubuntu2.2), ntpdate:i386 (4.2.6.p3+dfsg-1ubuntu3, 4.2.6.p3+dfsg-1ubuntu3.1), resolvconf:i386 (1.63ubuntu11, 1.63ubuntu16), libapt-inst1.4:i386 (0.8.16~exp12ubuntu10, 0.8.16~exp12ubuntu10.7), upstart:i386 (1.5-0ubuntu5, 1.5-0ubuntu7.2), sysv-rc:i386 (2.88dsf-13.10ubuntu11, 2.88dsf-13.10ubuntu11.1), busybox-initramfs:i386 (1.18.5-1ubuntu4, 1.18.5-1ubuntu4.1), mountall:i386 (2.36, 2.36.4), libc6:i386 (2.15-0ubuntu10, 2.15-0ubuntu10.3), initscripts:i386 (2.88dsf-13.10ubuntu11, 2.88dsf-13.10ubuntu11.1), lsb-release:i386 (4.0-0ubuntu20, 4.0-0ubuntu20.2), libnih1:i386 (1.0.3-4ubuntu9, 1.0.3-4ubuntu9.1), plymouth:i386 (0.8.2-2ubuntu30, 0.8.2-2ubuntu31), libssl1.0.0:i386 (1.0.1-4ubuntu3, 1.0.1-4ubuntu5.5), gnupg:i386 (1.4.11-3ubuntu2, 1.4.11-3ubuntu2.2)
End-Date: 2013-02-13  22:07:57

Start-Date: 2013-02-13  22:08:18
Commandline: apt-get --yes install linux-generic-lts-quantal ubuntu-minimal ubuntu-standard ubuntu-desktop libqt4-sql-sqlite notify-osd xserver-xorg-lts-quantal
Install: xserver-xorg-video-cirrus-lts-quantal:i386 (1.5.1-0ubuntu2~precise1, automatic), ubuntuone-client:i386 (3.0.2-0ubuntu1, automatic), popularity-contest:i386 (1.53ubuntu1), x11-apps:i386 (7.6+5ubuntu1, automatic), python-crypto:i386 (2.4.1-1ubuntu0.1, automatic), policykit-1-gnome:i386 (0.105-1ubuntu3.1, automatic), libgs9-common:i386 (9.05~dfsg-0ubuntu4.2, automatic), gir1.2-appindicator3-0.1:i386 (0.4.92-0ubuntu1, automatic), libfolks-telepathy25:i386 (0.6.8-2, automatic), libopencc1:i386 (0.3.0-1, automatic), ubuntuone-control-panel:i386 (3.0.1-0ubuntu1, automatic), sane-utils:i386 (1.0.22-7ubuntu1, automatic), gnome-keyring:i386 (3.2.2-2ubuntu4, automatic), activity-log-manager-control-center:i386 (0.9.4-0ubuntu3.2), libkeyutils1:i386 (1.5.2-2, automatic), fonts-tlwg-mono:i386 (0.4.17-1ubuntu1, automatic), libplist1:i386 (1.8-1, automatic), branding-ubuntu:i386 (0.7), aspell-en:i386 (6.0-0-6ubuntu2, automatic), libpci3:i386 (3.1.8-2ubuntu5, automatic), libgtk2.0-common:i386 (2.24.10-0ubuntu6, automatic), libedit2:i386 (2.11-20080614-3ubuntu2, automatic), libstlport4.6ldbl:i386 (4.6.2-7, automatic), xserver-xorg-input-all-lts-quantal:i386 (7.7+1ubuntu4~precise1, automatic), gstreamer0.10-alsa:i386 (0.10.36-1ubuntu0.1), bluez-alsa:i386 (4.98-2ubuntu7), libsdl1.2debian:i386 (1.2.14-6.4ubuntu3), unity-asset-pool:i386 (0.8.23-0ubuntu1, automatic), libkrb5-3:i386 (1.10+dfsg~beta1-2ubuntu0.3, automatic), libatk1.0-0:i386 (2.4.0-0ubuntu1, automatic), xorg-docs-core:i386 (1.6-1ubuntu2, automatic), libgnomekbd7:i386 (3.4.0.2-1, automatic), thunderbird-globalmenu:i386 (17.0.2+build1-0ubuntu0.12.04.1, automatic), python-lazr.restfulclient:i386 (0.12.0-1ubuntu1, automatic), xserver-xorg-video-neomagic-lts-quantal:i386 (1.2.7-0ubuntu1~precise1, automatic), libpurple0:i386 (2.10.3-0ubuntu1.1, automatic), ttf-freefont:i386 (20100919-1, automatic), python-twisted-names:i386 (11.1.0-1, automatic), apturl-common:i386 (0.5.1ubuntu3, automatic), syslinux:i386 (4.05+dfsg-2, automatic), libtalloc2:i386 (2.0.7-3, automatic), libpeas-common:i386 (1.2.0-1ubuntu1, automatic), libical0:i386 (0.48-1ubuntu3, automatic), libxatracker1-lts-quantal:i386 (9.0-0ubuntu1~precise4, automatic), nano:i386 (2.2.6-1), ttf-dejavu-core:i386 (2.33-2ubuntu1, automatic), geoclue:i386 (0.12.0-1ubuntu12, automatic), unity:i386 (5.18.0-0ubuntu2, automatic), libcdio13:i386 (0.83-1, automatic), hdparm:i386 (9.37-0ubuntu3.1, automatic), plymouth-theme-ubuntu-text:i386 (0.8.2-2ubuntu31), libglib-perl:i386 (1.241-1, automatic), python-twisted-core:i386 (11.1.0-1ubuntu2, automatic), libxfixes3:i386 (5.0-4ubuntu4, automatic), espeak:i386 (1.46.02-0ubuntu1, automatic), liborc-0.4-0:i386 (0.4.16-1ubuntu2, automatic), libgtkmm-3.0-1:i386 (3.4.0-0ubuntu1, automatic), gir1.2-totem-1.0:i386 (3.0.1-0ubuntu21.1, automatic), shared-mime-info:i386 (1.0-0ubuntu4.1, automatic), python-gst0.10:i386 (0.10.22-3ubuntu0.1, automatic), libqt4-opengl:i386 (4.8.1-0ubuntu4.3, automatic), libcanberra-gtk-module:i386 (0.28-3ubuntu3, automatic), libmtp9:i386 (1.1.3-1ubuntu0.1, automatic), libenchant1c2a:i386 (1.6.0-7, automatic), gwibber-service:i386 (3.4.2-0ubuntu2.1, automatic), libnm-glib-vpn1:i386 (0.9.4.0-0ubuntu4.2, automatic), libkrb5support0:i386 (1.10+dfsg~beta1-2ubuntu0.3, automatic), libatasmart4:i386 (0.18-3, automatic), unity-2d:i386 (5.12.0-0ubuntu1.2), gcalctool:i386 (6.4.1.1-0ubuntu3), libpolkit-gobject-1-0:i386 (0.104-1ubuntu1, automatic), libyelp0:i386 (3.4.1-0ubuntu1, automatic), mlocate:i386 (0.23.1-1ubuntu2), libdconf-dbus-1-0:i386 (0.12.0-0ubuntu1.1, automatic), libnl-3-200:i386 (3.2.3-2ubuntu2, automatic), libgmp10:i386 (5.0.2+dfsg-2ubuntu1, automatic), gstreamer0.10-x:i386 (0.10.36-1ubuntu0.1, automatic), libcompizconfig0:i386 (0.9.7.0~bzr428-0ubuntu6, automatic), libpango-perl:i386 (1.222-1build1, automatic), libgail18:i386 (2.24.10-0ubuntu6, automatic), telepathy-salut:i386 (0.8.0-0ubuntu1, automatic), update-manager:i386 (0.156.14.11, automatic), libmpfr4:i386 (3.1.0-3ubuntu2, automatic), fonts-khmeros-core:i386 (5.0-5ubuntu1), libpth20:i386 (2.0.7-16ubuntu3, automatic), gtk3-engines-unico:i386 (1.0.2-0ubuntu1, automatic), xz-lzma:i386 (5.1.1alpha+20110809-3, automatic), gnome-nettool:i386 (3.2.0-0ubuntu1), libqt4-declarative:i386 (4.8.1-0ubuntu4.3, automatic), libgphoto2-port0:i386 (2.4.13-1ubuntu1.2, automatic), python-pyinotify:i386 (0.9.2-1, automatic), gnome-media:i386 (3.4.0-0ubuntu3.1), libv4l-0:i386 (0.8.6-1ubuntu2, automatic), liblcms1:i386 (1.19.dfsg-1ubuntu3, automatic), metacity:i386 (2.34.1-1ubuntu11, automatic), libxrandr-ltsq2:i386 (1.4.0-1~precise1, automatic), libraptor2-0:i386 (2.0.6-1, automatic), python-pexpect:i386 (2.3-1ubuntu2, automatic), unity-2d-panel:i386 (5.12.0-0ubuntu1.2, automatic), nautilus:i386 (3.4.2-0ubuntu6, automatic), libunity9:i386 (5.12.0-0ubuntu1.1, automatic), aisleriot:i386 (3.2.3.2-0ubuntu1), gir1.2-gtk-2.0:i386 (2.24.10-0ubuntu6, automatic), libqtgconf1:i386 (0.1-0ubuntu5, automatic), libgnome-media-profiles-3.0-0:i386 (3.0.0-1, automatic), libpackagekit-glib2-14:i386 (0.7.2-4ubuntu3, automatic), libnettle4:i386 (2.4-1, automatic), bind9-host:i386 (9.8.1.dfsg.P1-4ubuntu0.5, automatic), python-notify:i386 (0.1.1-3, automatic), bluez-gstreamer:i386 (4.98-2ubuntu7), xfonts-scalable:i386 (1.0.3-1, automatic), irqbalance:i386 (0.56-1ubuntu4), python-aptdaemon.gtk3widgets:i386 (0.43+bzr805-0ubuntu7, automatic), python-renderpm:i386 (2.5-1.1build1, automatic), network-manager-pptp-gnome:i386 (0.9.4.0-0ubuntu1, automatic), gvfs-fuse:i386 (1.12.1-0ubuntu1.1), baobab:i386 (3.4.1-0ubuntu1), libidn11:i386 (1.23-2, automatic), gir1.2-gtk-3.0:i386 (3.4.2-0ubuntu0.5, automatic), libgtop2-common:i386 (2.28.4-2, automatic), python-aptdaemon.pkcompat:i386 (0.43+bzr805-0ubuntu7, automatic), ubuntu-docs:i386 (12.04.6, automatic), libgstreamer0.10-0:i386 (0.10.36-1ubuntu1, automatic), libtelepathy-glib0:i386 (0.18.2-0ubuntu1, automatic), ttf-punjabi-fonts:i386 (0.5.11ubuntu1), python-mako:i386 (0.5.0-1, automatic), libportaudio2:i386 (19+svn20111121-1, automatic), libgtksourceview-3.0-0:i386 (3.4.2-0ubuntu1, automatic), aspell:i386 (0.60.7~20110707-1, automatic), libgtkspell-3-0:i386 (3.0.0~hg20110814-1, automatic), libnss3:i386 (3.14.1-0ckbi1.93ubuntu.0.12.04.1, automatic), usbmuxd:i386 (1.0.7-2, automatic), libsensors4:i386 (3.3.1-2ubuntu1, automatic), libwrap0:i386 (7.6.q-21, automatic), appmenu-gtk:i386 (0.3.92-0ubuntu1.1, automatic), libcanberra-gtk3-0:i386 (0.28-3ubuntu3, automatic), libebook-1.2-12:i386 (3.2.3-0ubuntu7, automatic), pkg-config:i386 (0.26-1ubuntu1, automatic), libglib2.0-bin:i386 (2.32.3-0ubuntu1, automatic), python-dirspec:i386 (3.0.0-0ubuntu1, automatic), gir1.2-javascriptcoregtk-3.0:i386 (1.8.3-0ubuntu0.12.04.1, automatic), telnet:i386 (0.17-36build1), python-debian:i386 (0.1.21ubuntu1, automatic), libcupscgi1:i386 (1.5.3-0ubuntu6, automatic), lshw:i386 (02.15-2), mobile-broadband-provider-info:i386 (20120410-0ubuntu1, automatic), libcaca0:i386 (0.99.beta17-2.1ubuntu2, automatic), python-zope.interface:i386 (3.6.1-1ubuntu3, automatic), libhx509-5-heimdal:i386 (1.6~git20120311.dfsg.1-2, automatic), libindicator7:i386 (0.5.0-0ubuntu1, automatic), enchant:i386 (1.6.0-7, automatic), libiec61883-0:i386 (1.2.0-0.1ubuntu1, automatic), libsnmp15:i386 (5.4.3~dfsg-2.4ubuntu1.1, automatic), genisoimage:i386 (1.1.11-2ubuntu2, automatic), lsof:i386 (4.81.dfsg.1-1build1), brasero-cdrkit:i386 (3.4.1-0ubuntu1.1, automatic), libwmf0.2-7:i386 (0.2.8.4-10ubuntu1, automatic), libdjvulibre21:i386 (3.5.24-9, automatic), xserver-xorg-input-synaptics-lts-quantal:i386 (1.6.2-1ubuntu5~precise1, automatic), oneconf:i386 (0.2.8.1, automatic), gnome-settings-daemon:i386 (3.4.2-0ubuntu0.6.2, automatic), obex-data-server:i386 (0.4.6-0ubuntu1, automatic), xserver-xorg-video-vmware-lts-quantal:i386 (12.0.2+git.e5ac80d8-0ubuntu1~precise2, automatic), indicator-application:i386 (0.5.0-0ubuntu1, automatic), fonts-tlwg-typewriter:i386 (0.4.17-1ubuntu1, automatic), wireless-tools:i386 (30~pre9-5ubuntu2), gir1.2-unity-5.0:i386 (5.12.0-0ubuntu1.1, automatic), librdf0:i386 (1.0.14-1, automatic), apport-symptoms:i386 (0.16.1, automatic), libutempter0:i386 (1.1.5-4, automatic), fonts-tlwg-garuda:i386 (0.4.17-1ubuntu1, automatic), libicu48:i386 (4.8.1.1-3, automatic), network-manager-pptp:i386 (0.9.4.0-0ubuntu1, automatic), python-software-properties:i386 (0.82.7.3, automatic), smbclient:i386 (3.6.3-2ubuntu2.3, automatic), libraw5:i386 (0.14.4-0ubuntu2, automatic), python-protobuf:i386 (2.4.1-1ubuntu2, automatic), libjpeg8:i386 (8c-2ubuntu7, automatic), brasero-common:i386 (3.4.1-0ubuntu1.1, automatic), gir1.2-gst-plugins-base-0.10:i386 (0.10.36-1ubuntu0.1, automatic), xserver-xorg-video-sis-lts-quantal:i386 (0.10.7-0ubuntu1~precise2, automatic), libvorbisfile3:i386 (1.3.2-1ubuntu3, automatic), python-debtagshw:i386 (1.9+git20120320-0ubuntu1, automatic), ubuntu-standard:i386 (1.267.1), libsane-common:i386 (1.0.22-7ubuntu1, automatic), libreoffice-calc:i386 (3.5.4-0ubuntu1.1), iso-codes:i386 (3.31-1, automatic), doc-base:i386 (0.10.3), python-ubuntuone-storageprotocol:i386 (3.0.2-0ubuntu1, automatic), gucharmap:i386 (3.4.1.1-0ubuntu1), libclass-isa-perl:i386 (0.36-3, automatic), libcamel-1.2-29:i386 (3.2.3-0ubuntu7, automatic), network-manager:i386 (0.9.4.0-0ubuntu4.2, automatic), iputils-tracepath:i386 (20101006-1ubuntu1, automatic), zenity:i386 (3.4.0-0ubuntu4, automatic), printer-driver-c2esp:i386 (23-1), bash-completion:i386 (1.3-1ubuntu8), avahi-daemon:i386 (0.6.30-5ubuntu2, automatic), libdiscid0:i386 (0.2.2-3, automatic), libgail-common:i386 (2.24.10-0ubuntu6), qdbus:i386 (4.8.1-0ubuntu4.3, automatic), libgnome-keyring0:i386 (3.2.2-2, automatic), memtest86+:i386 (4.20-1.1ubuntu1), libecal-1.2-10:i386 (3.2.3-0ubuntu7, automatic), gnome-desktop3-data:i386 (3.4.2-0ubuntu0.1, automatic), x11-utils:i386 (7.6+4ubuntu0.1, automatic), gnome-session-canberra:i386 (0.28-3ubuntu3), libpixman-1-0:i386 (0.24.4-1, automatic), gir1.2-gdkpixbuf-2.0:i386 (2.26.1-1, automatic), upower:i386 (0.9.15-3git1, automatic), krb5-locales:i386 (1.10+dfsg~beta1-2ubuntu0.3, automatic), libgck-1-0:i386 (3.2.2-2ubuntu4, automatic), libx11-data:i386 (1.4.99.1-0ubuntu2, automatic), libdbusmenu-glib4:i386 (0.6.2-0ubuntu0.1, automatic), python-twisted-web:i386 (11.1.0-1, automatic), pulseaudio:i386 (1.1-0ubuntu15.2, automatic), gnome-bluetooth:i386 (3.2.2-0ubuntu5), dnsutils:i386 (9.8.1.dfsg.P1-4ubuntu0.5, automatic), aptdaemon-data:i386 (0.43+bzr805-0ubuntu7, automatic), libspectre1:i386 (0.2.6-1build1, automatic), command-not-found:i386 (0.2.46ubuntu6), libnm-gtk0:i386 (0.9.4.1-0ubuntu2, automatic), software-center-aptdaemon-plugins:i386 (0.1.2, automatic), gir1.2-gstreamer-0.10:i386 (0.10.36-1ubuntu1, automatic), libexttextcat-data:i386 (3.2.0-1ubuntu1, automatic), xserver-xorg-core-lts-quantal:i386 (1.13.0-0ubuntu6.1~precise2, automatic), libswitch-perl:i386 (2.16-2, automatic), update-manager-core:i386 (0.156.14.11, automatic), libunique-3.0-0:i386 (3.0.2-1, automatic), sound-theme-freedesktop:i386 (0.7.pristine-2, automatic), libart-2.0-2:i386 (2.3.21-1ubuntu0.1, automatic), app-install-data:i386 (0.12.04.4, automatic), ibus-gtk3:i386 (1.4.1-3ubuntu1, automatic), python-wadllib:i386 (1.3.0-2, automatic), libfolks-eds25:i386 (0.6.8-2, automatic), bamfdaemon:i386 (0.2.124.2-0ubuntu1, automatic), gnome-power-manager:i386 (3.4.0-0ubuntu1.1), libavahi-common-data:i386 (0.6.30-5ubuntu2, automatic), glib-networking-services:i386 (2.32.1-1ubuntu2, automatic), libsane:i386 (1.0.22-7ubuntu1, automatic), udisks:i386 (1.0.4-5ubuntu2.1, automatic), gir1.2-launchpad-integration-3.0:i386 (0.1.56.1, automatic), python-aptdaemon:i386 (0.43+bzr805-0ubuntu7, automatic), install-info:i386 (4.13a.dfsg.1-8ubuntu2, automatic), gir1.2-ubuntuoneui-3.0:i386 (3.0.1-0ubuntu1, automatic), libreoffice-gnome:i386 (3.5.4-0ubuntu1.1), unzip:i386 (6.0-4ubuntu1, automatic), perl:i386 (5.14.2-6ubuntu2.2, automatic), gir1.2-atspi-2.0:i386 (2.4.2-0ubuntu0.1, automatic), glib-networking:i386 (2.32.1-1ubuntu2, automatic), libnfnetlink0:i386 (1.0.0-1, automatic), python-pycurl:i386 (7.19.0-4ubuntu3, automatic), libhyphen0:i386 (2.8.3-1, automatic), unity-lens-applications:i386 (5.18.0-0ubuntu1, automatic), totem-plugins:i386 (3.0.1-0ubuntu21.1, automatic), qt-at-spi:i386 (0.2.0+git20120411-0ubuntu1), libdbus-glib-1-2:i386 (0.98-1ubuntu1, automatic), x11-xfs-utils:i386 (7.6+1, automatic), libdconf-qt0:i386 (0.0.0.110722-0ubuntu4, automatic), libglew1.6:i386 (1.6.0-4, automatic), thunderbird:i386 (17.0.2+build1-0ubuntu0.12.04.1), libqt4-dbus:i386 (4.8.1-0ubuntu4.3, automatic), gnome-screensaver:i386 (3.4.1-0ubuntu1), libgucharmap-2-90-7:i386 (3.4.1.1-0ubuntu1, automatic), rhythmbox:i386 (2.96-0ubuntu4.2, automatic), libburn4:i386 (1.1.8-1, automatic), libxxf86vm1:i386 (1.1.1-2build1, automatic), ubuntuone-couch:i386 (0.3.0-0ubuntu4, automatic), ubuntu-sso-client:i386 (3.0.2-0ubuntu3, automatic), libcap2:i386 (2.22-1ubuntu3, automatic), libproxy1:i386 (0.4.7-0ubuntu4.1, automatic), xterm:i386 (271-1ubuntu2.1), liblcms2-2:i386 (2.2+git20110628-2ubuntu3, automatic), gnome-screenshot:i386 (3.4.1-0ubuntu1), libwpg-0.2-2:i386 (0.2.1-1, automatic), ibus-gtk:i386 (1.4.1-3ubuntu1, automatic), system-config-printer-gnome:i386 (1.3.8+20120201-0ubuntu8.1, automatic), manpages-dev:i386 (3.35-0.1ubuntu1, automatic), gedit:i386 (3.4.1-0ubuntu1), python-libxml2:i386 (2.7.8.dfsg-5.1ubuntu4.3, automatic), libnm-util2:i386 (0.9.4.0-0ubuntu4.2, automatic), libdecoration0:i386 (0.9.7.12-0ubuntu1, automatic), plymouth-label:i386 (0.8.2-2ubuntu31, automatic), gnome-menus:i386 (3.4.0-0ubuntu1, automatic), liblircclient0:i386 (0.9.0-0ubuntu1, automatic), xdg-user-dirs-gtk:i386 (0.9-0ubuntu1), libgexiv2-1:i386 (0.4.1-1build1, automatic), libproxy1-plugin-networkmanager:i386 (0.4.7-0ubuntu4.1), gnome-session-common:i386 (3.2.1-0ubuntu8, automatic), bluez-cups:i386 (4.98-2ubuntu7), lightdm:i386 (1.2.3-0ubuntu1), libtdb1:i386 (1.2.9-4, automatic), thunderbird-gnome-support:i386 (17.0.2+build1-0ubuntu0.12.04.1), foomatic-db-compressed-ppds:i386 (20120322-0ubuntu1), hunspell-en-us:i386 (20070829-4ubuntu3, automatic), x11-xserver-utils:i386 (7.6+3, automatic), grub2-common:i386 (1.99-21ubuntu3.9, automatic), dvd+rw-tools:i386 (7.1-10, automatic), protobuf-compiler:i386 (2.4.1-1ubuntu2, automatic), libindicate-gtk3:i386 (0.6.92-0ubuntu1, automatic), libpam-gnome-keyring:i386 (3.2.2-2ubuntu4, automatic), libglu1-mesa:i386 (8.0.4-0ubuntu0.3, automatic), libxcb-glx0:i386 (1.8.1-1ubuntu0.1, automatic), cups-client:i386 (1.5.3-0ubuntu6, automatic), apt-transport-https:i386 (0.8.16~exp12ubuntu10.7), evince-common:i386 (3.4.0-0ubuntu1.4, automatic), inputattach:i386 (1.4.2-1), libjack-jackd2-0:i386 (1.9.8~dfsg.1-1ubuntu1, automatic), brltty:i386 (4.3-1ubuntu5), libieee1284-3:i386 (0.2.11-10build1, automatic), libcryptsetup4:i386 (1.4.1-2ubuntu4, automatic), libcupsmime1:i386 (1.5.3-0ubuntu6, automatic), libc-dev-bin:i386 (2.15-0ubuntu10.3, automatic), gir1.2-soup-2.4:i386 (2.38.1-1, automatic), xserver-xorg-input-evdev-lts-quantal:i386 (2.7.3-0ubuntu2~precise1, automatic), xserver-xorg-input-wacom-lts-quantal:i386 (0.17.0-0ubuntu2~precise1, automatic), xserver-common:i386 (1.11.4-0ubuntu10.11, automatic), accountsservice:i386 (0.6.15-2ubuntu9.4, automatic), ubuntu-artwork:i386 (57), printer-driver-pxljr:i386 (1.3+repack0-2), libunity-2d-private0:i386 (5.12.0-0ubuntu1.2, automatic), libpcap0.8:i386 (1.1.1-10, automatic), libx86-1:i386 (1.1+ds1-7ubuntu1, automatic), gnome-control-center:i386 (3.4.2-0ubuntu0.9), gir1.2-dbusmenu-glib-0.4:i386 (0.6.2-0ubuntu0.1, automatic), libsasl2-modules:i386 (2.1.25.dfsg1-3ubuntu0.1, automatic), fonts-lao:i386 (0.0.20060226-8), libspeex1:i386 (1.2~rc1-3ubuntu2, automatic), libnotify-bin:i386 (0.7.5-1), bc:i386 (1.06.95-2), printer-driver-postscript-hp:i386 (3.12.2-1ubuntu3.1, automatic), libjs-jquery:i386 (1.7.1-1ubuntu1, automatic), gvfs-libs:i386 (1.12.1-0ubuntu1.1, automatic), hplip:i386 (3.12.2-1ubuntu3.1), libavahi-ui-gtk3-0:i386 (0.6.30-5ubuntu2, automatic), python-ubuntuone-control-panel:i386 (3.0.1-0ubuntu1, automatic), libglewmx1.6:i386 (1.6.0-4, automatic), libgcr-3-1:i386 (3.2.2-2ubuntu4, automatic), libdns81:i386 (9.8.1.dfsg.P1-4ubuntu0.5, automatic), ibus-pinyin:i386 (1.4.0-1), libheimbase1-heimdal:i386 (1.6~git20120311.dfsg.1-2, automatic), dc:i386 (1.06.95-2, automatic), gconf2:i386 (3.2.5-0ubuntu2, automatic), at:i386 (3.1.13-1ubuntu1), libminiupnpc8:i386 (1.6-3ubuntu1, automatic), strace:i386 (4.5.20-2.3ubuntu1), dosfstools:i386 (3.0.12-1ubuntu1, automatic), ed:i386 (1.5-3), xauth:i386 (1.0.6-1, automatic), compizconfig-backend-gconf:i386 (0.9.5.92-0ubuntu5, automatic), libwnck-common:i386 (2.30.7-0ubuntu1, automatic), python-dbus-dev:i386 (1.0.0-1ubuntu1, automatic), libvncserver0:i386 (0.9.8.2-2ubuntu1, automatic), libupower-glib1:i386 (0.9.15-3git1, automatic), linux-generic-lts-quantal:i386 (3.5.0.23.30), command-not-found-data:i386 (0.2.46ubuntu6, automatic), libxslt1.1:i386 (1.1.26-8ubuntu1.2, automatic), update-notifier-common:i386 (0.119ubuntu8.6, automatic), libfile-copy-recursive-perl:i386 (0.38-1, automatic), fonts-thai-tlwg:i386 (0.4.17-1ubuntu1), ubuntu-desktop:i386 (1.267.1), seahorse:i386 (3.2.2-0ubuntu2.1), metacity-common:i386 (2.34.1-1ubuntu11, automatic), libnux-2.0-common:i386 (2.14.1-0ubuntu1, automatic), python-keyring:i386 (0.9.2-0ubuntu0.12.04.2, automatic), librest-0.7-0:i386 (0.7.12-1ubuntu2, automatic), xserver-xorg-video-trident-lts-quantal:i386 (1.3.6-0ubuntu2~precise1, automatic), ubuntu-system-service:i386 (0.2.2, automatic), libgomp1:i386 (4.6.3-1ubuntu5, automatic), system-config-printer-udev:i386 (1.3.8+20120201-0ubuntu8.1, automatic), printer-driver-gutenprint:i386 (5.2.8~pre1-0ubuntu2.1, automatic), remmina-plugin-rdp:i386 (1.0.0-1ubuntu6.1, automatic), empathy:i386 (3.4.2.3-0ubuntu1), libframe6:i386 (2.2.4-0ubuntu0.12.04.1, automatic), iw:i386 (3.2-1, automatic), python-apt:i386 (0.8.3ubuntu7, automatic), python-virtkey:i386 (0.60.0-0ubuntu5, automatic), apt-xapian-index:i386 (0.44ubuntu5, automatic), libgl1-mesa-glx-lts-quantal:i386 (9.0-0ubuntu1~precise4, automatic), unity-2d-shell:i386 (5.12.0-0ubuntu1.2, automatic), libreoffice-emailmerge:i386 (3.5.4-0ubuntu1.1, automatic), libslp1:i386 (1.2.1-7.8ubuntu1, automatic), ubuntu-sounds:i386 (0.13), groff-base:i386 (1.21-7, automatic), ubuntu-wallpapers:i386 (0.34.1, automatic), whois:i386 (5.0.15ubuntu2, automatic), printer-driver-foo2zjs:i386 (20111202dfsg0-1ubuntu1), xserver-xorg-video-r128-lts-quantal:i386 (6.9.1-0ubuntu1~precise2, automatic), cups-filters:i386 (1.0.18-0ubuntu0.1, automatic), libusb-1.0-0:i386 (1.0.9~rc3-2ubuntu1, automatic), libtotem-plparser17:i386 (3.4.1-1, automatic), totem-common:i386 (3.0.1-0ubuntu21.1, automatic), libpoppler19:i386 (0.18.4-1ubuntu3, automatic), libcairo2:i386 (1.10.2-6.1ubuntu3, automatic), rfkill:i386 (0.4-1ubuntu2), libnotify4:i386 (0.7.5-1, automatic), libfontconfig1:i386 (2.8.0-3ubuntu9.1, automatic), unity-services:i386 (5.18.0-0ubuntu2, automatic), ghostscript-x:i386 (9.05~dfsg-0ubuntu4.2), libnetfilter-conntrack3:i386 (0.9.1-1ubuntu1, automatic), libx11-xcb1:i386 (1.4.99.1-0ubuntu2, automatic), libquvi-scripts:i386 (0.4.2-1, automatic), light-themes:i386 (0.1.9.1-0ubuntu1.2, automatic), libxcb-util0:i386 (0.3.8-2, automatic), checkbox:i386 (0.13.9, automatic), python-gconf:i386 (2.28.1+dfsg-1, automatic), unity-2d-common:i386 (5.12.0-0ubuntu1.2, automatic), python-simplejson:i386 (2.3.2-1, automatic), gir1.2-gudev-1.0:i386 (175-0ubuntu9.2, automatic), fontconfig-config:i386 (2.8.0-3ubuntu9.1, automatic), libevent-2.0-5:i386 (2.0.16-stable-1, automatic), libreoffice-core:i386 (3.5.4-0ubuntu1.1, automatic), gvfs-bin:i386 (1.12.1-0ubuntu1.1, automatic), libgnutls26:i386 (2.12.14-5ubuntu3.1, automatic), fonts-takao-pgothic:i386 (003.02.01-5ubuntu1), python-reportlab-accel:i386 (2.5-1.1build1, automatic), libqtbamf1:i386 (0.2.4-0ubuntu1, automatic), libpulse-mainloop-glib0:i386 (1.1-0ubuntu15.2, automatic), libtotem0:i386 (3.0.1-0ubuntu21.1, automatic), libraw1394-11:i386 (2.0.7-1ubuntu1, automatic), policykit-1:i386 (0.104-1ubuntu1, automatic), update-notifier:i386 (0.119ubuntu8.6, automatic), gvfs-common:i386 (1.12.1-0ubuntu1.1, automatic), overlay-scrollbar:i386 (0.2.16-0ubuntu1.1), apport:i386 (2.0.1-0ubuntu17.1, automatic), gstreamer0.10-gconf:i386 (0.10.31-1ubuntu1, automatic), libvorbisenc2:i386 (1.3.2-1ubuntu3, automatic), psmisc:i386 (22.15-2ubuntu1.1, automatic), gir1.2-atk-1.0:i386 (2.4.0-0ubuntu1, automatic), libgdk-pixbuf2.0-common:i386 (2.26.1-1, automatic), linux-libc-dev:i386 (3.2.0-37.58, automatic), xml-core:i386 (0.13, automatic), libgoa-1.0-common:i386 (3.4.0-0ubuntu1, automatic), libbsd0:i386 (0.3.0-2, automatic), libfile-basedir-perl:i386 (0.03-1fakesync1, automatic), nautilus-data:i386 (3.4.2-0ubuntu6, automatic), libgpod4:i386 (0.8.2-4, automatic), mtools:i386 (4.0.12-1, automatic), librasqal3:i386 (0.9.28-1, automatic), bluez:i386 (4.98-2ubuntu7), libxmuu1:i386 (1.1.0-3, automatic), libwacom-common:i386 (0.4-1ubuntu1, automatic), libnl-route-3-200:i386 (3.2.3-2ubuntu2, automatic), libgnome-menu2:i386 (3.0.1-0ubuntu7, automatic), libdbusmenu-gtk3-4:i386 (0.6.2-0ubuntu0.1, automatic), gvfs-daemons:i386 (1.12.1-0ubuntu1.1, automatic), ubuntuone-client-gnome:i386 (3.0.1-0ubuntu1), libcurl3-gnutls:i386 (7.22.0-3ubuntu4, automatic), python-gi-cairo:i386 (3.2.2-1~precise, automatic), gnome-font-viewer:i386 (3.4.0-1), gir1.2-gtksource-3.0:i386 (3.4.2-0ubuntu1, automatic), libtasn1-3:i386 (2.10-1ubuntu1.1, automatic), gstreamer0.10-plugins-good:i386 (0.10.31-1ubuntu1, automatic), libparted0debian1:i386 (2.3-8ubuntu5.1, automatic), libgeoclue0:i386 (0.12.0-1ubuntu12, automatic), libxcb-render0:i386 (1.8.1-1ubuntu0.1, automatic), libsoup2.4-1:i386 (2.38.1-1, automatic), remmina-plugin-vnc:i386 (1.0.0-1ubuntu6.1, automatic), libgcr-3-common:i386 (3.2.2-2ubuntu4, automatic), gnome-terminal:i386 (3.4.1.1-0ubuntu1), libgphoto2-2:i386 (2.4.13-1ubuntu1.2, automatic), xdg-user-dirs:i386 (0.14-0ubuntu2), xserver-xorg-video-siliconmotion-lts-quantal:i386 (1.7.7-0ubuntu1~precise1, automatic), liblvm2app2.2:i386 (2.02.66-4ubuntu7.1, automatic), printer-driver-hpijs:i386 (3.12.2-1ubuntu3.1, automatic), foomatic-db-engine:i386 (4.0.8-2ubuntu1, automatic), humanity-icon-theme:i386 (0.5.3.11, automatic), rhythmbox-data:i386 (2.96-0ubuntu4.2, automatic), parted:i386 (2.3-8ubuntu5.1, automatic), zeitgeist:i386 (0.9.0-1ubuntu1, automatic), libwavpack1:i386 (4.60.1-2, automatic), telepathy-indicator:i386 (0.2.1-0ubuntu1, automatic), sni-qt:i386 (0.2.5-0ubuntu3), grub-pc:i386 (1.99-21ubuntu3.9, automatic), libpaper-utils:i386 (1.1.24+nmu1build1, automatic), libqtdee2:i386 (0.2.4-0ubuntu1, automatic), hicolor-icon-theme:i386 (0.12-1ubuntu2, automatic), gnome-user-share:i386 (3.0.2-0ubuntu1, automatic), libcolord1:i386 (0.1.16-2ubuntu0.1, automatic), libreoffice-writer:i386 (3.5.4-0ubuntu1.1, automatic), libsmbclient:i386 (3.6.3-2ubuntu2.3, automatic), liblaunchpad-integration-common:i386 (0.1.56.1, automatic), libcap2-bin:i386 (2.22-1ubuntu3, automatic), nautilus-sendto-empathy:i386 (3.4.2.3-0ubuntu1, automatic), pptp-linux:i386 (1.7.2-6, automatic), libmission-control-plugins0:i386 (5.12.0-0ubuntu2.1, automatic), gcc-4.6:i386 (4.6.3-1ubuntu5, automatic), avahi-utils:i386 (0.6.30-5ubuntu2, automatic), gsettings-desktop-schemas:i386 (3.4.1-0ubuntu1, automatic), libisccc80:i386 (9.8.1.dfsg.P1-4ubuntu0.5, automatic), libreoffice-draw:i386 (3.5.4-0ubuntu1.1, automatic), toshset:i386 (1.76-2, automatic), unity-lens-video:i386 (0.3.5-0ubuntu1.3, automatic), network-manager-gnome:i386 (0.9.4.1-0ubuntu2, automatic), friendly-recovery:i386 (0.2.25), unity-scope-musicstores:i386 (5.12.0-0ubuntu2, automatic), zeitgeist-core:i386 (0.9.0-1ubuntu1, automatic), gir1.2-gnomekeyring-1.0:i386 (3.2.2-2, automatic), libgconf-2-4:i386 (3.2.5-0ubuntu2, automatic), geoip-database:i386 (20111220-1, automatic), libk5crypto3:i386 (1.10+dfsg~beta1-2ubuntu0.3, automatic), libfuse2:i386 (2.8.6-2ubuntu2, automatic), libfolks25:i386 (0.6.8-2, automatic), libcanberra-gtk3-module:i386 (0.28-3ubuntu3, automatic), libpcsclite1:i386 (1.7.4-2ubuntu2, automatic), cups-ppdc:i386 (1.5.3-0ubuntu6, automatic), pppconfig:i386 (2.3.18+nmu3ubuntu1), fonts-tlwg-purisa:i386 (0.4.17-1ubuntu1, automatic), libgnome-bluetooth8:i386 (3.2.2-0ubuntu5, automatic), libmtp-common:i386 (1.1.3-1ubuntu0.1, automatic), xserver-xorg-video-modesetting-lts-quantal:i386 (0.5.0-0ubuntu1~precise2, automatic), tcpd:i386 (7.6.q-21, automatic), tcpdump:i386 (4.2.1-1ubuntu2), mtr-tiny:i386 (0.80-1ubuntu1), glib-networking-common:i386 (2.32.1-1ubuntu2, automatic), guile-1.8-libs:i386 (1.8.8+1-6ubuntu2, automatic), shotwell:i386 (0.12.3-0ubuntu0.1), libnss-mdns:i386 (0.10-3.2, automatic), dnsmasq-base:i386 (2.59-4, automatic), duplicity:i386 (0.6.18-0ubuntu3.1, automatic), libck-connector0:i386 (0.4.5-2, automatic), libheimntlm0-heimdal:i386 (1.6~git20120311.dfsg.1-2, automatic), printer-driver-sag-gdi:i386 (0.1-3), libproxy1-plugin-gsettings:i386 (0.4.7-0ubuntu4.1), libgnome-desktop-3-2:i386 (3.4.2-0ubuntu0.1, automatic), openssh-client:i386 (5.9p1-5ubuntu1, automatic), libdatrie1:i386 (0.2.5-3, automatic), jockey-common:i386 (0.9.7-0ubuntu7.7, automatic), xserver-xorg-video-all-lts-quantal:i386 (7.7+1ubuntu4~precise1, automatic), python-defer:i386 (1.0.2+bzr481-1, automatic), fontconfig:i386 (2.8.0-3ubuntu9.1, automatic), libdmapsharing-3.0-2:i386 (2.9.14-1, automatic), libgrip0:i386 (0.3.5-0ubuntu1~12.04.1, automatic), libgwibber-gtk2:i386 (3.4.2-0ubuntu2.1, automatic), deja-dup:i386 (22.0-0ubuntu3), libwnck22:i386 (2.30.7-0ubuntu1, automatic), python-serial:i386 (2.5-2.1build1, automatic), libgl1-mesa-dri-lts-quantal:i386 (9.0-0ubuntu1~precise4, automatic), folks-common:i386 (0.6.8-2, automatic), libgnomekbd-common:i386 (3.4.0.2-1, automatic), appmenu-qt:i386 (0.2.6-0ubuntu1, automatic), gedit-common:i386 (3.4.1-0ubuntu1, automatic), libboost-serialization1.46.1:i386 (1.46.1-7ubuntu3, automatic), rhythmbox-mozilla:i386 (2.96-0ubuntu4.2, automatic), vbetool:i386 (1.1-2ubuntu1, automatic), libcairomm-1.0-1:i386 (1.10.0-1ubuntu1, automatic), libqt4-xmlpatterns:i386 (4.8.1-0ubuntu4.3, automatic), firefox-globalmenu:i386 (18.0.2+build1-0ubuntu0.12.04.1, automatic), compiz-plugins-default:i386 (0.9.7.12-0ubuntu1, automatic), acl:i386 (2.2.51-5ubuntu1, automatic), software-center:i386 (5.2.7), libxfont1:i386 (1.4.4-1, automatic), python-pam:i386 (0.4.2-12.2ubuntu4, automatic), libsyncdaemon-1.0-1:i386 (3.0.2-0ubuntu1, automatic), libnice10:i386 (0.1.1-2ubuntu1, automatic), uuid-runtime:i386 (2.20.1-1ubuntu3), libgconf2-4:i386 (3.2.5-0ubuntu2, automatic), python-openssl:i386 (0.12-1ubuntu2, automatic), rhythmbox-plugin-zeitgeist:i386 (2.96-0ubuntu4.2, automatic), notify-osd:i386 (0.9.34-0ubuntu2), xinput:i386 (1.5.99.1-0ubuntu2, automatic), libjson0:i386 (0.9-1ubuntu1, automatic), linux-image-generic-lts-quantal:i386 (3.5.0.23.30), libgtk-3-common:i386 (3.4.2-0ubuntu0.5, automatic), fonts-tlwg-typist:i386 (0.4.17-1ubuntu1, automatic), libgssdp-1.0-3:i386 (0.12.1-2, automatic), libbrlapi0.5:i386 (4.3-1ubuntu5, automatic), libxres1:i386 (1.0.5-1, automatic), libgdu-gtk0:i386 (3.0.2-2ubuntu7, automatic), libwebkitgtk-3.0-0:i386 (1.8.3-0ubuntu0.12.04.1, automatic), python-gi:i386 (3.2.2-1~precise, automatic), libmtdev1:i386 (1.1.0-2ubuntu1, automatic), acpid:i386 (2.0.10-1ubuntu3, automatic), simple-scan:i386 (3.4.1-0ubuntu1.1), libcupsppdc1:i386 (1.5.3-0ubuntu6, automatic), libjavascriptcoregtk-3.0-0:i386 (1.8.3-0ubuntu0.12.04.1, automatic), gir1.2-webkit-3.0:i386 (1.8.3-0ubuntu0.12.04.1, automatic), python-lazr.uri:i386 (1.0.3-1, automatic), libvte-2.90-9:i386 (0.32.1-0ubuntu1, automatic), dbus:i386 (1.4.18-1ubuntu1.3, automatic), gir1.2-freedesktop:i386 (1.32.0-1, automatic), libcmis-0.2-0:i386 (0.1.0-1, automatic), libxcb1:i386 (1.8.1-1ubuntu0.1, automatic), libpeas-1.0-0:i386 (1.2.0-1ubuntu1, automatic), libglibmm-2.4-1c2a:i386 (2.32.0-0ubuntu1, automatic), syslinux-legacy:i386 (3.63+dfsg-2ubuntu5, automatic), apg:i386 (2.2.3.dfsg.1-2, automatic), indicator-messages:i386 (0.6.0-0ubuntu2, automatic), ubuntu-sso-client-gtk:i386 (3.0.2-0ubuntu3, automatic), libreoffice-base-core:i386 (3.5.4-0ubuntu1.1, automatic), gnome-orca:i386 (3.4.2-0ubuntu0.1), libaccountsservice0:i386 (0.6.15-2ubuntu9.4, automatic), python-markupsafe:i386 (0.15-1, automatic), libp11-kit0:i386 (0.12-2ubuntu1, automatic), time:i386 (1.7-23.1), firefox:i386 (18.0.2+build1-0ubuntu0.12.04.1, automatic), xbitmaps:i386 (1.1.1-1, automatic), samba-common-bin:i386 (3.6.3-2ubuntu2.3, automatic), xserver-xorg-video-sisusb-lts-quantal:i386 (0.9.6-0ubuntu1~precise1, automatic), libgee2:i386 (0.6.4-1, automatic), libglapi-mesa-lts-quantal:i386 (9.0-0ubuntu1~precise4, automatic), libgnome2-common:i386 (2.32.1-2ubuntu1.1, automatic), libatkmm-1.6-1:i386 (2.22.6-1ubuntu1, automatic), printer-driver-ptouch:i386 (1.3-3ubuntu0.1), cups-common:i386 (1.5.3-0ubuntu6, automatic), powermgmt-base:i386 (1.31, automatic), uno-libs3:i386 (3.5.4-0ubuntu1.1, automatic), libmythes-1.2-0:i386 (1.2.2-1, automatic), rtkit:i386 (0.10-2, automatic), libstartup-notification0:i386 (0.12-1ubuntu1, automatic), libxau6:i386 (1.0.6-4, automatic), libedataserverui-3.0-1:i386 (3.2.3-0ubuntu7, automatic), gir1.2-dbusmenu-gtk-0.4:i386 (0.6.2-0ubuntu0.1, automatic), rhythmbox-plugin-cdrecorder:i386 (2.96-0ubuntu4.2, automatic), telepathy-haze:i386 (0.6.0-0ubuntu1, automatic), libexempi3:i386 (2.2.0-1, automatic), xserver-xorg-lts-quantal:i386 (7.7+1ubuntu4~precise1), gconf-service:i386 (3.2.5-0ubuntu2, automatic), libxxf86dga1:i386 (1.1.2-1, automatic), libfile-mimeinfo-perl:i386 (0.15-2, automatic), libcdio-cdda1:i386 (0.83-1, automatic), libhpmud0:i386 (3.12.2-1ubuntu3.1, automatic), libxaw7:i386 (1.0.9-3ubuntu1, automatic), libgdata13:i386 (0.12.0-1, automatic), gtk2-engines:i386 (2.20.2-1ubuntu1, automatic), cpp:i386 (4.6.3-1ubuntu5, automatic), grub-gfxpayload-lists:i386 (0.6, automatic), libpango1.0-0:i386 (1.30.0-0ubuntu3.1, automatic), libubuntuoneui-3.0-1:i386 (3.0.1-0ubuntu1, automatic), remmina-common:i386 (1.0.0-1ubuntu6.1, automatic), python-imaging:i386 (1.1.7-4, automatic), librhythmbox-core5:i386 (2.96-0ubuntu4.2, automatic), liblwres80:i386 (9.8.1.dfsg.P1-4ubuntu0.5, automatic), libkpathsea5:i386 (2009-11ubuntu2, automatic), fonts-tlwg-umpush:i386 (0.4.17-1ubuntu1, automatic), libijs-0.35:i386 (0.35-8, automatic), libgdbm3:i386 (1.8.3-10, automatic), libreoffice-help-en-us:i386 (3.5.4-0ubuntu1.1), xserver-xorg-video-ati-lts-quantal:i386 (6.99.99~git20120913.8637f772-0ubuntu1~precise2, automatic), at-spi2-core:i386 (2.4.2-0ubuntu0.1), libcups2:i386 (1.5.3-0ubuntu6, automatic), libt1-5:i386 (5.1.2-3.4ubuntu1, automatic), xserver-xorg-video-savage-lts-quantal:i386 (2.3.6-0ubuntu1~precise1, automatic), python-speechd:i386 (0.7.1-6ubuntu3, automatic), gcc:i386 (4.6.3-1ubuntu5), libhunspell-1.3-0:i386 (1.3.2-4, automatic), libgdu0:i386 (3.0.2-2ubuntu7, automatic), gdb:i386 (7.4-2012.04-0ubuntu2.1, automatic), landscape-client-ui-install:i386 (12.05-0ubuntu1.12.04), liblightdm-gobject-1-0:i386 (1.2.3-0ubuntu1, automatic), ubuntu-wallpapers-precise:i386 (0.34.1), libsonic0:i386 (0.1.17-1.1, automatic), libtag1-vanilla:i386 (1.7-1ubuntu5, automatic), gs-cjk-resource:i386 (1.20100103-3, automatic), libcurl3:i386 (7.22.0-3ubuntu4, automatic), eog:i386 (3.4.2-0ubuntu1.1), compiz-plugins-main-default:i386 (0.9.7.0~bzr19-0ubuntu10, automatic), xserver-xorg-video-s3-lts-quantal:i386 (0.6.5-0ubuntu1~precise1, automatic), xfonts-base:i386 (1.0.3, automatic), libwebkitgtk-3.0-common:i386 (1.8.3-0ubuntu0.12.04.1, automatic), libavc1394-0:i386 (0.5.3-1ubuntu2, automatic), libdbusmenu-qt2:i386 (0.9.2-0ubuntu1, automatic), libsigc++-2.0-0c2a:i386 (2.2.10-0ubuntu2, automatic), gwibber-service-twitter:i386 (3.4.2-0ubuntu2.1, automatic), libpangomm-1.4-1:i386 (2.28.4-1ubuntu1, automatic), busybox-static:i386 (1.18.5-1ubuntu4.1), libqtcore4:i386 (4.8.1-0ubuntu4.3, automatic), libavahi-gobject0:i386 (0.6.30-5ubuntu2, automatic), libprotobuf7:i386 (2.4.1-1ubuntu2, automatic), gnome-disk-utility:i386 (3.0.2-2ubuntu7), geoclue-ubuntu-geoip:i386 (0.0.2-0ubuntu6, automatic), liblouis2:i386 (2.3.0-3, automatic), python-uno:i386 (3.5.4-0ubuntu1.1, automatic), libreoffice-style-human:i386 (3.5.4-0ubuntu1.1, automatic), libgtk-3-0:i386 (3.4.2-0ubuntu0.5, automatic), python-brlapi:i386 (4.3-1ubuntu5, automatic), obexd-client:i386 (0.44-0ubuntu1, automatic), libgtk2.0-bin:i386 (2.24.10-0ubuntu6, automatic), ftp:i386 (0.17-25), python-xdg:i386 (0.19-3ubuntu2, automatic), fonts-tlwg-sawasdee:i386 (0.4.17-1ubuntu1, automatic), gconf-service-backend:i386 (3.2.5-0ubuntu2, automatic), fonts-tlwg-norasi:i386 (0.4.17-1ubuntu1, automatic), crda:i386 (1.1.2-1ubuntu1, automatic), libxft2:i386 (2.2.0-3ubuntu2, automatic), pciutils:i386 (3.1.8-2ubuntu5, automatic), fonts-tlwg-typo:i386 (0.4.17-1ubuntu1, automatic), libgwibber2:i386 (3.4.2-0ubuntu2.1, automatic), gir1.2-glib-2.0:i386 (1.32.0-1, automatic), sessioninstaller:i386 (0.20+bzr128-0ubuntu1.2, automatic), espeak-data:i386 (1.46.02-0ubuntu1, automatic), launchpad-integration:i386 (0.1.56.1, automatic), libdbusmenu-gtk4:i386 (0.6.2-0ubuntu0.1, automatic), libgssapi3-heimdal:i386 (1.6~git20120311.dfsg.1-2, automatic), libtelepathy-logger2:i386 (0.4.0-0ubuntu1, automatic), pulseaudio-module-bluetooth:i386 (1.1-0ubuntu15.2), telepathy-idle:i386 (0.1.11-2), dictionaries-common:i386 (1.12.1ubuntu2, automatic), syslinux-common:i386 (4.05+dfsg-2, automatic), libgutenprint2:i386 (5.2.8~pre1-0ubuntu2.1, automatic), usb-creator-gtk:i386 (0.2.38), libedata-cal-1.2-13:i386 (3.2.3-0ubuntu7, automatic), unattended-upgrades:i386 (0.76ubuntu1, automatic), libnm-glib4:i386 (0.9.4.0-0ubuntu4.2, automatic), libxcb-shape0:i386 (1.8.1-1ubuntu0.1, automatic), gir1.2-dee-1.0:i386 (1.0.10-0ubuntu1, automatic), usb-creator-common:i386 (0.2.38, automatic), alsa-utils:i386 (1.0.25-1ubuntu5, automatic), libxcomposite1:i386 (0.4.3-2build1, automatic), libgtk2-perl:i386 (1.223-1build3, automatic), libcroco3:i386 (0.6.5-1, automatic), libjbig2dec0:i386 (0.11-1ubuntu1, automatic), gnome-session-bin:i386 (3.2.1-0ubuntu8, automatic), libvte-2.90-common:i386 (0.32.1-0ubuntu1, automatic), libtelepathy-farstream2:i386 (0.4.0-0ubuntu1, automatic), libgweather-common:i386 (3.4.1-0ubuntu1, automatic), python-xapian:i386 (1.2.8-1, automatic), activity-log-manager-common:i386 (0.9.4-0ubuntu3.2, automatic), python-smbc:i386 (1.0.13-0ubuntu1, automatic), dconf-service:i386 (0.12.0-0ubuntu1.1, automatic), app-install-data-partner:i386 (12.12.04.1), libfreerdp-plugins-standard:i386 (1.0.1-1ubuntu2.2, automatic), gstreamer0.10-pulseaudio:i386 (0.10.31-1ubuntu1, automatic), libtheora0:i386 (1.1.1+dfsg.1-3ubuntu2, automatic), libice6:i386 (1.0.7-2build1, automatic), update-inetd:i386 (4.41, automatic), gir1.2-wnck-3.0:i386 (3.4.0-0ubuntu1, automatic), libaa1:i386 (1.4p5-39ubuntu1, automatic), fonts-liberation:i386 (1.07.0-2ubuntu0.1), avahi-autoipd:i386 (0.6.30-5ubuntu2), xserver-xorg-video-mach64-lts-quantal:i386 (6.9.3-0ubuntu1~precise2, automatic), libevince3-3:i386 (3.4.0-0ubuntu1.4, automatic), ca-certificates:i386 (20111211), pulseaudio-module-x11:i386 (1.1-0ubuntu15.2, automatic), libxdmcp6:i386 (1.1.0-4, automatic), libqt4-sql-sqlite:i386 (4.8.1-0ubuntu4.3), libpipeline1:i386 (1.2.1-1, automatic), libgcrypt11:i386 (1.5.0-3ubuntu0.1, automatic), libgphoto2-l10n:i386 (2.4.13-1ubuntu1.2, automatic), libnux-2.0-0:i386 (2.14.1-0ubuntu1, automatic), wodim:i386 (1.1.11-2ubuntu2, automatic), libthai0:i386 (0.1.16-3, automatic), python-louis:i386 (2.3.0-3, automatic), ssl-cert:i386 (1.0.28ubuntu0.1, automatic), indicator-status-provider-mc5:i386 (0.6.0-0ubuntu2, automatic), rsync:i386 (3.0.9-1ubuntu1), vino:i386 (3.4.2-0ubuntu1.2), gir1.2-pango-1.0:i386 (1.30.0-0ubuntu3.1, automatic), python-dbus:i386 (1.0.0-1ubuntu1, automatic), mousetweaks:i386 (3.4.1-0ubuntu1, automatic), aptdaemon:i386 (0.43+bzr805-0ubuntu7, automatic), libpython2.7:i386 (2.7.3-0ubuntu3.1, automatic), libgail-3-0:i386 (3.4.2-0ubuntu0.5, automatic), gnome-system-monitor:i386 (3.4.1-0ubuntu1), libgmime-2.6-0:i386 (2.6.7-1, automatic), system-config-printer-common:i386 (1.3.8+20120201-0ubuntu8.1, automatic), manpages:i386 (3.35-0.1ubuntu1, automatic), gnome-online-accounts:i386 (3.4.0-0ubuntu1, automatic), anacron:i386 (2.3-14ubuntu1), unity-lens-music:i386 (5.12.0-0ubuntu2, automatic), libxml2:i386 (2.7.8.dfsg-5.1ubuntu4.3, automatic), libcanberra-gtk0:i386 (0.28-3ubuntu3, automatic), usb-modeswitch-data:i386 (20120120-0ubuntu1, automatic), python-gnupginterface:i386 (0.3.2-9.1ubuntu3, automatic), libimobiledevice2:i386 (1.1.1-4, automatic), libxapian22:i386 (1.2.8-1, automatic), unity-common:i386 (5.18.0-0ubuntu2, automatic), libedata-book-1.2-11:i386 (3.2.3-0ubuntu7, automatic), libuuid-perl:i386 (0.02-4ubuntu1, automatic), libbind9-80:i386 (9.8.1.dfsg.P1-4ubuntu0.5, automatic), firefox-gnome-support:i386 (18.0.2+build1-0ubuntu0.12.04.1), libgirepository-1.0-1:i386 (1.32.0-1, automatic), libdee-1.0-4:i386 (1.0.10-0ubuntu1, automatic), gir1.2-notify-0.7:i386 (0.7.5-1, automatic), wget:i386 (1.13.4-2ubuntu1, automatic), cups:i386 (1.5.3-0ubuntu6, automatic), libgudev-1.0-0:i386 (175-0ubuntu9.2, automatic), libsamplerate0:i386 (0.1.8-4, automatic), libdrm-nouveau2:i386 (2.4.39-0ubuntu0.1, automatic), python-problem-report:i386 (2.0.1-0ubuntu17.1, automatic), evince:i386 (3.4.0-0ubuntu1.4), xserver-xorg-video-nouveau-lts-quantal:i386 (1.0.2-0ubuntu3~precise2, automatic), libpam-cap:i386 (2.22-1ubuntu3, automatic), libbluetooth3:i386 (4.98-2ubuntu7, automatic), libfile-desktopentry-perl:i386 (0.04-3, automatic), xserver-xorg-video-fbdev-lts-quantal:i386 (0.4.3-0ubuntu1~precise1, automatic), gnome-games-data:i386 (3.4.1-0ubuntu2.2, automatic), libgtksourceview-3.0-common:i386 (3.4.2-0ubuntu1, automatic), libgoa-1.0-0:i386 (3.4.0-0ubuntu1, automatic), growisofs:i386 (7.1-10, automatic), libjpeg-turbo8:i386 (1.1.90+svn733-0ubuntu4.1, automatic), libxmu6:i386 (1.1.0-3, automatic), libcdparanoia0:i386 (3.10.2+debian-10ubuntu1, automatic), libgpm2:i386 (1.20.4-4, automatic), plymouth-theme-ubuntu-logo:i386 (0.8.2-2ubuntu31), libtimezonemap1:i386 (0.3.2, automatic), media-player-info:i386 (16-1, automatic), pm-utils:i386 (1.4.1-9, automatic), python-piston-mini-client:i386 (0.7.2+bzr57-0ubuntu1, automatic), telepathy-mission-control-5:i386 (5.12.0-0ubuntu2.1, automatic), libroken18-heimdal:i386 (1.6~git20120311.dfsg.1-2, automatic), notify-osd-icons:i386 (0.7, automatic), libspeechd2:i386 (0.7.1-6ubuntu3, automatic), libqt4-sql:i386 (4.8.1-0ubuntu4.3, automatic), libcupsdriver1:i386 (1.5.3-0ubuntu6, automatic), libglib2.0-data:i386 (2.32.3-0ubuntu1, automatic), libatk-adaptor-schemas:i386 (2.4.0-1ubuntu2, automatic), pulseaudio-utils:i386 (1.1-0ubuntu15.2, automatic), gnome-user-guide:i386 (3.4.1-1, automatic), xdiagnose:i386 (2.5.2ubuntu0.1), fonts-tlwg-waree:i386 (0.4.17-1ubuntu1, automatic), libasound2:i386 (1.0.25-1ubuntu10.1, automatic), unity-2d-spread:i386 (5.12.0-0ubuntu1.2, automatic), libatk1.0-data:i386 (2.4.0-0ubuntu1, automatic), libjson-glib-1.0-0:i386 (0.14.2-1, automatic), telepathy-logger:i386 (0.4.0-0ubuntu1, automatic), bsdmainutils:i386 (8.2.3ubuntu1, automatic), libwnck-3-0:i386 (3.4.0-0ubuntu1, automatic), libxpm4:i386 (3.5.9-4, automatic), libflac8:i386 (1.2.1-6, automatic), libqt4-svg:i386 (4.8.1-0ubuntu4.3, automatic), libgpg-error0:i386 (1.10-2ubuntu1, automatic), apturl:i386 (0.5.1ubuntu3, automatic), im-switch:i386 (1.20ubuntu5.1, automatic), python-launchpadlib:i386 (1.9.12-1, automatic), ppp:i386 (2.4.5-5ubuntu1, automatic), gnome-sudoku:i386 (3.4.1-0ubuntu2.2), xdg-utils:i386 (1.1.0~rc1-2ubuntu6, automatic), python-dateutil:i386 (1.5-1, automatic), libxrender1:i386 (0.9.6-2build1, automatic), xinit:i386 (1.3.1-1, automatic), iputils-arping:i386 (20101006-1ubuntu1, automatic), libgeis1:i386 (2.2.9.2-0ubuntu1, automatic), printer-driver-pnm2ppa:i386 (1.13+nondbs-0ubuntu1, automatic), ubuntu-mono:i386 (0.0.40, automatic), python-appindicator:i386 (0.4.92-0ubuntu1, automatic), libmtp-runtime:i386 (1.1.3-1ubuntu0.1, automatic), gir1.2-gnomebluetooth-1.0:i386 (3.2.2-0ubuntu5, automatic), libreoffice-impress:i386 (3.5.4-0ubuntu1.1), libnspr4:i386 (4.9.4-0ubuntu0.12.04.1, automatic), liboverlay-scrollbar3-0.2-0:i386 (0.2.16-0ubuntu1.1, automatic), libespeak1:i386 (1.46.02-0ubuntu1, automatic), x11-session-utils:i386 (7.6+2, automatic), libshout3:i386 (2.2.2-7ubuntu1, automatic), telepathy-gabble:i386 (0.16.0-0ubuntu2, automatic), xserver-xorg-video-vesa-lts-quantal:i386 (2.3.2-0ubuntu1~precise1, automatic), sgml-base:i386 (1.26+nmu1ubuntu1, automatic), ibus-pinyin-db-android:i386 (1.4.0-1, automatic), libnautilus-extension1a:i386 (3.4.2-0ubuntu6, automatic), libdv4:i386 (1.0.0-3ubuntu1, automatic), gwibber-service-identica:i386 (3.4.2-0ubuntu2.1, automatic), python-packagekit:i386 (0.7.2-4ubuntu3, automatic), libwbclient0:i386 (3.6.3-2ubuntu2.3, automatic), ubuntu-extras-keyring:i386 (2010.09.27, automatic), usb-modeswitch:i386 (1.2.3+repack0-1ubuntu2, automatic), software-properties-common:i386 (0.82.7.3, automatic), indicator-datetime:i386 (0.3.94-0ubuntu2, automatic), python-oauth:i386 (1.0.1-3build1, automatic), nautilus-share:i386 (0.7.3-1ubuntu2), os-prober:i386 (1.51ubuntu3, automatic), libdevmapper-event1.02.1:i386 (1.02.48-4ubuntu7.1, automatic), openprinting-ppds:i386 (20120322-0ubuntu1), pcmciautils:i386 (018-6), libwps-0.2-2:i386 (0.2.4-1, automatic), printer-driver-splix:i386 (2.0.0+svn300-1.1ubuntu2), liboverlay-scrollbar-0.2-0:i386 (0.2.16-0ubuntu1.1, automatic), printer-driver-hpcups:i386 (3.12.2-1ubuntu3.1, automatic), libfs6:i386 (1.0.3-1, automatic), libgpod-common:i386 (0.8.2-4, automatic), libqt4-xml:i386 (4.8.1-0ubuntu4.3, automatic), libsoup-gnome2.4-1:i386 (2.38.1-1, automatic), evolution-data-server:i386 (3.2.3-0ubuntu7, automatic), gettext-base:i386 (0.18.1.1-5ubuntu3, automatic), python-gnomekeyring:i386 (2.32.0+dfsg-1, automatic), libasyncns0:i386 (0.8-4, automatic), ufw:i386 (0.31.1-1), rhythmbox-plugins:i386 (2.96-0ubuntu4.2, automatic), linux-headers-3.5.0-23:i386 (3.5.0-23.35~precise1, automatic), xcursor-themes:i386 (1.0.3-1), libdconf0:i386 (0.12.0-0ubuntu1.1, automatic), libiw30:i386 (30~pre9-5ubuntu2, automatic), libgd2-xpm:i386 (2.0.36~rc1~dfsg-6ubuntu2, automatic), libido3-0.1-0:i386 (0.3.4-0ubuntu1, automatic), acpi-support:i386 (0.140), gconf2-common:i386 (3.2.5-0ubuntu2, automatic), grub-pc-bin:i386 (1.99-21ubuntu3.9, automatic), libgs9:i386 (9.05~dfsg-0ubuntu4.2, automatic), python-ubuntu-sso-client:i386 (3.0.2-0ubuntu3, automatic), libunity-core-5.0-5:i386 (5.18.0-0ubuntu2, automatic), libappindicator1:i386 (0.4.92-0ubuntu1, automatic), ginn:i386 (0.2.4.1-0ubuntu1), libkrb5-26-heimdal:i386 (1.6~git20120311.dfsg.1-2, automatic), cups-bsd:i386 (1.5.3-0ubuntu6), libtiff4:i386 (3.9.5-2ubuntu1.4, automatic), libfontenc1:i386 (1.1.0-1, automatic), perl-modules:i386 (5.14.2-6ubuntu2.2, automatic), x11-xserver-utils-lts-quantal:i386 (7.7~3ubuntu1~precise1, automatic), ure:i386 (3.5.4-0ubuntu1.1, automatic), gstreamer0.10-nice:i386 (0.1.1-2ubuntu1, automatic), xul-ext-ubufox:i386 (2.6-0ubuntu0.12.04.1, automatic), libatk-adaptor:i386 (2.4.0-1ubuntu2), fonts-opensymbol:i386 (102.2+LibO3.5.4-0ubuntu1.1, automatic), xserver-xorg-input-vmmouse-lts-quantal:i386 (12.9.0-0ubuntu3~precise1, automatic), software-properties-gtk:i386 (0.82.7.3, automatic), libbrasero-media3-1:i386 (3.4.1-0ubuntu1.1, automatic), libjasper1:i386 (1.900.1-13, automatic), libgtop2-7:i386 (2.28.4-2, automatic), libqt4-network:i386 (4.8.1-0ubuntu4.3, automatic), unity-lens-files:i386 (5.10.0-0ubuntu1, automatic), xserver-xorg-video-intel-lts-quantal:i386 (2.20.9-0ubuntu2~precise2, automatic), rhythmbox-ubuntuone:i386 (3.0.0-0ubuntu1, automatic), libcap-ng0:i386 (0.6.6-1ubuntu1, automatic), libusbmuxd1:i386 (1.0.7-2, automatic), python-libproxy:i386 (0.4.7-0ubuntu4.1, automatic), yelp:i386 (3.4.1-0ubuntu1, automatic), libgeoip1:i386 (1.4.8+dfsg-2, automatic), xfonts-utils:i386 (7.6+1, automatic), python-egenix-mxdatetime:i386 (3.2.1-1ubuntu1, automatic), libquvi7:i386 (0.4.0-1, automatic), libcupsfilters1:i386 (1.0.18-0ubuntu0.1, automatic), libhcrypto4-heimdal:i386 (1.6~git20120311.dfsg.1-2, automatic), gir1.2-rb-3.0:i386 (2.96-0ubuntu4.2, automatic), libperl5.14:i386 (5.14.2-6ubuntu2.2, automatic), libexttextcat0:i386 (3.2.0-1ubuntu1, automatic), libexiv2-11:i386 (0.22-2, automatic), libcdio-paranoia1:i386 (0.83-1, automatic), gir1.2-indicate-0.7:i386 (0.6.92-0ubuntu1, automatic), gir1.2-gmenu-3.0:i386 (3.4.0-0ubuntu1, automatic), wpasupplicant:i386 (0.7.3-6ubuntu2.1, automatic), indicator-appmenu:i386 (0.3.97-0ubuntu1, automatic), libcanberra0:i386 (0.28-3ubuntu3, automatic), libwacom2:i386 (0.4-1ubuntu1, automatic), libebackend-1.2-1:i386 (3.2.3-0ubuntu7, automatic), language-selector-gnome:i386 (0.79.1), libedataserver-1.2-15:i386 (3.2.3-0ubuntu7, automatic), laptop-detect:i386 (0.13.7ubuntu2, automatic), libldap-2.4-2:i386 (2.4.28-1.1ubuntu4.2, automatic), gksu:i386 (2.0.2-6ubuntu1, automatic), libdaemon0:i386 (0.14-2, automatic), libpam-ck-connector:i386 (0.4.5-2, automatic), libfreetype6:i386 (2.4.8-1ubuntu2.1, automatic), libthai-data:i386 (0.1.16-3, automatic), libxtst6:i386 (1.2.0-4, automatic), gnome-icon-theme:i386 (3.4.0-0ubuntu1.1, automatic), libasound2-plugins:i386 (1.0.25-1ubuntu1, automatic), usbutils:i386 (005-1, automatic), unity-greeter:i386 (0.2.9-0ubuntu1, automatic), zeitgeist-datahub:i386 (0.8.2-1ubuntu2, automatic), libxvmc1:i386 (1.0.6-1ubuntu2, automatic), libwnck-3-common:i386 (3.4.0-0ubuntu1, automatic), libisccfg82:i386 (9.8.1.dfsg.P1-4ubuntu0.5, automatic), zip:i386 (3.0-4, automatic), python-gdbm:i386 (2.7.3-1ubuntu1, automatic), libgdk-pixbuf2.0-0:i386 (2.26.1-1, automatic), python-cups:i386 (1.9.61-0ubuntu2, automatic), libcrypt-passwdmd5-perl:i386 (1.3-10, automatic), libgupnp-1.0-4:i386 (0.18.1-2, automatic), whoopsie:i386 (0.1.32), libavahi-client3:i386 (0.6.30-5ubuntu2, automatic), libarchive12:i386 (3.0.3-6ubuntu1, automatic), alsa-base:i386 (1.0.25+dfsg-0ubuntu1), ibus:i386 (1.4.1-3ubuntu1), libc6-dev:i386 (2.15-0ubuntu10.3, automatic), libqtgui4:i386 (4.8.1-0ubuntu4.3, automatic), libgrail5:i386 (3.0.6-0ubuntu0.12.04.01, automatic), libreoffice-math:i386 (3.5.4-0ubuntu1.1, automatic), libpurple-bin:i386 (2.10.3-0ubuntu1.1, automatic), libatspi2.0-0:i386 (2.4.2-0ubuntu0.1, automatic), apparmor:i386 (2.7.102-0ubuntu3.7), linux-headers-generic-lts-quantal:i386 (3.5.0.23.30), dmz-cursor-theme:i386 (0.4.3), ttf-indic-fonts-core:i386 (0.5.11ubuntu1), libcupsimage2:i386 (1.5.3-0ubuntu6, automatic), policykit-desktop-privileges:i386 (0.10), python-configglue:i386 (1.0-1build1, automatic), liblua5.1-0:i386 (5.1.4-12ubuntu1, automatic), libwmf0.2-7-gtk:i386 (0.2.8.4-10ubuntu1), language-selector-common:i386 (0.79.1, automatic), nvidia-common:i386 (0.2.44.2), ghostscript:i386 (9.05~dfsg-0ubuntu4.2, automatic), libtag1c2a:i386 (1.7-1ubuntu5, automatic), pulseaudio-module-gconf:i386 (1.1-0ubuntu15.2), libgnome-keyring-common:i386 (3.2.2-2, automatic), librsvg2-2:i386 (2.36.1-0ubuntu1, automatic), libgnome-menu-3-0:i386 (3.4.0-0ubuntu1, automatic), pppoeconf:i386 (1.20ubuntu1), libcairo-gobject2:i386 (1.10.2-6.1ubuntu3, automatic), cmap-adobe-japan2:i386 (0+20090930-2), libxcb-dri2-0:i386 (1.8.1-1ubuntu0.1, automatic), libpolkit-backend-1-0:i386 (0.104-1ubuntu1, automatic), colord:i386 (0.1.16-2ubuntu0.1, automatic), ibus-table:i386 (1.3.9.20110827-1ubuntu1), libxklavier16:i386 (5.2.1-1ubuntu1, automatic), x11-common:i386 (7.6+12ubuntu2, automatic), python-egenix-mxtools:i386 (3.2.1-1ubuntu1, automatic), libyajl1:i386 (1.0.12-2, automatic), libsane-hpaio:i386 (3.12.2-1ubuntu3.1, automatic), foomatic-filters:i386 (4.0.16-0ubuntu0.2, automatic), gnome-terminal-data:i386 (3.4.1.1-0ubuntu1, automatic), onboard:i386 (0.97.0-0ubuntu4), ttf-wqy-microhei:i386 (0.2.0-beta-1ubuntu1), libmeanwhile1:i386 (1.0.2-4ubuntu1, automatic), libgksu2-0:i386 (2.0.13~pre1-5ubuntu2, automatic), poppler-utils:i386 (0.18.4-1ubuntu3, automatic), mahjongg:i386 (3.4.1-0ubuntu2.2), gstreamer0.10-plugins-base-apps:i386 (0.10.36-1ubuntu0.1), jockey-gtk:i386 (0.9.7-0ubuntu7.7), indicator-sound:i386 (0.8.5.0-0ubuntu2.1, automatic), libsnmp-base:i386 (5.4.3~dfsg-2.4ubuntu1.1, automatic), libsysfs2:i386 (2.1.0+repack-1, automatic), libcanberra-pulse:i386 (0.28-3ubuntu3, automatic), libx11-6:i386 (1.4.99.1-0ubuntu2, automatic), python-pkg-resources:i386 (0.6.24-1ubuntu1, automatic), gir1.2-vte-2.90:i386 (0.32.1-0ubuntu1, automatic), fuse:i386 (2.8.6-2ubuntu2, automatic), xorg:i386 (7.6+12ubuntu2), python-pyatspi2:i386 (2.4.0+dfsg-0ubuntu3, automatic), libsasl2-2:i386 (2.1.25.dfsg1-3ubuntu0.1, automatic), xserver-xorg-video-openchrome-lts-quantal:i386 (0.3.1-0ubuntu1~precise2, automatic), libgpgme11:i386 (1.2.0-1.4ubuntu2, automatic), cryptsetup-bin:i386 (1.4.1-2ubuntu4, automatic), libindicate5:i386 (0.6.92-0ubuntu1, automatic), wireless-regdb:i386 (2011.04.28-1ubuntu3, automatic), libsgutils2-2:i386 (1.33-1, automatic), man-db:i386 (2.6.1-2ubuntu1, automatic), dconf-gsettings-backend:i386 (0.12.0-0ubuntu1.1, automatic), zenity-common:i386 (3.4.0-0ubuntu4, automatic), gtk2-engines-murrine:i386 (0.98.2-0ubuntu1, automatic), libgweather-3-0:i386 (3.4.1-0ubuntu1, automatic), unity-scope-video-remote:i386 (0.3.5-0ubuntu2.1, automatic), indicator-session:i386 (0.3.96-0ubuntu1, automatic), ubuntuone-installer:i386 (3.0.2-0ubuntu1.1, automatic), radeontool:i386 (1.6.2-1.1, automatic), openssl:i386 (1.0.1-4ubuntu5.5, automatic), libzephyr4:i386 (3.0.1-1, automatic), gnome-control-center-data:i386 (3.4.2-0ubuntu0.9, automatic), samba-common:i386 (3.6.3-2ubuntu2.3, automatic), libquadmath0:i386 (4.6.3-1ubuntu5, automatic), libunity-misc4:i386 (4.0.4-0ubuntu2, automatic), checkbox-qt:i386 (0.13.9), libsm6:i386 (1.2.0-2build1, automatic), cpp-4.6:i386 (4.6.3-1ubuntu5, automatic), libpulse0:i386 (1.1-0ubuntu15.2, automatic), brasero:i386 (3.4.1-0ubuntu1.1, automatic), linux-sound-base:i386 (1.0.25+dfsg-0ubuntu1, automatic), libmhash2:i386 (0.9.9.9-1, automatic), gnome-icon-theme-symbolic:i386 (3.4.0-1, automatic), libavahi-glib1:i386 (0.6.30-5ubuntu2, automatic), libappindicator3-1:i386 (0.4.92-0ubuntu1, automatic), adium-theme-ubuntu:i386 (0.3.2-0ubuntu1, automatic), nux-tools:i386 (2.14.1-0ubuntu1, automatic), fonts-kacst:i386 (2.01+mry-3, automatic), libwind0-heimdal:i386 (1.6~git20120311.dfsg.1-2, automatic), libpulsedsp:i386 (1.1-0ubuntu15.2, automatic), libjte1:i386 (1.19-1, automatic), compiz:i386 (0.9.7.12-0ubuntu1, automatic), libxdamage1:i386 (1.1.3-2build1, automatic), speech-dispatcher:i386 (0.7.1-6ubuntu3), fonts-kacst-one:i386 (5.0+svn11846-2), gvfs:i386 (1.12.1-0ubuntu1.1, automatic), python-ubuntuone-client:i386 (3.0.2-0ubuntu1, automatic), ltrace:i386 (0.5.3-2.1ubuntu2), libreoffice-common:i386 (3.5.4-0ubuntu1.1, automatic), patch:i386 (2.6.1-3, automatic), libindicator3-7:i386 (0.5.0-0ubuntu1, automatic), libgtk-3-bin:i386 (3.4.2-0ubuntu0.5, automatic), x11-xkb-utils:i386 (7.6+4, automatic), libgssapi-krb5-2:i386 (1.10+dfsg~beta1-2ubuntu0.3, automatic), gwibber-service-facebook:i386 (3.4.2-0ubuntu2.1, automatic), libcairo-perl:i386 (1.081-1build2, automatic), xserver-xorg-video-tdfx-lts-quantal:i386 (1.4.5-0ubuntu1~precise2, automatic), yelp-xsl:i386 (3.4.1-1, automatic), gvfs-backends:i386 (1.12.1-0ubuntu1.1, automatic), xfonts-mathml:i386 (4ubuntu1, automatic), libnl-genl-3-200:i386 (3.2.3-2ubuntu2, automatic), python-gobject-2:i386 (2.28.6-10ubuntu1, automatic), libisofs6:i386 (1.1.6-1ubuntu1, automatic), grub-common:i386 (1.99-21ubuntu3.9, automatic), libnm-gtk-common:i386 (0.9.4.1-0ubuntu2, automatic), fonts-nanum:i386 (3.010-2), info:i386 (4.13a.dfsg.1-8ubuntu2), gwibber:i386 (3.4.2-0ubuntu2.1), libvisual-0.4-0:i386 (0.4.0-4, automatic), python-apport:i386 (2.0.1-0ubuntu17.1, automatic), fonts-tlwg-kinnari:i386 (0.4.17-1ubuntu1, automatic), libexif12:i386 (0.6.20-2ubuntu0.1, automatic), libfreerdp1:i386 (1.0.1-1ubuntu2.2, automatic), python-xkit:i386 (0.4.2.3build1, automatic), librtmp0:i386 (2.4~20110711.gitc28f1bab-1, automatic), libqt4-script:i386 (4.8.1-0ubuntu4.3, automatic), dbus-x11:i386 (1.4.18-1ubuntu1.3, automatic), libxi6:i386 (1.6.0-0ubuntu2, automatic), intel-gpu-tools:i386 (1.2-1, automatic), libvorbis0a:i386 (1.3.2-1ubuntu3, automatic), libisc83:i386 (9.8.1.dfsg.P1-4ubuntu0.5, automatic), compiz-core:i386 (0.9.7.12-0ubuntu1, automatic), totem:i386 (3.0.1-0ubuntu21.1), gnome-accessibility-themes:i386 (3.4.1-0ubuntu1.2), xserver-xorg-video-mga-lts-quantal:i386 (1.6.2-0ubuntu1~precise2, automatic), liblouis-data:i386 (2.3.0-3, automatic), libgnome-control-center1:i386 (3.4.2-0ubuntu0.9, automatic), libv4lconvert0:i386 (0.8.6-1ubuntu2, automatic), python-cupshelpers:i386 (1.3.8+20120201-0ubuntu8.1, automatic), linux-headers-3.5.0-23-generic:i386 (3.5.0-23.35~precise1, automatic), evolution-data-server-common:i386 (3.2.3-0ubuntu7, automatic), libxp6:i386 (1.0.1-2), libssh-4:i386 (0.5.2-1ubuntu0.12.04.2, automatic), libaudio2:i386 (1.9.3-4, automatic), libxcursor1:i386 (1.1.12-1, automatic), xfonts-encodings:i386 (1.0.4-1ubuntu1, automatic), libxcb-shm0:i386 (1.8.1-1ubuntu0.1, automatic), libavahi-common3:i386 (0.6.30-5ubuntu2, automatic), python-chardet:i386 (2.0.1-2build1, automatic), python-ibus:i386 (1.4.1-3ubuntu1, automatic), binutils:i386 (2.22-6ubuntu1, automatic), libdjvulibre-text:i386 (3.5.24-9, automatic), libxt6:i386 (1.1.1-2build1, automatic), libasn1-8-heimdal:i386 (1.6~git20120311.dfsg.1-2, automatic), gstreamer0.10-plugins-base:i386 (0.10.36-1ubuntu0.1, automatic), desktop-file-utils:i386 (0.20-0ubuntu3, automatic), libxinerama1:i386 (1.1.1-3build1, automatic), libzeitgeist-1.0-1:i386 (0.3.18-1ubuntu1, automatic), libxv1:i386 (1.0.6-2build1, automatic), indicator-power:i386 (2.0-0ubuntu1, automatic), apport-gtk:i386 (2.0.1-0ubuntu17.1, automatic), libxext6:i386 (1.3.0-3build1, automatic), libgstreamer-plugins-base0.10-0:i386 (0.10.36-1ubuntu0.1, automatic), transmission-common:i386 (2.51-0ubuntu1.1, automatic), gnome-session:i386 (3.2.1-0ubuntu8), mscompress:i386 (0.3-3.1, automatic), python-reportlab:i386 (2.5-1.1build1, automatic), libprotoc7:i386 (2.4.1-1ubuntu2, automatic), printer-driver-min12xxw:i386 (0.0.9-6ubuntu1, automatic), iptables:i386 (1.4.12-1ubuntu4, automatic), ttf-ubuntu-font-family:i386 (0.80-0ubuntu2), librsync1:i386 (0.9.7-8build1, automatic), xserver-xorg-video-radeon-lts-quantal:i386 (6.99.99~git20120913.8637f772-0ubuntu1~precise2, automatic), libxrandr2:i386 (1.3.2-2, automatic), libfarstream-0.1-0:i386 (0.1.2-0ubuntu1, automatic), liboauth0:i386 (0.9.4-3, automatic), libbamf3-0:i386 (0.2.124.2-0ubuntu1, automatic), liblaunchpad-integration-3.0-1:i386 (0.1.56.1, automatic), linux-image-3.5.0-23-generic:i386 (3.5.0-23.35~precise1), fonts-tlwg-loma:i386 (0.4.17-1ubuntu1, automatic), python-twisted-bin:i386 (11.1.0-1ubuntu2, automatic), libcurl3-nss:i386 (7.22.0-3ubuntu4, automatic), gstreamer0.10-tools:i386 (0.10.36-1ubuntu1, automatic), gir1.2-totem-plparser-1.0:i386 (3.4.1-1, automatic), appmenu-gtk3:i386 (0.3.92-0ubuntu1.1, automatic), librsvg2-common:i386 (2.36.1-0ubuntu1, automatic), libavahi-core7:i386 (0.6.30-5ubuntu2, automatic), ntfs-3g:i386 (2012.1.15AR.1-1ubuntu1.2, automatic), python-gtk2:i386 (2.24.0-3, automatic), indicator-printers:i386 (0.1.6-0ubuntu1, automatic), libsndfile1:i386 (1.0.25-4, automatic), linux-firmware:i386 (1.79.1), xserver-common-lts-quantal:i386 (1.13.0-0ubuntu6.1~precise2, automatic), libbamf0:i386 (0.2.124.2-0ubuntu1, automatic), libaspell15:i386 (0.60.7~20110707-1, automatic), dmidecode:i386 (2.11-4, automatic), modemmanager:i386 (0.5.2.0-0ubuntu2, automatic), totem-mozilla:i386 (3.0.1-0ubuntu21.1, automatic), libreoffice-style-tango:i386 (3.5.4-0ubuntu1.1, automatic), libgupnp-igd-1.0-4:i386 (0.2.1-2, automatic), libwpd-0.9-9:i386 (0.9.4-1, automatic), libmng1:i386 (1.0.10-3, automatic), kerneloops-daemon:i386 (0.12+git20090217-1ubuntu19), python-cairo:i386 (1.8.8-1ubuntu3, automatic), xserver-xorg-input-mouse-lts-quantal:i386 (1.7.2-2build1~precise1, automatic), libgtk2.0-0:i386 (2.24.10-0ubuntu6, automatic), python-httplib2:i386 (0.7.2-1ubuntu2, automatic), libreoffice-gtk:i386 (3.5.4-0ubuntu1.1, automatic), gir1.2-peas-1.0:i386 (1.2.0-1ubuntu1, automatic), make:i386 (3.81-8.1ubuntu1.1), rhythmbox-plugin-magnatune:i386 (2.96-0ubuntu4.2), gnome-system-log:i386 (3.4.1-0ubuntu1), example-content:i386 (46), libpolkit-agent-1-0:i386 (0.104-1ubuntu1, automatic), gsfonts:i386 (8.11+urwcyr1.0.7~pre44-4.2ubuntu1, automatic), libxkbfile1:i386 (1.0.7-1ubuntu0.1, automatic), file-roller:i386 (3.4.1-0ubuntu1), libmpc2:i386 (0.9-4, automatic), libopenobex1:i386 (1.5-2build1, automatic), libspeexdsp1:i386 (1.2~rc1-3ubuntu2, automatic), compiz-gnome:i386 (0.9.7.12-0ubuntu1, automatic), libneon27-gnutls:i386 (0.29.6-1, automatic), python-zeitgeist:i386 (0.9.0-1ubuntu1, automatic), nautilus-sendto:i386 (3.0.1-2ubuntu2, automatic), libpaper1:i386 (1.1.24+nmu1build1, automatic), transmission-gtk:i386 (2.51-0ubuntu1.1), libltdl7:i386 (2.4.2-1ubuntu1, automatic), libvisual-0.4-plugins:i386 (0.4.0.dfsg.1-7, automatic), remmina:i386 (1.0.0-1ubuntu6.1), libgdata-common:i386 (0.12.0-1, automatic), empathy-common:i386 (3.4.2.3-0ubuntu1, automatic), ssh-askpass-gnome:i386 (5.9p1-5ubuntu1), libpoppler-glib8:i386 (0.18.4-1ubuntu3, automatic), hwdata:i386 (0.233-1ubuntu1, automatic), hplip-data:i386 (3.12.2-1ubuntu3.1, automatic), python-gobject:i386 (3.2.2-1~precise, automatic), libllvm3.1:i386 (3.1-2ubuntu1~12.04, automatic), libdotconf1.0:i386 (1.0.13-3, automatic), libindicator-messages-status-provider1:i386 (0.6.0-0ubuntu2, automatic), ghostscript-cups:i386 (9.05~dfsg-0ubuntu4.2, automatic), libogg0:i386 (1.2.2~dfsg-1ubuntu1, automatic), libmetacity-private0:i386 (2.34.1-1ubuntu11, automatic), libmusicbrainz3-6:i386 (3.0.2-2.1, automatic), libibus-1.0-0:i386 (1.4.1-3ubuntu1, automatic), gnomine:i386 (3.4.1-0ubuntu2.2), libyaml-tiny-perl:i386 (1.50-1, automatic), consolekit:i386 (0.4.5-2, automatic), python-apt-common:i386 (0.8.3ubuntu7, automatic)
End-Date: 2013-02-13  22:10:56

Start-Date: 2013-02-13  22:11:00
Commandline: apt-get --yes install lupin-casper
Install: casper:i386 (1.315.1, automatic), lupin-casper:i386 (0.51), user-setup:i386 (1.42ubuntu3, automatic), localechooser-data:i386 (2.39ubuntu2, automatic)
End-Date: 2013-02-13  22:11:02

Start-Date: 2013-02-13  22:11:09
Commandline: apt-get --yes install ubuntu-live^
Install: wamerican:i386 (7.1-1), language-pack-pt-base:i386 (12.04+20130128), language-pack-zh-hans:i386 (12.04+20130128), gir1.2-json-1.0:i386 (0.14.2-1), realpath:i386 (1.16), libdmraid1.0.0.rc16:i386 (1.0.0.rc16-4.1ubuntu8), language-pack-en-base:i386 (12.04+20130128), ubiquity-frontend-gtk:i386 (2.10.24), language-pack-gnome-zh-hans-base:i386 (12.04+20130128), ubiquity-slideshow-ubuntu:i386 (58.2), gir1.2-timezonemap-1.0:i386 (0.3.2), jfsutils:i386 (1.1.15-2), kpartx-boot:i386 (0.4.9-3ubuntu5), archdetect-deb:i386 (1.88ubuntu2), gparted:i386 (0.11.0-2), language-pack-gnome-pt-base:i386 (12.04+20130128), language-pack-de-base:i386 (12.04+20130128), language-pack-gnome-zh-hans:i386 (12.04+20130128), python-pyicu:i386 (1.3-1), language-pack-gnome-en-base:i386 (12.04+20130128), ubiquity:i386 (2.10.24), libdebian-installer4:i386 (0.79ubuntu2.1), ubiquity-casper:i386 (1.315.1), language-pack-gnome-de-base:i386 (12.04+20130128), kpartx:i386 (0.4.9-3ubuntu5), cryptsetup:i386 (1.4.1-2ubuntu4), libecryptfs0:i386 (96-0ubuntu3), reiserfsprogs:i386 (3.6.21-1build1), rdate:i386 (1.2-4build1), xfsprogs:i386 (3.1.7), language-pack-es-base:i386 (12.04+20130128), btrfs-tools:i386 (0.19+20100601-3ubuntu3), libgtkmm-2.4-1c2a:i386 (2.24.2-1ubuntu1), apt-clone:i386 (0.2.2ubuntu2), gir1.2-xkl-1.0:i386 (5.2.1-1ubuntu1), language-pack-gnome-es-base:i386 (12.04+20130128), ecryptfs-utils:i386 (96-0ubuntu3), ubiquity-ubuntu-artwork:i386 (2.10.24), dpkg-repack:i386 (1.37), cifs-utils:i386 (5.1-1ubuntu1), firefox-locale-de:i386 (18.0.2+build1-0ubuntu0.12.04.1), firefox-locale-en:i386 (18.0.2+build1-0ubuntu0.12.04.1), firefox-locale-es:i386 (18.0.2+build1-0ubuntu0.12.04.1), libdebconfclient0:i386 (0.158ubuntu1), language-pack-zh-hans-base:i386 (12.04+20130128), firefox-locale-pt:i386 (18.0.2+build1-0ubuntu0.12.04.1), firefox-locale-zh-hans:i386 (18.0.2+build1-0ubuntu0.12.04.1), dmraid:i386 (1.0.0.rc16-4.1ubuntu8), language-pack-de:i386 (12.04+20130128), language-pack-en:i386 (12.04+20130128), language-pack-es:i386 (12.04+20130128), language-pack-pt:i386 (12.04+20130128), libreadline5:i386 (5.2-11), libnss3-1d:i386 (3.14.1-0ckbi1.93ubuntu.0.12.04.1), language-pack-gnome-de:i386 (12.04+20130128), keyutils:i386 (1.5.2-2), language-pack-gnome-en:i386 (12.04+20130128), language-pack-gnome-es:i386 (12.04+20130128), language-pack-gnome-pt:i386 (12.04+20130128)
End-Date: 2013-02-13  22:12:06

Start-Date: 2013-02-13  22:13:16
Commandline: apt-get remove --purge -y language-pack-de-base firefox-locale-de
Purge: language-pack-de-base:i386 (12.04+20130128), language-pack-gnome-de-base:i386 (12.04+20130128), firefox-locale-de:i386 (18.0.2+build1-0ubuntu0.12.04.1), language-pack-de:i386 (12.04+20130128), language-pack-gnome-de:i386 (12.04+20130128)
End-Date: 2013-02-13  22:13:18

Start-Date: 2013-02-13  22:13:18
Commandline: apt-get remove --purge -y language-pack-pt-base firefox-locale-pt
Purge: language-pack-pt-base:i386 (12.04+20130128), language-pack-gnome-pt-base:i386 (12.04+20130128), firefox-locale-pt:i386 (18.0.2+build1-0ubuntu0.12.04.1), language-pack-pt:i386 (12.04+20130128), language-pack-gnome-pt:i386 (12.04+20130128)
End-Date: 2013-02-13  22:13:19

Start-Date: 2013-04-21  04:33:25
Install: thunderbird-locale-en-us:i386 (17.0.5+build1-0ubuntu0.12.04.1), mythes-en-us:i386 (3.3.0-2ubuntu3), openoffice.org-hyphenation:i386 (0.6), hyphen-en-us:i386 (2.8.3-1), myspell-en-au:i386 (2.1-5.3ubuntu1), myspell-en-gb:i386 (3.3.0-2ubuntu3), thunderbird-locale-en:i386 (17.0.5+build1-0ubuntu0.12.04.1), poppler-data:i386 (0.4.5-2), myspell-en-za:i386 (3.3.0-2ubuntu3), wbritish:i386 (7.1-1)
Upgrade: thunderbird-globalmenu:i386 (17.0.2+build1-0ubuntu0.12.04.1, 17.0.5+build1-0ubuntu0.12.04.1), libreoffice-calc:i386 (3.5.4-0ubuntu1.1, 3.5.7-0ubuntu4), libreoffice-gnome:i386 (3.5.4-0ubuntu1.1, 3.5.7-0ubuntu4), thunderbird:i386 (17.0.2+build1-0ubuntu0.12.04.1, 17.0.5+build1-0ubuntu0.12.04.1), thunderbird-gnome-support:i386 (17.0.2+build1-0ubuntu0.12.04.1, 17.0.5+build1-0ubuntu0.12.04.1), libreoffice-core:i386 (3.5.4-0ubuntu1.1, 3.5.7-0ubuntu4), libreoffice-writer:i386 (3.5.4-0ubuntu1.1, 3.5.7-0ubuntu4), libreoffice-draw:i386 (3.5.4-0ubuntu1.1, 3.5.7-0ubuntu4), libreoffice-base-core:i386 (3.5.4-0ubuntu1.1, 3.5.7-0ubuntu4), uno-libs3:i386 (3.5.4-0ubuntu1.1, 3.5.7-0ubuntu4), libreoffice-help-en-us:i386 (3.5.4-0ubuntu1.1, 3.5.7-0ubuntu4), python-uno:i386 (3.5.4-0ubuntu1.1, 3.5.7-0ubuntu4), libreoffice-impress:i386 (3.5.4-0ubuntu1.1, 3.5.7-0ubuntu4), ure:i386 (3.5.4-0ubuntu1.1, 3.5.7-0ubuntu4), libreoffice-math:i386 (3.5.4-0ubuntu1.1, 3.5.7-0ubuntu4), firefox-locale-en:i386 (18.0.2+build1-0ubuntu0.12.04.1, 20.0+build1-0ubuntu0.12.04.3), libreoffice-common:i386 (3.5.4-0ubuntu1.1, 3.5.7-0ubuntu4), libreoffice-gtk:i386 (3.5.4-0ubuntu1.1, 3.5.7-0ubuntu4)
End-Date: 2013-04-21  04:34:34

Start-Date: 2013-04-21  04:35:24
End-Date: 2013-04-21  04:35:24

Start-Date: 2013-04-21  04:36:14
Purge: casper:i386 (1.315.1), language-pack-zh-hans:i386 (12.04+20130128), gir1.2-json-1.0:i386 (0.14.2-1), lupin-casper:i386 (0.51), realpath:i386 (1.16), libdmraid1.0.0.rc16:i386 (1.0.0.rc16-4.1ubuntu8), ubiquity-frontend-gtk:i386 (2.10.24), language-pack-gnome-zh-hans-base:i386 (12.04+20130128), ubiquity-slideshow-ubuntu:i386 (58.2), gir1.2-timezonemap-1.0:i386 (0.3.2), jfsutils:i386 (1.1.15-2), kpartx-boot:i386 (0.4.9-3ubuntu5), archdetect-deb:i386 (1.88ubuntu2), gparted:i386 (0.11.0-2), language-pack-gnome-zh-hans:i386 (12.04+20130128), python-pyicu:i386 (1.3-1), ubiquity:i386 (2.10.24), libdebian-installer4:i386 (0.79ubuntu2.1), user-setup:i386 (1.42ubuntu3), ubiquity-casper:i386 (1.315.1), kpartx:i386 (0.4.9-3ubuntu5), cryptsetup:i386 (1.4.1-2ubuntu4), libecryptfs0:i386 (96-0ubuntu3), reiserfsprogs:i386 (3.6.21-1build1), rdate:i386 (1.2-4build1), xfsprogs:i386 (3.1.7), language-pack-es-base:i386 (12.04+20130128), btrfs-tools:i386 (0.19+20100601-3ubuntu3), libgtkmm-2.4-1c2a:i386 (2.24.2-1ubuntu1), localechooser-data:i386 (2.39ubuntu2), apt-clone:i386 (0.2.2ubuntu2), gir1.2-xkl-1.0:i386 (5.2.1-1ubuntu1), language-pack-gnome-es-base:i386 (12.04+20130128), ecryptfs-utils:i386 (96-0ubuntu3), ubiquity-ubuntu-artwork:i386 (2.10.24), dpkg-repack:i386 (1.37), cifs-utils:i386 (5.1-1ubuntu1), firefox-locale-es:i386 (18.0.2+build1-0ubuntu0.12.04.1), libdebconfclient0:i386 (0.158ubuntu1), language-pack-zh-hans-base:i386 (12.04+20130128), firefox-locale-zh-hans:i386 (18.0.2+build1-0ubuntu0.12.04.1), dmraid:i386 (1.0.0.rc16-4.1ubuntu8), language-pack-es:i386 (12.04+20130128), libreadline5:i386 (5.2-11), libnss3-1d:i386 (3.14.1-0ckbi1.93ubuntu.0.12.04.1), keyutils:i386 (1.5.2-2), language-pack-gnome-es:i386 (12.04+20130128)
End-Date: 2013-04-21  04:37:44

Start-Date: 2013-04-21  04:37:49
End-Date: 2013-04-21  04:37:49

Start-Date: 2013-04-21  04:40:26
Install: libopenal1:i386 (1.13-4ubuntu3, automatic), libts-0.0-0:i386 (1.0-10, automatic), libswscale2:i386 (0.8.6-0ubuntu0.12.04.1, automatic), libmodplug1:i386 (0.8.8.4-1, automatic), libtwolame0:i386 (0.3.13-1build1, automatic), libwildmidi1:i386 (0.2.3.4-2.1, automatic), libzbar0:i386 (0.10+doc-7build2, automatic), libavutil51:i386 (0.8.6-0ubuntu0.12.04.1, automatic), libflite1:i386 (1.4-release-4, automatic), libdc1394-22:i386 (2.2.0-2, automatic), gstreamer0.10-plugins-ugly:i386 (0.10.18.3-1ubuntu1), libxvidcore4:i386 (1.3.2-6, automatic), libx264-120:i386 (0.120.2151+gita3f4407-2, automatic), libwildmidi-config:i386 (0.2.3.4-2.1, automatic), libzvbi0:i386 (0.2.33-4, automatic), libdca0:i386 (0.0.5-5, automatic), libopenspc0:i386 (0.3.99a-2, automatic), libpostproc52:i386 (0.8.6-0ubuntu0.12.04.1, automatic), libnspr4-0d:i386 (4.9.5-0ubuntu0.12.04.1, automatic), libfftw3-3:i386 (3.3-1ubuntu1, automatic), libslv2-9:i386 (0.6.6+dfsg1-1, automatic), libass4:i386 (0.10.0-3, automatic), libvo-aacenc0:i386 (0.1.1-2, automatic), libavformat53:i386 (0.8.6-0ubuntu0.12.04.1, automatic), libschroedinger-1.0-0:i386 (1.0.11-1, automatic), libdirectfb-1.2-9:i386 (1.2.10.0-4.3ubuntu1, automatic), gstreamer0.10-ffmpeg:i386 (0.10.13-1), libmp3lame0:i386 (3.99.3+repack1-1, automatic), libenca0:i386 (1.13-4, automatic), libvo-amrwbenc0:i386 (0.1.1-2, automatic), libsoundtouch0:i386 (1.6.0-2build1, automatic), libvpx1:i386 (1.0.0-1, automatic), libzvbi-common:i386 (0.2.33-4, automatic), libgme0:i386 (0.5.5-2, automatic), libspandsp2:i386 (0.0.6~pre18-2build1, automatic), freepats:i386 (20060219-1, automatic), flashplugin-installer:i386 (11.2.202.280ubuntu0.12.04.1), libgsm1:i386 (1.0.13-3, automatic), libdvdnav4:i386 (4.2.0-1, automatic), gstreamer0.10-plugins-bad:i386 (0.10.22.3-2ubuntu2.2), libdvdread4:i386 (4.2.0-1ubuntu3, automatic), libgstreamer-plugins-bad0.10-0:i386 (0.10.22.3-2ubuntu2.2, automatic), libkate1:i386 (0.4.1-1, automatic), ubuntu-restricted-addons:i386 (12), libcdaudio1:i386 (0.99.12p2-10build1, automatic), libmimic0:i386 (1.0.4-2.1build1, automatic), gstreamer0.10-fluendo-mp3:i386 (0.10.15.debian-1ubuntu1), libsidplay1:i386 (1.36.59-5, automatic), libavcodec53:i386 (0.8.6-0ubuntu0.12.04.1, automatic), tsconf:i386 (1.0-10, automatic), libmad0:i386 (0.15.1b-7ubuntu1, automatic), libva1:i386 (1.0.15-4, automatic), liboil0.3:i386 (0.3.17-2ubuntu3, automatic), libopenal-data:i386 (1.13-4ubuntu3, automatic), libopencore-amrnb0:i386 (0.1.2-1, automatic), libcelt0-0:i386 (0.7.1-1, automatic), libdirac-encoder0:i386 (1.0.2-4build1, automatic), libmpcdec6:i386 (0.1~r459-1ubuntu1, automatic), libnss3-1d:i386 (3.14.3-0ubuntu0.12.04.1, automatic), libopencore-amrwb0:i386 (0.1.2-1, automatic), libofa0:i386 (0.9.3-4, automatic), libmpeg2-4:i386 (0.4.1-3, automatic), libmms0:i386 (0.6.2-2, automatic), libfaad2:i386 (2.7-7, automatic), liba52-0.7.4:i386 (0.7.4-16build1, automatic)
Upgrade: libnss3:i386 (3.14.1-0ckbi1.93ubuntu.0.12.04.1, 3.14.3-0ubuntu0.12.04.1), libnspr4:i386 (4.9.4-0ubuntu0.12.04.1, 4.9.5-0ubuntu0.12.04.1)
End-Date: 2013-04-21  04:42:04

Start-Date: 2013-04-21  04:55:01
Commandline: aptdaemon role='role-commit-packages' sender=':1.79'
Install: linux-headers-3.5.0-27-generic:i386 (3.5.0-27.46~precise1), linux-image-3.5.0-27-generic:i386 (3.5.0-27.46~precise1), linux-headers-3.5.0-27:i386 (3.5.0-27.46~precise1)
Upgrade: dmsetup:i386 (1.02.48-4ubuntu7.1, 1.02.48-4ubuntu7.3), libgnomekbd7:i386 (3.4.0.2-1, 3.4.0.2-1ubuntu0.1), libpurple0:i386 (2.10.3-0ubuntu1.1, 2.10.3-0ubuntu1.3), libxatracker1-lts-quantal:i386 (9.0-0ubuntu1~precise4, 9.0.3-0ubuntu0.1~precise2), libqt4-opengl:i386 (4.8.1-0ubuntu4.3, 4.8.1-0ubuntu4.4), gwibber-service:i386 (3.4.2-0ubuntu2.1, 3.4.2-0ubuntu2.2), libqt4-declarative:i386 (4.8.1-0ubuntu4.3, 4.8.1-0ubuntu4.4), nautilus:i386 (3.4.2-0ubuntu6, 3.4.2-0ubuntu8), bind9-host:i386 (9.8.1.dfsg.P1-4ubuntu0.5, 9.8.1.dfsg.P1-4ubuntu0.6), python-aptdaemon.gtk3widgets:i386 (0.43+bzr805-0ubuntu7, 0.43+bzr805-0ubuntu8), python-aptdaemon.pkcompat:i386 (0.43+bzr805-0ubuntu7, 0.43+bzr805-0ubuntu8), usbmuxd:i386 (1.0.7-2, 1.0.7-2ubuntu0.1), libapt-pkg4.12:i386 (0.8.16~exp12ubuntu10.7, 0.8.16~exp12ubuntu10.10), smbclient:i386 (3.6.3-2ubuntu2.3, 3.6.3-2ubuntu2.6), qdbus:i386 (4.8.1-0ubuntu4.3, 4.8.1-0ubuntu4.4), dnsutils:i386 (9.8.1.dfsg.P1-4ubuntu0.5, 9.8.1.dfsg.P1-4ubuntu0.6), aptdaemon-data:i386 (0.43+bzr805-0ubuntu7, 0.43+bzr805-0ubuntu8), libnm-gtk0:i386 (0.9.4.1-0ubuntu2, 0.9.4.1-0ubuntu2.2), xserver-xorg-core-lts-quantal:i386 (1.13.0-0ubuntu6.1~precise2, 1.13.0-0ubuntu6.1~precise3), bamfdaemon:i386 (0.2.124.2-0ubuntu1, 0.2.126-0ubuntu1), python-aptdaemon:i386 (0.43+bzr805-0ubuntu7, 0.43+bzr805-0ubuntu8), perl:i386 (5.14.2-6ubuntu2.2, 5.14.2-6ubuntu2.3), libdbus-glib-1-2:i386 (0.98-1ubuntu1, 0.98-1ubuntu1.1), libqt4-dbus:i386 (4.8.1-0ubuntu4.3, 4.8.1-0ubuntu4.4), gnome-screenshot:i386 (3.4.1-0ubuntu1, 3.4.1-0ubuntu1.1), python-libxml2:i386 (2.7.8.dfsg-5.1ubuntu4.3, 2.7.8.dfsg-5.1ubuntu4.4), lightdm:i386 (1.2.3-0ubuntu1, 1.2.3-0ubuntu2), libglu1-mesa:i386 (8.0.4-0ubuntu0.3, 8.0.4-0ubuntu0.4), apt-transport-https:i386 (0.8.16~exp12ubuntu10.7, 0.8.16~exp12ubuntu10.10), evince-common:i386 (3.4.0-0ubuntu1.4, 3.4.0-0ubuntu1.6), libjack-jackd2-0:i386 (1.9.8~dfsg.1-1ubuntu1, 1.9.8~dfsg.1-1ubuntu2), xserver-common:i386 (1.11.4-0ubuntu10.11, 1.11.4-0ubuntu10.13), accountsservice:i386 (0.6.15-2ubuntu9.4, 0.6.15-2ubuntu9.5), gnome-control-center:i386 (3.4.2-0ubuntu0.9, 3.4.2-0ubuntu0.11), libdrm-intel1:i386 (2.4.39-0ubuntu0.1, 2.4.39-0ubuntu0.2), libdns81:i386 (9.8.1.dfsg.P1-4ubuntu0.5, 9.8.1.dfsg.P1-4ubuntu0.6), linux-generic-lts-quantal:i386 (3.5.0.23.30, 3.5.0.27.34), libxslt1.1:i386 (1.1.26-8ubuntu1.2, 1.1.26-8ubuntu1.3), perl-base:i386 (5.14.2-6ubuntu2.2, 5.14.2-6ubuntu2.3), libgl1-mesa-glx-lts-quantal:i386 (9.0-0ubuntu1~precise4, 9.0.3-0ubuntu0.1~precise2), libreoffice-emailmerge:i386 (3.5.4-0ubuntu1.1, 3.5.7-0ubuntu4), libpoppler19:i386 (0.18.4-1ubuntu3, 0.18.4-1ubuntu3.1), bash:i386 (4.2-2ubuntu2, 4.2-2ubuntu2.1), gir1.2-gudev-1.0:i386 (175-0ubuntu9.2, 175-0ubuntu9.3), libgnutls26:i386 (2.12.14-5ubuntu3.1, 2.12.14-5ubuntu3.2), apport:i386 (2.0.1-0ubuntu17.1, 2.0.1-0ubuntu17.2), gstreamer0.10-gconf:i386 (0.10.31-1ubuntu1, 0.10.31-1ubuntu1.2), linux-libc-dev:i386 (3.2.0-37.58, 3.2.0-40.64), libgoa-1.0-common:i386 (3.4.0-0ubuntu1, 3.4.0-0ubuntu1.1), nautilus-data:i386 (3.4.2-0ubuntu6, 3.4.2-0ubuntu8), libcurl3-gnutls:i386 (7.22.0-3ubuntu4, 7.22.0-3ubuntu4.1), gstreamer0.10-plugins-good:i386 (0.10.31-1ubuntu1, 0.10.31-1ubuntu1.2), liblvm2app2.2:i386 (2.02.66-4ubuntu7.1, 2.02.66-4ubuntu7.3), libsmbclient:i386 (3.6.3-2ubuntu2.3, 3.6.3-2ubuntu2.6), libisccc80:i386 (9.8.1.dfsg.P1-4ubuntu0.5, 9.8.1.dfsg.P1-4ubuntu0.6), libdevmapper1.02.1:i386 (1.02.48-4ubuntu7.1, 1.02.48-4ubuntu7.3), network-manager-gnome:i386 (0.9.4.1-0ubuntu2, 0.9.4.1-0ubuntu2.2), libpciaccess0:i386 (0.12.902-1ubuntu0.1, 0.12.902-1ubuntu0.2), apt-utils:i386 (0.8.16~exp12ubuntu10.7, 0.8.16~exp12ubuntu10.10), dnsmasq-base:i386 (2.59-4, 2.59-4ubuntu0.1), openssh-client:i386 (5.9p1-5ubuntu1, 5.9p1-5ubuntu1.1), libgwibber-gtk2:i386 (3.4.2-0ubuntu2.1, 3.4.2-0ubuntu2.2), deja-dup:i386 (22.0-0ubuntu3, 22.0-0ubuntu4), libgl1-mesa-dri-lts-quantal:i386 (9.0-0ubuntu1~precise4, 9.0.3-0ubuntu0.1~precise2), libgnomekbd-common:i386 (3.4.0.2-1, 3.4.0.2-1ubuntu0.1), libqt4-xmlpatterns:i386 (4.8.1-0ubuntu4.3, 4.8.1-0ubuntu4.4), firefox-globalmenu:i386 (18.0.2+build1-0ubuntu0.12.04.1, 20.0+build1-0ubuntu0.12.04.3), software-center:i386 (5.2.7, 5.2.9), linux-image-generic-lts-quantal:i386 (3.5.0.23.30, 3.5.0.27.34), simple-scan:i386 (3.4.1-0ubuntu1.1, 3.4.3-0ubuntu1), udev:i386 (175-0ubuntu9.2, 175-0ubuntu9.3), libaccountsservice0:i386 (0.6.15-2ubuntu9.4, 0.6.15-2ubuntu9.5), apt:i386 (0.8.16~exp12ubuntu10.7, 0.8.16~exp12ubuntu10.10), firefox:i386 (18.0.2+build1-0ubuntu0.12.04.1, 20.0+build1-0ubuntu0.12.04.3), samba-common-bin:i386 (3.6.3-2ubuntu2.3, 3.6.3-2ubuntu2.6), libdrm2:i386 (2.4.39-0ubuntu0.1, 2.4.39-0ubuntu0.2), libglapi-mesa-lts-quantal:i386 (9.0-0ubuntu1~precise4, 9.0.3-0ubuntu0.1~precise2), liblwres80:i386 (9.8.1.dfsg.P1-4ubuntu0.5, 9.8.1.dfsg.P1-4ubuntu0.6), liblightdm-gobject-1-0:i386 (1.2.3-0ubuntu1, 1.2.3-0ubuntu2), libcurl3:i386 (7.22.0-3ubuntu4, 7.22.0-3ubuntu4.1), gwibber-service-twitter:i386 (3.4.2-0ubuntu2.1, 3.4.2-0ubuntu2.2), libqtcore4:i386 (4.8.1-0ubuntu4.3, 4.8.1-0ubuntu4.4), geoclue-ubuntu-geoip:i386 (0.0.2-0ubuntu6, 0.0.2-0ubuntu6.3), libreoffice-style-human:i386 (3.5.4-0ubuntu1.1, 3.5.7-0ubuntu4), sudo:i386 (1.8.3p1-1ubuntu3.3, 1.8.3p1-1ubuntu3.4), libgwibber2:i386 (3.4.2-0ubuntu2.1, 3.4.2-0ubuntu2.2), libdrm-nouveau1a:i386 (2.4.39-0ubuntu0.1, 2.4.39-0ubuntu0.2), gir1.2-dee-1.0:i386 (1.0.10-0ubuntu1, 1.0.10-0ubuntu1.1), gstreamer0.10-pulseaudio:i386 (0.10.31-1ubuntu1, 0.10.31-1ubuntu1.2), libevince3-3:i386 (3.4.0-0ubuntu1.4, 3.4.0-0ubuntu1.6), libqt4-sql-sqlite:i386 (4.8.1-0ubuntu4.3, 4.8.1-0ubuntu4.4), aptdaemon:i386 (0.43+bzr805-0ubuntu7, 0.43+bzr805-0ubuntu8), gnome-online-accounts:i386 (3.4.0-0ubuntu1, 3.4.0-0ubuntu1.1), libxml2:i386 (2.7.8.dfsg-5.1ubuntu4.3, 2.7.8.dfsg-5.1ubuntu4.4), libbind9-80:i386 (9.8.1.dfsg.P1-4ubuntu0.5, 9.8.1.dfsg.P1-4ubuntu0.6), firefox-gnome-support:i386 (18.0.2+build1-0ubuntu0.12.04.1, 20.0+build1-0ubuntu0.12.04.3), libdee-1.0-4:i386 (1.0.10-0ubuntu1, 1.0.10-0ubuntu1.1), libgudev-1.0-0:i386 (175-0ubuntu9.2, 175-0ubuntu9.3), libdrm-nouveau2:i386 (2.4.39-0ubuntu0.1, 2.4.39-0ubuntu0.2), python-problem-report:i386 (2.0.1-0ubuntu17.1, 2.0.1-0ubuntu17.2), evince:i386 (3.4.0-0ubuntu1.4, 3.4.0-0ubuntu1.6), libgoa-1.0-0:i386 (3.4.0-0ubuntu1, 3.4.0-0ubuntu1.1), libqt4-sql:i386 (4.8.1-0ubuntu4.3, 4.8.1-0ubuntu4.4), libqt4-svg:i386 (4.8.1-0ubuntu4.3, 4.8.1-0ubuntu4.4), im-switch:i386 (1.20ubuntu5.1, 1.20ubuntu5.2), libnautilus-extension1a:i386 (3.4.2-0ubuntu6, 3.4.2-0ubuntu8), gwibber-service-identica:i386 (3.4.2-0ubuntu2.1, 3.4.2-0ubuntu2.2), libwbclient0:i386 (3.6.3-2ubuntu2.3, 3.6.3-2ubuntu2.6), libdevmapper-event1.02.1:i386 (1.02.48-4ubuntu7.1, 1.02.48-4ubuntu7.3), libqt4-xml:i386 (4.8.1-0ubuntu4.3, 4.8.1-0ubuntu4.4), libdrm-radeon1:i386 (2.4.39-0ubuntu0.1, 2.4.39-0ubuntu0.2), acpi-support:i386 (0.140, 0.140.1), perl-modules:i386 (5.14.2-6ubuntu2.2, 5.14.2-6ubuntu2.3), fonts-opensymbol:i386 (102.2+LibO3.5.4-0ubuntu1.1, 102.2+LibO3.5.7-0ubuntu4), libqt4-network:i386 (4.8.1-0ubuntu4.3, 4.8.1-0ubuntu4.4), libusbmuxd1:i386 (1.0.7-2, 1.0.7-2ubuntu0.1), libperl5.14:i386 (5.14.2-6ubuntu2.2, 5.14.2-6ubuntu2.3), libudev0:i386 (175-0ubuntu9.2, 175-0ubuntu9.3), language-selector-gnome:i386 (0.79.1, 0.79.3), unity-greeter:i386 (0.2.9-0ubuntu1, 0.2.9-0ubuntu1.1), libisccfg82:i386 (9.8.1.dfsg.P1-4ubuntu0.5, 9.8.1.dfsg.P1-4ubuntu0.6), alsa-base:i386 (1.0.25+dfsg-0ubuntu1, 1.0.25+dfsg-0ubuntu1.1), libqtgui4:i386 (4.8.1-0ubuntu4.3, 4.8.1-0ubuntu4.4), libpurple-bin:i386 (2.10.3-0ubuntu1.1, 2.10.3-0ubuntu1.3), linux-headers-generic-lts-quantal:i386 (3.5.0.23.30, 3.5.0.27.34), language-selector-common:i386 (0.79.1, 0.79.3), poppler-utils:i386 (0.18.4-1ubuntu3, 0.18.4-1ubuntu3.1), openssl:i386 (1.0.1-4ubuntu5.5, 1.0.1-4ubuntu5.8), gnome-control-center-data:i386 (3.4.2-0ubuntu0.9, 3.4.2-0ubuntu0.11), samba-common:i386 (3.6.3-2ubuntu2.3, 3.6.3-2ubuntu2.6), rsyslog:i386 (5.8.6-1ubuntu8, 5.8.6-1ubuntu8.1), linux-sound-base:i386 (1.0.25+dfsg-0ubuntu1, 1.0.25+dfsg-0ubuntu1.1), libapt-inst1.4:i386 (0.8.16~exp12ubuntu10.7, 0.8.16~exp12ubuntu10.10), gwibber-service-facebook:i386 (3.4.2-0ubuntu2.1, 3.4.2-0ubuntu2.2), libnm-gtk-common:i386 (0.9.4.1-0ubuntu2, 0.9.4.1-0ubuntu2.2), gwibber:i386 (3.4.2-0ubuntu2.1, 3.4.2-0ubuntu2.2), python-apport:i386 (2.0.1-0ubuntu17.1, 2.0.1-0ubuntu17.2), libqt4-script:i386 (4.8.1-0ubuntu4.3, 4.8.1-0ubuntu4.4), libisc83:i386 (9.8.1.dfsg.P1-4ubuntu0.5, 9.8.1.dfsg.P1-4ubuntu0.6), libgnome-control-center1:i386 (3.4.2-0ubuntu0.9, 3.4.2-0ubuntu0.11), apport-gtk:i386 (2.0.1-0ubuntu17.1, 2.0.1-0ubuntu17.2), transmission-common:i386 (2.51-0ubuntu1.1, 2.51-0ubuntu1.3), iptables:i386 (1.4.12-1ubuntu4, 1.4.12-1ubuntu5), libxrandr2:i386 (1.3.2-2, 1.3.2-2ubuntu0.1), libbamf3-0:i386 (0.2.124.2-0ubuntu1, 0.2.126-0ubuntu1), libcurl3-nss:i386 (7.22.0-3ubuntu4, 7.22.0-3ubuntu4.1), xserver-common-lts-quantal:i386 (1.13.0-0ubuntu6.1~precise2, 1.13.0-0ubuntu6.1~precise3), libbamf0:i386 (0.2.124.2-0ubuntu1, 0.2.126-0ubuntu1), libreoffice-style-tango:i386 (3.5.4-0ubuntu1.1, 3.5.7-0ubuntu4), libneon27-gnutls:i386 (0.29.6-1, 0.29.6-1ubuntu1), transmission-gtk:i386 (2.51-0ubuntu1.1, 2.51-0ubuntu1.3), libssl1.0.0:i386 (1.0.1-4ubuntu5.5, 1.0.1-4ubuntu5.8), ssh-askpass-gnome:i386 (5.9p1-5ubuntu1, 5.9p1-5ubuntu1.1), libpoppler-glib8:i386 (0.18.4-1ubuntu3, 0.18.4-1ubuntu3.1), libllvm3.1:i386 (3.1-2ubuntu1~12.04, 3.1-2ubuntu1~12.04.1)
End-Date: 2013-04-21  05:00:27

Start-Date: 2013-04-21  05:49:20
Commandline: aptdaemon role='role-commit-packages' sender=':1.81'
Install: libept1.4.12:i386 (1.0.6~exp1ubuntu1, automatic), docbook-xml:i386 (4.5-7ubuntu1, automatic), rarian-compat:i386 (0.8.1-5, automatic), libvte9:i386 (0.28.2-3ubuntu2, automatic), librarian0:i386 (0.8.1-5, automatic), synaptic:i386 (0.75.9ubuntu1), sgml-data:i386 (2.0.6, automatic), libvte-common:i386 (0.28.2-3ubuntu2, automatic)
End-Date: 2013-04-21  05:49:44
```
```
2013-02-13 22:09:12 install gtk2-engines <none> 1:2.20.2-1ubuntu1
2013-02-13 22:09:12 install gtk2-engines-murrine <none> 0.98.2-0ubuntu1
2013-02-13 22:09:12 install gtk3-engines-unico <none> 1.0.2-0ubuntu1
2013-02-13 22:09:12 install libgucharmap-2-90-7 <none> 1:3.4.1.1-0ubuntu1
2013-02-13 22:09:12 install gucharmap <none> 1:3.4.1.1-0ubuntu1
2013-02-13 22:09:12 install libcdio13 <none> 0.83-1
2013-02-13 22:09:12 install libcdio-cdda1 <none> 0.83-1
2013-02-13 22:09:12 install libcdio-paranoia1 <none> 0.83-1
2013-02-13 22:09:12 install gvfs-backends <none> 1.12.1-0ubuntu1.1
2013-02-13 22:09:12 install gvfs-bin <none> 1.12.1-0ubuntu1.1
2013-02-13 22:09:12 install gvfs-fuse <none> 1.12.1-0ubuntu1.1
2013-02-13 22:09:12 install python-egenix-mxtools <none> 3.2.1-1ubuntu1
2013-02-13 22:09:12 install python-egenix-mxdatetime <none> 3.2.1-1ubuntu1
2013-02-13 22:09:12 install libgtkspell-3-0 <none> 3.0.0~hg20110814-1
2013-02-13 22:09:12 install python-imaging <none> 1.1.7-4
2013-02-13 22:09:12 install gwibber-service <none> 3.4.2-0ubuntu2.1
2013-02-13 22:09:12 install libgwibber2 <none> 3.4.2-0ubuntu2.1
2013-02-13 22:09:12 install libgwibber-gtk2 <none> 3.4.2-0ubuntu2.1
2013-02-13 22:09:12 install gwibber <none> 3.4.2-0ubuntu2.1
2013-02-13 22:09:12 install gwibber-service-facebook <none> 3.4.2-0ubuntu2.1
2013-02-13 22:09:12 install gwibber-service-identica <none> 3.4.2-0ubuntu2.1
2013-02-13 22:09:13 install gwibber-service-twitter <none> 3.4.2-0ubuntu2.1
2013-02-13 22:09:13 install libsnmp-base <none> 5.4.3~dfsg-2.4ubuntu1.1
2013-02-13 22:09:13 install libperl5.14 <none> 5.14.2-6ubuntu2.2
2013-02-13 22:09:13 install libsnmp15 <none> 5.4.3~dfsg-2.4ubuntu1.1
2013-02-13 22:09:13 install libhpmud0 <none> 3.12.2-1ubuntu3.1
2013-02-13 22:09:13 install libsane-hpaio <none> 3.12.2-1ubuntu3.1
2013-02-13 22:09:13 install hplip-data <none> 3.12.2-1ubuntu3.1
2013-02-13 22:09:13 install printer-driver-hpcups <none> 3.12.2-1ubuntu3.1
2013-02-13 22:09:13 install python-pexpect <none> 2.3-1ubuntu2
2013-02-13 22:09:13 install python-reportlab <none> 2.5-1.1build1
2013-02-13 22:09:13 install hplip <none> 3.12.2-1ubuntu3.1
2013-02-13 22:09:13 install hwdata <none> 0.233-1ubuntu1
2013-02-13 22:09:13 install python-gtk2 <none> 2.24.0-3
2013-02-13 22:09:13 install python-ibus <none> 1.4.1-3ubuntu1
2013-02-13 22:09:13 install python-notify <none> 0.1.1-3
2013-02-13 22:09:13 install ibus <none> 1.4.1-3ubuntu1
2013-02-13 22:09:13 install ibus-gtk <none> 1.4.1-3ubuntu1
2013-02-13 22:09:13 install ibus-gtk3 <none> 1.4.1-3ubuntu1
2013-02-13 22:09:13 install ibus-pinyin-db-android <none> 1.4.0-1
2013-02-13 22:09:14 install libopencc1 <none> 0.3.0-1
2013-02-13 22:09:14 install ibus-pinyin <none> 1.4.0-1
2013-02-13 22:09:14 install ibus-table <none> 1.3.9.20110827-1ubuntu1
2013-02-13 22:09:14 install im-switch <none> 1.20ubuntu5.1
2013-02-13 22:09:14 install indicator-application <none> 0.5.0-0ubuntu1
2013-02-13 22:09:14 install indicator-appmenu <none> 0.3.97-0ubuntu1
2013-02-13 22:09:14 install libedataserverui-3.0-1 <none> 3.2.3-0ubuntu7
2013-02-13 22:09:14 install libtimezonemap1 <none> 0.3.2
2013-02-13 22:09:14 install indicator-datetime <none> 0.3.94-0ubuntu2
2013-02-13 22:09:14 install libindicator-messages-status-provider1 <none> 0.6.0-0ubuntu2
2013-02-13 22:09:14 install indicator-messages <none> 0.6.0-0ubuntu2
2013-02-13 22:09:14 install indicator-power <none> 2.0-0ubuntu1
2013-02-13 22:09:14 install libpackagekit-glib2-14 <none> 0.7.2-4ubuntu3
2013-02-13 22:09:14 install indicator-session <none> 0.3.96-0ubuntu1
2013-02-13 22:09:14 install indicator-status-provider-mc5 <none> 0.6.0-0ubuntu2
2013-02-13 22:09:14 install intel-gpu-tools <none> 1.2-1
2013-02-13 22:09:14 install iw <none> 3.2-1
2013-02-13 22:09:14 install jockey-common <none> 0.9.7-0ubuntu7.7
2013-02-13 22:09:14 install jockey-gtk <none> 0.9.7-0ubuntu7.7
2013-02-13 22:09:14 install kerneloops-daemon <none> 0.12+git20090217-1ubuntu19
2013-02-13 22:09:14 install landscape-client-ui-install <none> 12.05-0ubuntu1.12.04
2013-02-13 22:09:14 install aptdaemon <none> 0.43+bzr805-0ubuntu7
2013-02-13 22:09:14 install language-selector-gnome <none> 0.79.1
2013-02-13 22:09:14 install launchpad-integration <none> 0.1.56.1
2013-02-13 22:09:15 install libindicator7 <none> 0.5.0-0ubuntu1
2013-02-13 22:09:15 install libappindicator1 <none> 0.4.92-0ubuntu1
2013-02-13 22:09:15 install libasound2-plugins <none> 1.0.25-1ubuntu1
2013-02-13 22:09:15 install libatk-adaptor <none> 2.4.0-1ubuntu2
2013-02-13 22:09:15 install libatk-adaptor-schemas <none> 2.4.0-1ubuntu2
2013-02-13 22:09:15 install libc-dev-bin <none> 2.15-0ubuntu10.3
2013-02-13 22:09:15 install linux-libc-dev <none> 3.2.0-37.58
2013-02-13 22:09:15 install libc6-dev <none> 2.15-0ubuntu10.3
2013-02-13 22:09:15 install libcairo-perl <none> 1.081-1build2
2013-02-13 22:09:15 install libcanberra-gtk-module <none> 0.28-3ubuntu3
2013-02-13 22:09:15 install pulseaudio-utils <none> 1:1.1-0ubuntu15.2
2013-02-13 22:09:15 install pulseaudio <none> 1:1.1-0ubuntu15.2
2013-02-13 22:09:15 install libcanberra-pulse <none> 0.28-3ubuntu3
2013-02-13 22:09:15 install libcrypt-passwdmd5-perl <none> 1.3-10
2013-02-13 22:09:15 install libdconf-qt0 <none> 0.0.0.110722-0ubuntu4
2013-02-13 22:09:15 install libdmapsharing-3.0-2 <none> 2.9.14-1
2013-02-13 22:09:15 install libdotconf1.0 <none> 1.0.13-3
2013-02-13 22:09:16 install libevent-2.0-5 <none> 2.0.16-stable-1
2013-02-13 22:09:16 install libexiv2-11 <none> 0.22-2
2013-02-13 22:09:16 install libfile-basedir-perl <none> 0.03-1fakesync1
2013-02-13 22:09:16 install libfile-copy-recursive-perl <none> 0.38-1
2013-02-13 22:09:16 install libfile-desktopentry-perl <none> 0.04-3
2013-02-13 22:09:16 install libfile-mimeinfo-perl <none> 0.15-2
2013-02-13 22:09:16 install libfolks-eds25 <none> 0.6.8-2
2013-02-13 22:09:16 install libfreerdp1 <none> 1.0.1-1ubuntu2.2
2013-02-13 22:09:16 install libfreerdp-plugins-standard <none> 1.0.1-1ubuntu2.2
2013-02-13 22:09:16 install libfs6 <none> 2:1.0.3-1
2013-02-13 22:09:16 install libgail-common <none> 2.24.10-0ubuntu6
2013-02-13 22:09:16 install libgexiv2-1 <none> 0.4.1-1build1
2013-02-13 22:09:16 install libglib-perl <none> 2:1.241-1
2013-02-13 22:09:16 install libgnome-menu2 <none> 3.0.1-0ubuntu7
2013-02-13 22:09:16 install libgnome2-common <none> 2.32.1-2ubuntu1.1
2013-02-13 22:09:16 install libpth20 <none> 2.0.7-16ubuntu3
2013-02-13 22:09:16 install libgpgme11 <none> 1.2.0-1.4ubuntu2
2013-02-13 22:09:16 install libgphoto2-l10n <none> 2.4.13-1ubuntu1.2
2013-02-13 22:09:16 install libgpod4 <none> 0.8.2-4
2013-02-13 22:09:16 install libgpod-common <none> 0.8.2-4
2013-02-13 22:09:16 install libpango-perl <none> 1.222-1build1
2013-02-13 22:09:16 install libgtk2-perl <none> 2:1.223-1build3
2013-02-13 22:09:16 install libgtk2.0-bin <none> 2.24.10-0ubuntu6
2013-02-13 22:09:16 install libindicate-gtk3 <none> 0.6.92-0ubuntu1
2013-02-13 22:09:16 install libjs-jquery <none> 1.7.1-1ubuntu1
2013-02-13 22:09:17 install libmeanwhile1 <none> 1.0.2-4ubuntu1
2013-02-13 22:09:17 install libminiupnpc8 <none> 1.6-3ubuntu1
2013-02-13 22:09:17 install libmtdev1 <none> 1.1.0-2ubuntu1
2013-02-13 22:09:17 install libmtp-runtime <none> 1.1.3-1ubuntu0.1
2013-02-13 22:09:17 install libmusicbrainz3-6 <none> 3.0.2-2.1
2013-02-13 22:09:17 install libnm-glib-vpn1 <none> 0.9.4.0-0ubuntu4.2
2013-02-13 22:09:17 install libnotify-bin <none> 0.7.5-1
2013-02-13 22:09:17 install libnss-mdns <none> 0.10-3.2
2013-02-13 22:09:17 install libnux-2.0-common <none> 2.14.1-0ubuntu1
2013-02-13 22:09:17 install libnux-2.0-0 <none> 2.14.1-0ubuntu1
2013-02-13 22:09:17 install liboverlay-scrollbar-0.2-0 <none> 0.2.16-0ubuntu1.1
2013-02-13 22:09:17 install liboverlay-scrollbar3-0.2-0 <none> 0.2.16-0ubuntu1.1
2013-02-13 22:09:17 install libpam-cap <none> 1:2.22-1ubuntu3
2013-02-13 22:09:17 install libpam-ck-connector <none> 0.4.5-2
2013-02-13 22:09:17 install libpam-gnome-keyring <none> 3.2.2-2ubuntu4
2013-02-13 22:09:17 install libpaper-utils <none> 1.1.24+nmu1build1
2013-02-13 22:09:17 install libproxy1-plugin-gsettings <none> 0.4.7-0ubuntu4.1
2013-02-13 22:09:17 install libproxy1-plugin-networkmanager <none> 0.4.7-0ubuntu4.1
2013-02-13 22:09:17 install libpurple-bin <none> 1:2.10.3-0ubuntu1.1
2013-02-13 22:09:17 install libzephyr4 <none> 3.0.1-1
2013-02-13 22:09:17 install libpurple0 <none> 1:2.10.3-0ubuntu1.1
2013-02-13 22:09:17 install libqtbamf1 <none> 0.2.4-0ubuntu1
2013-02-13 22:09:17 install libqtdee2 <none> 0.2.4-0ubuntu1
2013-02-13 22:09:17 install libqtgconf1 <none> 0.1-0ubuntu5
2013-02-13 22:09:17 install libraw5 <none> 0.14.4-0ubuntu2
2013-02-13 22:09:18 install libreoffice-base-core <none> 1:3.5.4-0ubuntu1.1
2013-02-13 22:09:18 install libreoffice-calc <none> 1:3.5.4-0ubuntu1.1
2013-02-13 22:09:19 install libwpd-0.9-9 <none> 0.9.4-1
2013-02-13 22:09:19 install libwpg-0.2-2 <none> 0.2.1-1
2013-02-13 22:09:19 install libreoffice-draw <none> 1:3.5.4-0ubuntu1.1
2013-02-13 22:09:19 install python-uno <none> 1:3.5.4-0ubuntu1.1
2013-02-13 22:09:19 install libreoffice-emailmerge <none> 1:3.5.4-0ubuntu1.1
2013-02-13 22:09:20 install libreoffice-gtk <none> 1:3.5.4-0ubuntu1.1
2013-02-13 22:09:20 install libreoffice-gnome <none> 1:3.5.4-0ubuntu1.1
2013-02-13 22:09:20 install libwps-0.2-2 <none> 0.2.4-1
2013-02-13 22:09:20 install libreoffice-writer <none> 1:3.5.4-0ubuntu1.1
2013-02-13 22:09:21 install libreoffice-help-en-us <none> 1:3.5.4-0ubuntu1.1
2013-02-13 22:09:22 install libreoffice-impress <none> 1:3.5.4-0ubuntu1.1
2013-02-13 22:09:22 install libreoffice-math <none> 1:3.5.4-0ubuntu1.1
2013-02-13 22:09:23 install unity-services <none> 5.18.0-0ubuntu2
2013-02-13 22:09:23 install libunity-core-5.0-5 <none> 5.18.0-0ubuntu2
2013-02-13 22:09:23 install libunity-2d-private0 <none> 5.12.0-0ubuntu1.2
2013-02-13 22:09:23 install libunity-misc4 <none> 4.0.4-0ubuntu2
2013-02-13 22:09:23 install libutempter0 <none> 1.1.5-4
2013-02-13 22:09:23 install libvisual-0.4-plugins <none> 0.4.0.dfsg.1-7
2013-02-13 22:09:23 install libvncserver0 <none> 0.9.8.2-2ubuntu1
2013-02-13 22:09:23 install libwmf0.2-7-gtk <none> 0.2.8.4-10ubuntu1
2013-02-13 22:09:23 install libx86-1 <none> 1.1+ds1-7ubuntu1
2013-02-13 22:09:23 install libxfont1 <none> 1:1.4.4-1
2013-02-13 22:09:23 install libxvmc1 <none> 2:1.0.6-1ubuntu2
2013-02-13 22:09:23 install ubuntu-mono <none> 0.0.40
2013-02-13 22:09:23 install light-themes <none> 0.1.9.1-0ubuntu1.2
2013-02-13 22:09:23 install linux-firmware <none> 1.79.1
2013-02-13 22:09:24 install linux-image-generic-lts-quantal <none> 3.5.0.23.30
2013-02-13 22:09:24 install linux-headers-3.5.0-23 <none> 3.5.0-23.35~precise1
2013-02-13 22:09:26 install linux-headers-3.5.0-23-generic <none> 3.5.0-23.35~precise1
2013-02-13 22:09:27 install linux-headers-generic-lts-quantal <none> 3.5.0.23.30
2013-02-13 22:09:27 install linux-generic-lts-quantal <none> 3.5.0.23.30
2013-02-13 22:09:27 install mahjongg <none> 1:3.4.1-0ubuntu2.2
2013-02-13 22:09:27 install make <none> 3.81-8.1ubuntu1.1
2013-02-13 22:09:27 install manpages-dev <none> 3.35-0.1ubuntu1
2013-02-13 22:09:27 install media-player-info <none> 16-1
2013-02-13 22:09:27 install zenity-common <none> 3.4.0-0ubuntu4
2013-02-13 22:09:27 install zenity <none> 3.4.0-0ubuntu4
2013-02-13 22:09:27 install metacity <none> 1:2.34.1-1ubuntu11
2013-02-13 22:09:27 install modemmanager <none> 0.5.2.0-0ubuntu2
2013-02-13 22:09:27 install mousetweaks <none> 3.4.1-0ubuntu1
2013-02-13 22:09:28 install mtools <none> 4.0.12-1
2013-02-13 22:09:28 install nautilus-sendto <none> 3.0.1-2ubuntu2
2013-02-13 22:09:28 install nautilus-sendto-empathy <none> 3.4.2.3-0ubuntu1
2013-02-13 22:09:28 install samba-common <none> 2:3.6.3-2ubuntu2.3
2013-02-13 22:09:28 install samba-common-bin <none> 2:3.6.3-2ubuntu2.3
2013-02-13 22:09:28 install nautilus-share <none> 0.7.3-1ubuntu2
2013-02-13 22:09:28 install network-manager-gnome <none> 0.9.4.1-0ubuntu2
2013-02-13 22:09:28 install pptp-linux <none> 1.7.2-6
2013-02-13 22:09:28 install network-manager-pptp <none> 0.9.4.0-0ubuntu1
2013-02-13 22:09:28 install network-manager-pptp-gnome <none> 0.9.4.0-0ubuntu1
2013-02-13 22:09:28 install notify-osd-icons <none> 0.7
2013-02-13 22:09:28 install nux-tools <none> 2.14.1-0ubuntu1
2013-02-13 22:09:28 install python-virtkey <none> 0.60.0-0ubuntu5
2013-02-13 22:09:28 install onboard <none> 0.97.0-0ubuntu4
2013-02-13 22:09:28 install openprinting-ppds <none> 20120322-0ubuntu1
2013-02-13 22:09:28 install os-prober <none> 1.51ubuntu3
2013-02-13 22:09:29 install overlay-scrollbar <none> 0.2.16-0ubuntu1.1
2013-02-13 22:09:29 install plymouth-label <none> 0.8.2-2ubuntu31
2013-02-13 22:09:29 install plymouth-theme-ubuntu-logo <none> 0.8.2-2ubuntu31
2013-02-13 22:09:29 install policykit-desktop-privileges <none> 0.10
2013-02-13 22:09:29 install printer-driver-c2esp <none> 23-1
2013-02-13 22:09:29 install mscompress <none> 0.3-3.1
2013-02-13 22:09:29 install printer-driver-foo2zjs <none> 20111202dfsg0-1ubuntu1
2013-02-13 22:09:29 install printer-driver-gutenprint <none> 5.2.8~pre1-0ubuntu2.1
2013-02-13 22:09:29 install printer-driver-hpijs <none> 3.12.2-1ubuntu3.1
2013-02-13 22:09:29 install printer-driver-min12xxw <none> 0.0.9-6ubuntu1
2013-02-13 22:09:29 install printer-driver-pnm2ppa <none> 1.13+nondbs-0ubuntu1
2013-02-13 22:09:29 install printer-driver-postscript-hp <none> 3.12.2-1ubuntu3.1
2013-02-13 22:09:29 install printer-driver-ptouch <none> 1.3-3ubuntu0.1
2013-02-13 22:09:29 install printer-driver-pxljr <none> 1.3+repack0-2
2013-02-13 22:09:29 install printer-driver-sag-gdi <none> 0.1-3
2013-02-13 22:09:29 install printer-driver-splix <none> 2.0.0+svn300-1.1ubuntu2
2013-02-13 22:09:29 install pulseaudio-module-gconf <none> 1:1.1-0ubuntu15.2
2013-02-13 22:09:29 install pulseaudio-module-x11 <none> 1:1.1-0ubuntu15.2
2013-02-13 22:09:29 install python-appindicator <none> 0.4.92-0ubuntu1
2013-02-13 22:09:29 install python-crypto <none> 2.4.1-1ubuntu0.1
2013-02-13 22:09:30 install python-cups <none> 1.9.61-0ubuntu2
2013-02-13 22:09:30 install python-cupshelpers <none> 1.3.8+20120201-0ubuntu8.1
2013-02-13 22:09:30 install python-dateutil <none> 1.5-1
2013-02-13 22:09:30 install python-debtagshw <none> 1.9+git20120320-0ubuntu1
2013-02-13 22:09:30 install python-gconf <none> 2.28.1+dfsg-1
2013-02-13 22:09:30 install python-gnomekeyring <none> 2.32.0+dfsg-1
2013-02-13 22:09:30 install python-gst0.10 <none> 0.10.22-3ubuntu0.1
2013-02-13 22:09:30 install python-libproxy <none> 0.4.7-0ubuntu4.1
2013-02-13 22:09:30 install python-markupsafe <none> 0.15-1
2013-02-13 22:09:30 install python-mako <none> 0.5.0-1
2013-02-13 22:09:30 install python-pam <none> 0.4.2-12.2ubuntu4
2013-02-13 22:09:30 install python-renderpm <none> 2.5-1.1build1
2013-02-13 22:09:30 install python-reportlab-accel <none> 2.5-1.1build1
2013-02-13 22:09:30 install python-serial <none> 2.5-2.1build1
2013-02-13 22:09:30 install python-smbc <none> 1.0.13-0ubuntu1
2013-02-13 22:09:30 install qdbus <none> 4:4.8.1-0ubuntu4.3
2013-02-13 22:09:30 install radeontool <none> 1.6.2-1.1
2013-02-13 22:09:30 install remmina-common <none> 1.0.0-1ubuntu6.1
2013-02-13 22:09:30 install remmina <none> 1.0.0-1ubuntu6.1
2013-02-13 22:09:30 install remmina-plugin-rdp <none> 1.0.0-1ubuntu6.1
2013-02-13 22:09:30 install remmina-plugin-vnc <none> 1.0.0-1ubuntu6.1
2013-02-13 22:09:31 install rfkill <none> 0.4-1ubuntu2
2013-02-13 22:09:31 install rhythmbox-data <none> 2.96-0ubuntu4.2
2013-02-13 22:09:31 install rhythmbox <none> 2.96-0ubuntu4.2
2013-02-13 22:09:31 install rhythmbox-mozilla <none> 2.96-0ubuntu4.2
2013-02-13 22:09:31 install rhythmbox-plugin-cdrecorder <none> 2.96-0ubuntu4.2
2013-02-13 22:09:31 install rhythmbox-plugin-magnatune <none> 2.96-0ubuntu4.2
2013-02-13 22:09:31 install rhythmbox-plugin-zeitgeist <none> 2.96-0ubuntu4.2
2013-02-13 22:09:31 install liblircclient0 <none> 0.9.0-0ubuntu1
2013-02-13 22:09:31 install rhythmbox-plugins <none> 2.96-0ubuntu4.2
2013-02-13 22:09:31 install rtkit <none> 0.10-2
2013-02-13 22:09:31 install update-inetd <none> 4.41
2013-02-13 22:09:31 install sane-utils <none> 1.0.22-7ubuntu1
2013-02-13 22:09:31 install seahorse <none> 3.2.2-0ubuntu2.1
2013-02-13 22:09:31 install xdg-utils <none> 1.1.0~rc1-2ubuntu6
2013-02-13 22:09:31 install simple-scan <none> 3.4.1-0ubuntu1.1
2013-02-13 22:09:31 install smbclient <none> 2:3.6.3-2ubuntu2.3
2013-02-13 22:09:32 install sni-qt <none> 0.2.5-0ubuntu3
2013-02-13 22:09:32 install software-center-aptdaemon-plugins <none> 0.1.2
2013-02-13 22:09:32 install ubuntu-sso-client-gtk <none> 3.0.2-0ubuntu3
2013-02-13 22:09:32 install python-piston-mini-client <none> 0.7.2+bzr57-0ubuntu1
2013-02-13 22:09:32 install oneconf <none> 0.2.8.1
2013-02-13 22:09:32 install ubuntu-extras-keyring <none> 2010.09.27
2013-02-13 22:09:32 install software-center <none> 5.2.7
2013-02-13 22:09:32 install ssh-askpass-gnome <none> 1:5.9p1-5ubuntu1
2013-02-13 22:09:32 install syslinux-common <none> 2:4.05+dfsg-2
2013-02-13 22:09:32 install syslinux <none> 2:4.05+dfsg-2
2013-02-13 22:09:32 install syslinux-legacy <none> 2:3.63+dfsg-2ubuntu5
2013-02-13 22:09:32 install system-config-printer-common <none> 1.3.8+20120201-0ubuntu8.1
2013-02-13 22:09:32 install system-config-printer-gnome <none> 1.3.8+20120201-0ubuntu8.1
2013-02-13 22:09:32 install system-config-printer-udev <none> 1.3.8+20120201-0ubuntu8.1
2013-02-13 22:09:33 install tcpd <none> 7.6.q-21
2013-02-13 22:09:33 install telepathy-gabble <none> 0.16.0-0ubuntu2
2013-02-13 22:09:33 install telepathy-haze <none> 0.6.0-0ubuntu1
2013-02-13 22:09:33 install telepathy-idle <none> 0.1.11-2
2013-02-13 22:09:33 install telepathy-indicator <none> 0.2.1-0ubuntu1
2013-02-13 22:09:33 install telepathy-salut <none> 0.8.0-0ubuntu1
2013-02-13 22:09:33 install thunderbird <none> 17.0.2+build1-0ubuntu0.12.04.1
2013-02-13 22:09:33 install thunderbird-globalmenu <none> 17.0.2+build1-0ubuntu0.12.04.1
2013-02-13 22:09:33 install thunderbird-gnome-support <none> 17.0.2+build1-0ubuntu0.12.04.1
2013-02-13 22:09:33 install toshset <none> 1.76-2
2013-02-13 22:09:33 install totem-common <none> 3.0.1-0ubuntu21.1
2013-02-13 22:09:34 install totem <none> 3.0.1-0ubuntu21.1
2013-02-13 22:09:34 install totem-mozilla <none> 3.0.1-0ubuntu21.1
2013-02-13 22:09:34 install totem-plugins <none> 3.0.1-0ubuntu21.1
2013-02-13 22:09:34 install transmission-common <none> 2.51-0ubuntu1.1
2013-02-13 22:09:34 install transmission-gtk <none> 2.51-0ubuntu1.1
2013-02-13 22:09:34 install ttf-indic-fonts-core <none> 1:0.5.11ubuntu1
2013-02-13 22:09:34 install ttf-punjabi-fonts <none> 1:0.5.11ubuntu1
2013-02-13 22:09:34 install ttf-ubuntu-font-family <none> 0.80-0ubuntu2
2013-02-13 22:09:34 install ttf-wqy-microhei <none> 0.2.0-beta-1ubuntu1
2013-02-13 22:09:34 install ubuntu-wallpapers-precise <none> 0.34.1
2013-02-13 22:09:34 install ubuntu-wallpapers <none> 0.34.1
2013-02-13 22:09:35 install adium-theme-ubuntu <none> 0.3.2-0ubuntu1
2013-02-13 22:09:35 install ubuntu-artwork <none> 57
2013-02-13 22:09:35 install inputattach <none> 1:1.4.2-1
2013-02-13 22:09:35 install ubuntu-sounds <none> 0.13
2013-02-13 22:09:35 install unity-common <none> 5.18.0-0ubuntu2
2013-02-13 22:09:35 install unity-asset-pool <none> 0.8.23-0ubuntu1
2013-02-13 22:09:35 install unity <none> 5.18.0-0ubuntu2
2013-02-13 22:09:35 install unity-2d-common <none> 5.12.0-0ubuntu1.2
2013-02-13 22:09:35 install unity-2d-panel <none> 5.12.0-0ubuntu1.2
2013-02-13 22:09:35 install unity-2d-spread <none> 5.12.0-0ubuntu1.2
2013-02-13 22:09:35 install unity-2d-shell <none> 5.12.0-0ubuntu1.2
2013-02-13 22:09:35 install unity-2d <none> 5.12.0-0ubuntu1.2
2013-02-13 22:09:35 install update-manager <none> 1:0.156.14.11
2013-02-13 22:09:35 install update-notifier <none> 0.119ubuntu8.6
2013-02-13 22:09:35 install libiw30 <none> 30~pre9-5ubuntu2
2013-02-13 22:09:35 install wireless-tools <none> 30~pre9-5ubuntu2
2013-02-13 22:09:35 install xdg-user-dirs <none> 0.14-0ubuntu2
2013-02-13 22:09:35 install xdg-user-dirs-gtk <none> 0.9-0ubuntu1
2013-02-13 22:09:35 install xdiagnose <none> 2.5.2ubuntu0.1
2013-02-13 22:09:35 install xserver-common <none> 2:1.11.4-0ubuntu10.11
2013-02-13 22:09:35 install xserver-common-lts-quantal <none> 2:1.13.0-0ubuntu6.1~precise2
2013-02-13 22:09:36 install xserver-xorg-core-lts-quantal <none> 2:1.13.0-0ubuntu6.1~precise2
2013-02-13 22:09:36 install xserver-xorg-video-r128-lts-quantal <none> 6.9.1-0ubuntu1~precise2
2013-02-13 22:09:36 install xserver-xorg-video-mach64-lts-quantal <none> 6.9.3-0ubuntu1~precise2
2013-02-13 22:09:36 install xserver-xorg-video-radeon-lts-quantal <none> 1:6.99.99~git20120913.8637f772-0ubuntu1~precise2
2013-02-13 22:09:36 install xserver-xorg-video-ati-lts-quantal <none> 1:6.99.99~git20120913.8637f772-0ubuntu1~precise2
2013-02-13 22:09:36 install xserver-xorg-video-cirrus-lts-quantal <none> 1:1.5.1-0ubuntu2~precise1
2013-02-13 22:09:36 install xserver-xorg-video-fbdev-lts-quantal <none> 1:0.4.3-0ubuntu1~precise1
2013-02-13 22:09:36 install xserver-xorg-video-intel-lts-quantal <none> 2:2.20.9-0ubuntu2~precise2
2013-02-13 22:09:36 install xserver-xorg-video-mga-lts-quantal <none> 1:1.6.2-0ubuntu1~precise2
2013-02-13 22:09:36 install xserver-xorg-video-modesetting-lts-quantal <none> 0.5.0-0ubuntu1~precise2
2013-02-13 22:09:36 install xserver-xorg-video-neomagic-lts-quantal <none> 1:1.2.7-0ubuntu1~precise1
2013-02-13 22:09:36 install xserver-xorg-video-nouveau-lts-quantal <none> 1:1.0.2-0ubuntu3~precise2
2013-02-13 22:09:36 install xserver-xorg-video-openchrome-lts-quantal <none> 1:0.3.1-0ubuntu1~precise2
2013-02-13 22:09:36 install xserver-xorg-video-s3-lts-quantal <none> 1:0.6.5-0ubuntu1~precise1
2013-02-13 22:09:36 install xserver-xorg-video-savage-lts-quantal <none> 1:2.3.6-0ubuntu1~precise1
2013-02-13 22:09:36 install xserver-xorg-video-siliconmotion-lts-quantal <none> 1:1.7.7-0ubuntu1~precise1
2013-02-13 22:09:36 install xserver-xorg-video-sis-lts-quantal <none> 1:0.10.7-0ubuntu1~precise2
2013-02-13 22:09:36 install xserver-xorg-video-sisusb-lts-quantal <none> 1:0.9.6-0ubuntu1~precise1
2013-02-13 22:09:36 install xserver-xorg-video-tdfx-lts-quantal <none> 1:1.4.5-0ubuntu1~precise2
2013-02-13 22:09:36 install xserver-xorg-video-trident-lts-quantal <none> 1:1.3.6-0ubuntu2~precise1
2013-02-13 22:09:36 install xserver-xorg-video-vesa-lts-quantal <none> 1:2.3.2-0ubuntu1~precise1
2013-02-13 22:09:36 install xserver-xorg-video-vmware-lts-quantal <none> 1:12.0.2+git.e5ac80d8-0ubuntu1~precise2
2013-02-13 22:09:36 install xserver-xorg-video-all-lts-quantal <none> 1:7.7+1ubuntu4~precise1
2013-02-13 22:09:36 install xserver-xorg-input-evdev-lts-quantal <none> 1:2.7.3-0ubuntu2~precise1
2013-02-13 22:09:37 install xserver-xorg-input-synaptics-lts-quantal <none> 1.6.2-1ubuntu5~precise1
2013-02-13 22:09:37 install xserver-xorg-input-mouse-lts-quantal <none> 1:1.7.2-2build1~precise1
2013-02-13 22:09:37 install xserver-xorg-input-vmmouse-lts-quantal <none> 1:12.9.0-0ubuntu3~precise1
2013-02-13 22:09:37 install xserver-xorg-input-wacom-lts-quantal <none> 1:0.17.0-0ubuntu2~precise1
2013-02-13 22:09:37 install xserver-xorg-input-all-lts-quantal <none> 1:7.7+1ubuntu4~precise1
2013-02-13 22:09:37 install xserver-xorg-lts-quantal <none> 1:7.7+1ubuntu4~precise1
2013-02-13 22:09:37 install xfonts-encodings <none> 1:1.0.4-1ubuntu1
2013-02-13 22:09:37 install xfonts-utils <none> 1:7.6+1
2013-02-13 22:09:37 install xfonts-base <none> 1:1.0.3
2013-02-13 22:09:37 install x11-apps <none> 7.6+5ubuntu1
2013-02-13 22:09:37 install x11-session-utils <none> 7.6+2
2013-02-13 22:09:37 install x11-xfs-utils <none> 7.6+1
2013-02-13 22:09:37 install xinit <none> 1.3.1-1
2013-02-13 22:09:37 install xorg-docs-core <none> 1:1.6-1ubuntu2
2013-02-13 22:09:37 install xbitmaps <none> 1.1.1-1
2013-02-13 22:09:37 install xterm <none> 271-1ubuntu2.1
2013-02-13 22:09:37 install xinput <none> 1.5.99.1-0ubuntu2
2013-02-13 22:09:37 install xorg <none> 1:7.6+12ubuntu2
2013-02-13 22:09:37 install ubuntu-desktop <none> 1.267.1
2013-02-13 22:09:37 install ubuntuone-client-gnome <none> 3.0.1-0ubuntu1
2013-02-13 22:09:37 install unity-lens-applications <none> 5.18.0-0ubuntu1
2013-02-13 22:09:37 install unity-lens-files <none> 5.10.0-0ubuntu1
2013-02-13 22:09:38 install unity-lens-music <none> 5.12.0-0ubuntu2
2013-02-13 22:09:38 install unity-lens-video <none> 0.3.5-0ubuntu1.3
2013-02-13 22:09:38 install python-dirspec <none> 3.0.0-0ubuntu1
2013-02-13 22:09:38 install rhythmbox-ubuntuone <none> 3.0.0-0ubuntu1
2013-02-13 22:09:38 install unity-scope-musicstores <none> 5.12.0-0ubuntu2
2013-02-13 22:09:38 install unity-scope-video-remote <none> 0.3.5-0ubuntu2.1
2013-02-13 22:09:38 install usb-creator-common <none> 0.2.38
2013-02-13 22:09:38 install usb-creator-gtk <none> 0.2.38
2013-02-13 22:09:38 install vbetool <none> 1.1-2ubuntu1
2013-02-13 22:09:38 install vino <none> 3.4.2-0ubuntu1.2
2013-02-13 22:09:38 install x11-xserver-utils-lts-quantal <none> 7.7~3ubuntu1~precise1
2013-02-13 22:09:38 install xcursor-themes <none> 1.0.3-1
2013-02-13 22:09:38 install xfonts-scalable <none> 1:1.0.3-1
2013-02-13 22:09:38 install xul-ext-ubufox <none> 2.6-0ubuntu0.12.04.1
2013-02-13 22:09:38 install cups-bsd <none> 1.5.3-0ubuntu6
2013-02-13 22:09:38 install ginn <none> 0.2.4.1-0ubuntu1
2013-02-13 22:09:38 install indicator-printers <none> 0.1.6-0ubuntu1
2013-02-13 22:09:38 install indicator-sound <none> 0.8.5.0-0ubuntu2.1
2013-02-13 22:09:38 install libcanberra-gtk3-module <none> 0.28-3ubuntu3
2013-02-13 22:09:38 install libprotoc7 <none> 2.4.1-1ubuntu2
2013-02-13 22:09:38 install libspeechd2 <none> 0.7.1-6ubuntu3
2013-02-13 22:09:38 install mobile-broadband-provider-info <none> 20120410-0ubuntu1
2013-02-13 22:09:38 install protobuf-compiler <none> 2.4.1-1ubuntu2
2013-02-13 22:09:39 install pulseaudio-module-bluetooth <none> 1:1.1-0ubuntu15.2
2013-02-13 22:09:39 install python-packagekit <none> 0.7.2-4ubuntu3
2013-02-13 22:09:39 install python-aptdaemon.pkcompat <none> 0.43+bzr805-0ubuntu7
2013-02-13 22:09:39 install python-ubuntuone-control-panel <none> 3.0.1-0ubuntu1
2013-02-13 22:09:39 install sessioninstaller <none> 0.20+bzr128-0ubuntu1.2
2013-02-13 22:09:39 install shotwell <none> 0.12.3-0ubuntu0.1
2013-02-13 22:09:39 install speech-dispatcher <none> 0.7.1-6ubuntu3
2013-02-13 22:09:39 install ubuntuone-control-panel <none> 3.0.1-0ubuntu1
2013-02-13 22:09:39 install ubuntuone-couch <none> 0.3.0-0ubuntu4
2013-02-13 22:09:39 install ubuntuone-installer <none> 3.0.2-0ubuntu1.1
2013-02-13 22:09:39 install xfonts-mathml <none> 4ubuntu1
2013-02-13 22:11:00 install localechooser-data <none> 2.39ubuntu2
2013-02-13 22:11:00 install user-setup <none> 1.42ubuntu3
2013-02-13 22:11:01 install casper <none> 1.315.1
2013-02-13 22:11:01 install lupin-casper <none> 0.51
2013-02-13 22:11:09 install language-pack-de-base <none> 1:12.04+20130128
2013-02-13 22:11:10 install language-pack-de <none> 1:12.04+20130128
2013-02-13 22:11:10 install language-pack-en-base <none> 1:12.04+20130128
2013-02-13 22:11:10 install language-pack-en <none> 1:12.04+20130128
2013-02-13 22:11:10 install language-pack-es-base <none> 1:12.04+20130128
2013-02-13 22:11:11 install language-pack-es <none> 1:12.04+20130128
2013-02-13 22:11:11 install language-pack-gnome-de-base <none> 1:12.04+20130128
2013-02-13 22:11:12 install language-pack-gnome-de <none> 1:12.04+20130128
2013-02-13 22:11:13 install language-pack-gnome-en-base <none> 1:12.04+20130128
2013-02-13 22:11:13 install language-pack-gnome-en <none> 1:12.04+20130128
2013-02-13 22:11:13 install language-pack-gnome-es-base <none> 1:12.04+20130128
2013-02-13 22:11:14 install language-pack-gnome-es <none> 1:12.04+20130128
2013-02-13 22:11:14 install language-pack-gnome-pt-base <none> 1:12.04+20130128
2013-02-13 22:11:15 install language-pack-pt-base <none> 1:12.04+20130128
2013-02-13 22:11:16 install language-pack-pt <none> 1:12.04+20130128
2013-02-13 22:11:16 install language-pack-gnome-pt <none> 1:12.04+20130128
2013-02-13 22:11:16 install language-pack-gnome-zh-hans-base <none> 1:12.04+20130128
2013-02-13 22:11:17 install language-pack-zh-hans-base <none> 1:12.04+20130128
2013-02-13 22:11:17 install language-pack-zh-hans <none> 1:12.04+20130128
2013-02-13 22:11:17 install language-pack-gnome-zh-hans <none> 1:12.04+20130128
2013-02-13 22:11:17 install libgtkmm-2.4-1c2a <none> 1:2.24.2-1ubuntu1
2013-02-13 22:11:17 install libreadline5 <none> 5.2-11
2013-02-13 22:11:17 install libdebian-installer4 <none> 0.79ubuntu2.1
2013-02-13 22:11:17 install archdetect-deb <none> 1.88ubuntu2
2013-02-13 22:11:17 install btrfs-tools <none> 0.19+20100601-3ubuntu3
2013-02-13 22:11:17 install cifs-utils <none> 2:5.1-1ubuntu1
2013-02-13 22:11:17 install cryptsetup <none> 2:1.4.1-2ubuntu4
2013-02-13 22:11:17 install libdmraid1.0.0.rc16 <none> 1.0.0.rc16-4.1ubuntu8
2013-02-13 22:11:17 install kpartx <none> 0.4.9-3ubuntu5
2013-02-13 22:11:17 install kpartx-boot <none> 0.4.9-3ubuntu5
2013-02-13 22:11:17 install dmraid <none> 1.0.0.rc16-4.1ubuntu8
2013-02-13 22:11:17 install dpkg-repack <none> 1.37
2013-02-13 22:11:18 install libecryptfs0 <none> 96-0ubuntu3
2013-02-13 22:11:18 install keyutils <none> 1.5.2-2
2013-02-13 22:11:18 install libnss3-1d <none> 3.14.1-0ckbi1.93ubuntu.0.12.04.1
2013-02-13 22:11:18 install ecryptfs-utils <none> 96-0ubuntu3
2013-02-13 22:11:18 install firefox-locale-de <none> 18.0.2+build1-0ubuntu0.12.04.1
2013-02-13 22:11:18 install firefox-locale-en <none> 18.0.2+build1-0ubuntu0.12.04.1
2013-02-13 22:11:18 install firefox-locale-es <none> 18.0.2+build1-0ubuntu0.12.04.1
2013-02-13 22:11:18 install firefox-locale-pt <none> 18.0.2+build1-0ubuntu0.12.04.1
2013-02-13 22:11:18 install firefox-locale-zh-hans <none> 18.0.2+build1-0ubuntu0.12.04.1
2013-02-13 22:11:18 install gir1.2-json-1.0 <none> 0.14.2-1
2013-02-13 22:11:18 install gir1.2-timezonemap-1.0 <none> 0.3.2
2013-02-13 22:11:18 install gir1.2-xkl-1.0 <none> 5.2.1-1ubuntu1
2013-02-13 22:11:18 install gparted <none> 0.11.0-2
2013-02-13 22:11:18 install jfsutils <none> 1.1.15-2
2013-02-13 22:11:18 install libdebconfclient0 <none> 0.158ubuntu1
2013-02-13 22:11:18 install python-pyicu <none> 1.3-1
2013-02-13 22:11:18 install rdate <none> 1:1.2-4build1
2013-02-13 22:11:18 install realpath <none> 1.16
2013-02-13 22:11:18 install reiserfsprogs <none> 1:3.6.21-1build1
2013-02-13 22:11:18 install ubiquity-frontend-gtk <none> 2.10.24
2013-02-13 22:11:19 install ubiquity-ubuntu-artwork <none> 2.10.24
2013-02-13 22:11:19 install ubiquity-casper <none> 1.315.1
2013-02-13 22:11:19 install apt-clone <none> 0.2.2ubuntu2
2013-02-13 22:11:19 install ubiquity <none> 2.10.24
2013-02-13 22:11:19 install ubiquity-slideshow-ubuntu <none> 58.2
2013-02-13 22:11:19 install wamerican <none> 7.1-1
2013-02-13 22:11:19 install xfsprogs <none> 3.1.7
2013-04-21 04:56:22 install linux-image-3.5.0-27-generic <none> 3.5.0-27.46~precise1
2013-04-21 04:57:34 install linux-headers-3.5.0-27 <none> 3.5.0-27.46~precise1
2013-04-21 04:57:41 install linux-headers-3.5.0-27-generic <none> 3.5.0-27.46~precise1
2013-04-21 05:49:22 install sgml-data <none> 2.0.6
2013-04-21 05:49:23 install docbook-xml <none> 4.5-7ubuntu1
2013-04-21 05:49:24 install libept1.4.12 <none> 1.0.6~exp1ubuntu1
2013-04-21 05:49:25 install libvte-common <none> 1:0.28.2-3ubuntu2
2013-04-21 05:49:25 install libvte9 <none> 1:0.28.2-3ubuntu2
2013-04-21 05:49:26 install librarian0 <none> 0.8.1-5
2013-04-21 05:49:27 install rarian-compat <none> 0.8.1-5
2013-04-21 05:49:27 install synaptic <none> 0.75.9ubuntu1


```

---

### Post by Dannox on 2013-05-11
Bump
Latest update to 3.5.0.28 now boots fine. Reccomend doing the same if you are experiencing the black screen.

---

