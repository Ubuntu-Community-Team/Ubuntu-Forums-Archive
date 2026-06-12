---
title: "I have to login twice to get in kde"
date: 2005-04-06
forum: Desktop Environments
---

### Post by bennie on 2005-04-06
When I log in to kde (after a fresh install of kubuntu) the login hangs on "initialising system services". When i do a Ctrl-Alt-Backspace and login again kde starts up. Anyone an idea what causes this?

---

### Post by bennie on 2005-04-06
the following tect appear in .xsession-errors:

Xsession: X session started for ben at wo apr  6 20:01:59 CEST 2005
startkde: Starting up...
kbuildsycoca running...
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libkdecore.so.4: undefined symbol: init_kdnssd
libhal.c 911 : Error sending msg: No reply within specified time
libhal.c 911 : Error sending msg: No reply within specified time
libhal.c 1869 : Error sending msg: No reply within specified time
libhal.c 911 : Error sending msg: No property info.category on device with id /org/freedesktop/Hal/devices/ide_0_0
libhal.c 911 : Error sending msg: No property info.category on device with id /org/freedesktop/Hal/devices/ide_0_0
libhal.c 911 : Error sending msg: No property info.category on device with id /org/freedesktop/Hal/devices/ide_0_0
libhal.c 911 : Error sending msg: No property info.category on device with id /org/freedesktop/Hal/devices/ide_0_0
libhal.c 911 : Error sending msg: No property info.category on device with id /org/freedesktop/Hal/devices/ide_0_0
libhal.c 911 : Error sending msg: No property info.category on device with id /org/freedesktop/Hal/devices/ide_0_0
libhal.c 911 : Error sending msg: No property info.category on device with id /org/freedesktop/Hal/devices/ide_0_0
libhal.c 911 : Error sending msg: No property info.category on device with id /org/freedesktop/Hal/devices/ide_0_0
libhal.c 911 : Error sending msg: No property info.category on device with id /org/freedesktop/Hal/devices/ide_0_0
libhal.c 911 : Error sending msg: No property info.category on device with id /org/freedesktop/Hal/devices/ide_0_0
libhal.c 911 : Error sending msg: No property info.category on device with id /org/freedesktop/Hal/devices/ide_0_0
libhal.c 911 : Error sending msg: No property info.category on device with id /org/freedesktop/Hal/devices/ide_0_0
libhal.c 911 : Error sending msg: No property info.category on device with id /org/freedesktop/Hal/devices/ide_0_0
libhal.c 911 : Error sending msg: No property info.category on device with id /org/freedesktop/Hal/devices/ide_0_0
libhal.c 911 : Error sending msg: No property info.category on device with id /org/freedesktop/Hal/devices/computer
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QLayout "unnamed" added to QVBox "m_body", which already has a layout
/usr/sbin/ntpdate
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QLayout "unnamed" added to QVBox "m_body", which already has a layout
/usr/sbin/ntpdate
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QLayout "unnamed" added to QVBox "m_body", which already has a layout
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QLayout "unnamed" added to QVBox "m_body", which already has a layout
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QLayout "unnamed" added to QVBox "m_body", which already has a layout
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QLayout "unnamed" added to QVBox "m_body", which already has a layout
/usr/sbin/ntpdate
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image


Anyone an idea???

---

### Post by dermotti on 2005-04-06
I had this issue. For whatever reason this fix it. I create a new user account, logged in teh new user account. Then logged out of the user account and logged back into my original account, the logged out and rebooted. Never saw the problem again. Might be worht a try.

---

