---
title: "Errors while installing packages: Problems with Samba"
date: 2006-06-07
forum: Desktop Environments
---

### Post by M4LFUNCT10N on 2006-06-07
So, still being a bit new to linux, I don't know what Samba controls or really does.  I'm trying to get videos imbedded in web pages working.  I want to say I had it working until I did the update to fix the firefox icons, however it might have been something else that caused the problem.  Can someone point me in the direction to get this working?

Here's a log of my terminal actions and responses:

logan@LHUbuntu:~$ sudo apt-get install win32codecs
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package win32codecs
logan@LHUbuntu:~$ sudo apt-get install mozilla-mplayer
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  mozilla-mplayer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 431kB of archives.
After unpacking 1536kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse mozilla-mplayer 3.17-1ubunt u1 [431kB]
Fetched 431kB in 18s (23.5kB/s)
Selecting previously deselected package mozilla-mplayer.
(Reading database ... 107952 files and directories currently installed.)
Unpacking mozilla-mplayer (from .../mozilla-mplayer_3.17-1ubuntu1_i386.deb) ...
Setting up samba (3.0.22-1ubuntu3) ...
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /e tc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /e tc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
Setting up mozilla-mplayer (3.17-1ubuntu1) ...
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
logan@LHUbuntu:~$ sudo apt-get upgrade mozilla-mplayer
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up samba (3.0.22-1ubuntu3) ...
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /e tc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /e tc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
logan@LHUbuntu:~$ sudo apt-get install mplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer-mozilla
logan@LHUbuntu:~$ sudo apt-get install totem-xine-firefox-plugin
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  totem-xine
The following packages will be REMOVED:
  totem-gstreamer totem-gstreamer-firefox-plugin
The following NEW packages will be installed:
  totem-xine totem-xine-firefox-plugin
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 1096kB of archives.
After unpacking 45.1kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe totem-xine 1.4.1-0ubuntu4 [1065kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe totem-xine-firefox-plugin 1.4.1-0ubuntu4 [31.2kB]
Fetched 1096kB in 18s (57.8kB/s)
(Reading database ... 108002 files and directories currently installed.)
Removing totem-gstreamer-firefox-plugin ...
dpkg: totem-gstreamer: dependency problems, but removing anyway as you request:
 totem depends on totem-gstreamer (>= 1.4.1-0ubuntu4) | totem-xine (>= 1.4.1-0ubuntu4); however:
  Package totem-gstreamer is to be removed.
  Package totem-xine is not installed.
Removing totem-gstreamer ...
Selecting previously deselected package totem-xine.
(Reading database ... 107877 files and directories currently installed.)
Unpacking totem-xine (from .../totem-xine_1.4.1-0ubuntu4_i386.deb) ...
Selecting previously deselected package totem-xine-firefox-plugin.
Unpacking totem-xine-firefox-plugin (from .../totem-xine-firefox-plugin_1.4.1-0ubuntu4_i386.deb) ...
Setting up samba (3.0.22-1ubuntu3) ...
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
Setting up totem-xine (1.4.1-0ubuntu4) ...

Setting up totem-xine-firefox-plugin (1.4.1-0ubuntu4) ...
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
logan@LHUbuntu:~$

---

### Post by dregs on 2006-06-16
I have this problem too.

---

### Post by givré on 2006-06-16
This is a bug that should be solve in a next update [https://launchpad.net/distros/ubuntu/+source/samba/+bug/48082](https://launchpad.net/distros/ubuntu/+source/samba/+bug/48082)
add your comment

---

