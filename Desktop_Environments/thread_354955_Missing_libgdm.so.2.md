---
title: "Missing libgdm.so.2"
date: 2007-02-06
forum: Desktop Environments
---

### Post by waltrothfuss on 2007-02-06
I have an edubuntu server set up in my office, and need to connect reliably to a windows terminal server using remote client.  The remote client that comes with edubuntu does not cleanly disconnect a sesson from the windows server, and automatically tries to reconnect.  Thinsoftinc has a product called winconnectVX for multi-user linux server application that does reliably connect to windows terminal servers using rdp5.1, and cleanly disconnects, but when running on edubuntu (or ubuntu when installed as the single user version, called simply winconnect), it insists that it needs libgdm.so.2.  I cannot find this library anywhere on the internet, including in sourceforge or debian.org, and rpmfind cannot find it either so that I could alien it into a debian package and install it.  An inquiry direct to thinsoftinc's tech support got the unhelpful response that I should contact my distribution's developers.  I know that winconnect can work under debian because I have it working on a Xandros 4 workstation, and Xandros is debian.  Does anyone know where this package is?

---

### Post by waltrothfuss on 2007-09-16
Hard to believe I am the only one who has had this problem.  Anyway, after much trial and error, I have found the necessary software packages in order to make this work.  They can all be added using Synaptic.

The packages are:
     
     libgdbmg1
     libg++2.8.1.3-glibc2.2
     libstdc++2.10-glibc2.2

Thinsoft's Winconnect reliably disconnects the terminal server session, and does NOT  automatically try to reconnect after a timeout expires, a feature that I found extremely annoying.

Winconnect also comes in a version called Winconnect VX, which is a multi-user version that can be installed on an Ubuntu server, allowing all the thin clients attached to your Ubuntu server to access a Windows terminal server on your network.  The base Winconnect is single user.

Thinsoft also sells a Windows terminal server program so that a standard Windows XP box can be used as a windows terminal server, without having to go through the hassle, headache and exorbitant expense of setting up a windows 2003 terminal server.  This is what I use, and it works well.  The only thing that Windows 2003 terminal server would reliably do, when I had one up and running on my network, was crash at least once a month.

---

### Post by mark laird on 2008-05-19
i have the packages my installation has complained of not having and get a invalid symbol error "dbm_open()" mailed thinsoft who we buy from regualarily with no success, any ideas - i have linked libgdbm.so.2 to libgdbm.so.3
mark

---

