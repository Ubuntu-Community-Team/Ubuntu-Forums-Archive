---
title: "XDG dir's in ~/ nuked"
date: 2011-07-18
forum: Desktop Environments
---

### Post by xSpidey01x on 2011-07-18
I have just spent over an hour getting my system back into a usable state. The install began life as a Netbook install of 10.10 (Maverick) on an ASUS EeePC 1015PE. I upgraded to Natty like a few weeks after it was released. Everything with the system has been EXCELLENT.


Today, after 4 days of uptime, and numerous hibernates/sleeps, I decided to shutdown. When I booted the system a few hours later, I found out that gnome-session --session=name didn't work because my session file was deleted. My Dropbox also got shafted enough to eed being relinked.

After a bit of inspection, I noticed that everything in .config, .local, .cache, etc has been screwed. This includes the eraser of my Chrome config, and several config files I had moved into these directories were gone (mpd, mutt, etc) and placed symlinks into the usual places. Good thing most of my stuff is in git or Dropbox, and except for my recent mpd setup, backed up if it is not part of GNOME or the OS.

It seems as if all the XDG directories and GNOME crapola in my $HOME got removed and replaced. How and why the hell?

This is rather annoying. Especially since using these directories is somewhat the modern form over ~/.appamerc!!!!!!!


Recent data from /var/log/apt/history.log:

```

Upgrade: xserver-xorg-video-ati:i386 (6.14.0-0ubuntu4, 6.14.0-0ubuntu4.1), software-center:i386 (4.0.3, 4.0.4), ntpdate:i386 (4.2.6.p2+dfsg-1ubuntu5, 4.2.6.p2+dfsg-1ubuntu5.1), xserver-xorg-video-radeon:i386 (6.14.0-0ubuntu4, 6.14.0-0ubuntu4.1), nautilus-sendto:i386 (2.32.0-0ubuntu1, 2.32.0-0ubuntu1.1)
End-Date: 2011-07-12  15:44:02

Start-Date: 2011-07-13  10:02:12
Install: linux-headers-2.6.38-10-generic:i386 (2.6.38-10.46), linux-headers-2.6.38-10:i386 (2.6.38-10.46), linux-image-2.6.38-10-generic:i386 (2.6.38-10.46)
Upgrade: qt4-doc:i386 (4.7.2-0ubuntu6.1, 4.7.2-0ubuntu6.2), libqt4-opengl:i386 (4.7.2-0ubuntu6.1, 4.7.2-0ubuntu6.2), libqt4-declarative:i386 (4.7.2-0ubuntu6.1, 4.7.2-0ubuntu6.2), linux-headers-generic:i386 (2.6.38.8.22, 2.6.38.10.25), libqt4-test:i386 (4.7.2-0ubuntu6.1, 4.7.2-0ubuntu6.2), linux-image-generic:i386 (2.6.38.8.22, 2.6.38.10.25), libqt4-sql-mysql:i386 (4.7.2-0ubuntu6.1, 4.7.2-0ubuntu6.2), libqt4-dbus:i386 (4.7.2-0ubuntu6.1, 4.7.2-0ubuntu6.2), libqt4-qt3support:i386 (4.7.2-0ubuntu6.1, 4.7.2-0ubuntu6.2), libqt4-opengl-dev:i386 (4.7.2-0ubuntu6.1, 4.7.2-0ubuntu6.2), qt4-designer:i386 (4.7.2-0ubuntu6.1, 4.7.2-0ubuntu6.2), linux-libc-dev:i386 (2.6.38-8.42, 2.6.38-10.46), qt4-demos:i386 (4.7.2-0ubuntu6.1, 4.7.2-0ubuntu6.2), libqt4-xmlpatterns:i386 (4.7.2-0ubuntu6.1, 4.7.2-0ubuntu6.2), libqt4-dev:i386 (4.7.2-0ubuntu6.1, 4.7.2-0ubuntu6.2), libqt4-help:i386 (4.7.2-0ubuntu6.1, 4.7.2-0ubuntu6.2), qt4-dev-tools:i386 (4.7.2-0ubuntu6.1, 4.7.2-0ubuntu6.2), libqtcore4:i386 (4.7.2-0ubuntu6.1, 4.7.2-0ubuntu6.2), qt4-qmake:i386 (4.7.2-0ubuntu6.1, 4.7.2-0ubuntu6.2), libqt4-sql-sqlite:i386 (4.7.2-0ubuntu6.1, 4.7.2-0ubuntu6.2), libqt4-sql:i386 (4.7.2-0ubuntu6.1, 4.7.2-0ubuntu6.2), libqt4-svg:i386 (4.7.2-0ubuntu6.1, 4.7.2-0ubuntu6.2), libqt4-xml:i386 (4.7.2-0ubuntu6.1, 4.7.2-0ubuntu6.2), libqt4-network:i386 (4.7.2-0ubuntu6.1, 4.7.2-0ubuntu6.2), libqt4-designer:i386 (4.7.2-0ubuntu6.1, 4.7.2-0ubuntu6.2), libqtgui4:i386 (4.7.2-0ubuntu6.1, 4.7.2-0ubuntu6.2), google-chrome-stable:i386 (12.0.742.112-r90304, 12.0.742.124-r92024), libqt4-script:i386 (4.7.2-0ubuntu6.1, 4.7.2-0ubuntu6.2), libqt4-scripttools:i386 (4.7.2-0ubuntu6.1, 4.7.2-0ubuntu6.2), linux-generic:i386 (2.6.38.8.22, 2.6.38.10.25)
End-Date: 2011-07-13  10:09:48

Start-Date: 2011-07-14  09:12:51
Upgrade: apt-transport-https:i386 (0.8.13.2ubuntu4, 0.8.13.2ubuntu4.1), apt-utils:i386 (0.8.13.2ubuntu4, 0.8.13.2ubuntu4.1), apt:i386 (0.8.13.2ubuntu4, 0.8.13.2ubuntu4.1)
End-Date: 2011-07-14  09:16:36

Start-Date: 2011-07-18  13:11:12
Commandline: apt-get upgrade
Upgrade: libgstreamer0.10-0:i386 (0.10.32-3ubuntu3, 0.10.32-3ubuntu3.1), gstreamer0.10-tools:i386 (0.10.32-3ubuntu3, 0.10.32-3ubuntu3.1)
End-Date: 2011-07-18  13:11:36

Start-Date: 2011-07-18  19:36:09
Commandline: /usr/sbin/synaptic
End-Date: 2011-07-18  19:37:13

```


In my entire life, I have only ever had funky problems with two operating systems: Windows XP and Ubuntu. Everything else I've used from DOS to OpenBSD, has never poked me back :P

---

