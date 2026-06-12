---
title: "gdm and Gnome Shell elements not visible/clickable after recent apt-get dist-upgrade"
date: 2014-08-20
forum: Desktop Environments
---

### Post by kogz on 2014-08-20
Hi guys,

After last "apt-get dist-upgrade" I cannot use gdm.. When computer starts, I receive grey gdm background wallpaper, but no elements there, like account list or buttons.. I can only move mouse cursor on empty screen.

I switched from gdm to lightdm, I received logon screen and I can login, but I use Gnome Shell environment and after successful login I get only wallpaper and top menu, but I cannot click anything, just move a mouse cursor.. very similar symptom to gdm..

I think it's kind of gnome/gtk-related. Any idea how could I troubleshoot this?

This is apt-get history for that event:

```
Start-Date: 2014-08-19  17:47:11
Commandline: apt-get dist-upgrade
Install: linux-image-extra-3.13.0-34-generic:amd64 (3.13.0-34.60, automatic)
 linux-image-3.13.0-34-generic:amd64 (3.13.0-34.60, automatic)
 mircommon-dev:amd64 (0.1.8+14.04.20140411-0ubuntu1, automatic)
 linux-headers-3.13.0-34-generic:amd64 (3.13.0-34.60, automatic)
 libprotobuf-dev:amd64 (2.5.0-9ubuntu1, automatic)
 libmirclient7:amd64 (0.1.8+14.04.20140411-0ubuntu1, automatic)
 libmirprotobuf-dev:amd64 (0.1.8+14.04.20140411-0ubuntu1, automatic)
 linux-headers-3.13.0-34:amd64 (3.13.0-34.60, automatic)
 linux-signed-image-3.13.0-34-generic:amd64 (3.13.0-34.60, automatic)
 ca-certificates-java:amd64 (20130815ubuntu1, automatic)
 libmirclientplatform-mesa:amd64 (0.1.8+14.04.20140411-0ubuntu1, automatic)
 libmirprotobuf0:amd64 (0.1.8+14.04.20140411-0ubuntu1, automatic)
 libmirclient-dev:amd64 (0.1.8+14.04.20140411-0ubuntu1, automatic)
 libprotobuf-lite8:amd64 (2.5.0-9ubuntu1, automatic)
Upgrade: libgl1-mesa-dev:amd64 (10.3.0~git20140812.fa5b76e3-0ubuntu0ricotz~trusty, 10.3.0~git20140818.e9a4e749-0ubuntu0sarvatt2~trusty)
 libsystemd-login0:amd64 (204-5ubuntu20.3, 204-5ubuntu20.4)
 linux-headers-generic:amd64 (3.13.0.33.39, 3.13.0.34.40)
 libegl1-mesa:amd64 (10.3.0~git20140812.fa5b76e3-0ubuntu0ricotz~trusty, 10.3.0~git20140818.e9a4e749-0ubuntu0sarvatt2~trusty)
 libopenvg1-mesa:amd64 (10.3.0~git20140812.fa5b76e3-0ubuntu0ricotz~trusty, 10.3.0~git20140818.e9a4e749-0ubuntu0sarvatt2~trusty)
 oracle-java7-installer:amd64 (7u65+7u60arm-0~webupd8~2, 7u67+7u60arm-0~webupd8~2)
 systemd-services:amd64 (204-5ubuntu20.3, 204-5ubuntu20.4)
 libegl1-mesa-drivers:amd64 (10.3.0~git20140812.fa5b76e3-0ubuntu0ricotz~trusty, 10.3.0~git20140818.e9a4e749-0ubuntu0sarvatt2~trusty)
 oracle-java7-set-default:amd64 (7u65+7u60arm-0~webupd8~2, 7u67+7u60arm-0~webupd8~2)
 libegl1-mesa-dev:amd64 (10.3.0~git20140812.fa5b76e3-0ubuntu0ricotz~trusty, 10.3.0~git20140818.e9a4e749-0ubuntu0sarvatt2~trusty)
 libgl1-mesa-dri:amd64 (10.3.0~git20140812.fa5b76e3-0ubuntu0ricotz~trusty, 10.3.0~git20140818.e9a4e749-0ubuntu0sarvatt2~trusty)
 libgl1-mesa-dri:i386 (10.3.0~git20140812.fa5b76e3-0ubuntu0ricotz~trusty, 10.3.0~git20140818.e9a4e749-0ubuntu0sarvatt2~trusty)
 libsystemd-daemon0:amd64 (204-5ubuntu20.3, 204-5ubuntu20.4)
 libgudev-1.0-0:amd64 (204-5ubuntu20.3, 204-5ubuntu20.4)
 libpam-systemd:amd64 (204-5ubuntu20.3, 204-5ubuntu20.4)
 libglapi-mesa:amd64 (10.3.0~git20140812.fa5b76e3-0ubuntu0ricotz~trusty, 10.3.0~git20140818.e9a4e749-0ubuntu0sarvatt2~trusty)
 libglapi-mesa:i386 (10.3.0~git20140812.fa5b76e3-0ubuntu0ricotz~trusty, 10.3.0~git20140818.e9a4e749-0ubuntu0sarvatt2~trusty)
 xbmc-bin:amd64 (13.1~git20140606.0917-gotham-0trusty, 13.2~git20140817.2155-final-0trusty)
 udev:amd64 (204-5ubuntu20.3, 204-5ubuntu20.4)
 gir1.2-gudev-1.0:amd64 (204-5ubuntu20.3, 204-5ubuntu20.4)
 libgles2-mesa:amd64 (10.3.0~git20140812.fa5b76e3-0ubuntu0ricotz~trusty, 10.3.0~git20140818.e9a4e749-0ubuntu0sarvatt2~trusty)
 libudev1:amd64 (204-5ubuntu20.3, 204-5ubuntu20.4)
 libudev1:i386 (204-5ubuntu20.3, 204-5ubuntu20.4)
 libgl1-mesa-glx:amd64 (10.3.0~git20140812.fa5b76e3-0ubuntu0ricotz~trusty, 10.3.0~git20140818.e9a4e749-0ubuntu0sarvatt2~trusty)
 libgl1-mesa-glx:i386 (10.3.0~git20140812.fa5b76e3-0ubuntu0ricotz~trusty, 10.3.0~git20140818.e9a4e749-0ubuntu0sarvatt2~trusty)
 libxatracker2:amd64 (10.3.0~git20140812.fa5b76e3-0ubuntu0ricotz~trusty, 10.3.0~git20140818.e9a4e749-0ubuntu0sarvatt2~trusty)
 linux-signed-generic:amd64 (3.13.0.33.39, 3.13.0.34.40)
 xserver-xorg-video-intel:amd64 (2.99.914+git20140811.6554cf0a-0ubuntu0sarvatt~trusty, 2.99.914+git20140818.f5469681-0ubuntu0sarvatt~trusty)
 xbmc:amd64 (13.1~git20140606.0917-gotham-0trusty, 13.2~git20140817.2155-final-0trusty)
 libsystemd-journal0:amd64 (204-5ubuntu20.3, 204-5ubuntu20.4)
 libosmesa6:amd64 (10.3.0~git20140812.fa5b76e3-0ubuntu0ricotz~trusty, 10.3.0~git20140818.e9a4e749-0ubuntu0sarvatt2~trusty)
 libosmesa6:i386 (10.3.0~git20140812.fa5b76e3-0ubuntu0ricotz~trusty, 10.3.0~git20140818.e9a4e749-0ubuntu0sarvatt2~trusty)
 libwayland-egl1-mesa:amd64 (10.3.0~git20140812.fa5b76e3-0ubuntu0ricotz~trusty, 10.3.0~git20140818.e9a4e749-0ubuntu0sarvatt2~trusty)
 libgbm1:amd64 (10.3.0~git20140812.fa5b76e3-0ubuntu0ricotz~trusty, 10.3.0~git20140818.e9a4e749-0ubuntu0sarvatt2~trusty)
 linux-signed-image-generic:amd64 (3.13.0.33.39, 3.13.0.34.40)
 mesa-common-dev:amd64 (10.3.0~git20140812.fa5b76e3-0ubuntu0ricotz~trusty, 10.3.0~git20140818.e9a4e749-0ubuntu0sarvatt2~trusty)
 libgles2-mesa-dev:amd64 (10.3.0~git20140812.fa5b76e3-0ubuntu0ricotz~trusty, 10.3.0~git20140818.e9a4e749-0ubuntu0sarvatt2~trusty)
 linux-libc-dev:amd64 (3.13.0-33.58, 3.13.0-34.60)
 net-tools:amd64 (1.60-25ubuntu2, 1.60-25ubuntu2.1)
 linux-image-generic:amd64 (3.13.0.33.39, 3.13.0.34.40)
 linux-generic:amd64 (3.13.0.33.39, 3.13.0.34.40)
 xserver-xorg-video-nouveau:amd64 (1.0.10+git20140811.17de663a-0ubuntu0sarvatt~trusty, 1.0.10+git20140818.16c885ce-0ubuntu0sarvatt~trusty)
End-Date: 2014-08-19  17:52:24
```

Thank you.

Kind regards,
K

---

