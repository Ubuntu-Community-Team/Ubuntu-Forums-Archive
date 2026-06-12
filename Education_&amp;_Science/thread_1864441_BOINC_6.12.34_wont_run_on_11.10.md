---
title: "BOINC 6.12.34 wont run on 11.10"
date: 2011-10-19
forum: Education &amp; Science
---

### Post by Z3ro3X on 2011-10-19
When I try to run BOINC 6.12.34 for Linux x64 on Ubuntu 11.10 x64 I get this error in Terminal.

:~$ /run_manager
./boincmgr: error while loading shared libraries: libnotify.so.1: cannot open shared object file: No such file or directory

Any ideas?

---

### Post by CiaoCiao on 2011-10-19
Same problem here, post if you find a solution before me....

---

### Post by ubupirate on 2011-10-19
> **Z3ro3X said:**
> When I try to run BOINC 6.12.34 for Linux x64 on Ubuntu 11.10 x64 I get this error in Terminal.

:~$ /run_manager
./boincmgr: error while loading shared libraries: libnotify.so.1: cannot open shared object file: No such file or directory

Any ideas?

> **CiaoCiao said:**
> Same problem here, post if you find a solution before me....


[http://bolt.berkeley.edu/dev/forum_thread.php?id=6925&nowrap=true#40717](http://bolt.berkeley.edu/dev/forum_thread.php?id=6925&nowrap=true#40717)

---

### Post by webbertiger on 2011-12-17
I got a pre-release version (7.0.2) from:
[http://boinc.berkeley.edu/download_all.php](http://boinc.berkeley.edu/download_all.php)
For Ubuntu 11.10, also install the following packages:
apt-get install libwxgtk2.8-dev libcurl4-openssl-dev libxss-dev
Then it works okay.

---

