---
title: "Kiba dock fails when trying to install"
date: 2010-01-15
forum: Desktop Environments
---

### Post by Gajhede on 2010-01-15
Hello out there.. I have installed Kiba dock thorugh this thread

[http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)

but when i try to install the last plugin it comes with a error, this is where i am in the guide

cd kiba-dbus-plugins/
./autogen.sh
sudo make install
cd ..

while using the command ./autogen.sh i get this:

checking for KIBA_DOCK... configure: error: Package requirements (kiba-dock = 9999) were not met:

Requested 'kiba-dock = 9999' but version of kiba-dock is 9999.0.0

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables KIBA_DOCK_CFLAGS
and KIBA_DOCK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

the only place i could find this error was some russian forum tried to use google translate but didn't really work out :/ 

hope someone out there got some ideas?!

---

### Post by Gajhede on 2010-01-17
dump

---

### Post by Gajhede on 2010-01-21
no one out there?

---

### Post by Rongidge on 2010-03-17
Had this problem myself, here's the solution:

```
sudo nano /usr/lib64/pkgconfig/kiba-dock.pc
```look for a line with Version in front of it and change it from "9999.0.0" to "9999"

If you cant find your kiba-dock.pc and you have no clue where it could be, just run:

```
cd /; sudo find -name kiba-dock.pc
```

---

### Post by conceptrat on 2010-04-12
> **Rongidge said:**
> Had this problem myself, here's the solution:

```
sudo nano /usr/lib64/pkgconfig/kiba-dock.pc
```look for a line with Version in front of it and change it from "9999.0.0" to "9999"

If you cant find your kiba-dock.pc and you have no clue where it could be, just run:

```
cd /; sudo find -name kiba-dock.pc
```

Actually you probably want to modify "kiba-dbus-plugins/configure.ac" in the compilation directory and change the following:

```
Line#52: PKG_CHECK_MODULES(KIBA_DOCK, [kiba-dock = 9999])
```

to:

```
Line#52: PKG_CHECK_MODULES(KIBA_DOCK, [kiba-dock >= 9999])
```

This might be a little cleaner as I think the requirement is for a version of KibaDock of at least 9999 (development).  I'm not so sure about the reasoning behind such a high version number other than this being a development version.

---

