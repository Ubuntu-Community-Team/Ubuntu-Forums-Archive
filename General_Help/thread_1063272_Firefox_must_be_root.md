---
title: "Firefox must be root?"
date: 2009-02-07
forum: General Help
---

### Post by Java Geek on 2009-02-07
Every time I run firefox normally, it looks for a website called chrome://<distro>. If I change the homepage in the preferences, then it just changes back to default when I log back in. IT ALSO HAS NO INTERNET CAPABILITY. Only if I run Firefox as sudo does it do anything right at all.  

BTW I run XUBUNTU 8.10 with KDE Desktop environment so I have to log into XFCE to make any changes.

---

### Post by taurus on 2009-02-07
Did you install firefox from the repos or did you install it by hand?

---

### Post by Java Geek on 2009-02-07
repos

---

### Post by taurus on 2009-02-07
Which version do you have, 3.0.5?  Are you the owner of ~/.mozilla (or ~/.mozilla/firefox)?

```
ls -la ~/.mozilla/firefox
```

---

### Post by Java Geek on 2009-02-07
yes, I have 3.05.
Yes, I am owner of .mozilla/firefox

---

### Post by taurus on 2009-02-07
What's the output of that command from a terminal?

---

### Post by Java Geek on 2009-02-07
> **taurus said:**
> What's the output of that command from a terminal?

Here ya go:
```

stephen@stephen-desktop:~$ ls -la ~/.mozilla/firefox
total 16
drwxr-xr-x 3 stephen stephen 4096 2008-08-06 12:33 .
drwxr-xr-x 4 stephen stephen 4096 2008-08-06 17:50 ..
-rw-r--r-- 1 stephen stephen   94 2008-08-06 12:33 profiles.ini
drwxr-xr-x 8 stephen stephen 4096 2009-02-07 19:20 vkuuxfit.default

```

---

### Post by taurus on 2009-02-07
```
ls -la ~/.mozilla/firefox/vkuuxfit.default
```

---

### Post by Java Geek on 2009-02-07
```
stephen@stephen-desktop:~$ ls -la ~/.mozilla/firefox/vkuuxfit.default
total 60908
drwxr-xr-x 8 stephen stephen     4096 2009-02-07 19:26 .
drwxr-xr-x 3 stephen stephen     4096 2008-08-06 12:33 ..
drwxr-xr-x 2 stephen stephen     4096 2009-02-07 19:22 adblockplus
-rw-r--r-- 1 stephen stephen     1561 2009-02-06 21:37 blocklist.xml
drwx------ 2 stephen stephen     4096 2009-02-06 23:02 bookmarkbackups
-rw-r--r-- 1 stephen stephen    16914 2008-08-06 12:33 bookmarks.html
drwxr-xr-x 2 root    root        4096 2009-02-07 19:24 Cache
-rw------- 1 stephen stephen    98304 2009-02-07 19:22 cert8.db
drwxr-xr-x 2 stephen stephen     4096 2009-02-03 22:24 chrome
-rw------- 1 stephen stephen      158 2009-01-04 22:08 compatibility.ini
-rw-r--r-- 1 stephen stephen   152322 2009-02-07 18:09 compreg.dat
-rw-r--r-- 1 stephen stephen     7168 2009-02-07 16:10 content-prefs.sqlite
-rw-r--r-- 1 stephen stephen    53248 2009-02-07 19:26 cookies.sqlite
-rw-r--r-- 1 stephen stephen     9216 2009-02-07 17:03 downloads.sqlite
drwxr-xr-x 4 stephen stephen     4096 2009-02-07 18:01 extensions
-rw-r--r-- 1 stephen stephen      596 2009-02-07 18:09 extensions.cache
-rw-r--r-- 1 stephen stephen      577 2009-02-07 18:09 extensions.ini
-rw-r--r-- 1 stephen stephen     7548 2009-02-07 18:09 extensions.rdf
-rw-r--r-- 1 stephen stephen    11264 2009-02-07 18:20 formhistory.sqlite
-rw------- 1 stephen stephen        0 2009-02-07 19:22 Invalidprefs.js
-rw------- 1 stephen stephen    16384 2009-02-07 19:22 key3.db
-rw-r--r-- 1 stephen stephen    18817 2009-02-07 18:09 localstore.rdf
lrwxrwxrwx 1 root    root          16 2009-02-07 19:23 lock -> 127.0.1.1:+18696
-rw-r--r-- 1 stephen stephen    16122 2009-01-30 21:05 mimeTypes.rdf
drwx------ 2 stephen stephen     4096 2009-02-07 18:06 OfflineCache
-rw-r--r-- 1 stephen stephen        0 2009-02-07 19:23 .parentlock
-rw-r--r-- 1 stephen stephen     2048 2009-01-05 21:10 permissions.sqlite
-rw-r--r-- 1 stephen stephen  4194304 2009-02-07 19:24 places.sqlite
-rw-r--r-- 1 root    root       37448 2009-02-07 19:24 places.sqlite-journal
-rw------- 1 stephen stephen    10682 2009-02-07 19:24 pluginreg.dat
-rw------- 1 root    root       22911 2009-02-07 18:06 prefs.js
-rw-r--r-- 1 stephen stephen     2048 2008-08-06 17:04 search.sqlite
-rw------- 1 stephen stephen    16384 2009-02-07 19:23 secmod.db
-rw------- 1 root    root       10993 2009-02-07 19:22 sessionstore.bak
-rw------- 1 root    root        1979 2009-02-07 19:26 sessionstore.js
-rw------- 1 stephen stephen     3777 2009-02-01 10:58 signons3.txt
-rw-r--r-- 1 stephen stephen 54292480 2009-02-07 19:25 urlclassifier3.sqlite
-rw-r--r-- 1 stephen stephen      154 2009-02-07 19:24 urlclassifierkey3.txt
-rw-r--r-- 1 stephen stephen     2048 2009-02-07 16:05 webappsstore.sqlite
-rw-r--r-- 1 stephen stephen  2109223 2009-02-07 18:01 XPC.mfasl
-rw-r--r-- 1 stephen stephen   107193 2009-02-07 18:09 xpti.dat
-rw-r--r-- 1 stephen stephen   974674 2009-02-07 18:09 XUL.mfasl

```

---

### Post by taurus on 2009-02-07
Interesting that root is the owner of a few files (and a cache) in there!  Did you run firefox with root privilege anytime before?

What happens if you change the ownership of all files and directories back to your login name, stephen?  Shut down firefox and run

```
sudo chown -R stephen:stephen /home/stephen/.mozilla/firefox/vkuuxfit.default
ls -la ~/.mozilla/firefox/vkuuxfit.default
```
Start firefox again and see if your settings stick this time.

---

### Post by Java Geek on 2009-02-07
> **taurus said:**
> Interesting that root is the owner of a few files (and a cache) in there!  Did you run firefox with root privilege anytime before?


Yes, once before

---

### Post by Java Geek on 2009-02-07
The command worked. Yes, I had run firefox as root before, but i learned my lesson. Thanks Taurus!

BTW, Is this topic supposed to have a thank button option or a way to mark it as SOLVED because I'M not seeing either

---

