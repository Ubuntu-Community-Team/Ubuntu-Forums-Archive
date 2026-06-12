---
title: "gstreamer-plugins-base0.10 backport?"
date: 2006-07-30
forum: Desktop Environments
---

### Post by kjkrum on 2006-07-30
I'm having problems with RhythmBox flipping out, as described here: [http://bugzilla.gnome.org/show_bug.cgi?id=347966](http://bugzilla.gnome.org/show_bug.cgi?id=347966)

Apparently it's a bug in gstreamer0.10-plugins-base < 0.10.9.  Dapper still uses 0.10.7.  Would it be possible to get a backport for this bug fix?  Or should I attempt to build it from source?  If I build from source, what will I have to do to get it to use my local version of the library rather than the packaged one?  I'm leery of installing a whole bunch of libraries from edgy.

Also, I tried to use dpkg -i to install version 0.10.9-1ubuntu1 of just gstreamer0.10-plugins-base from edgy.  It didn't work because of dependencies.  But now, even though it didn't upgrade, when I try to remove it it tries to remove RhythmBox and a bunch of other packages.  How do I fix my dpkg database?

---

### Post by doclivingston on 2006-07-31
[https://launchpad.net/products/dapper-backports/+bug/53269](https://launchpad.net/products/dapper-backports/+bug/53269)

---

### Post by kjkrum on 2006-07-31
Hello again. :-)  Thanks.

Do you know how to fix what I did to my dpkg database?

---

### Post by RAOF on 2006-07-31
You should probably grab the correct version -plugins-base deb from [packages.ubuntu.com](packages.ubuntu.com), and then **dpkg --install --force-version** that.

Alternatively, you could possibly run **sudo aptitude install gstreamer0.10-plugins-base=0.10.7-*whatever_the_dapper_version_is***

---

### Post by kjkrum on 2006-07-31
Thanks!

---

