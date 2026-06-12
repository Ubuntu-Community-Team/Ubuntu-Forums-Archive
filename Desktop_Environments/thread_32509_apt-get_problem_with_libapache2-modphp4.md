---
title: "apt-get problem with libapache2-modphp4"
date: 2005-05-08
forum: Desktop Environments
---

### Post by stardotstar on 2005-05-08
Please can someone help me with this problem.

I tried to install php4 and the mod for apache2.  Have done this successfully using apt-get on Debian on a server...

I got the errors shown here when trying to get nvidia-glx - it comes up when I try to get anything !!!

```

wparker@monitor:~ $ sudo apt-get install nvidia-glx
Password:
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  nvidia-settings nvidia-kernel-source
The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 3052kB of archives.
After unpacking 9986kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com hoary/restricted nvidia-glx 1.0.7174-0ubuntu1 [3052kB]
Fetched 3052kB in 16s (184kB/s)

Preconfiguring packages ...
Selecting previously deselected package nvidia-glx.
(Reading database ... 83257 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1.0.7174-0ubuntu1_i386.deb) ...
Setting up libapache2-mod-php4 (4.3.10-10ubuntu4) ...
cp: cannot stat `/usr/share/doc/php4-common/examples/php.ini': No such file or directory
dpkg: error processing libapache2-mod-php4 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of php4:
 php4 depends on libapache2-mod-php4 (>= 4:4.3.10-10) | libapache-mod-php4 (>= 4:4.3.10-10); however:
  Package libapache2-mod-php4 is not configured yet.
  Package libapache-mod-php4 is not installed.
dpkg: error processing php4 (--configure):
 dependency problems - leaving unconfigured
Setting up nvidia-glx (1.0.7174-0ubuntu1) ...
Creating NVIDIA TLS links... done.

Errors were encountered while processing:
 libapache2-mod-php4
 php4
E: Sub-process /usr/bin/dpkg returned an error code (1)
wparker@monitor:~ $

```

Do I need to cleanse the cache or what?!?!

TIA

---

### Post by stardotstar on 2005-05-08
sudo apt-get install nvidia-glx

worked but the problem with the libapache-mod-php4 problem persists whenever I try to install anything.

Thanks

Will.*

---

