---
title: "Error installing cairo-dock in 8.04 Beta - &quot;No package 'dbus-glib-1' found&quot;"
date: 2008-04-07
forum: Desktop Effects &amp; Customization
---

### Post by diablo75 on 2008-04-07
I am trying to compile the source using this command:

```
/opt/cairo-dock/trunk/cairo-dock$ **autoreconf -i -v -f && ./configure --prefix=/usr && make**
```

And I get this after a lot of good looking progress in the compiling:

```
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... configure: error: Package requirements ("gtk+-2.0 gthread-2.0 cairo librsvg-2.0 glitz dbus-glib-1") were not met:

**No package 'dbus-glib-1' found**

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I am currently running a fresh install of 8.04 Beta.

---

### Post by nuclearpidgeon on 2008-04-07
Try this -
```
sudo apt-get install dbus-glib-1
```
or, just type
```
sudo apt-get install dbus
```
then press TAB twice to get a list of all available packages starting with 'dbus'

---

### Post by diablo75 on 2008-04-07
I tried that, and here's what I got:

```
zeke@zeke-desktop:~$ sudo apt-get install dbus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dbus is already the newest version.
dbus set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
zeke@zeke-desktop:~$ sudo apt-get install dbus-glib-1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package dbus-glib-1
zeke@zeke-desktop:~$ 

```

Almost forgot, the TAB output:

```
zeke@zeke-desktop:~$ sudo apt-get install dbus
dbus             dbus-1-doc       dbus-qt-1        dbus-x11
dbus-1           dbus-1-utils     dbus-qt-1c2      
dbus-1-dev       dbus-glib-1-dev  dbus-qt-1-dev    
```

---

### Post by diablo75 on 2008-04-07
Here's what I did to fix this missing package problem:

```
zeke@zeke-desktop:~$ sudo apt-get install dbus-glib-1-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package dbus-glib-1-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libdbus-glib-1-dev
E: Package dbus-glib-1-dev has no installation candidate
zeke@zeke-desktop:~$ 
zeke@zeke-desktop:~$ sudo apt-get install libdbus-glib-1-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdbus-1-dev
The following NEW packages will be installed:
  libdbus-1-dev libdbus-glib-1-dev
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 345kB of archives.
After this operation, 1135kB of additional disk space will be used.
Do you want to continue [Y/n]? y

```

But when I tried to compile, it now says I'm missing another package:

```
checking for PACKAGE... yes
checking for GLITZ... configure: error: Package requirements ("glitz-glx") were not met:

No package 'glitz-glx' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLITZ_CFLAGS
and GLITZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I can't find this glitz-glx package in synaptic...

---

### Post by nuclearpidgeon on 2008-04-08
```
sudo apt-get install libglitz1 libglitz-glx1
```

---

### Post by diablo75 on 2008-04-08
```
zeke@zeke-desktop:~$ sudo apt-get install libglitz1 libglitz-glx1
[sudo] password for zeke: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglitz1 is already the newest version.
libglitz-glx1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
zeke@zeke-desktop:~$ 

```

Hmmm.....Just tried to run the "**autoreconf -i -v -f && ./configure --prefix=/usr && make**" command and the same glitz package is said to be missing...

---

### Post by nuclearpidgeon on 2008-04-09
> **diablo75 said:**
> ```
zeke@zeke-desktop:~$ sudo apt-get install libglitz1 libglitz-glx1
[sudo] password for zeke: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglitz1 is already the newest version.
libglitz-glx1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
zeke@zeke-desktop:~$ 

```

Hmmm.....Just tried to run the "**autoreconf -i -v -f && ./configure --prefix=/usr && make**" command and the same glitz package is said to be missing...

why even compile? just use the repos. add 'http://ppa.launchpad.net/gilir/ubuntu main universe'
EDIT: Not sure if it works with hardy...
EDIT: IT DOESN'T. Try grabbing a .deb package

---

### Post by kawaji on 2008-04-09
check out this **[cairo-dock official wiki pages]("http://www.cairo-dock.org/ww_page.php?p=Accueil&lang=en")**.

maybe, libglitz-glx1-dev is needed.

---

