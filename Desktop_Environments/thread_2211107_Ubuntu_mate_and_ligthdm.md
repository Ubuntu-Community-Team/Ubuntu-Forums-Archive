---
title: "Ubuntu mate and ligthdm"
date: 2014-03-14
forum: Desktop Environments
---

### Post by priestnot on 2014-03-14
Hello  I have a fresh installation of ubuntu server 32bit on my Virtualbox environment and I would like to install Mate with lightdm.

I did the following process:

Add the  deb [http://repo.mate-desktop.org/ubuntu](http://repo.mate-desktop.org/ubuntu) raring main to /etc/apt/sources.list
> sudo apt-get update
> sudo apt-get --yes --quiet --allow-unauthenticated install mate-archive-keyring
> sudo apt-get update
> sudo apt-get install mate-core
> sudo apt-get install mate-desktop-environment-extra
> sudo apt-get install lightdm
> sudo reboot

And everything went great. 
But after reboot I am greeted with a login window but after I login with username and password it does nothing, just freezes.

Is there something I must do in order for this to work?

---

