---
title: "gaim 2.0 beta 3.1 ssl problem"
date: 2006-08-23
forum: Desktop Environments
---

### Post by schreck494 on 2006-08-23
I was trying to ugrade gaim 2.0 beta 3 to gaim 2.0 beta 3.1.  I downloaded the tarball and installed it.  When I try to start up gaim it says that SSL support is needed for MSN, and that a supported SSL library needs to be installed.  What library do I need and can I just get in in Synaptic?

---

### Post by mlind on 2006-08-23
> **schreck494 said:**
> I was trying to ugrade gaim 2.0 beta 3 to gaim 2.0 beta 3.1.  I downloaded the tarball and installed it.  When I try to start up gaim it says that SSL support is needed for MSN, and that a supported SSL library needs to be installed.  What library do I need and can I just get in in Synaptic?

I think the library you're looking is called **libgnutls11**. You should probably get the source package from Debian and build that?
**libgnutls11-dev** is required as build dependency for SSL.

---

### Post by schreck494 on 2006-08-23
Do I need to reinstall gaim?  It still gives me the error

---

### Post by mlind on 2006-08-23
> **schreck494 said:**
> Do I need to reinstall gaim?  It still gives me the error

How did you exactly install gaim?

---

### Post by schreck494 on 2006-08-23
I downloaded the tarball from the sf page.  Then I navigated to the directory in terminal and used ./configure.  Then I used make and all that stuff.  I used the guide from here: [http://www.monkeyblog.org/ubuntu/installing/#source](http://www.monkeyblog.org/ubuntu/installing/#source)

---

### Post by mlind on 2006-08-23
> **schreck494 said:**
> I downloaded the tarball from the sf page.  Then I navigated to the directory in terminal and used ./configure.  Then I used make and all that stuff.  I used the guide from here: [http://www.monkeyblog.org/ubuntu/installing/#source](http://www.monkeyblog.org/ubuntu/installing/#source)

You didn't configure package with required libgnutls11-dev package installed or missed some configure option. Try with these,
```

./configure --disable-nas --disable-nss -enable-perl --disable-silc --with-zephyr=/usr --enable-dbus --with-python=python2.4

```

Here are the build dependencies for gaim2 beta3.x
```

bzip2, cdbs, debhelper, libgtk2.0-dev, libxss-dev, libmeanwhile-dev, libgadu-dev, libgnutls11-dev, tcl8.4-dev, tk8.4-dev, libao-dev, libaudiofile-dev, libgtkspell-dev, libltdl3-dev, libperl-dev, libstartup-notification0-dev, xutils, libzephyr-dev, libxml2-dev, libebook1.2-dev, libedata-book1.2-dev, libcamel1.2-dev, libdbus-glib-1-dev, dbus, python2.4, libavahi-compat-howl-dev, libxml-parser-perl

```


I recommend to build gaim from source package, it should be easier and less error prone.

---

### Post by schreck494 on 2006-08-24
Can I install it from the deb package you put up in another thread.  If so, the how do I install it from a deb?

---

### Post by mlind on 2006-08-24
> **schreck494 said:**
> Can I install it from the deb package you put up in another thread.  If so, the how do I install it from a deb?

If you have Dapper, then yes.

To install a local package:
```

sudo dpkg -i *package.deb*

```

---

