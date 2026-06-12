---
title: "Netgen 4.9.13 not run (More details)"
date: 2013-01-26
forum: Education &amp; Science
---

### Post by ybUnetgen on 2013-01-26
Could you please help?

More detail about the installation.   Hopefully this can provide more info so that you can help me out.   Really appreciate any suggestions.

My first several attempts to install Netgen were not successful.  After manually download and install a depending lib:

[INDENT]*$ sodu dpkg -i libfontconfig1-dev_2.8.0-3ubuntu9.1_amd64.deb*
[/INDENT]
the installation of Netgen went thru:

[INDENT]*$ sudo apt-get install netgen*
*Reading package lists... Done*
*Building dependency tree       *
*Reading state information... Done*
*The following extra packages will be installed:*
*  libftgl2 libnglib-4.9.13 libopencascade-foundation-6.5.0*
*  libopencascade-modeling-6.5.0 libopencascade-ocaf-6.5.0*
*  libopencascade-ocaf-lite-6.5.0 libopencascade-visualization-6.5.0*
*  libpthread-stubs0 libpthread-stubs0-dev libtogl1 libx11-dev libx11-doc*
*  libxau-dev libxcb1-dev libxdmcp-dev libxext-dev libxft-dev libxrender-dev*
*  libxss-dev tcl8.5-dev tix-dev tk8.5-dev x11proto-core-dev x11proto-input-dev*
*  x11proto-kb-dev x11proto-render-dev x11proto-scrnsaver-dev x11proto-xext-dev*
*  xorg-sgml-doctools xtrans-dev*
*Suggested packages:*
*  libxcb-doc tcl8.5-doc tk8.5-doc*
*The following NEW packages will be installed:*
*  libftgl2 libnglib-4.9.13 libopencascade-foundation-6.5.0*
*  libopencascade-modeling-6.5.0 libopencascade-ocaf-6.5.0*
*  libopencascade-ocaf-lite-6.5.0 libopencascade-visualization-6.5.0*
*  libpthread-stubs0 libpthread-stubs0-dev libtogl1 libx11-dev libx11-doc*
*  libxau-dev libxcb1-dev libxdmcp-dev libxext-dev libxft-dev libxrender-dev*
*  libxss-dev netgen tcl8.5-dev tix-dev tk8.5-dev x11proto-core-dev*
*  x11proto-input-dev x11proto-kb-dev x11proto-render-dev*
*  x11proto-scrnsaver-dev x11proto-xext-dev xorg-sgml-doctools xtrans-dev*
*0 upgraded, 31 newly installed, 0 to remove and 0 not upgraded.*
*Need to get 0 B/33.3 MB of archives.*
*After this operation, 99.1 MB of additional disk space will be used.*
*Do you want to continue [Y/n]? y*
*Extracting templates from packages: 100%*
*Selecting previously unselected package libftgl2.*
*(Reading database ... 226384 files and directories currently installed.)*
*Unpacking libftgl2 (from .../libftgl2_2.1.3~rc5-4_amd64.deb) ...*
*Selecting previously unselected package libopencascade-foundation-6.5.0.*
*Unpacking libopencascade-foundation-6.5.0 (from .../libopencascade-foundation-6.5.0_6.5.0.dfsg-2build1_amd64.deb) ...*
*Selecting previously unselected package libopencascade-modeling-6.5.0.*
*Unpacking libopencascade-modeling-6.5.0 (from .../libopencascade-modeling-6.5.0_6.5.0.dfsg-2build1_amd64.deb) ...*
*Selecting previously unselected package libopencascade-ocaf-lite-6.5.0.*
*Unpacking libopencascade-ocaf-lite-6.5.0 (from .../libopencascade-ocaf-lite-6.5.0_6.5.0.dfsg-2build1_amd64.deb) ...*
*Selecting previously unselected package libopencascade-visualization-6.5.0.*
*Unpacking libopencascade-visualization-6.5.0 (from .../libopencascade-visualization-6.5.0_6.5.0.dfsg-2build1_amd64.deb) ...*
*Selecting previously unselected package libopencascade-ocaf-6.5.0.*
*Unpacking libopencascade-ocaf-6.5.0 (from .../libopencascade-ocaf-6.5.0_6.5.0.dfsg-2build1_amd64.deb) ...*
*Selecting previously unselected package libnglib-4.9.13.*
*Unpacking libnglib-4.9.13 (from .../libnglib-4.9.13_4.9.13.dfsg-3ubuntu1_amd64.deb) ...*
*Selecting previously unselected package libpthread-stubs0.*
*Unpacking libpthread-stubs0 (from .../libpthread-stubs0_0.3-3_amd64.deb) ...*
*Selecting previously unselected package libpthread-stubs0-dev.*
*Unpacking libpthread-stubs0-dev (from .../libpthread-stubs0-dev_0.3-3_amd64.deb) ...*
*Selecting previously unselected package xorg-sgml-doctools.*
*Unpacking xorg-sgml-doctools (from .../xorg-sgml-doctools_1%3a1.10-1_all.deb) ...*
*Selecting previously unselected package x11proto-core-dev.*
*Unpacking x11proto-core-dev (from .../x11proto-core-dev_7.0.22-1_all.deb) ...*
*Selecting previously unselected package libxau-dev.*
*Unpacking libxau-dev (from .../libxau-dev_1%3a1.0.6-4_amd64.deb) ...*
*Selecting previously unselected package libxdmcp-dev.*
*Unpacking libxdmcp-dev (from .../libxdmcp-dev_1%3a1.1.0-4_amd64.deb) ...*
*Selecting previously unselected package x11proto-input-dev.*
*Unpacking x11proto-input-dev (from .../x11proto-input-dev_2.1.99.6-1_all.deb) ...*
*Selecting previously unselected package x11proto-kb-dev.*
*Unpacking x11proto-kb-dev (from .../x11proto-kb-dev_1.0.5-2_all.deb) ...*
*Selecting previously unselected package xtrans-dev.*
*Unpacking xtrans-dev (from .../xtrans-dev_1.2.6-2_all.deb) ...*
*Selecting previously unselected package libxcb1-dev.*
*Unpacking libxcb1-dev (from .../libxcb1-dev_1.8.1-1_amd64.deb) ...*
*Selecting previously unselected package libx11-dev.*
*Unpacking libx11-dev (from .../libx11-dev_2%3a1.4.99.1-0ubuntu2_amd64.deb) ...*
*Selecting previously unselected package libx11-doc.*
*Unpacking libx11-doc (from .../libx11-doc_2%3a1.4.99.1-0ubuntu2_all.deb) ...*
*Selecting previously unselected package x11proto-xext-dev.*
*Unpacking x11proto-xext-dev (from .../x11proto-xext-dev_7.2.0-3_all.deb) ...*
*Selecting previously unselected package libxext-dev.*
*Unpacking libxext-dev (from .../libxext-dev_2%3a1.3.0-3build1_amd64.deb) ...*
*Selecting previously unselected package x11proto-render-dev.*
*Unpacking x11proto-render-dev (from .../x11proto-render-dev_2%3a0.11.1-2_all.deb) ...*
*Selecting previously unselected package libxrender-dev.*
*Unpacking libxrender-dev (from .../libxrender-dev_1%3a0.9.6-2build1_amd64.deb) ...*
*Selecting previously unselected package libxft-dev.*
*Unpacking libxft-dev (from .../libxft-dev_2.2.0-3ubuntu2_amd64.deb) ...*
*Selecting previously unselected package x11proto-scrnsaver-dev.*
*Unpacking x11proto-scrnsaver-dev (from .../x11proto-scrnsaver-dev_1.2.1-2_all.deb) ...*
*Selecting previously unselected package libxss-dev.*
*Unpacking libxss-dev (from .../libxss-dev_1%3a1.2.1-2_amd64.deb) ...*
*Selecting previously unselected package tcl8.5-dev.*
*Unpacking tcl8.5-dev (from .../tcl8.5-dev_8.5.11-1ubuntu1_amd64.deb) ...*
*Selecting previously unselected package tk8.5-dev.*
*Unpacking tk8.5-dev (from .../tk8.5-dev_8.5.11-1_amd64.deb) ...*
*Selecting previously unselected package tix-dev.*
*Unpacking tix-dev (from .../tix-dev_8.4.3-4_amd64.deb) ...*
*Selecting previously unselected package libtogl1.*
*Unpacking libtogl1 (from .../libtogl1_1.7-12_amd64.deb) ...*
*Selecting previously unselected package netgen.*
*Unpacking netgen (from .../netgen_4.9.13.dfsg-3ubuntu1_amd64.deb) ...*
*Processing triggers for man-db ...*
*Processing triggers for desktop-file-utils ...*
*Processing triggers for bamfdaemon ...*
*Rebuilding /usr/share/applications/bamf.index...*
*Processing triggers for gnome-menus ...*
*Setting up libftgl2 (2.1.3~rc5-4) ...*
*Setting up libopencascade-foundation-6.5.0 (6.5.0.dfsg-2build1) ...*
*Setting up libopencascade-modeling-6.5.0 (6.5.0.dfsg-2build1) ...*
*Setting up libopencascade-ocaf-lite-6.5.0 (6.5.0.dfsg-2build1) ...*
*Setting up libopencascade-visualization-6.5.0 (6.5.0.dfsg-2build1) ...*
*Setting up libopencascade-ocaf-6.5.0 (6.5.0.dfsg-2build1) ...*
*Setting up libnglib-4.9.13 (4.9.13.dfsg-3ubuntu1) ...*
*Setting up libpthread-stubs0 (0.3-3) ...*
*Setting up libpthread-stubs0-dev (0.3-3) ...*
*Setting up xorg-sgml-doctools (1:1.10-1) ...*
*Setting up x11proto-core-dev (7.0.22-1) ...*
*Setting up libxau-dev (1:1.0.6-4) ...*
*Setting up libxdmcp-dev (1:1.1.0-4) ...*
*Setting up x11proto-input-dev (2.1.99.6-1) ...*
*Setting up x11proto-kb-dev (1.0.5-2) ...*
*Setting up xtrans-dev (1.2.6-2) ...*
*Setting up libxcb1-dev (1.8.1-1) ...*
*Setting up libx11-dev (2:1.4.99.1-0ubuntu2) ...*
*Setting up libx11-doc (2:1.4.99.1-0ubuntu2) ...*
*Setting up x11proto-xext-dev (7.2.0-3) ...*
*Setting up libxext-dev (2:1.3.0-3build1) ...*
*Setting up x11proto-render-dev (2:0.11.1-2) ...*
*Setting up libxrender-dev (1:0.9.6-2build1) ...*
*Setting up libxft-dev (2.2.0-3ubuntu2) ...*
*Setting up x11proto-scrnsaver-dev (1.2.1-2) ...*
*Setting up libxss-dev (1:1.2.1-2) ...*
*Setting up tcl8.5-dev (8.5.11-1ubuntu1) ...*
*Setting up tk8.5-dev (8.5.11-1) ...*
*Setting up tix-dev (8.4.3-4) ...*
*Setting up libtogl1 (1.7-12) ...*
*Setting up netgen (4.9.13.dfsg-3ubuntu1) ...*
*Processing triggers for libc-bin ...*
*ldconfig deferred processing now taking place*
[/INDENT]
However, when I run the Netgen program, I got a error and the program did not start. 

*$ netgen*
*NETGEN-4.9.13*
*Developed at RWTH Aachen University, Germany*
*and Johannes Kepler University Linz, Austria*
*Including OpenCascade geometry kernel*
*Parsing ng.tcl*
*optfile ./ng.opt does not exist - using default values*
*X Error of failed request:  BadRequest (invalid request code or no such operation)*
*  Major opcode of failed request:  135 (GLX)*
*  Minor opcode of failed request:  19 (X_GLXQueryServerString)*
*  Serial number of failed request:  546*
*  Current serial number in output stream:  546*

---

### Post by besial on 2013-01-26
try running```
man netgen
```If im not mistaken, it is a cli program, and you'll need to add args to get it to work.

---

### Post by steeldriver on 2013-01-26
It's actually a GUI app (using Tk / OpenGL I think) - that error looks like an OpenGL thing, what graphics card / driver do you have?

I was able to run it on a 12.04 desktop and in a Mint13 VM

---

### Post by ybUnetgen on 2013-01-30
Thank you, Steeldriver.  You are right, it is a GUI app.  My graphic card is ATI Radeon Xpresss 200m.  I really need to get this going on my Ubuntu machine. 

Thanks again.

---

### Post by steeldriver on 2013-01-31
Hmm... I'm not sure what opengl support is for that card - I presume you're using the 'radeon' driver? (I don't think the proprietary fglrx drivers support that card anymore...?)

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

You *might* find something in xorg-edgers

---

### Post by ybUnetgen on 2013-01-31
Thank you for the information.  I will try it out.

---

