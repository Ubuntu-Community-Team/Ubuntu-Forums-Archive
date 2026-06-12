---
title: "Lost the ability for apt-get"
date: 2005-08-16
forum: Desktop Environments
---

### Post by raven on 2005-08-16
I lost apt-get, my browser is working
but I lost my system and I am trying to revive it from the ashes
old tread [http://www.ubuntuforums.org/showthread.php?p=304832#post304832](http://www.ubuntuforums.org/showthread.php?p=304832#post304832)
where I can download apt-get so I can install it and start 
rebuilding all lost packeges

---

### Post by GreyFox503 on 2005-08-16
I would try to install some basic ones from debian.org like dpkg and apt.  apt is the package that actually gives you 'apt-get' functionality it seems.

These both depend on a lot of other packages, it seems, so hopefully you still have them.  I don't know how bad you messed up your system.

[http://packages.debian.org/stable/base/dpkg](http://packages.debian.org/stable/base/dpkg)
[http://packages.debian.org/stable/base/apt](http://packages.debian.org/stable/base/apt)

EDIT: I just read your other thread  :shock: 

The Ubuntu install CD has all those packages on it somewhere, maybe you could use that instead.. it would be easier than downloading them.

---

### Post by jasmuz on 2005-08-16
Well if you still have the Install CD you can access your CDROM drive, then its in 

/pool/main/a/apt

Then just type sudo dpkg -i *.*

Or via internet @ [http://archive.ubuntu.com/ubuntu/pool/main/a/apt/](http://archive.ubuntu.com/ubuntu/pool/main/a/apt/)

just download all the debs for your platform and then sudo dpkg all of them :)

---

### Post by raven on 2005-08-16
I am trying to do a miracle here
no I can not mount anything cdrom or others, no filemanager working
when ever I use this command
sudo dpkg -i apt-utils_0.6.40.1ubuntu1_i386.deb
I get this error

" (Reading database ... 63812 files and directories currently installed.)
Preparing to replace apt-utils 0.6.40.1ubuntu1 (using apt-utils_0.6.40.1ubuntu1_i386.deb) ...
Unpacking replacement apt-utils ...
dpkg (subprocess): unable to execute old post-removal script: No such file or directory
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new post-removal script: No such file or directory
dpkg: error processing apt-utils_0.6.40.1ubuntu1_i386.deb (--install):
 subprocess new post-removal script returned error exit status 2
dpkg (subprocess): unable to execute new post-removal script: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 apt-utils_0.6.40.1ubuntu1_i386.deb"

but this error comes when ever I try to install apt-utils_0.6.40.1ubuntu1_i386.deb
or any other packages I will get dependecies errors for other packages
ex: libc6
I can only use internet for now 
the moment I close this browser I will loose all contact
the system is in a prety bad shape, nothing is working except my open apps
the moment I close they would not function anymore
what it seems to me that I need are the most basic packages
I can get them only from the net
and Thanx for the replys

---

