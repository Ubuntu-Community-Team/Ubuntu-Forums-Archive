---
title: "apt-get refuses to update system"
date: 2006-05-11
forum: Desktop Environments
---

### Post by adamb10 on 2006-05-11
I have to do a apt-get install -f to fix a issue so I do but I get the following error message:

> 
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libfame0
The following NEW packages will be installed:
  libfame0
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
57 not fully installed or removed.
Need to get 0B/86.0kB of archives.
After unpacking 352kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libfame0
Install these packages without verification [y/N]? y

Preconfiguring packages ...
(Reading database ... 82604 files and directories currently installed.)
Unpacking libfame0 (from .../libfame0_0.9.0-0unofficialubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libfame0_0.9.0-0unofficialubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libfame-0.9.so.0.0.0', which is also in package libfame-0.9
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libfame0_0.9.0-0unofficialubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


How can I fix this?  Thanks!

---

### Post by tonyr on 2006-05-11
Force it.
```

cd /var/cache/apt/archives
sudo dpkg -i --force-overwrite libfame0_0.9.0-0unofficialubuntu1_i386.deb 

```

See [this]("http://www.ubuntuforums.org/showthread.php?t=174160") thread for a similar experience, different package.  Are you
using some non-standard repo?

---

### Post by arnieboy on 2006-05-11
```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/libfame0_0.9.0-0unofficialubuntu1_i386.deb
```

---

