---
title: "Kiba-dock problem"
date: 2007-06-13
forum: Desktop Effects &amp; Customization
---

### Post by Flikoman on 2007-06-13
I've installed kiba-dock, kiba-dock-dev, kiba-plugins and when I type kiba-dock in terminal error appears. 

Error: Unable to open dir /home/rocky/.kiba-dock/config_schemas
notifications: Error opening directory '/home/rocky/.kiba-dock/config_schemas': No such file or directory

Any ideas how to fix that?

---

### Post by ste82 on 2007-06-13
im having exactly the same problem. Followed the instructions on the kiba dock website. Havent worked out how to fix it though :(

---

### Post by Flikoman on 2007-06-14
Nobody doesn't even have a clue how to fix this? :(

---

### Post by Flikoman on 2007-06-14
I have removed kiba-dock from my system and then I have tryied to install it again, but in another way as it is described here!

[http://ubuntuforums.org/showthread.php?t=268645&highlight=kiba-dock](http://ubuntuforums.org/showthread.php?t=268645&highlight=kiba-dock)

Now, everything was fine, except kibaplugins. when I type ./autogen.sh it finished what it is working and then I type make and I get the following.

```
make  all-recursive
make[1]: Entering directory `/home/rocky/kiba-dock/kibaplugins/trunk'
Making all in src
make[2]: Entering directory `/home/rocky/kiba-dock/kibaplugins/trunk/src'
make  all-am
make[3]: Entering directory `/home/rocky/kiba-dock/kibaplugins/trunk/src'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/rocky/kiba-dock/kibaplugins/trunk/src'
make[2]: Leaving directory `/home/rocky/kiba-dock/kibaplugins/trunk/src'
Making all in files
make[2]: Entering directory `/home/rocky/kiba-dock/kibaplugins/trunk/files'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/rocky/kiba-dock/kibaplugins/trunk/files'
Making all in po
make[2]: Entering directory `/home/rocky/kiba-dock/kibaplugins/trunk/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/rocky/kiba-dock/kibaplugins/trunk/po'
make[2]: Entering directory `/home/rocky/kiba-dock/kibaplugins/trunk'
make[2]: Leaving directory `/home/rocky/kiba-dock/kibaplugins/trunk'
make[1]: Leaving directory `/home/rocky/kiba-dock/kibaplugins/trunk'

```

And after that I type sudo checkinstall...I pressed number 3 and I've replaced all that 0.1s with number 1. After that I press ENTER and the following comes out...

```

Installing with make install...

========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/home/rocky/kiba-dock/kibaplugins/trunk/src'
make  install-am
make[2]: Entering directory `/home/rocky/kiba-dock/kibaplugins/trunk/src'
make[3]: Entering directory `/home/rocky/kiba-dock/kibaplugins/trunk/src'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/kiba-dock" || /bin/mkdir -p "/usr/local/lib/kiba-dock"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'liblauncher.la' '/usr/local/lib/kiba-dock/liblauncher.la'
/usr/bin/install -c .libs/liblauncher.so /usr/local/lib/kiba-dock/liblauncher.so
/usr/bin/install: setting permissions for `/usr/local/lib/kiba-dock/liblauncher.so': No such file or directory
/usr/bin/install -c .libs/liblauncher.lai /usr/local/lib/kiba-dock/liblauncher.la
/usr/bin/install: setting permissions for `/usr/local/lib/kiba-dock/liblauncher.la': No such file or directory
/usr/bin/install -c .libs/liblauncher.a /usr/local/lib/kiba-dock/liblauncher.a
/usr/bin/install: setting permissions for `/usr/local/lib/kiba-dock/liblauncher.a': No such file or directory
chmod 644 /usr/local/lib/kiba-dock/liblauncher.a
ranlib /usr/local/lib/kiba-dock/liblauncher.a
ranlib: could not create temporary file whilst writing archive: No more archived files
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libtaskbar.la' '/usr/local/lib/kiba-dock/libtaskbar.la'
/usr/bin/install -c .libs/libtaskbar.so /usr/local/lib/kiba-dock/libtaskbar.so
/usr/bin/install: setting permissions for `/usr/local/lib/kiba-dock/libtaskbar.so': No such file or directory
/usr/bin/install -c .libs/libtaskbar.lai /usr/local/lib/kiba-dock/libtaskbar.la
/usr/bin/install: setting permissions for `/usr/local/lib/kiba-dock/libtaskbar.la': No such file or directory
/usr/bin/install -c .libs/libtaskbar.a /usr/local/lib/kiba-dock/libtaskbar.a
/usr/bin/install: setting permissions for `/usr/local/lib/kiba-dock/libtaskbar.a': No such file or directory
chmod 644 /usr/local/lib/kiba-dock/libtaskbar.a
ranlib /usr/local/lib/kiba-dock/libtaskbar.a
ranlib: could not create temporary file whilst writing archive: No more archived files
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libwinlist.la' '/usr/local/lib/kiba-dock/libwinlist.la'
/usr/bin/install -c .libs/libwinlist.so /usr/local/lib/kiba-dock/libwinlist.so
/usr/bin/install: setting permissions for `/usr/local/lib/kiba-dock/libwinlist.so': No such file or directory
/usr/bin/install -c .libs/libwinlist.lai /usr/local/lib/kiba-dock/libwinlist.la
/usr/bin/install: setting permissions for `/usr/local/lib/kiba-dock/libwinlist.la': No such file or directory
/usr/bin/install -c .libs/libwinlist.a /usr/local/lib/kiba-dock/libwinlist.a
/usr/bin/install: setting permissions for `/usr/local/lib/kiba-dock/libwinlist.a': No such file or directory
chmod 644 /usr/local/lib/kiba-dock/libwinlist.a
ranlib /usr/local/lib/kiba-dock/libwinlist.a
ranlib: could not create temporary file whilst writing archive: No more archived files
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libclock.la' '/usr/local/lib/kiba-dock/libclock.la'
/usr/bin/install -c .libs/libclock.so /usr/local/lib/kiba-dock/libclock.so
/usr/bin/install: setting permissions for `/usr/local/lib/kiba-dock/libclock.so': No such file or directory
/usr/bin/install -c .libs/libclock.lai /usr/local/lib/kiba-dock/libclock.la
/usr/bin/install: setting permissions for `/usr/local/lib/kiba-dock/libclock.la': No such file or directory
/usr/bin/install -c .libs/libclock.a /usr/local/lib/kiba-dock/libclock.a
/usr/bin/install: setting permissions for `/usr/local/lib/kiba-dock/libclock.a': No such file or directory
chmod 644 /usr/local/lib/kiba-dock/libclock.a
ranlib /usr/local/lib/kiba-dock/libclock.a
ranlib: could not create temporary file whilst writing archive: No more archived files
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libclipman.la' '/usr/local/lib/kiba-dock/libclipman.la'
/usr/bin/install -c .libs/libclipman.so /usr/local/lib/kiba-dock/libclipman.so
/usr/bin/install: setting permissions for `/usr/local/lib/kiba-dock/libclipman.so': No such file or directory
/usr/bin/install -c .libs/libclipman.lai /usr/local/lib/kiba-dock/libclipman.la
/usr/bin/install: setting permissions for `/usr/local/lib/kiba-dock/libclipman.la': No such file or directory
/usr/bin/install -c .libs/libclipman.a /usr/local/lib/kiba-dock/libclipman.a
/usr/bin/install: setting permissions for `/usr/local/lib/kiba-dock/libclipman.a': No such file or directory
chmod 644 /usr/local/lib/kiba-dock/libclipman.a
ranlib /usr/local/lib/kiba-dock/libclipman.a
ranlib: could not create temporary file whilst writing archive: No more archived files
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libsysinfo.la' '/usr/local/lib/kiba-dock/libsysinfo.la'
/usr/bin/install -c .libs/libsysinfo.so /usr/local/lib/kiba-dock/libsysinfo.so
/usr/bin/install: setting permissions for `/usr/local/lib/kiba-dock/libsysinfo.so': No such file or directory
/usr/bin/install -c .libs/libsysinfo.lai /usr/local/lib/kiba-dock/libsysinfo.la
/usr/bin/install: setting permissions for `/usr/local/lib/kiba-dock/libsysinfo.la': No such file or directory
/usr/bin/install -c .libs/libsysinfo.a /usr/local/lib/kiba-dock/libsysinfo.a
/usr/bin/install: setting permissions for `/usr/local/lib/kiba-dock/libsysinfo.a': No such file or directory
chmod 644 /usr/local/lib/kiba-dock/libsysinfo.a
ranlib /usr/local/lib/kiba-dock/libsysinfo.a
ranlib: could not create temporary file whilst writing archive: No more archived files
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libtrash.la' '/usr/local/lib/kiba-dock/libtrash.la'
/usr/bin/install -c .libs/libtrash.so /usr/local/lib/kiba-dock/libtrash.so
/usr/bin/install: setting permissions for `/usr/local/lib/kiba-dock/libtrash.so': No such file or directory
/usr/bin/install -c .libs/libtrash.lai /usr/local/lib/kiba-dock/libtrash.la
/usr/bin/install: setting permissions for `/usr/local/lib/kiba-dock/libtrash.la': No such file or directory
/usr/bin/install -c .libs/libtrash.a /usr/local/lib/kiba-dock/libtrash.a
/usr/bin/install: setting permissions for `/usr/local/lib/kiba-dock/libtrash.a': No such file or directory
chmod 644 /usr/local/lib/kiba-dock/libtrash.a
ranlib /usr/local/lib/kiba-dock/libtrash.a
ranlib: could not create temporary file whilst writing archive: No more archived files
make[3]: *** [install-moduleLTLIBRARIES] Error 1
make[3]: Leaving directory `/home/rocky/kiba-dock/kibaplugins/trunk/src'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/rocky/kiba-dock/kibaplugins/trunk/src'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/rocky/kiba-dock/kibaplugins/trunk/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

**ANY IDEAS HOW TO FIX THIS?? **Please, this is the last step for installing kiba-dock. How do I know that? Because when I type kiba-dock in the terminal, this message appears.

```
Error: Unable to open dir /usr/local/share/kiba-dock/config_schemas/plugins
notifications: Error opening directory '/usr/local/share/kiba-dock/config_schemas/plugins': No such file or directory
Error: Unable to open dir /home/rocky/.kiba-dock/config_schemas
notifications: Error opening directory '/home/rocky/.kiba-dock/config_schemas': No such file or directory
Error (dialog.c @ line 212):
        Failed to load Plugins from /usr/local/lib/kiba-dock!
Please install the Plugins and Kiba under the same Prefix

FATAL (main.c @ line 200):
        Failed to load Plugins

```

---

### Post by ste82 on 2007-06-14
i partially solved this by creating the directories it  asks for. kiba-dock now loads but it is just a black bar at the bottom of the screen, and i cant add anything to it!

---

### Post by Ub1476 on 2007-06-14
Uninstall kiba-dock, then try to follow this guide: [Linky]("http://ubuntu1501.blogspot.com/2007/04/install-kiba-dock-oncedgy-eft.html")

---

