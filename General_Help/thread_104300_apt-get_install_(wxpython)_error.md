---
title: "apt-get install (wxpython) error"
date: 2005-12-15
forum: General Help
---

### Post by Mr. Electric Wizard on 2005-12-15
Hello all, I am getting an error when I try to install wxpythonversion through apt-get...
Here is the error:

```

eric@ubuntu:~$ sudo apt-get install python-wxversion
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  python-wxversion
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
16 not fully installed or removed.
Need to get 0B/20.3kB of archives.
After unpacking 81.9kB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 102870 files and directories currently installed.)
Unpacking python-wxversion (from .../python-wxversion_2.6.1.1.1ubuntu2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/python-wxversion_2.6.1.1.1ubuntu2_all.deb (--unpack):
 trying to overwrite `/usr/lib/python2.4/site-packages/wxversion.py', which is also in package wxpython2.5.3
Errors were encountered while processing:
 /var/cache/apt/archives/python-wxversion_2.6.1.1.1ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


Any idea what I need to do to get this package updated?

---

### Post by Mr. Electric Wizard on 2005-12-15
Nevermind guys, got it...

```
dpkg -i --force-overwrite /var/cache/apt/archives/python-wxversion_2.6.1.1.1ubuntu2_all.deb
```

This did the trick

---

