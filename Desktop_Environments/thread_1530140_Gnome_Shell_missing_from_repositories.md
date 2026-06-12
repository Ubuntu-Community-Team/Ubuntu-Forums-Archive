---
title: "Gnome Shell missing from repositories"
date: 2010-07-13
forum: Desktop Environments
---

### Post by isoscelesrectangle on 2010-07-13
Hi, I'm attempting to play around with Gnome Shell, both in Lucid, and now in the Maverick Alpha. However, when I attempt to install it (from software center), I get an error. 
```
Package Dependencies could not be resolved. This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time. Details > gnome-shell
``` What dependency is missing from the repository?

---

### Post by wojox on 2010-07-13
What does it tell you from the terminal?

```
sudo apt-get update; sudo apt-get install gnome-shell
```

You may want to look at the ppa as well:[Gnome Shell]("https://launchpad.net/ubuntu/+source/gnome-shell")

---

### Post by isoscelesrectangle on 2010-07-13
```
sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-shell: Depends: libgjs0 but it is not going to be installed
E: Broken packages

```

---

### Post by wojox on 2010-07-13
Take a look here and see if anything looks familiar [Gnome Shell: 'Depends: libgjs0 but it is not going to be installed']("http://www.webmaster-forums.net/computer-help/gnome-shell-depends-libgjs0-it-not-going-be-installed")

---

### Post by isoscelesrectangle on 2010-07-13
Ah ok, I'm going to attempt a force install, and if not, I'll try compiling from source. 
Thanks!

---

### Post by KdotJ on 2010-07-13
Compiling from source will give you the most up to date version. The one in the repos (if it hasn't been updated since I used it) is very old indeed. It doesn't have many of the features and fixes that the freshly compiled version will have

---

### Post by isoscelesrectangle on 2010-07-13
Ok, I'm following the directions shown on here. [http://live.gnome.org/GnomeShell#building](http://live.gnome.org/GnomeShell#building) However, when I do so, I get this: 
```
curl -O http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  6494  100  6494    0     0   9197      0 --:--:-- --:--:-- --:--:-- 13935

```
and this
```
/bin/bash gnome-shell-build-setup.sh
Please run 'sudo apt-get install libtiff-dev libpng-dev libjpeg-dev ' and try again.

```
However, when I run apt-get for those packages, I get this. 
```
sudo apt-get install libtiff-dev libpng-dev libjpeg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libtiff4-dev instead of libtiff-dev
libtiff4-dev is already the newest version.
Note, selecting libpng12-dev instead of libpng-dev
libpng12-dev is already the newest version.
Note, selecting libjpeg62-dev instead of libjpeg-dev
libjpeg62-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
```
What happened here? 
Much thanks.

---

### Post by isoscelesrectangle on 2010-07-14
umm... bump?

---

### Post by vbsteven on 2010-07-15
Try this script instead of the one on the gnome shell website.

[http://pastebin.com/JTEmsRne](http://pastebin.com/JTEmsRne)

This is a temporary fix so don't forget to check back from time to time to see if the original script is working.

---

