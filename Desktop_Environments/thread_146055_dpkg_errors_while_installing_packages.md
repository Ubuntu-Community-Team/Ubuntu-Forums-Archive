---
title: "dpkg: errors while installing packages"
date: 2006-03-17
forum: Desktop Environments
---

### Post by teak on 2006-03-17
every time I try to install something using apt-get it returns a pile of errors. For example here in the case of yatex:

```

The following NEW packages will be installed:
  yatex
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/266kB of archives.
After unpacking 823kB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 101299 files and directories currently installed.)
Unpacking yatex (from .../archives/yatex_1.71-1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/yatex_1.71-1_all.deb (--unpack):
 unable to create `./usr/share/info/yahtmlj.gz': Read-only file system
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/yatex_1.71-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

$sudo dpkg -i --force-overwrite /var/cache/apt/archives/yatex_1.71-1_all.deb

returns:

```

(Reading database ... 101299 files and directories currently installed.)
Unpacking yatex (from .../archives/yatex_1.71-1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/yatex_1.71-1_all.deb (--install):
 unable to create `./usr/share/info/yahtmlj.gz': Read-only file system
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/yatex_1.71-1_all.deb

```

any ideas?

---

### Post by Xian on 2006-03-17
[QUOTE=teak]unable to create `./usr/share/info/yahtmlj.gz': Read-only file system[/QUOTE]

What is this all about?? Check the permissions on your /usr/share path.

---

### Post by teak on 2006-03-18
thanks.... this does it

cant believe didnt think of it :)

---

