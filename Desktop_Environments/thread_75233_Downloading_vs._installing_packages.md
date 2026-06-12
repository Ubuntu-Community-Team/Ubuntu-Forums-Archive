---
title: "Downloading vs. installing packages"
date: 2005-10-13
forum: Desktop Environments
---

### Post by applewax on 2005-10-13
Hello,

I'd like to add software to an installation, in particular, the kubuntu-desktop metapackage.  The problem is, I can't use apt-get to install such a large package through a modem.  It would literally take days.  (Broadband is not available where I live.)  

Being primarily a Red Hat user, what I've always done in the past is to download all the necessary .rpm packages while I was at work, where we have a fast T3 connection, burn them on a CD, then take them home.  Is it possible to do this with Ubuntu packages?  If so, how do I go about downloading the necessary packages, and how do I know which ones I need for something like the kubuntu-desktop metapackage?

I'm currently using CentOS 4.0 (Red Hat Enterprise Linux 4.0) here at work, which does not use apt-get.  If apt-get gives you the option of downloading packages to your harddrive instead of installing them, I guess I could install apt-get on this machine and go that route?  Any suggestions would be greatly appreciated,

Thanks,

Joe

---

### Post by SilverTab on 2005-10-13
Sure! you can download the rpms, and convert them to debian package using alien....

then, you just have to install the .deb package using
sudo dpkg -i packagename.deb

(Note: if the program you need offers the debian package already, grab this one instead of the rpms! ;) )

---

### Post by aysiu on 2005-10-13
You can download .deb files at work instead of .rpm files. .rpm can be installed through alien, but native .debs are better.

---

### Post by matthew on 2005-10-13
You can get the official Ubuntu debs from [this site]("http://packages.ubuntu.com/") while you are at work and make a cd. To install when you get home, use
```
sudo dpkg -i packagename.deb
```

---

