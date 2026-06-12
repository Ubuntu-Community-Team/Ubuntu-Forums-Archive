---
title: "Audacious dependancy hell"
date: 2006-01-16
forum: Desktop Environments
---

### Post by veratyr on 2006-01-16
Trying to install the latest debian/ubuntu package of audacious from their website and hitting a wall.

```
mike@yggdrasill:~/Desktop$ sudo dpkg -i audacious_0.1.2+svn472-0vd1_i386.deb
Selecting previously deselected package audacious.
(Reading database ... 114094 files and directories currently installed.)
Unpacking audacious (from audacious_0.1.2+svn472-0vd1_i386.deb) ...
dpkg: dependency problems prevent configuration of audacious:
 audacious depends on libasound2 (>> 1.0.10); however:
  Version of libasound2 on system is 1.0.9-2.
 audacious depends on libbinio1c2 (>= 1.3-3); however:
  Package libbinio1c2 is not installed.
 audacious depends on libcairo2 (>= 1.0.2-2); however:
  Version of libcairo2 on system is 1.0.2-0ubuntu1.
 audacious depends on libgcc1 (>= 1:4.0.2); however:
  Version of libgcc1 on system is 1:4.0.1-4ubuntu9.
 audacious depends on libglib2.0-0 (>= 2.8.5); however:
  Version of libglib2.0-0 on system is 2.8.3-0ubuntu1.
 audacious depends on libid3-3.8.3c2a; however:
  Package libid3-3.8.3c2a is not installed.
 audacious depends on libjack0.100.0-0 (>= 0.100.0); however:
  Package libjack0.100.0-0 is not installed.
 audacious depends on libpango1.0-0 (>= 1.10.2); however:
  Version of libpango1.0-0 on system is 1.10.1-0ubuntu1.
 audacious depends on libstdc++6 (>= 4.0.2-4); however:
  Version of libstdc++6 on system is 4.0.1-4ubuntu9.
 audacious depends on libtag1c2a (>= 1.4); however:
  Package libtag1c2a is not installed.
 audacious depends on libvisual0.2 (>= 0.2.0); however:
  Package libvisual0.2 is not installed.
 audacious depends on libxml2 (>= 2.6.23); however:
  Version of libxml2 on system is 2.6.21-0ubuntu1.
 audacious depends on libxrender1 (>= 1:0.9.0.2); however:
  Version of libxrender1 on system is 1:0.9.0-1.
dpkg: error processing audacious (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 audacious
```

---

### Post by RAOF on 2006-01-16
You can **try**
```
sudo apt-get install -f
```
That should get apt to download and install the deps for the broken package (Audacious).

However, it looks like that package is built for straight debian, and so you might not be able to satisfy some of the dependencies.

---

