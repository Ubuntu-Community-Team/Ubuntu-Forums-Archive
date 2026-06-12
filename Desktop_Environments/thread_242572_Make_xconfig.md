---
title: "Make xconfig"
date: 2006-08-23
forum: Desktop Environments
---

### Post by dsjas297 on 2006-08-23
Here's my current problem:

```
make xconfig
  CHECK   qt
*
* Unable to find the QT installation. Please make sure that
* the QT development package is correctly installed and
* either install pkg-config or set the QTDIR environment
* variable to the correct location.
*

```

With Synaptic, I find plenty qt packages, but I am not sure which one to install.

Help greatly appreciated.

---

### Post by RAOF on 2006-08-23
A quick solution is to "make gconfig" instead.  That'll use GTK (which you definietly have installed) rather than QT.

You might still need the GTK development files, though.  They'll be in the **libgtk2.0-dev** package.

---

### Post by dsjas297 on 2006-08-24
This can't be good. I have all necessary packages installed, and this happens:

```
sudo make gconfig
*
* Unable to find the GTK+ installation. Please make sure that
* the GTK+ 2.0 development package is correctly installed...
* You need gtk+-2.0, glib-2.0 and libglade-2.0.
*

```

Anyone have any ideas here?

---

### Post by dsjas297 on 2006-08-24
This can't be good. I have all necessary packages installed, and this happens:

```
sudo make gconfig
*
* Unable to find the GTK+ installation. Please make sure that
* the GTK+ 2.0 development package is correctly installed...
* You need gtk+-2.0, glib-2.0 and libglade-2.0.
*

```

Anyone have any ideas here?

---

### Post by RAOF on 2006-08-24
Firstly, you probably shouldn't be building **anything** with sudo.  You don't need root privs to compile!

Secondly, do you have **libgtk2.0-dev libglib2.0-dev libglade2-dev** installed?

---

### Post by dsjas297 on 2006-08-24
Everything is there.

---

### Post by RAOF on 2006-08-24
Do you have **pkg-config** installed?  That's probably what it's using to try to find the development libraries.

---

### Post by xtknight on 2006-08-24
I'm pretty sure it's libqt3-mt-dev you need.  That was listed in one of the kernel HOWTOs (2.6.17) here.

sudo apt-get install libqt3-mt-dev

If it still fails to find QT (or GTK), then:

export PKG_CONFIG_PATH=/usr/lib/pkgconfig
make xconfig

If that doesn't work, please report the location of gtk+-2.0.pc ("locate gtk+-2.0.pc").

---

### Post by dsjas297 on 2006-08-25
Befor I read the replies to my last post, I decided to just stick with make menuconfig. It worled perfectly (as it should).

Thanks for all your help.

---

