---
title: "HELP with compiz installation."
date: 2007-08-23
forum: Desktop Effects &amp; Customization
---

### Post by tool666 on 2007-08-23
I try to install and i get the folowing messaga....


Depends: libatk1.0-0 (>=1.13.1) but 1.11.4-0ubuntu1 is to be installed
  Depends: libbonobo2-0 (>=2.15.0) but 2.14.0-0ubuntu2 is to be installed
  Depends: libbonoboui2-0 (>=2.15.1) but 2.14.0-0ubuntu1 is to be installed
  Depends: libc6 (>=2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is to be installed
  Depends: libcairo2 (>=1.4.0) but 1.0.4-0ubuntu1 is to be installed
  Depends: libfontconfig1 (>=2.4.0) but 2.3.2-1.1ubuntu12 is to be installed
  Depends: libglib2.0-0 (>=2.12.9) but 2.10.3-0ubuntu1 is to be installed
 Depends: libgnome-compiz-manager0 but it is not going to be installed
  Depends: libgnome-keyring0 (>=0.7.1) but 0.4.9-1ubuntu1 is to be installed
  Depends: libgnomeui-0 (>=2.17.1) but 2.14.1-0ubuntu3 is to be installed
  Depends: libgnomevfs2-0 (>=1:2.17.90) but 2.14.2-0ubuntu1 is to be installed
  Depends: libgtk2.0-0 (>=2.10.3) but 2.8.20-0ubuntu1.1 is to be installed
  Depends: liborbit2 (>=1:2.14.1) but 1:2.14.0-0ubuntu1 is to be installed
  Depends: libpango1.0-0 (>=1.16.2) but 1.12.3-0ubuntu3 is to be installed
  Depends: libpopt0 (>=1.10) but 1.7-5 is to be installed
  Depends: libwnck18 (>=2.15.90) but 2.14.2-0ubuntu1 is to be installed
  Depends: libxfixes3 (>=1:4.0.1) but 1:3.0.1.2-0ubuntu3 is to be installed
  Depends: libxml2 (>=2.6.27) but 2.6.24.dfsg-1ubuntu1 is to be installed
  Depends: libxrandr2 (>=2:1.2.0) but 1:1.1.0.2-0ubuntu4 is to be installed
 Depends: compiz but it is not going to be installed
 Depends: compiz-gnome but it is not going to be installed



I'm new to linux and i don't knom many things. any suggestions?
thanx...

---

### Post by Chymera on 2007-08-23
it means you have to install the dependencies, either type ```
sudo apt-get install
``` followed by all the libs which are needed, or look for a how-to compiz fusion guide.

There are quite a few on the forum and they may help you if you encounter certain problems on the way.

---

### Post by Inxsible on 2007-08-23
what repo, if any, are you using?

all repos had a few problems, but Trevino's repos seem to be working now. Try using his repos.

---

