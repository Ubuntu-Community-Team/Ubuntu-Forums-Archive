---
title: "Touchpad quit working with X"
date: 2013-01-29
forum: Desktop Environments
---

### Post by celem on 2013-01-29
The touchpad of my Asus Eee PC 1015 used to work fine but stopped working about 3 weeks ago - maybe during my last upgrade on Jan 7, 2013. It is not a hardware problem because the touchpad works during the login prompts but then fails after login, when X loads.

Linux Asus-1015PEM 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux

I reinstalled xserver-xorg-input-synaptics without effect.

Xorg.0.log
```

[     6.658] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event11)
[     6.710] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[     6.710] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[     6.710] (II) LoadModule: "synaptics"
[     6.711] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     6.713] (II) Module synaptics: vendor="X.Org Foundation"
[     6.713] 	compiled for 1.10.4, module version = 1.4.1
[     6.713] 	Module class: X.Org XInput Driver
[     6.713] 	ABI class: X.Org XInput driver, version 12.3
[     6.713] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[     6.713] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     6.713] (**) ETPS/2 Elantech Touchpad: always reports core events
[     6.713] (**) Option "Device" "/dev/input/event11"
[     6.768] (--) ETPS/2 Elantech Touchpad: x-axis range 8 - 1144
[     6.768] (--) ETPS/2 Elantech Touchpad: y-axis range 8 - 760
[     6.768] (--) ETPS/2 Elantech Touchpad: pressure range 0 - 255
[     6.768] (--) ETPS/2 Elantech Touchpad: finger width range 0 - 15
[     6.768] (--) ETPS/2 Elantech Touchpad: buttons: left right double triple
[     6.820] (--) ETPS/2 Elantech Touchpad: touchpad found
[     6.894] (**) ETPS/2 Elantech Touchpad: always reports core events
[     6.984] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input11/event11"
[     6.984] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD)
[     6.984] (**) ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[     6.984] (**) ETPS/2 Elantech Touchpad: MaxSpeed is now 1.75
[     6.984] (**) ETPS/2 Elantech Touchpad: AccelFactor is now 0.147
[     6.985] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[     6.985] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[     6.985] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[     6.985] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[     6.987] (--) ETPS/2 Elantech Touchpad: touchpad found
[     6.989] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[     6.989] (II) No input driver/identifier specified (ignoring)
```

$ grep " upgrade " /var/log/dpkg.log
```
g $ grep " upgrade " /var/log/dpkg.log
2013-01-07 22:30:10 upgrade dpkg 1.16.0.3ubuntu5 1.16.0.3ubuntu5.1
2013-01-07 22:30:19 upgrade ncurses-bin 5.9-1ubuntu5 5.9-1ubuntu5.1
2013-01-07 22:30:26 upgrade perl 5.12.4-4 5.12.4-4ubuntu0.1
2013-01-07 22:30:28 upgrade libperl5.12 5.12.4-4 5.12.4-4ubuntu0.1
2013-01-07 22:30:29 upgrade perl-base 5.12.4-4 5.12.4-4ubuntu0.1
2013-01-07 22:30:38 upgrade perl-modules 5.12.4-4 5.12.4-4ubuntu0.1
2013-01-07 22:30:41 upgrade upstart 1.3-0ubuntu11 1.3-0ubuntu12
2013-01-07 22:30:41 upgrade libc-dev-bin 2.13-20ubuntu5.1 2.13-20ubuntu5.3
2013-01-07 22:30:42 upgrade libc6-dev 2.13-20ubuntu5.1 2.13-20ubuntu5.3
2013-01-07 22:30:44 upgrade libc-bin 2.13-20ubuntu5.1 2.13-20ubuntu5.3
2013-01-07 22:30:52 upgrade libc6 2.13-20ubuntu5.1 2.13-20ubuntu5.3
2013-01-07 22:31:02 upgrade libudev0 173-0ubuntu4.2 173-0ubuntu4.3
2013-01-07 22:31:02 upgrade tzdata 2012b-0ubuntu0.11.10 2012e-0ubuntu0.11.10
2013-01-07 22:31:09 upgrade ncurses-base 5.9-1ubuntu5 5.9-1ubuntu5.1
2013-01-07 22:31:13 upgrade libssl1.0.0 1.0.0e-2ubuntu4.4 1.0.0e-2ubuntu4.6
2013-01-07 22:31:18 upgrade libncursesw5 5.9-1ubuntu5 5.9-1ubuntu5.1
2013-01-07 22:31:18 upgrade libtinfo5 5.9-1ubuntu5 5.9-1ubuntu5.1
2013-01-07 22:31:22 upgrade libncurses5 5.9-1ubuntu5 5.9-1ubuntu5.1
2013-01-07 22:31:25 upgrade mawk 1.3.3-15ubuntu2 1.3.3-15ubuntu2.11.10
2013-01-07 22:31:26 upgrade libtasn1-3-dev 2.9-4 2.9-4ubuntu0.1
2013-01-07 22:31:26 upgrade libtasn1-3 2.9-4 2.9-4ubuntu0.1
2013-01-07 22:31:27 upgrade libgnutls26 2.10.5-1ubuntu3.1 2.10.5-1ubuntu3.2
2013-01-07 22:31:27 upgrade libk5crypto3 1.9.1+dfsg-1ubuntu2.2 1.9.1+dfsg-1ubuntu2.3
2013-01-07 22:31:27 upgrade libgssapi-krb5-2 1.9.1+dfsg-1ubuntu2.2 1.9.1+dfsg-1ubuntu2.3
2013-01-07 22:31:28 upgrade libkrb5-3 1.9.1+dfsg-1ubuntu2.2 1.9.1+dfsg-1ubuntu2.3
2013-01-07 22:31:28 upgrade libkrb5support0 1.9.1+dfsg-1ubuntu2.2 1.9.1+dfsg-1ubuntu2.3
2013-01-07 22:31:29 upgrade chromium-browser-l10n 18.0.1025.142~r129054-0ubuntu0.11.10.1 18.0.1025.168~r134367-0ubuntu0.11.10.1
2013-01-07 22:31:30 upgrade libcups2 1.5.0-8ubuntu6 1.5.0-8ubuntu7.3
2013-01-07 22:31:31 upgrade libexpat1-dev 2.0.1-7ubuntu3 2.0.1-7ubuntu3.11.10.1
2013-01-07 22:31:31 upgrade libexpat1 2.0.1-7ubuntu3 2.0.1-7ubuntu3.11.10.1
2013-01-07 22:31:31 upgrade libnss3-1d 3.12.9+ckbi-1.82-0ubuntu6 3.12.9+ckbi-1.82-0ubuntu6.1
2013-01-07 22:31:32 upgrade libnss3 3.12.9+ckbi-1.82-0ubuntu6 3.12.9+ckbi-1.82-0ubuntu6.1
2013-01-07 22:31:33 upgrade chromium-codecs-ffmpeg 18.0.1025.142~r129054-0ubuntu0.11.10.1 18.0.1025.168~r134367-0ubuntu0.11.10.1
2013-01-07 22:31:33 upgrade chromium-browser 18.0.1025.142~r129054-0ubuntu0.11.10.1 18.0.1025.168~r134367-0ubuntu0.11.10.1
2013-01-07 22:31:48 upgrade libcupscgi1 1.5.0-8ubuntu6 1.5.0-8ubuntu7.3
2013-01-07 22:31:48 upgrade libcupsdriver1 1.5.0-8ubuntu6 1.5.0-8ubuntu7.3
2013-01-07 22:31:49 upgrade libtiff4 3.9.5-1ubuntu1.1 3.9.5-1ubuntu1.5
2013-01-07 22:31:49 upgrade libcupsimage2 1.5.0-8ubuntu6 1.5.0-8ubuntu7.3
2013-01-07 22:31:50 upgrade libcupsmime1 1.5.0-8ubuntu6 1.5.0-8ubuntu7.3
2013-01-07 22:31:50 upgrade libcupsppdc1 1.5.0-8ubuntu6 1.5.0-8ubuntu7.3
2013-01-07 22:31:50 upgrade libgudev-1.0-0 1:173-0ubuntu4.2 1:173-0ubuntu4.3
2013-01-07 22:31:51 upgrade libqt4-opengl 4:4.7.4-0ubuntu8.1 4:4.7.4-0ubuntu8.2
2013-01-07 22:31:51 upgrade libqt4-svg 4:4.7.4-0ubuntu8.1 4:4.7.4-0ubuntu8.2
2013-01-07 22:31:52 upgrade libxi-dev 2:1.4.3-3ubuntu1 2:1.4.3-3ubuntu1.1
2013-01-07 22:31:52 upgrade libxi6 2:1.4.3-3ubuntu1 2:1.4.3-3ubuntu1.1
2013-01-07 22:31:53 upgrade libqt4-declarative 4:4.7.4-0ubuntu8.1 4:4.7.4-0ubuntu8.2
2013-01-07 22:31:54 upgrade libqtgui4 4:4.7.4-0ubuntu8.1 4:4.7.4-0ubuntu8.2
2013-01-07 22:31:57 upgrade libqt4-xmlpatterns 4:4.7.4-0ubuntu8.1 4:4.7.4-0ubuntu8.2
2013-01-07 22:31:58 upgrade libqt4-network 4:4.7.4-0ubuntu8.1 4:4.7.4-0ubuntu8.2
2013-01-07 22:31:59 upgrade libqt4-script 4:4.7.4-0ubuntu8.1 4:4.7.4-0ubuntu8.2
2013-01-07 22:32:00 upgrade mysql-common 5.1.61-0ubuntu0.11.10.1 5.1.66-0ubuntu0.11.10.3
2013-01-07 22:32:01 upgrade libmysqlclient16 5.1.61-0ubuntu0.11.10.1 5.1.66-0ubuntu0.11.10.3
2013-01-07 22:32:01 upgrade libqt4-sql-mysql 4:4.7.4-0ubuntu8.1 4:4.7.4-0ubuntu8.2
2013-01-07 22:32:02 upgrade libqt4-sql 4:4.7.4-0ubuntu8.1 4:4.7.4-0ubuntu8.2
2013-01-07 22:32:02 upgrade qdbus 4:4.7.4-0ubuntu8.1 4:4.7.4-0ubuntu8.2
2013-01-07 22:32:02 upgrade libqt4-dbus 4:4.7.4-0ubuntu8.1 4:4.7.4-0ubuntu8.2
2013-01-07 22:32:03 upgrade libqt4-xml 4:4.7.4-0ubuntu8.1 4:4.7.4-0ubuntu8.2
2013-01-07 22:32:04 upgrade libqtcore4 4:4.7.4-0ubuntu8.1 4:4.7.4-0ubuntu8.2
2013-01-07 22:32:05 upgrade lightdm 1.0.6-0ubuntu1.6 1.0.6-0ubuntu1.7
2013-01-07 22:32:06 upgrade libapt-pkg4.11 0.8.16~exp5ubuntu13.2 0.8.16~exp5ubuntu13.6
2013-01-07 22:32:21 upgrade gpgv 1.4.11-3ubuntu1 1.4.11-3ubuntu1.11.10.1
2013-01-07 22:32:28 upgrade gnupg 1.4.11-3ubuntu1 1.4.11-3ubuntu1.11.10.1
2013-01-07 22:32:36 upgrade apt 0.8.16~exp5ubuntu13.2 0.8.16~exp5ubuntu13.6
2013-01-07 22:32:43 upgrade multiarch-support 2.13-20ubuntu5.1 2.13-20ubuntu5.3
2013-01-07 22:32:46 upgrade libpython2.7 2.7.2-5ubuntu1 2.7.2-5ubuntu1.1
2013-01-07 22:32:47 upgrade python2.7 2.7.2-5ubuntu1 2.7.2-5ubuntu1.1
2013-01-07 22:32:49 upgrade python2.7-minimal 2.7.2-5ubuntu1 2.7.2-5ubuntu1.1
2013-01-07 22:32:59 upgrade libapt-inst1.3 0.8.16~exp5ubuntu13.2 0.8.16~exp5ubuntu13.6
2013-01-07 22:32:59 upgrade apt-utils 0.8.16~exp5ubuntu13.2 0.8.16~exp5ubuntu13.6
2013-01-07 22:33:00 upgrade isc-dhcp-client 4.1.1-P1-17ubuntu10.1 4.1.1-P1-17ubuntu10.5
2013-01-07 22:33:00 upgrade isc-dhcp-common 4.1.1-P1-17ubuntu10.1 4.1.1-P1-17ubuntu10.5
2013-01-07 22:33:01 upgrade sudo 1.7.4p6-1ubuntu2 1.7.4p6-1ubuntu2.1
2013-01-07 22:33:01 upgrade udev 173-0ubuntu4.2 173-0ubuntu4.3
2013-01-07 22:33:03 upgrade vim-tiny 2:7.3.154+hg~74503f6ee649-2ubuntu3 2:7.3.154+hg~74503f6ee649-2ubuntu3.1
2013-01-07 22:33:03 upgrade vim-common 2:7.3.154+hg~74503f6ee649-2ubuntu3 2:7.3.154+hg~74503f6ee649-2ubuntu3.1
2013-01-07 22:33:04 upgrade ubuntu-minimal 1.245 1.245.1
2013-01-07 22:33:04 upgrade insserv 1.14.0-2.1 1.14.0-2.1ubuntu0.2
2013-01-07 22:33:05 upgrade libxml2 2.7.8.dfsg-4ubuntu0.2 2.7.8.dfsg-4ubuntu0.5
2013-01-07 22:33:05 upgrade bind9-host 1:9.7.3.dfsg-1ubuntu4.1 1:9.7.3.dfsg-1ubuntu4.5
2013-01-07 22:33:06 upgrade dnsutils 1:9.7.3.dfsg-1ubuntu4.1 1:9.7.3.dfsg-1ubuntu4.5
2013-01-07 22:33:06 upgrade libisc62 1:9.7.3.dfsg-1ubuntu4.1 1:9.7.3.dfsg-1ubuntu4.5
2013-01-07 22:33:06 upgrade libdns69 1:9.7.3.dfsg-1ubuntu4.1 1:9.7.3.dfsg-1ubuntu4.5
2013-01-07 22:33:07 upgrade libisccc60 1:9.7.3.dfsg-1ubuntu4.1 1:9.7.3.dfsg-1ubuntu4.5
2013-01-07 22:33:07 upgrade libisccfg62 1:9.7.3.dfsg-1ubuntu4.1 1:9.7.3.dfsg-1ubuntu4.5
2013-01-07 22:33:08 upgrade liblwres60 1:9.7.3.dfsg-1ubuntu4.1 1:9.7.3.dfsg-1ubuntu4.5
2013-01-07 22:33:08 upgrade libbind9-60 1:9.7.3.dfsg-1ubuntu4.1 1:9.7.3.dfsg-1ubuntu4.5
2013-01-07 22:33:08 upgrade iso-codes 3.27-1 3.27-1ubuntu1
2013-01-07 22:33:13 upgrade update-manager-core 1:0.152.25.8 1:0.152.25.13
2013-01-07 22:33:14 upgrade accountsservice 0.6.14-1git1ubuntu1.1 0.6.14-1git1ubuntu1.2
2013-01-07 22:33:15 upgrade libaccountsservice0 0.6.14-1git1ubuntu1.1 0.6.14-1git1ubuntu1.2
2013-01-07 22:33:15 upgrade acpi-support 0.138 0.138.1
2013-01-07 22:33:16 upgrade apt-transport-https 0.8.16~exp5ubuntu13.2 0.8.16~exp5ubuntu13.6
2013-01-07 22:33:16 upgrade samba 2:3.5.11~dfsg-1ubuntu2.2 2:3.5.11~dfsg-1ubuntu2.3
2013-01-07 22:33:21 upgrade libwbclient0 2:3.5.11~dfsg-1ubuntu2.2 2:3.5.11~dfsg-1ubuntu2.3
2013-01-07 22:33:21 upgrade smbclient 2:3.5.11~dfsg-1ubuntu2.2 2:3.5.11~dfsg-1ubuntu2.3
2013-01-07 22:33:25 upgrade samba-common 2:3.5.11~dfsg-1ubuntu2.2 2:3.5.11~dfsg-1ubuntu2.3
2013-01-07 22:33:25 upgrade samba-common-bin 2:3.5.11~dfsg-1ubuntu2.2 2:3.5.11~dfsg-1ubuntu2.3
2013-01-07 22:33:27 upgrade cups-common 1.5.0-8ubuntu6 1.5.0-8ubuntu7.3
2013-01-07 22:33:28 upgrade cups-bsd 1.5.0-8ubuntu6 1.5.0-8ubuntu7.3
2013-01-07 22:33:30 upgrade cups-client 1.5.0-8ubuntu6 1.5.0-8ubuntu7.3
2013-01-07 22:33:31 upgrade cups-ppdc 1.5.0-8ubuntu6 1.5.0-8ubuntu7.3
2013-01-07 22:33:31 upgrade cups 1.5.0-8ubuntu6 1.5.0-8ubuntu7.3
2013-01-07 22:33:34 upgrade libexif12 0.6.20-1 0.6.20-1ubuntu0.1
2013-01-07 22:33:36 upgrade libgrip0 0.3.2-0ubuntu3.1 0.3.2.1-0ubuntu1
2013-01-07 22:33:36 upgrade eog 3.2.1-0ubuntu1 3.2.1-0ubuntu1.1
2013-01-07 22:33:40 upgrade evince 3.2.1-0ubuntu2.2 3.2.1-0ubuntu2.3
2013-01-07 22:33:40 upgrade libevince3-3 3.2.1-0ubuntu2.2 3.2.1-0ubuntu2.3
2013-01-07 22:33:41 upgrade evince-common 3.2.1-0ubuntu2.2 3.2.1-0ubuntu2.3
2013-01-07 22:33:47 upgrade firefox-globalmenu 11.0+build1-0ubuntu0.11.10.1 17.0.1+build1-0ubuntu0.11.10.1
2013-01-07 22:33:47 upgrade firefox 11.0+build1-0ubuntu0.11.10.1 17.0.1+build1-0ubuntu0.11.10.1
2013-01-07 22:33:53 upgrade firefox-gnome-support 11.0+build1-0ubuntu0.11.10.1 17.0.1+build1-0ubuntu0.11.10.1
2013-01-07 22:33:53 upgrade firefox-locale-en 11.0+build1-0ubuntu0.11.10.1 17.0.1+build1-0ubuntu0.11.10.1
2013-01-07 22:33:54 upgrade libgimp2.0 2.6.11-2ubuntu4 2.6.11-2ubuntu4.2
2013-01-07 22:33:54 upgrade gimp-data 2.6.11-2ubuntu4 2.6.11-2ubuntu4.2
2013-01-07 22:33:56 upgrade gimp 2.6.11-2ubuntu4 2.6.11-2ubuntu4.2
2013-01-07 22:33:58 upgrade gir1.2-accountsservice-1.0 0.6.14-1git1ubuntu1.1 0.6.14-1git1ubuntu1.2
2013-01-07 22:33:59 upgrade gir1.2-evince-3.0 3.2.1-0ubuntu2.2 3.2.1-0ubuntu2.3
2013-01-07 22:33:59 upgrade libnm-util2 0.9.1.90-0ubuntu5.1 0.9.1.90-0ubuntu5.2
2013-01-07 22:33:59 upgrade libnm-glib4 0.9.1.90-0ubuntu5.1 0.9.1.90-0ubuntu5.2
2013-01-07 22:34:00 upgrade gir1.2-networkmanager-1.0 0.9.1.90-0ubuntu5.1 0.9.1.90-0ubuntu5.2
2013-01-07 22:34:00 upgrade gvfs-fuse 1.10.0-0ubuntu1 1.10.0-0ubuntu1.1
2013-01-07 22:34:01 upgrade gvfs-bin 1.10.0-0ubuntu1 1.10.0-0ubuntu1.1
2013-01-07 22:34:01 upgrade libsmbclient 2:3.5.11~dfsg-1ubuntu2.2 2:3.5.11~dfsg-1ubuntu2.3
2013-01-07 22:34:02 upgrade gvfs 1.10.0-0ubuntu1 1.10.0-0ubuntu1.1
2013-01-07 22:34:03 upgrade gvfs-backends 1.10.0-0ubuntu1 1.10.0-0ubuntu1.1
2013-01-07 22:34:03 upgrade im-switch 1.20ubuntu5 1.20ubuntu5.0
2013-01-07 22:34:05 upgrade libmagickcore3 8:6.6.0.4-3ubuntu1 8:6.6.0.4-3ubuntu1.2
2013-01-07 22:34:06 upgrade libmagickwand3 8:6.6.0.4-3ubuntu1 8:6.6.0.4-3ubuntu1.2
2013-01-07 22:34:06 upgrade imagemagick 8:6.6.0.4-3ubuntu1 8:6.6.0.4-3ubuntu1.2
2013-01-07 22:34:07 upgrade libatk-adaptor 2.2.1-0ubuntu1 2.2.2-0ubuntu1
2013-01-07 22:34:07 upgrade libpostproc52 4:0.7.3-0ubuntu0.11.10.1 4:0.7.6-0ubuntu0.11.10.2
2013-01-07 22:34:08 upgrade libswscale2 4:0.7.3-0ubuntu0.11.10.1 4:0.7.6-0ubuntu0.11.10.2
2013-01-07 22:34:08 upgrade libavformat53 4:0.7.3-0ubuntu0.11.10.1 4:0.7.6-0ubuntu0.11.10.2
2013-01-07 22:34:09 upgrade libavcodec53 4:0.7.3-0ubuntu0.11.10.1 4:0.7.6-0ubuntu0.11.10.2
2013-01-07 22:34:10 upgrade libavutil51 4:0.7.3-0ubuntu0.11.10.1 4:0.7.6-0ubuntu0.11.10.2
2013-01-07 22:34:11 upgrade libgdata-common 0.9.1-0ubuntu2 0.9.1-0ubuntu2.1
2013-01-07 22:34:11 upgrade libgdata13 0.9.1-0ubuntu2 0.9.1-0ubuntu2.1
2013-01-07 22:34:12 upgrade liblightdm-gobject-1-0 1.0.6-0ubuntu1.6 1.0.6-0ubuntu1.7
2013-01-07 22:34:12 upgrade libmission-control-plugins0 1:5.9.1-0ubuntu2 1:5.9.1-0ubuntu2.1
2013-01-07 22:34:13 upgrade libmono-system-xml4.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:13 upgrade libmono-system-security4.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:14 upgrade libmono-system-configuration4.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:14 upgrade libmono-system4.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:15 upgrade libmono-security4.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:15 upgrade mono-runtime 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:16 upgrade mono-gac 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:16 upgrade mono-4.0-gac 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:17 upgrade libmono-corlib4.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:17 upgrade libmono-cairo4.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:18 upgrade libmono-corlib2.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:18 upgrade libmono-posix4.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:19 upgrade libmono-system-core4.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:19 upgrade libmono-csharp4.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:20 upgrade libmono-posix2.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:20 upgrade libmono-system2.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:21 upgrade libmono-security2.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:21 upgrade libmono-data-tds2.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:22 upgrade libmono-i18n-west2.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:22 upgrade libmono-i18n4.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:22 upgrade libmono-i18n-west4.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:23 upgrade libmono-messaging2.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:23 upgrade libmono-sharpzip2.84-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:23 upgrade libmono-sharpzip4.84-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:24 upgrade libmono-system-data2.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:24 upgrade libmono-sqlite2.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:25 upgrade libmono-system-messaging2.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:25 upgrade libmono2.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:25 upgrade libmono-system-web2.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:26 upgrade libmono-wcf3.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:27 upgrade libmono-system-data-linq2.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:27 upgrade libmono-system-drawing4.0-cil 2.10.5-1 2.10.5-1ubuntu0.1
2013-01-07 22:34:28 upgrade libnm-glib-vpn1 0.9.1.90-0ubuntu5.1 0.9.1.90-0ubuntu5.2
2013-01-07 22:34:28 upgrade libnm-gtk-common 0.9.1.90-0ubuntu6 0.9.1.90-0ubuntu6.1
2013-01-07 22:34:28 upgrade libnm-gtk0 0.9.1.90-0ubuntu6 0.9.1.90-0ubuntu6.1
2013-01-07 22:34:29 upgrade libproxy0 0.3.1-2ubuntu6 0.3.1-2ubuntu6.1
2013-01-07 22:34:29 upgrade libpurple-bin 1:2.10.0-0ubuntu2 1:2.10.0-0ubuntu2.1
2013-01-07 22:34:30 upgrade libpurple0 1:2.10.0-0ubuntu2 1:2.10.0-0ubuntu2.1
2013-01-07 22:34:31 upgrade ure 3.4.4-0ubuntu1 3.4.4-0ubuntu1.4
2013-01-07 22:34:33 upgrade uno-libs3 3.4.4-0ubuntu1 3.4.4-0ubuntu1.4
2013-01-07 22:34:33 upgrade libreoffice-writer 1:3.4.4-0ubuntu1 1:3.4.4-0ubuntu1.4
2013-01-07 22:34:38 upgrade libreoffice-calc 1:3.4.4-0ubuntu1 1:3.4.4-0ubuntu1.4
2013-01-07 22:34:42 upgrade libreoffice-base 1:3.4.4-0ubuntu1 1:3.4.4-0ubuntu1.4
2013-01-07 22:34:44 upgrade libreoffice-base-core 1:3.4.4-0ubuntu1 1:3.4.4-0ubuntu1.4
2013-01-07 22:34:45 upgrade libreoffice-impress 1:3.4.4-0ubuntu1 1:3.4.4-0ubuntu1.4
2013-01-07 22:34:46 upgrade libreoffice-draw 1:3.4.4-0ubuntu1 1:3.4.4-0ubuntu1.4
2013-01-07 22:34:49 upgrade libreoffice-gtk 1:3.4.4-0ubuntu1 1:3.4.4-0ubuntu1.4
2013-01-07 22:34:49 upgrade libreoffice-gnome 1:3.4.4-0ubuntu1 1:3.4.4-0ubuntu1.4
2013-01-07 22:34:50 upgrade python-uno 1:3.4.4-0ubuntu1 1:3.4.4-0ubuntu1.4
2013-01-07 22:34:51 upgrade libreoffice-common 1:3.4.4-0ubuntu1 1:3.4.4-0ubuntu1.4
2013-01-07 22:35:02 upgrade libreoffice-style-tango 1:3.4.4-0ubuntu1 1:3.4.4-0ubuntu1.4
2013-01-07 22:35:04 upgrade ttf-opensymbol 2:2.4.3+LibO3.4.4-0ubuntu1 2:2.4.3+LibO3.4.4-0ubuntu1.4
2013-01-07 22:35:04 upgrade libreoffice-math 1:3.4.4-0ubuntu1 1:3.4.4-0ubuntu1.4
2013-01-07 22:35:05 upgrade libxslt1.1 1.1.26-7 1.1.26-7ubuntu0.1
2013-01-07 22:35:05 upgrade libreoffice-core 1:3.4.4-0ubuntu1 1:3.4.4-0ubuntu1.4
2013-01-07 22:35:23 upgrade libreoffice-java-common 1:3.4.4-0ubuntu1 1:3.4.4-0ubuntu1.4
2013-01-07 22:35:25 upgrade libreoffice-emailmerge 1:3.4.4-0ubuntu1 1:3.4.4-0ubuntu1.4
2013-01-07 22:35:26 upgrade libreoffice-help-en-us 1:3.4.4-0ubuntu1 1:3.4.4-0ubuntu1.4
2013-01-07 22:35:30 upgrade libservlet2.5-java 6.0.32-5ubuntu1.2 6.0.32-5ubuntu1.3
2013-01-07 22:35:30 upgrade libsnmp-base 5.4.3~dfsg-2.2ubuntu1 5.4.3~dfsg-2.2ubuntu1.1
2013-01-07 22:35:31 upgrade libsnmp15 5.4.3~dfsg-2.2ubuntu1 5.4.3~dfsg-2.2ubuntu1.1
2013-01-07 22:35:32 upgrade libunity-core-4.0-4 4.28.0-0ubuntu2 4.30.0-0ubuntu1
2013-01-07 22:35:32 upgrade unity-services 4.28.0-0ubuntu2 4.30.0-0ubuntu1
2013-01-07 22:35:33 upgrade libxml2-utils 2.7.8.dfsg-4ubuntu0.2 2.7.8.dfsg-4ubuntu0.5
2013-01-07 22:35:36 upgrade network-manager 0.9.1.90-0ubuntu5.1 0.9.1.90-0ubuntu5.2
2013-01-07 22:35:37 upgrade network-manager-gnome 0.9.1.90-0ubuntu6 0.9.1.90-0ubuntu6.1
2013-01-07 22:35:38 upgrade openssl 1.0.0e-2ubuntu4.4 1.0.0e-2ubuntu4.6
2013-01-07 22:35:38 upgrade pidgin-data 1:2.10.0-0ubuntu2 1:2.10.0-0ubuntu2.1
2013-01-07 22:35:40 upgrade pidgin 1:2.10.0-0ubuntu2 1:2.10.0-0ubuntu2.1
2013-01-07 22:35:41 upgrade python-crypto 2.3-2 2.3-2ubuntu0.1
2013-01-07 22:35:43 upgrade python-egenix-mxtools 3.2.0-1 3.2.1-1~oneiric0.1
2013-01-07 22:35:44 upgrade python-egenix-mxdatetime 3.2.0-1 3.2.1-1~oneiric0.1
2013-01-07 22:35:45 upgrade python-keyring 0.6.2-1 0.9.2-0ubuntu0.11.10.2
2013-01-07 22:35:46 upgrade python-libproxy 0.3.1-2ubuntu6 0.3.1-2ubuntu6.1
2013-01-07 22:35:47 upgrade python-libxml2 2.7.8.dfsg-4ubuntu0.2 2.7.8.dfsg-4ubuntu0.5
2013-01-07 22:35:48 upgrade python-problem-report 1.23-0ubuntu4 1.23-0ubuntu4.1
2013-01-07 22:35:49 upgrade thunderbird-globalmenu 11.0.1+build1-0ubuntu0.11.10.1 17.0+build2-0ubuntu0.11.10.1
2013-01-07 22:35:50 upgrade thunderbird 11.0.1+build1-0ubuntu0.11.10.1 17.0+build2-0ubuntu0.11.10.1
2013-01-07 22:35:55 upgrade thunderbird-gnome-support 11.0.1+build1-0ubuntu0.11.10.1 17.0+build2-0ubuntu0.11.10.1
2013-01-07 22:35:55 upgrade update-notifier-common 0.117ubuntu3.2 0.117ubuntu3.3
2013-01-07 22:35:56 upgrade virtualbox-guest-x11 4.1.2-dfsg-1ubuntu1 4.1.2-dfsg-1ubuntu1.1
2013-01-07 22:35:57 upgrade virtualbox-guest-utils 4.1.2-dfsg-1ubuntu1 4.1.2-dfsg-1ubuntu1.1
2013-01-07 22:35:57 upgrade virtualbox-guest-dkms 4.1.2-dfsg-1ubuntu1 4.1.2-dfsg-1ubuntu1.1
2013-01-07 22:36:06 upgrade xserver-common 2:1.10.4-1ubuntu4.2 2:1.10.4-1ubuntu4.3
2013-01-07 22:36:07 upgrade aptdaemon-data 0.43+bzr697-0ubuntu1.2 0.43+bzr697-0ubuntu1.3
2013-01-07 22:36:07 upgrade python-aptdaemon-gtk 0.43+bzr697-0ubuntu1.2 0.43+bzr697-0ubuntu1.3
2013-01-07 22:36:08 upgrade python-aptdaemon.gtk3widgets 0.43+bzr697-0ubuntu1.2 0.43+bzr697-0ubuntu1.3
2013-01-07 22:36:09 upgrade python-aptdaemon.gtkwidgets 0.43+bzr697-0ubuntu1.2 0.43+bzr697-0ubuntu1.3
2013-01-07 22:36:10 upgrade aptdaemon 0.43+bzr697-0ubuntu1.2 0.43+bzr697-0ubuntu1.3
2013-01-07 22:36:10 upgrade python-aptdaemon 0.43+bzr697-0ubuntu1.2 0.43+bzr697-0ubuntu1.3
2013-01-07 22:36:11 upgrade cups-pk-helper 0.1.2-1 0.1.2-1ubuntu0.1
2013-01-07 22:36:12 upgrade ginn 0.2.4-0ubuntu1 0.2.4.1-0ubuntu1~11.10.1
2013-01-07 22:36:12 upgrade gnome-settings-daemon 3.2.2-0ubuntu2.1 3.2.2-0ubuntu2.3
2013-01-07 22:36:13 upgrade jupiter 0.1.2-1~webupd8-1 0.1.9-2~webupd8~0
2013-01-07 22:36:13 upgrade libtasn1-3-bin 2.9-4 2.9-4ubuntu0.1
2013-01-07 22:46:17 upgrade xserver-xorg-input-synaptics 1.4.1-1ubuntu2 1.4.1-1ubuntu2.1

```

---

### Post by papibe on 2013-01-29
Hi celem.

There's used to be a bug on 11.11 (apparently fixed now). I wonder if it is what you are experiencing: [Bug #868400]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/868400").

The partial solution (described on the comments) is to do this:
```
sudo killall -u lightdm syndaemon

synclient Touchpadoff=0

```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by celem on 2013-01-29
Thank you for the reply. Unfortunately, this isn't my problem - I have only one syndaemon instance running,

```
ecomer@Asus-1015PEM ~ $ ps -A|grep syndaemon
 1825 ?        00:00:00 syndaemon
ecomer@Asus-1015PEM ~ $ 

```

---

### Post by forced-rhythm on 2013-05-11
I have the same problem. I thought it was a driver error, and upon restarting thought I was saved. Logged in, and there it went. It's recognized by xinput - it just freezes for some reason...

---

