---
title: "is their a way to fix /usr/lib/libgconf-2.so.4"
date: 2011-02-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by skubo on 2011-02-21
before i reinstalls the dell dvd on the 910 netbook.

did the file always have an orange color
CrwS--Sr-x1 61440 11653 79,133 /usr/lib/libgconf-2.so.4

etc/gdm/Xsession: beginning session setup...
setting im through im-switch for locale=en_us.
start im through /etc/X11/xinit/xinput.d/all_ALL
linked to/etc/X11/xinit/xinput.d/default.

/usr/bin/seahorse-agent:error while loading
shared libraries:libgconf-2.so.4:
cannot open shared object file: error6

sudo apt-get install seahorse
the following packages were automatically installed
and are no longer required:
libam-util0 libgg2mod4 guile-1.6-libs dhedbd
libggz2 libqthreads-12 libggzcore9 libisc32
libguile-ltdl-1 

processing triggers for libc6...
ldconfig deferred processing now taking place
/sbin/ldconfig.real:/usr/lib/libgconf-2.so.4 is
not a symbolic link
/sbin/ldconfig.real:/usr/lib/libXmu.so.6 is not a
symbolic link

-rw-r--r--1 root root 185252 apr 22 2008 /usr/lib/libgconf-2.so.4.1.5

aptitude reinstall gconf2
0 packages upgraded, 0 newlyinstalled, 1 reinstalled
0 to remove and 3 not upgraded

aptitude reinstall
err [http://dell-mini.archive.cononical.com](http://dell-mini.archive.cononical.com)
hardy_dell-mini/main rhythmbox 0.11.5
-0ubuntu8netbook1belmont3
could not resolve 'dell-mini.archive.canonical.com'

E:failed to fetch [http://dell-mini.archive.canonical.com/](http://dell-mini.archive.canonical.com/)
ubuntu/dists/hardy-dell-mini/
main/binary-lpia/rhythmbox_0.11.5-0unbuntu8
netbook1belmont3_lpia.deb: could not 
resolve 'dell-mini.archive.canonical.com

what would cause the file to go bad to avoid the login crash
again.

i tried newuser but said it was at its limit allready

---

