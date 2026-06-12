---
title: "apt-get can't update gnome-panel"
date: 2007-05-12
forum: Desktop Environments
---

### Post by orrorin on 2007-05-12
I'm a new to Ubuntu and I recently installed Feisty (7.04) on my x86.
Whenever I do apt-get, I get the following errors. It looks like gnome-panel, gnome-panel-data and gnome-applets were not installed properly.

It complains about missing file /usr/share/gconf/defaults/10_libgksu, which is a link to /etc/alternatives/libgksu-gconf-defaults, which in turn is a link to /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo.

However, the entire "debian" dir under /usr/share/libgksu seems to be missing.

What do I need to install to get this entire directory correctly installed?

Thanks.




$ sudo apt-get install gnome-panel
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
gnome-panel is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/322kB of archives.
After unpacking 0B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 87997 files and directories currently installed.)
Preparing to replace gnome-applets 2.18.0-0ubuntu1 (using .../gnome-applets_2.18.0-0ubuntu1_i386.deb) ...
Unpacking replacement gnome-applets ...
Traceback (most recent call last):
File "/usr/sbin/update-gconf-defaults", line 118, in <module>
read_entries(realname)
File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/10_libgksu'
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
File "/usr/sbin/update-gconf-defaults", line 118, in <module>
read_entries(realname)
File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/10_libgksu'
dpkg: error processing /var/cache/apt/archives/gnome-applets_2.18.0-0ubuntu1_i386.deb (--unpack):
subprocess new post-removal script returned error exit status 1
Traceback (most recent call last):
File "/usr/sbin/update-gconf-defaults", line 118, in <module>
read_entries(realname)
File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/10_libgksu'
dpkg: error while cleaning up:
subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
/var/cache/apt/archives/gnome-applets_2.18.0-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Kevinator on 2007-05-12
It looks to me like the package you need is libgksu2-0.

---

### Post by orrorin on 2007-05-12
> **Kevinator said:**
> It looks to me like the package you need is libgksu2-0.

Thanks for the response, Kevinator. Unfortunately, every time I run apt-get/aptitude/synaptics, it tries to update gnome-panel and gnome-panel-data and then seems to abort the upgrade.

here's my attempt at upgrading the library libgksu2-0

$ sudo aptitude install libgksu2-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 322kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main gnome-applets 2.18.0-0ubuntu1 [322kB]
Fetched 322kB in 4s (80.1kB/s)        
Preconfiguring packages ...
(Reading database ... 87997 files and directories currently installed.)
Preparing to replace gnome-applets 2.18.0-0ubuntu1 (using .../gnome-applets_2.18.0-0ubuntu1_i386.deb) ...
Unpacking replacement gnome-applets ...
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 118, in <module>
    read_entries(realname)
  File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/10_libgksu'
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 118, in <module>
    read_entries(realname)
  File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/10_libgksu'
dpkg: error processing /var/cache/apt/archives/gnome-applets_2.18.0-0ubuntu1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 118, in <module>
    read_entries(realname)
  File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/10_libgksu'
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-applets_2.18.0-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up gnome-panel-data (2.18.1-0ubuntu3.1) ...
desktop configuration
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 118, in <module>
    read_entries(realname)
  File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/10_libgksu'
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (= 1:2.18.1-0ubuntu3.1); however:
  Package gnome-panel-data is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-panel-data
 gnome-panel
$

---

### Post by orrorin on 2007-05-12
Looks like my install of Feisty had run into problems towards the end, when it downloads the latest updates for some (15) packages.

apt-get had ungracefully aborted. I did a fresh install and it works fine now.

But, is it possible to use apt-get in some kind of safe mode, so even in case of network problems, we can resume later?

---

