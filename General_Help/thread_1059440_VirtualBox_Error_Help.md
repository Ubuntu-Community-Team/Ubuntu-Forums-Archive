---
title: "VirtualBox Error Help"
date: 2009-02-03
forum: General Help
---

### Post by Ranger1230 on 2009-02-03
I have been trying to get virtualBox up and running and when I'm trying to build the modules I get and error saying:

 module-assistant, interactive mode &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
       &#9474; Build of the package virtualbox-ose failed! How do you wish   &#9474; 
       &#9474; to proceed?                   

When I look at the Log I see:

Build log starting, file:                                                  &#8593;
 &#9474; /var/cache/modass/virtualbox-ose.buildlog.2.6.27-7-generic.1233705195      &#9646;
 &#9474; Date: Tue, 03 Feb 2009 18:53:15 -0500   

I followed the steps in a guide and I installed virtualBox the way it tells me too. and this last step has the error:

sudo m-a a-i virtualbox-ose

Updated infos about 1 packages
Getting source for kernel version: 2.6.27-7-generic
Kernel headers available in /usr/src/linux-headers-2.6.27-7-generic
Creating symlink...
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 234 not upgraded.

Done!
unpack 
The source tarball could not be found!
Package virtualbox-ose not installed?
Running "m-a -f get virtualbox-ose" may help.
"/usr/share/modass/packages/default.sh" build KVERS=2.6.27-7-generic KSRC=/usr/src/linux KDREV=2.6.27-7.13 kdist_image
find: `/usr/src/modules/virtualbox*': No such file or directory

How do I fix this?

---

### Post by Therion on 2009-02-03
Would it not be simpler to install one of the .debs?

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

