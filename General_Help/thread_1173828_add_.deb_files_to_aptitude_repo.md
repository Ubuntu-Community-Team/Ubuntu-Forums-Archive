---
title: "add *.deb files to aptitude repo"
date: 2009-05-30
forum: General Help
---

### Post by frpaul on 2009-05-30
I just installed Ubuntu on my laptop.
Id like to find out how to use deb packages already downloaded from ubuntu repo to my desctop comp.
First I copied /var/cache/apt/archives to corresponding dir of my laptop hdd (using usb card)
But Im still not able to install, for example, mc.
Theres a package mc_2%3a4.6.2~git20080311-4ubuntu1_i386.deb
but I cant install it. Seems like Aptitude is ignoring it for some reason.
What am I doing wrong?

---

### Post by mcduck on 2009-05-30
Just use dpkg to install the .deb package.

"sudo dpkg -i *package.deb*" (run in the same directory where you have the package).

---

### Post by bacardiandwatermelon on 2009-05-30
normally you can just double click it, are there any errors at all?

---

### Post by frpaul on 2009-05-30
> **mcduck said:**
> Just use dpkg to install the .deb package.

"sudo dpkg -i *package.deb*" (run in the same directory where you have the package).

Thanks! This worked all right.
Could you please tell why sudo aptitude install or apt-get install doesnt work?
How to make apt see /var/cahe/apt/archive/ contents?

---

### Post by frpaul on 2009-05-30
> **bacardiandwatermelon said:**
> normally you can just double click it, are there any errors at all?

Well, it just didnt come to my mind. I generally more often use command line, or mc for passing commands. Will try it out later, probably there're some specific bindings in nautilus for deb files?

---

### Post by mcduck on 2009-05-30
> **frpaul said:**
> Thanks! This worked all right.
Could you please tell why sudo aptitude install or apt-get install doesnt work?
How to make apt see /var/cahe/apt/archive/ contents?

apt-get and aptitude handle downloading and installing stuff from repositories, based on the package name that one sure isn't (and has never been in any of repositories you might have enabled. So the package isn't included in any of the repository indexes, thus apt-get doesn't know it exists.

Had the package been something that is available in the repositories you have available apt-get would have used it if you had tried installing mc.

apt-get is for downloading & installing stuff from repositories, dpkg is for installing .deb packages you already have on your computer.

---

### Post by frpaul on 2009-05-31
> **mcduck said:**
> 
apt-get is for downloading & installing stuff from repositories, dpkg is for installing .deb packages you already have on your computer.

Good! Now I understand the difference. And AFAIK, Aptitude is more user-friendly than apt-get (it even has pseudo-graphical interface).

I asked the same question about moving deb files from one comp to another on Russian ubuntu forum. As it often happens it provoked massive discussion. Im waiting for the ending so that I can post here some of the results. There seems to be quite a lot of useful tricks. May be of use to someone besides me.

---

### Post by mcduck on 2009-05-31
Aptitude also has a bad habit of trying to be too smart, and messing things up as result (like removing half of your system just to solve some minor dependency issue). Which is why most people these days will recommend using apt-get instead.

Moving .deb packages from one computer to other is a no-brainer, as long as they are made for the same Ubuntu version and you have all the required packages to solve dependencies (or Internet connection so the necessary packages can be downloaded).

Easiest way to install large quantities of .deb packages is to just put them in pone place and then run "sudo dpkg -i *.deb" to install them all at once.

---

