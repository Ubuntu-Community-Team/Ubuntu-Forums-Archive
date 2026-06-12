---
title: "Problems with compiling... any help will be greatly appreciated."
date: 2006-09-10
forum: Desktop Environments
---

### Post by diabx0r on 2006-09-10
Hey, guys!  First post here and first time in Ubuntu, and loving it so far.

I have been using apt-get to get most of the things I've needed, but I openbox wasn't in there, so I decided to download it from the OB site.

Well, I untarred and such but when I ./configure I get this error:

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking build type... RELEASE
checking for style of include used by make... none
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

Any ideas? 

I just used apt-get for GCC but to no avail.

---

### Post by Ramses de Norre on 2006-09-10
Did you try ```
sudo aptitude install build-essential
```
If so: look in config.log for error messages.

---

### Post by moore.bryan on 2006-09-10
*openbox is in the repos ```
sudo apt-get install openbox
``` but the openbox website ([http://www.icculus.org/openbox/](http://www.icculus.org/openbox/)) has the newest one.*

---

### Post by diabx0r on 2006-09-10
Just did, and it gets further, but now it says this

```
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... configure: error: Package requirements (glib-2.0) were notmet:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_CFLAGS
and GLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

---

### Post by Ramses de Norre on 2006-09-10
```
sudo aptitude install libglib2.0-dev
```

---

