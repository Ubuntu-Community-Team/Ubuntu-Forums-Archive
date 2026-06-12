---
title: "Installing CGWD failed ..... Relp....!!!"
date: 2006-08-25
forum: Desktop Environments
---

### Post by savimonty on 2006-08-25
dpkg: error processing /var/cache/apt/archives/compiz-core_0.0.13.38-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/compiz.real', which is also in package compiz
dpkg-deb: subprocess paste killed by signal (Broken pipe)

---

### Post by Woei on 2006-08-25
> **savimonty said:**
> dpkg: error processing /var/cache/apt/archives/compiz-core_0.0.13.38-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/compiz.real', which is also in package compiz
dpkg-deb: subprocess paste killed by signal (Broken pipe)

Okay, let me try to 'Relp' you. ;) It seems you have a package conflict. You probably enabled various repositories that hold unofficial packages to enable all the new bling made possible by the compiz compositor and XGL/AIGLX servers. Note that they are unsupported, and that they may break at any point in time, although they usually revert back to a working state soon.

My guess is that in this case, you probably enabled two conflicting repositories. Please post the relevant lines from /etc/apt/sources.list here. Moreover, have you tried to remove the (probably stale) 'compiz' package by issuing something like apt-get remove --purge compiz, and then retrying what you're trying to do ?

---

### Post by savimonty on 2006-08-25
This is the sources.list file ... (w/o comments)

################################

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted]

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main

################################################################

**Well the purge option gave me the following errors :**

$ sudo apt-get remove --purge compiz
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  cgwd: Depends: compiz-plugins (>= 0.2) but it is not going to be installed or
                 compiz-vanilla but it is not going to be installed
  compiz-gnome: Depends: compiz (= 0.0.2-4ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

##############################################################3

**after trying apt-get -f install**

$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  compiz-core compiz-plugins
The following NEW packages will be installed:
  compiz-core compiz-plugins
0 upgraded, 2 newly installed, 0 to remove and 192 not upgraded.
1 not fully installed or removed.
Need to get 0B/626kB of archives.
After unpacking 2928kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 90847 files and directories currently installed.)
Unpacking compiz-core (from .../compiz-core_0.0.13.38-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-core_0.0.13.38-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/compiz.real', which is also in package compiz
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking compiz-plugins (from .../compiz-plugins_0.5-0ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-plugins_0.5-0ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libresize.so', which is also in package compiz
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-core_0.0.13.38-0ubuntu1_i386.deb
 /var/cache/apt/archives/compiz-plugins_0.5-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

###########################################################3

---

### Post by Woei on 2006-08-25
Well, the error messages definately point in the direction of a packaging conflict, although your repository sources seem fine. It's entirely possible the conflicting packages have been installed through repositories that have since been removed from the sources.conf file though.

Anyway, when dealing with problems like these, I *remove* all packages dpkg complains about. So in this case, apt-get remove --purge compiz-core. Then apt-get remove --purge compiz-plugins compiz. After that, you should be clear to install compiz-core again. The problem lies in the fact that compiz and compiz-core are two different packages, but both have approximately the same package contents, leading to the conflicts you're experiencing now.

---

### Post by savimonty on 2006-08-26
I understood the package conflict you explained ...!
But now I see there is a cyclic dependency problem here ...

Should I explicitly get rid of these installations? If so how?
Any solutions you can think of!

Thanks a lot!

Have a look below ...!

$ sudo apt-get remove --purge compiz-core
Password:
Reading package lists... Done
Building dependency tree... Done
Package compiz-core is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  cgwd: Depends: compiz-plugins (>= 0.2) but it is not going to be installed or
                 compiz-vanilla but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

$ sudo apt-get remove --purge compiz-plugins
Reading package lists... Done
Building dependency tree... Done
Package compiz-plugins is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  cgwd: Depends: compiz-plugins (>= 0.2) but it is not going to be installed or
                 compiz-vanilla but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by Woei on 2006-08-26
Just remove all the packages dpkg is complaining about. For instance, now you should remove cgwd and compiz-vanilla.

---

