---
title: "QGLViewer in Xubuntu"
date: 2006-07-16
forum: Desktop Environments
---

### Post by mindead on 2006-07-16
I got this error while trying to install the QGLViewer header files.
I already have the QGLViewer installed and before this message I got a complain about libgnome2-perl library. I installed this library and then:
```
sudo apt-get install libqglviewer-dev
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  libqglviewer-dev
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2556kB of archives.
After unpacking, 11.7MB of additional disk space will be used.
(Reading database ... 84426 files and directories currently installed.)
Unpacking libqglviewer-dev (from .../libqglviewer-dev_1.4-2ubuntu1_i386.deb) ...dpkg: error processing /var/cache/apt/archives/libqglviewer-dev_1.4-2ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libqglviewer.1.0.0', which is also in package libqglviewer1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libqglviewer-dev_1.4-2ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
``` I'm using Xubuntu.

---

### Post by islam_ce on 2008-03-12
Hi,
I have faced same problem.

[COLOR="Blue"]>... libqglviewer-dev
 ...Building dependency tree... Done
  dpkg-deb: subprocess paste killed by signal (Broken pipe)

E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]

Check the dependency of-- libqglviewer-dev...there is libqglviewer1.

[COLOR="Purple"]For qglviewer... u need -
>libqglviewer-dev
>libqglviewer1[/COLOR] but this libqglviewer1 is not same as dependency libqglviewer1 of libqglviewer-dev.And cause overwrite ...and Broken Pipe..
(My opinion,there are 2 libqglviewer with same names)

Regards,
Nurul Islam

---

