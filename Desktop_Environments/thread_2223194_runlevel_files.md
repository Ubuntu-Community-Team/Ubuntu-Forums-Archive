---
title: "runlevel files"
date: 2014-05-09
forum: Desktop Environments
---

### Post by marbew on 2014-05-09
Hello beautiful mind, I would like to find a good answer to this silly question.
I'm using 3 different distros to study for my LPCI-1 certificate and RHEL, Ubuntu, Debian have 3 different files to store the default runlevel.
Why a linux technician should be struggle every time he needs to work on different distro?????????
Is maybe the time to create a solid rule to make it clear at least the most important config file must be the same?????

---

### Post by tfrue on 2014-05-10
I believe the LPCI-1 uses the 2.6 kernel, Ubuntu 14.04 is on 3.13 and the other distro's are probably on the equivalent. So I don't know when they stopped supporting runlevels but that is a thing of the past. I know Fedora 13 supports it as that is the distro we used in my System Administrating class which was geared at the LPIC tests. So that distro would be a good one to use and learn for the test. I believe the runlevel in Fedora 13 was /etc/inittab file.

Good luck on the test!

Chris

---

### Post by buzzingrobot on 2014-05-10
Different versions of Linux use different init systems. Such is life.  If everything was dead easy, we wouldn't need to pay professional Linux techs.

---

### Post by mcduck on 2014-05-10
Also Ubuntu, like many other distros, is heading away from runlevel-based init system and instead uses event-based Upstart (so pretty much all runlevel stuff is only for backwards compatibility reasons).

---

### Post by sisco311 on 2014-05-10
> **marbew said:**
> Hello beautiful mind, I would like to find a good answer to this silly question.
I'm using 3 different distros to study for my LPCI-1 certificate and RHEL, Ubuntu, Debian have 3 different files to store the default runlevel.
Why a linux technician should be struggle every time he needs to work on different distro?????????
Is maybe the time to create a solid rule to make it clear at least the most important config file must be the same?????

We just have to figure out which config file is the most important [.exrc or .emacs]("http://en.wikipedia.org/wiki/Editor_war"). :) 

Linux and Linux distributions are in constant development. As a Linux technician you will also have to "struggle" with every new release of the same distro (But *the struggle itself is enough to fill a man's heart*).  ;)

RHEL 6 and Ubuntu since 6.10 uses Upstart, but RHEL 7 ships with systemd and Debian "jessie" will also use systemd as the default system management daemon for Linux and Ubuntu will follow (See: [http://www.markshuttleworth.com/archives/1316](http://www.markshuttleworth.com/archives/1316)). It seams that,for now, systemd is the new sysvinit. Who knows for how long? ;)

 Keep up the learning and good luck on your exam.

---

