---
title: "Installing packages"
date: 2009-03-18
forum: General Help
---

### Post by winiman on 2009-03-18
I install 8.10 server successfully but without internet connection. I had installed ndiswrapper for my wireless card. Problem is gedit is not install on the machine. When I try to to install gedit there is lots of dependencies that are required to be installed.

My question is is there  away where each package can be downloaded together with all the dependencies file?

---

### Post by ruel- on 2009-03-18
gedit uses gnome and some gtk libraries if I'm not mistaken, and you need x-server running to use it.. alternatively, you can install command line editors like pico,vi,vim..etc,

---

### Post by mb_webguy on 2009-03-18
I'm pretty sure nano should be installed by default on a server installation.  It's text-based, so you don't have to install a desktop to use it, and it's fairly user-friendly.

EDIT: As far as the offline download of packages and dependencies, [this]("http://theunixgeek.blogspot.com/2008/08/installing-ubuntu-packages-offline.html") might be of some help -- as long as you have access to another computer running Linux or OS X that has Internet access.

---

### Post by t0p on 2009-03-18
There's [APTonCD]("http://aptoncd.sourceforge.net/"),  which you can set up if there is an internet-connected computer you can use for the purpose.  I've never used it, but I've seen good reports.

---

### Post by winiman on 2009-03-18
Thanks for the ideas.

---

### Post by sahabcse on 2009-03-18
Hi

Collect the packages cd of ubuntu. then add the cd using following command

 #apt-cdrom add

then run #apt-get update

For more information please refer following link

[http://sahabm.blogspot.com/2009/01/package-management-debian-and-ubuntu.html](http://sahabm.blogspot.com/2009/01/package-management-debian-and-ubuntu.html)

---

### Post by EXCiD3 on 2009-03-19
Check out [Keryx]("http://keryxproject.org"), it's as easy to use as Synaptic to grab packages and updates and it runs on any operating system allowing you to easily download packages, updates and all of their dependencies easily.

---

