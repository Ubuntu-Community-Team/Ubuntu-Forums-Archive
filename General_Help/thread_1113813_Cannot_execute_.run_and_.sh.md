---
title: "Cannot execute .run and .sh"
date: 2009-04-02
forum: General Help
---

### Post by Hetor on 2009-04-02
Whenever I doubleckick a .run or .sh file, it opens with a text editor. I tried do it through terminal, but I get this error:

```
sudo: /Desktop/xfce4-4.6-installer.run: command not found

```

So, I can't upgrade my Xfce D: Please help, thank you.

---

### Post by iaculallad on 2009-04-02
While on terminal, try the commands below:

```
cd ~/Desktop
sudo chmod a+x xfce4-4.6-installer.run
sudo ./xfce4-4.6-installer.run
```

---

### Post by Hetor on 2009-04-02
```
Verifying file integrity... OK.
Extracting the installer... OK.
Checking for usable C compiler... gcc
Checking for usable C++ compiler... g++
Checking for GNU make... make
Checking for package config tool... not found, see /home/hetor/.xfce4.installer-log for details
Cleaning up... OK.

```

---

### Post by canadiandude007 on 2009-04-02
What does the installer log say?

---

### Post by Hetor on 2009-04-02
That's all it says. After that, nothing happens.

---

### Post by kpatz on 2009-04-02
Try: **sudo apt-get install pkg-config** and then re-run the installer.

If that doesn't work, **cat /home/hetor/.xfce4.installer-log** and post the results.

---

### Post by Hetor on 2009-04-02
```
##
## Started installation of xfce4 at 19:29h
##
## Visit http://forum.xfce.org/ if you have problems using this installer.
##

# Environment variables
PATH is set to "/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/bin:/usr/bin:/usr/local/ssl/bin:/usr/local/bin:/opt/openssl/bin:/usr/local/openssl/bin:/usr/pkg/bin:/usr/ucb:/usr/X11R6/bin:/usr/X11R6/bin:/usr/openwin/bin:/usr/local/bin:/opt/local/bin:/usr/pkg/bin:/opt/gnome2/bin:/opt/gnome/bin:/opt/xfce4/bin:/opt/xfce/bin:/home/hetor/local/bin:/home/hetor/xfce/bin:/home/hetor/xfce4/bin"
PKG_CONFIG_PATH is set to ":/usr/lib/pkgconfig:/usr/lib/pkgconfig"

## Checking for usable C compiler
gcc --version
gcc (Ubuntu 4.3.2-1ubuntu12) 4.3.2
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

## Checking for usable C++ compiler
g++ --version
./bootstrap.sh: 67: g++: not found
## Checking for GNU make
gmake --version
make --version
GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

This program built for i486-pc-linux-gnu

## Checking for package config tool
pkg-config --version
0.22

## Checking for GLib (GModule) >= 2.6.0
pkg-config --atleast-version=2.6.0 glib-2.0 gmodule-2.0
!! Please install GLib 2.6.0 or above and the GLib development files. It is
!! important that you install GModule, which is part of GLib as well. GLib
!! can be downloaded from http://www.gtk.org/.
```

---

### Post by oldos2er on 2009-04-02
You're missing some dependencies according to "Please install GLib 2.6.0 or above and the GLib development files."

 You might want to look at [http://jeromeg.blog.free.fr/index.php?post/2009/03/04/Installing-Xfce-4.6-on-Ubuntu-8.04-and-Ubuntu-8.10](http://jeromeg.blog.free.fr/index.php?post/2009/03/04/Installing-Xfce-4.6-on-Ubuntu-8.04-and-Ubuntu-8.10)

---

### Post by abhilashm86 on 2009-04-02
maybe some basic tools are missing to compile and run,
try this,
```

sudo apt-get install build-essential

```
then you can run packages..........

---

### Post by Hetor on 2009-04-02
**oldos2er**: The packages I got from that site fails to install.
**abhilashm86**: Didn't help, still same error.

---

### Post by Hetor on 2009-04-03
...anyone?

---

