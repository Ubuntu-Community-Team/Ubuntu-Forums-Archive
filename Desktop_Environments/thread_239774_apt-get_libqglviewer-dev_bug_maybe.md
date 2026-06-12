---
title: "apt-get libqglviewer-dev: bug maybe?"
date: 2006-08-19
forum: Desktop Environments
---

### Post by t_boyd on 2006-08-19
andrew@dakken:~/Desktop/yade-all-0.10.0$ sudo apt-get install libqglviewer-dev Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  libqglviewer-dev
0 upgraded, 1 newly installed, 0 to remove and 63 not upgraded.
Need to get 0B/2556kB of archives.
After unpacking 11.7MB of additional disk space will be used.
(Reading database ... 72675 files and directories currently installed.)
Unpacking libqglviewer-dev (from .../libqglviewer-dev_1.4-2ubuntu1_i386.deb) ...
[B]dpkg: error processing /var/cache/apt/archives/libqglviewer-dev_1.4-2ubuntu1_i386.deb (--unpack):
 _trying to overwrite `/usr/lib/libqglviewer.1.0.0', which is also in package libqglviewer1_[/B]
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libqglviewer-dev_1.4-2ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
andrew@dakken:~/Desktop/yade-all-0.10.0$

I'm using xubuntu, I can't work out what's wrong. I've tried manually deleting the file etc...

Is this a bug? How do I work around this? I'm just trying to compile a package that depends on qglviewer.h.

---

