---
title: "Help! How to install wxWidgets in Ubuntu 8.10 Desktop 64bit"
date: 2009-06-05
forum: General Help
---

### Post by boykadyot on 2009-06-05
Hi to everyone,

I wondering if anyone could help me install wxwidgets in ubuntu 8.10 desktop 64bit.

I already tried doing the instruction from "http://wiki.wxpython.org/InstallingOnUbuntuOrDebian" but it gives the error:

W: Failed to fetch [http://apt.wxwidgets.org/dists/intrepid-wx/main/binary-amd64/Packages.bz2](http://apt.wxwidgets.org/dists/intrepid-wx/main/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://apt.wxwidgets.org/dists/intrepid-wx/main/source/Sources.bz2](http://apt.wxwidgets.org/dists/intrepid-wx/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.


I hope anyone can help me.


thanks

---

### Post by mb_webguy on 2009-06-05
All of the wxWidgets libraries you need to run or create software that uses wxWidgets are available in the Ubuntu repositories.  Just open System > Administration > Synaptic Package Manager, and search for wxwidgets.

If you're trying to install software that uses wxWidgets, if you're installing it through a package manager like Add/Remove, Synaptic, or apt-get, then the necessary wxWidgets libraries are automatically installed for you.

If you're trying to install software that uses wxWidgets and doing so by compiling from source, then you should first check to see if the software is available in the software repositories, a Launchpad PPA, or a deb package.  If it's not, then you should examine the output of ./configure to determine the specific wxWidgets libraries (and other dependencies) you'll need, which are almost certainly available in the repositories.

---

### Post by jcobban on 2009-06-10
I am really anxious to have a cross-platform GUI development platform for C++!  But I am completely mystified by the obscurity of WxWidgets packaging and installation.

I have installed libwxbase2.8.0, wx-common, wx2.8-headers, and wx2.8-examples using the package manager.

1) Where are the samples put?
2) The macros are put into a directory /usr/include/wx2.8/wx that requires either manually creating a link to give them the right hierarchy, or else adding an include to every wxWidgets project.  I can appreciate that the intention is to permit installing more than one version of wxWidgets in a system, but this is overkill for the first installation.
3) I cannot get any samples that I copy from the web to compile.  Not even close.  I get HUNDREDS of error messages that probably make sense to the developers of WxWidgets but are completely meaningless to somebody who just wants to write a few programs.  Since the first hundred messages are about configuration macros that haven't been defined I think I have to run the configure command manually to deal with this, but since I don't know where the install put anything, except the macros, I have no idea of where I am supposed to run that command.  All of the documentation that I can find assumes that you perform the entire installation manually from scratch.  If the Package Manager installs all of the files why doesn't IT run the configure command?

This is my THIRD try at getting this product to install and run.  Each time after days of struggling I get so frustrated I put it away, in the hope that when I cool off I will be able to make sense of it.  I have been installing software of all kinds for over 30 years and this is the most frustrating package I have ever dealt with!

I am trying to run this on Ubuntu 9.04 with gcc on an X86.  Ideally I would like to develop under Eclipse so I can do all of my development in the same IDE.

---

