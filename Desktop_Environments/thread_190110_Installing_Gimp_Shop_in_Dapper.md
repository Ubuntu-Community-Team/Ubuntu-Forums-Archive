---
title: "Installing Gimp Shop in Dapper"
date: 2006-06-05
forum: Desktop Environments
---

### Post by spyke01 on 2006-06-05
Can anyone give a guide to installing GimpShop on Dapper, i got the deb but i get the following error:
```

checking for GLIB - version >= 2.4.5... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.

```
I checked synaptic, and it looks like its freaking because ubuntu uses its own version of GLIB among other things?

---

### Post by ntd on 2006-06-05
[QUOTE=spyke01]Can anyone give a guide to installing GimpShop on Dapper, i got the deb but i get the following error:
```

checking for GLIB - version >= 2.4.5... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.

```
I checked synaptic, and it looks like its freaking because ubuntu uses its own version of GLIB among other things?[/QUOTE]

Do you have the -dev packages installed?  libglib2.0-dev (or whatever it is, I can't remember the exact name) for example?

---

### Post by spyke01 on 2006-06-06
ok checked synaptics again, found a problem. Ubuntu is using its own version of
GLIB(2.10.3-0ubuntu1) while the dev packages for GLIB are 2.8.3-0ubuntu1
Should i just download and install the newest version of GLIB(looks like its 11) from [ftp://ftp.gtk.org/pub/gtk?](ftp://ftp.gtk.org/pub/gtk?)

---

### Post by onesojourner on 2006-06-06
I would also like to give gimpshop a try.

---

### Post by jeffreyvergara.NET on 2006-06-06
im trying to build Gimpshop 2.2.4 from source but no luck, I got an error on XML Parser

> error: XML::Parser perl module is required

---

### Post by jeffreyvergara.NET on 2006-06-06
btw, is gimpshop interface is only 1 window like in photoshop?

---

### Post by sharperguy on 2006-06-06
anyone used Krita?

---

### Post by spyke01 on 2006-06-06
[QUOTE=jeffreyvergara.NET]btw, is gimpshop interface is only 1 window like in photoshop?[/QUOTE]

no its the gimp layout but with the buttons and labels like in PS

[QUOTE=sharperguy]anyone used Krita?[/QUOTE]
nope, but it looks really nice

---

### Post by nocloud on 2006-06-06
if i already have gimp installed, will installing gimpshop just overwrite that installation?

---

### Post by duktape on 2006-09-15
I was having the same problems compiling from source on ubuntu. Luckily, Scott has a deb ready to install. Worked flawlessly. [http://plasticbugs.com](http://plasticbugs.com)

---

