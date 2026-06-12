---
title: "Greek fonts in console"
date: 2009-06-25
forum: General Help
---

### Post by ThanosP on 2009-06-25
Dear ubuntu users and developers,
Under X, greek file names show correctly, but are garbled on the console (Alt-Ctrl-F1). How would I remedy that? A corresponding solution for Debian ([http://www.debian-administration.org/article/Greek_Support_in_the_Debian_Console](http://www.debian-administration.org/article/Greek_Support_in_the_Debian_Console)) did not bear fruit.

Thank you very much,
Thanos

Information
------------
~> cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.2"

~> cat .zshrc|grep L
export LC_CTYPE='en_GB.UTF-8'
export LC_ALL='en_GB.UTF-8'
export LANG='en_GB.UTF-8'

---

### Post by ThanosP on 2009-06-26
Problem solved by editing ```
/etc/default/console-setup
``` to include the line ```
CODESET="Greek"
```

The options in that file may also be edited indirectly, via
```
sudo dpkg-reconfigure console-setup
```

---

