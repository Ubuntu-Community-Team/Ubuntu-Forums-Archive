---
title: "problem with apt-proxy"
date: 2006-11-11
forum: Desktop Environments
---

### Post by dihfg on 2006-11-11
I cannot get apt-proxy working as it should in spite of reading manpages, wikis and forum postings. I hope one of the experts here can help.

A few weeks ago I installed apt-proxy and it seemed to work (1 PC as server, 1 PC and 1 laptop as clients). One day I noticed that the clients did not really get their updates from the proxy-server but fetched it directly from the internet (although those packages were already downloaded and saved in /var/cache/apt/archives on the server. To find out why I reinstalled apt-proxy and tried to set it up step by step. When executing 

sudo apt-proxy-import /var/cache/apt/archives 

I got these messages:
WARNING: apt-proxy has not been tested under this version of twisted (2.2.0).
WARNING: although it should work without problem.
2006/11/11 12:49 CET [-] Log opened.
2006/11/11 12:49 CET [-] verbose
2006/11/11 12:49 CET [-] [import] Importing packages from directory tree: /var/cache/apt/archives
2006/11/11 12:49 CET [-] [import] Ignoring (unknown file type):lock
2006/11/11 12:49 CET [-] [apt_pkg] No Packages files available for ubuntu-security backend
2006/11/11 12:49 CET [-] [apt_pkg] No Packages files available for ubuntu backend
2006/11/11 12:49 CET [-] [apt_pkg] No Packages files available for ubuntu-security backend
2006/11/11 12:49 CET [-] [apt_pkg] No Packages files available for ubuntu backend
2006/11/11 12:49 CET [-] [import] apt-proxy_1.9.33ubuntu1_all.deb skipped - no suitable backend found
2006/11/11 12:49 CET [-] [apt_pkg] No Packages files available for ubuntu-security backend
2006/11/11 12:49 CET [-] [apt_pkg] No Packages files available for ubuntu backend
2006/11/11 12:49 CET [-] [apt_pkg] No Packages files available for ubuntu-security backend
2006/11/11 12:49 CET [-] [apt_pkg] No Packages files available for ubuntu backend
2006/11/11 12:49 CET [-] [import] libavahi-common-data_0.6.10-0ubuntu3.2_i386.deb skipped - no suitable backend found
2006/11/11 12:49 CET [-] [apt_pkg] No Packages files available for ubuntu-security backend
2006/11/11 12:49 CET [-] [apt_pkg] No Packages files available for ubuntu backend
2006/11/11 12:49 CET [-] [apt_pkg] No Packages files available for ubuntu-security backend
2006/11/11 12:49 CET [-] [apt_pkg] No Packages files available for ubuntu backend
2006/11/11 12:49 CET [-] [import] libavahi-common3_0.6.10-0ubuntu3.2_i386.deb skipped - no suitable backend found
......
......
......
This is what I do not understand: it says "...no suitable backend found" although I have edited  apt-proxy-v2.conf exactly as suggested and the same servers are in my sources.list:

[ubuntu]
;; Ubuntu archive
backends = [http://at.archive.ubuntu.com/ubuntu](http://at.archive.ubuntu.com/ubuntu)
	[http://ftp.inf.tu-dresden.de/os/linux/dists/ubuntu](http://ftp.inf.tu-dresden.de/os/linux/dists/ubuntu)

[ubuntu-security]
;; Ubuntu security updates
backends = [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)

Sources.list:
deb [http://at.archive.ubuntu.com/ubuntu](http://at.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb [http://ftp.inf.tu-dresden.de/os/linux/dists/ubuntu](http://ftp.inf.tu-dresden.de/os/linux/dists/ubuntu) dapper main restricted universe multiverse
deb [http://at.archive.ubuntu.com/ubuntu](http://at.archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb [http://ftp.inf.tu-dresden.de/os/linux/dists/ubuntu](http://ftp.inf.tu-dresden.de/os/linux/dists/ubuntu) dapper-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse


Grateful for any hints on how to solve this problem![FONT="Arial"][SIZE="2"][/SIZE][/FONT]

---

### Post by petruha on 2006-11-14
I've got exactly same issues with apt-proxy-import (v1.9.33ubuntu1 on Dapper).

[http://packages.debian.org/changelogs/pool/main/a/apt-proxy/apt-proxy_1.9.35/changelog](http://packages.debian.org/changelogs/pool/main/a/apt-proxy/apt-proxy_1.9.35/changelog)
suggests that the import problem might have been fixed in v1.9.35. However I could not manage to install 1.9.35 due to all the dependencies on new phyton-tons-of-pckgs.

So the question is: can I install apt-proxy 1.9.35 on Dapper? And if yes - how can I (detailed answer or sample script will be much appreciated)?

By the way I had to fix apt-proxy that gets installed by Ubuntu to make it working with Ubuntu :(
This post helped: [http://packages.debian.org/changelogs/pool/main/a/apt-proxy/apt-proxy_1.9.35/changelog](http://packages.debian.org/changelogs/pool/main/a/apt-proxy/apt-proxy_1.9.35/changelog)

---

### Post by petruha on 2006-11-14
Sorry, here are the correct links to the fix from the post above:
[http://www.eng.uwaterloo.ca/twiki/bin/view/Linux/AptProxyDapper](http://www.eng.uwaterloo.ca/twiki/bin/view/Linux/AptProxyDapper)
[http://librarian.launchpad.net/3009153/apt-proxy-fix.diff](http://librarian.launchpad.net/3009153/apt-proxy-fix.diff)

---

### Post by petruha on 2006-11-15
Oh well, the bug has been confirmed...
[https://launchpad.net/distros/ubuntu/+source/apt-proxy/+bug/4844](https://launchpad.net/distros/ubuntu/+source/apt-proxy/+bug/4844)

---

### Post by comsciprof on 2006-11-19
How is the patch on [http://librarian.launchpad.net/3009153/apt-proxy-fix.diff](http://librarian.launchpad.net/3009153/apt-proxy-fix.diff) being applied?

---

