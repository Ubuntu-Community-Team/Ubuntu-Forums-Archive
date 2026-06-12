---
title: "Glib???"
date: 2007-03-09
forum: Desktop Environments
---

### Post by rlsteelman on 2007-03-09
```

rlsteelman@rlsteelman-desktop:~/sources/gaim$ ./autogen.sh

You must have glib-gettextize installed to compile Gaim.

```



That is whati did, that is the error I got. As far as I know the glib and everything is already installed.  I'm new to linux, i have the desktop 6.06 LTS, and wanted to update my gaim from the svn repo. I have svn, got all the way to the cd to gaim and do the ./autogen.sh

---

### Post by ComplexNumber on 2007-03-09
> **rlsteelman said:**
> ```

rlsteelman@rlsteelman-desktop:~/sources/gaim$ ./autogen.sh

You must have glib-gettextize installed to compile Gaim.

```That is whati did, that is the error I got. As far as I know the glib and everything is already installed.  I'm new to linux, i have the desktop 6.06 LTS, and wanted to update my gaim from the svn repo. I have svn, got all the way to the cd to gaim and do the ./autogen.sh
you need the "dev" packages installed. for exampe, do you have the libglib2.0-dev installed.


when you are compiling packages yourself, to find the dependencies it looks for the "pc" file in in the /usr/lib/pkgconfig and /usr/local/lib/pkgconfig directories to find if the dependencies are met. these are installed (usually) only in the dev packages when you are installing via synaptic or apt-get.

---

