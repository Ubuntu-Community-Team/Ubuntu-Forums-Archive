---
title: "Running Gnome 3.10, 3.12 or 13.13"
date: 2014-05-22
forum: Desktop Environments
---

### Post by Drone4four on 2014-05-22
I installed Gnome 3.12 on Ubuntu 14.04 with a guide on OMG Ubuntu called, "[How to Upgrade to GNOME 3.12 in Ubuntu 14.04]("http://www.omgubuntu.co.uk/2014/05/upgrade-gnome-3-12-ubuntu-14-04")"

Now I notice everytime I update my system, I am installing 3.13.1 packages.  See here:

```
~ $ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libgeocode-glib0
The following packages will be upgraded:
  gir1.2-gtk-3.0 libgail-3-0 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libgtk-3-dev
6 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 6,591 kB of archives.
After this operation, 5,120 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ppa.launchpad.net/ricotz/testing/ubuntu/ trusty/main libgtk-3-common all 3.13.1+git20140522.r1.65022c40-0ubuntu1~14.04~ricotz0 [3,062 kB]
Get:2 http://ppa.launchpad.net/ricotz/testing/ubuntu/ trusty/main libgtk-3-dev amd64 3.13.1+git20140522.r1.65022c40-0ubuntu1~14.04~ricotz0 [883 kB]
Get:3 http://ppa.launchpad.net/ricotz/testing/ubuntu/ trusty/main gir1.2-gtk-3.0 amd64 3.13.1+git20140522.r1.65022c40-0ubuntu1~14.04~ricotz0 [238 kB]
Get:4 http://ppa.launchpad.net/ricotz/testing/ubuntu/ trusty/main libgail-3-0 amd64 3.13.1+git20140522.r1.65022c40-0ubuntu1~14.04~ricotz0 [81.5 kB]
Get:5 http://ppa.launchpad.net/ricotz/testing/ubuntu/ trusty/main libgtk-3-0 amd64 3.13.1+git20140522.r1.65022c40-0ubuntu1~14.04~ricotz0 [2,247 kB]
Get:6 http://ppa.launchpad.net/ricotz/testing/ubuntu/ trusty/main libgtk-3-bin amd64 3.13.1+git20140522.r1.65022c40-0ubuntu1~14.04~ricotz0 [79.2 kB]
Fetched 6,591 kB in 4s (1,540 kB/s)
(Reading database ... 325592 files and directories currently installed.)
Preparing to unpack .../libgtk-3-common_3.13.1+git20140522.r1.65022c40-0ubuntu1~14.04~ricotz0_all.deb ...
Unpacking libgtk-3-common (3.13.1+git20140522.r1.65022c40-0ubuntu1~14.04~ricotz0) over (3.13.1+git20140521.a61a11a4-0ubuntu1~14.04~ricotz0) ...
Preparing to unpack .../libgtk-3-dev_3.13.1+git20140522.r1.65022c40-0ubuntu1~14.04~ricotz0_amd64.deb ...
Unpacking libgtk-3-dev (3.13.1+git20140522.r1.65022c40-0ubuntu1~14.04~ricotz0) over (3.13.1+git20140521.a61a11a4-0ubuntu1~14.04~ricotz0) ...
Preparing to unpack .../gir1.2-gtk-3.0_3.13.1+git20140522.r1.65022c40-0ubuntu1~14.04~ricotz0_amd64.deb ...
Unpacking gir1.2-gtk-3.0 (3.13.1+git20140522.r1.65022c40-0ubuntu1~14.04~ricotz0) over (3.13.1+git20140521.a61a11a4-0ubuntu1~14.04~ricotz0) ...
Preparing to unpack .../libgail-3-0_3.13.1+git20140522.r1.65022c40-0ubuntu1~14.04~ricotz0_amd64.deb ...
Unpacking libgail-3-0:amd64 (3.13.1+git20140522.r1.65022c40-0ubuntu1~14.04~ricotz0) over (3.13.1+git20140521.a61a11a4-0ubuntu1~14.04~ricotz0) ...
Preparing to unpack .../libgtk-3-0_3.13.1+git20140522.r1.65022c40-0ubuntu1~14.04~ricotz0_amd64.deb ...
Unpacking libgtk-3-0:amd64 (3.13.1+git20140522.r1.65022c40-0ubuntu1~14.04~ricotz0) over (3.13.1+git20140521.a61a11a4-0ubuntu1~14.04~ricotz0) ...
Preparing to unpack .../libgtk-3-bin_3.13.1+git20140522.r1.65022c40-0ubuntu1~14.04~ricotz0_amd64.deb ...
Leaving 'diversion of /usr/sbin/update-icon-caches to /usr/sbin/update-icon-caches.gtk2 by libgtk-3-bin'
Leaving 'diversion of /usr/share/man/man8/update-icon-caches.8.gz to /usr/share/man/man8/update-icon-caches.gtk2.8.gz by libgtk-3-bin'
Unpacking libgtk-3-bin (3.13.1+git20140522.r1.65022c40-0ubuntu1~14.04~ricotz0) over (3.13.1+git20140521.a61a11a4-0ubuntu1~14.04~ricotz0) ...
Processing triggers for libglib2.0-0:amd64 (2.41.0~git20140521.ace7658b-0ubuntu1~14.04~ricotz0) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up libgtk-3-common (3.13.1+git20140522.r1.65022c40-0ubuntu1~14.04~ricotz0) ...
Setting up libgtk-3-0:amd64 (3.13.1+git20140522.r1.65022c40-0ubuntu1~14.04~ricotz0) ...
Setting up gir1.2-gtk-3.0 (3.13.1+git20140522.r1.65022c40-0ubuntu1~14.04~ricotz0) ...
Setting up libgtk-3-dev (3.13.1+git20140522.r1.65022c40-0ubuntu1~14.04~ricotz0) ...
Setting up libgail-3-0:amd64 (3.13.1+git20140522.r1.65022c40-0ubuntu1~14.04~ricotz0) ...
Setting up libgtk-3-bin (3.13.1+git20140522.r1.65022c40-0ubuntu1~14.04~ricotz0) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
~ $ 

```
Is the gnome3-team/gnome3-staging ppa feeding me Gnome 3.13 software that is experimental and undergoing heavy development?  If so, is it my only option to either use the development release or uninstall Gnome 3.12/3.13 and reinstall the 3.10 which comes with stock Ubuntu 14.04?

---

### Post by kurt18947 on 2014-05-22
I'm NO expert at this stuff but did install Gnome 3.12 on Ubuntu-gnome.  I didn't do anything with ricotz - I think that is *really* bleeding edge.  I just enabled gnome using the instructions here:

[http://askubuntu.com/questions/452864/how-to-get-gnome-shell-3-12-on-ubuntu-14-04](http://askubuntu.com/questions/452864/how-to-get-gnome-shell-3-12-on-ubuntu-14-04).

So far 3.12 is as smooth as 3.10 except for the extensions that haven't made the jump yet.

---

### Post by grahammechanical on 2014-05-22
The Ubuntu Gnome3 staging PPA is deemed experimental.

> [COLOR=#333333][FONT=monospace]The packages here have been deemed not ready for general use, they have known bugs and/or regressions, sometimes of a critical nature. Mostly things should run smoothly but be prepared to use ppa-purge, when you encounter issues![/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]If they break your system, you get to keep both halves.[/FONT][/COLOR]


[https://launchpad.net/~gnome3-team/+archive/gnome3-staging/+index?batch=75&memo=150&start=150](https://launchpad.net/~gnome3-team/+archive/gnome3-staging/+index?batch=75&memo=150&start=150)

The ricozt PPA is even more experimental.

> [COLOR=#333333][FONT=monospace]Make sure you know what you are doing! You are getting bleeding edge snapshots![/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]You should have a stable experience most of the time, but there will be problems![/FONT][/COLOR]

[https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

> [COLOR=#333333][FONT=monospace]Using this ppa could break your system or make it unstable! [/FONT][/COLOR][COLOR=#333333][FONT=monospace]So you need to know how to repair it using something like ppa-purge.[/FONT][/COLOR]

The ricotz PPA does indeed bring in packages from Gnome 3.13. Some are intended for 14.10 users but there are also some bits for 14.04 that are mainly to do with themes.

Regards.

---

### Post by Drone4four on 2014-05-24
I purged my system of the ricotz PPA packages and installed the stable 3.12 release using gnome3-team / gnome3-staging.  Thank-you, **grahammechanical** and **kurt18947**.

---

