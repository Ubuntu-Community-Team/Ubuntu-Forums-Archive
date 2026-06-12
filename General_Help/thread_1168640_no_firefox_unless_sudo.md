---
title: "no firefox unless sudo?"
date: 2009-05-24
forum: General Help
---

### Post by muteXe on 2009-05-24
Hiya,
If i type "firefox" at the command line i get:
```
XDM authorization key matches an existing client!Error: cannot open display: :0.0
```
If i type "sudo firefox", then my password, firefox loads up okay.
Additionally if i click on the firefox icon on the gui i get ```
Failed to execute default web browser - input output error
```

I am wondering if somehow i've messed up when i added this user..
I'm on 8.04 with xfce desktop.
Any ideas anyone please?
Cheers,
mute

---

### Post by jonathanysp on 2009-05-24
mm did you install it through synaptics/deb files or did you compile it yourself? try purging (sudo apt-get purge firefox) and then reinstalling it again, this removes all your previous settings and stuff. Or trying starting it in safe-mode

---

### Post by muteXe on 2009-05-24
basically it's a fresh install, and i added a user using "adduser" and the commandline.
Almost as if my new user doesnt have rights.  I also notice i can't shutdown or reboot.  I only have log out as an option (unless i sudo).
very weird.

---

### Post by Kareeser on 2009-05-24
Hm, I have no problems with firefox, and I created a test user using "adduser".

Run this and report back:
```
ls -l ~/.mozilla
ls -l /usr/lib/firefox-3*
```

---

### Post by muteXe on 2009-05-24
First:
```
total 4
drwx------ 3 tom users 4096 2009-05-23 14:23 firefox
```

Second:
```
total 16460
-rw-r--r-- 1 root root      177 2008-10-30 04:25 README.txt
-rw-r--r-- 1 root root      825 2008-10-30 04:25 Throbber-small.gif
-rw-r--r-- 1 root root     2035 2008-10-30 04:25 application.ini
-rwxr-xr-x 1 root root     1561 2008-10-30 04:25 blocklist.xml
-rw-r--r-- 1 root root      232 2008-10-30 04:25 browserconfig.properties
drwxr-xr-x 3 root root     4096 2008-10-30 04:25 chrome
drwxr-xr-x 2 root root     4096 2009-05-23 13:58 components
-rwxr-xr-x 1 root root    45096 2008-10-30 04:25 crashreporter
-rw-r--r-- 1 root root      583 2008-10-30 04:25 crashreporter-override.ini
-rw-r--r-- 1 root root     3558 2008-10-30 04:25 crashreporter.ini
drwxr-xr-x 5 root root     4096 2008-10-30 04:25 defaults
drwxr-xr-x 2 root root     4096 2008-10-30 04:25 dictionaries
drwxr-xr-x 3 root root     4096 2008-10-30 04:25 extensions
-rwxr-xr-x 1 root root     4212 2008-11-14 23:24 firefox
-rwxr-xr-x 1 root root     7476 2008-10-30 04:25 firefox-bin
-rwxr-xr-x 1 root root     3945 2008-11-14 23:24 firefox.orig
drwxr-xr-x 2 root root     4096 2008-10-30 04:25 greprefs
drwxr-xr-x 2 root root     4096 2008-10-30 04:25 icons
-rw-r--r-- 1 root root      476 2008-10-30 04:25 libfreebl3.chk
-rwxr-xr-x 1 root root   292340 2008-10-30 04:25 libfreebl3.so
-rwxr-xr-x 1 root root    30724 2008-10-30 04:25 libjemalloc.so
-rwxr-xr-x 1 root root   602872 2008-10-30 04:25 libmozjs.so
-rwxr-xr-x 1 root root   200736 2008-10-30 04:25 libnspr4.so
-rwxr-xr-x 1 root root   918032 2008-10-30 04:25 libnss3.so
-rwxr-xr-x 1 root root   309236 2008-10-30 04:25 libnssckbi.so
-rwxr-xr-x 1 root root   119844 2008-10-30 04:25 libnssdbm3.so
-rwxr-xr-x 1 root root    77564 2008-10-30 04:25 libnssutil3.so
-rwxr-xr-x 1 root root    13224 2008-10-30 04:25 libplc4.so
-rwxr-xr-x 1 root root     8684 2008-10-30 04:25 libplds4.so
-rwxr-xr-x 1 root root   125676 2008-10-30 04:25 libsmime3.so
-rw-r--r-- 1 root root      476 2008-10-30 04:25 libsoftokn3.chk
-rwxr-xr-x 1 root root   181776 2008-10-30 04:25 libsoftokn3.so
-rwxr-xr-x 1 root root   406596 2008-10-30 04:25 libsqlite3.so
-rwxr-xr-x 1 root root   160036 2008-10-30 04:25 libssl3.so
-rwxr-xr-x 1 root root    11816 2008-10-30 04:25 libxpcom.so
-rwxr-xr-x 1 root root 13003616 2008-10-30 04:25 libxul.so
drwxr-xr-x 2 root root     4096 2008-10-30 04:25 modules
-rwxr-xr-x 1 root root    10772 2008-10-30 04:25 mozilla-xremote-client
-rw-r--r-- 1 root root      112 2008-10-30 04:25 old-homepage-default.properties
-rw-r--r-- 1 root root       45 2008-10-30 04:25 platform.ini
drwxr-xr-x 2 root root     4096 2008-10-30 04:25 plugins
-rwxr-xr-x 1 root root    15767 2008-10-30 04:25 removed-files
drwxr-xr-x 6 root root     4096 2008-10-30 04:25 res
-rwxr-xr-x 1 root root    11410 2008-10-30 04:25 run-mozilla.sh
drwxr-xr-x 2 root root     4096 2008-10-30 04:25 searchplugins
-rwxr-xr-x 1 root root    69672 2008-10-30 04:25 updater
-rw-r--r-- 1 root root      300 2008-10-30 04:25 updater.ini
drwxr-xr-x 3 root root     4096 2008-11-14 23:24 updates
 
```

thanks for the help :)

---

