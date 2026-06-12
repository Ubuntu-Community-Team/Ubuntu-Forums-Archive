---
title: "Error with GLIB/irssi compile"
date: 2009-07-04
forum: Desktop Environments
---

### Post by Kvothe on 2009-07-04
I just compiled GLIB 2.21.2 without any trouble and then proceeded to install irssi 0.8.13 and I get this error:

```
checking for GLIB - version >= 2.6.0... 
*** 'pkg-config --modversion glib-2.0' returned 2.21.2, but GLIB (2.16.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no

*** If you don't have GLIB, you can get it from ftp://ftp.gtk.org/pub/glib/
*** We recommend you get the latest stable GLIB 2 version.
*** Compile and install it, and make sure pkg-config finds it,
*** by adding the path where the .pc file is located to PKG_CONFIG_PATH

configure: error: GLIB is required to build irssi.
```
What to do?

---

### Post by Kvothe on 2009-07-04
This seems really out of place, now that I think about it. Meh...

---

### Post by Kvothe on 2009-07-04
Bump. Help would be much appreciated.

---

### Post by Kvothe on 2009-07-04
If none of you can help me with this, then please direct to someone who can, or tell me where it should be posted. Maybe I'm just being impatient, but you guys usually are not this slow...

---

### Post by andrew.46 on 2009-07-06
Hi Kvothe,

I am not quite sure what has happened to your installation of irssi there but having seen a bit of frustration creep into your posts I had a look at compiling the latest irssi under Jaunty with a different technique. 

First some building tools:

```
sudo apt-get install build-essential checkinstall
```

Then the required dependencies:

```
sudo apt-get build-dep irssi
```

then the source:

```
wget http://irssi.org/files/irssi-0.8.13.tar.bz2
```

Then decompress and compile:

```
tar xjvf irssi-0.8.13.tar.bz2
cd irssi-0.8.13
./configure
make
sudo checkinstall --pkgname irssi --pkgversion 0.8.13 --default

```

This worked perfectly and if you have a look in synaptic you will see that the version you compiled is slotted in neatly as the *newest* version. So perhaps undo your previous efforts and try this technique?

All the best,

Andrew

---

### Post by andrew.46 on 2009-07-11
Hey Kvothe,

Any luck with this? You seemed quite keen before :-).

Andrew

---

