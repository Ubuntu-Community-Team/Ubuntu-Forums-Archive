---
title: "Can't get updates, help !!"
date: 2006-09-14
forum: Desktop Environments
---

### Post by Julian David Pitt on 2006-09-14
When updates are notified to me as being ready to install I click the install button and receive "Authentication Failure when running apt-get -u upgrade". I used to be able to carry on and install through update manager but now that is telling me there are no updates available. I use the same root password I use to log in so what is going wrong please. Thanks for your help in advance.

---

### Post by Ramses de Norre on 2006-09-14
What's the output when you run this: ```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by Julian David Pitt on 2006-09-15
> **Ramses de Norre said:**
> What's the output when you run this: ```
sudo aptitude update && sudo aptitude upgrade
```

Here is the output seems ok?
root@ubuntu:/home/julian # sudo aptitude update && sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
Writing extended state information... Done
Get:1 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [49.1kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [4269B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [16.4kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages [2035B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [12.1kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [964B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [2253B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources [533B]
Fetched 119kB in 2s (46.3kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  mozilla-firefox-locale-en-gb
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 713kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 172153 files and directories currently installed.)
Removing mozilla-firefox-locale-en-gb ...
root@ubuntu:/home/julian #

---

