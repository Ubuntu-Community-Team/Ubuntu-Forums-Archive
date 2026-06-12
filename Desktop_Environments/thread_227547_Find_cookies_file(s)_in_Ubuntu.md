---
title: "Find cookies file(s) in Ubuntu"
date: 2006-08-01
forum: Desktop Environments
---

### Post by bigweb26 on 2006-08-01
For a class project, I need to be able to view the cookies files in Ubuntu.  I know how to view them using Firefox.  What I need is to find the location and file name of the file where Firefox stores them.  I have searched and been unable to find anything.  Can anyone offer a suggestion where to look?

Thanks

---

### Post by scxtt on 2006-08-01
```
scxtt@madiera.ubuntu [~/.mozilla/firefox/e4o51nl4.default]
:> ll
total 1.6M
drwx------ 2 scxtt scxtt 4.0K 2006-08-01 00:38 bookmarkbackups
drwxr-xr-x 2 scxtt scxtt 4.0K 2006-08-01 14:37 Cache
drwxr-xr-x 2 scxtt scxtt 4.0K 2006-07-28 05:17 chrome
drwxr-xr-x 2 scxtt scxtt 4.0K 2006-07-28 05:17 extensions
-rw-r--r-- 1 scxtt scxtt 9.9K 2006-08-01 14:37 bookmarks.bak
-rw-r--r-- 1 scxtt scxtt  204 2006-07-28 06:14 extensions.cache
-rw-r--r-- 1 scxtt scxtt 120K 2006-07-28 06:14 compreg.dat
-rw-r--r-- 1 scxtt scxtt 2.8K 2006-08-01 14:37 formhistory.dat
-rw-r--r-- 1 scxtt scxtt 255K 2006-08-01 14:37 history.dat
-rw-r--r-- 1 scxtt scxtt  90K 2006-07-31 01:17 xpti.dat
-rw------- 1 scxtt scxtt  64K 2006-08-01 14:37 cert8.db
-rw------- 1 scxtt scxtt  16K 2006-08-01 14:37 key3.db
-rw------- 1 scxtt scxtt  16K 2006-07-28 05:17 secmod.db
-rw-r--r-- 1 scxtt scxtt 9.9K 2006-08-01 14:37 bookmarks.html
-rw------- 1 scxtt scxtt  124 2006-07-28 06:14 compatibility.ini
-rw-r--r-- 1 scxtt scxtt  184 2006-07-28 06:14 extensions.ini
-rw-r--r-- 1 scxtt scxtt 1.3K 2006-08-01 14:37 prefs.js
-rw-r--r-- 1 scxtt scxtt  685 2006-07-30 06:34 install.log
-rw-r--r-- 1 scxtt scxtt 913K 2006-07-31 00:44 XUL.mfasl
-rw-r--r-- 1 scxtt scxtt  206 2006-08-01 04:42 downloads.rdf
-rw-r--r-- 1 scxtt scxtt 2.0K 2006-07-28 06:14 extensions.rdf
-rw-r--r-- 1 scxtt scxtt 2.7K 2006-08-01 14:37 localstore.rdf
-rw-r--r-- 1 scxtt scxtt 2.7K 2006-08-01 04:38 mimeTypes.rdf
-rw-r--r-- 1 scxtt scxtt  752 2006-07-28 05:17 search.rdf
[color=red]-rw------- 1 scxtt scxtt  11K 2006-08-01 14:37 cookies.txt[/color]
-rw------- 1 scxtt scxtt  434 2006-07-29 04:51 signons.txt
```you'll need to replace e4o51nl4.default w/ whatever your ***.default** directory in **~/.mozilla/firefox/** is ...

---

