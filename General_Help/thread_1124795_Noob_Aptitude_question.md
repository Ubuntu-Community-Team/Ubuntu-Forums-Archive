---
title: "Noob Aptitude question"
date: 2009-04-13
forum: General Help
---

### Post by interestinfellow on 2009-04-13
Sooo, I was looking at new fonts for ubuntu, and found this at [http://ubuntu.wordpress.com/2006/07/12/download-and-install-the-ubuntu-title-font/](http://ubuntu.wordpress.com/2006/07/12/download-and-install-the-ubuntu-title-font/) which tells you to use apt-get to retrieve the file in question.

I have also read that aptitude is better, because it can "uninstall" progs that it has installed, a little better than apt-get does.

SO, I did "sudo aptitude update", and then tried the above (replacing apt-get with aptitude) and got an output I don't understand.

here it is...

Reading package lists... Done
rob@basardo-gordo:~$ sudo aptitude install ttf-ubuntu-title
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  libboost-date-time1.34.1 libboost-filesystem1.34.1 libboost-python1.34.1 
  libboost-thread1.34.1 libgda3-3 libgda3-common libgdl-1-0 libgdl-1-common 
  libgdl-gnome-1-0 miro-data python-gnome2-extras 
The following packages have been automatically kept back:
  linux-headers-2.6.24-23 linux-headers-2.6.24-23-generic 
The following packages have been kept back:
  acpid dash doc-base evolution-data-server evolution-data-server-common 
  firefox firefox-3.0 firefox-3.0-gnome-support firefox-gnome-support gedit 
  gedit-common ghostscript ghostscript-x gnome-power-manager 
  gstreamer0.10-plugins-good hal-info initscripts jockey-common jockey-gtk 
  libcamel1.2-11 libcurl3 libcurl3-gnutls libebook1.2-9 libecal1.2-7 
  libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 
  libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3 
  libgdata-google1.2-1 libgdata1.2-1 libglib2.0-0 libgs8 libicu38 
  libjasper1 libkrb53 liblcms1 libldap-2.4-2 libnss3-1d libpng12-0 
  libpurple0 libsndfile1 libssl0.9.8 linux-image-2.6.24-23-generic 
  linux-ubuntu-modules-2.6.24-23-generic network-manager-gnome openssl 
  pidgin pidgin-data python-apt python-gobject ssl-cert sudo sysv-rc 
  sysvutils totem totem-common totem-gstreamer totem-mozilla totem-plugins 
  tzdata ufw update-manager update-manager-core vim-common vim-tiny 
  xserver-xorg-video-ati xserver-xorg-video-intel xulrunner-1.9 
  xulrunner-1.9-gnome-support 
The following NEW packages will be installed:
  ttf-ubuntu-title 
0 packages upgraded, 1 newly installed, 11 to remove and 73 not upgraded.
Need to get 29.2kB of archives. After unpacking 13.5MB will be freed.
Do you want to continue? [Y/n/?] 

And I'm not sure if I want to continue.  Why is it trying to remove stuff, when I was only trying to install something?  And is it safe to allow it to remove all that stuff?
I have also used apt-get and the add/remove to install and remove items.  Are apt-get and add/remove connected?  How about aptitude? Synaptecs is a front for apt-get, correct?  

Yeah.... I have a half a clue, but it's not enough.....

thanks.

---

### Post by fabricator4 on 2009-04-13
> **interestinfellow said:**
> 

And I'm not sure if I want to continue.  Why is it trying to remove stuff, when I was only trying to install something?  And is it safe to allow it to remove all that stuff?
I have also used apt-get and the add/remove to install and remove items.  Are apt-get and add/remove connected?  How about aptitude? Synaptecs is a front for apt-get, correct?  
thanks.

It's not trying to remove all of it - just three lines.  The rest it is saying it will keep.  Synaptic will normally do similar things.

Mostly what it is trying to remove is Boost, which is a set of open source C++ libraries. Some of it may get installed by default, and if you've removed the development stuff it may no longer be required.

It's probably safe to remove it. 

Add/Remove appears to call Synaptic with the ability to install only applications (not system software) however I believe apt-get is a completely separate CLI program.

Chris

---

