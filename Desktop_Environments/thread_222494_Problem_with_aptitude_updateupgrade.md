---
title: "Problem with aptitude update/upgrade"
date: 2006-07-25
forum: Desktop Environments
---

### Post by simone.brunozzi on 2006-07-25
Hi there,
I have the following problem:

This is my sources.list file:

```

##
deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/plf dapper free non-free
deb-src http://packages.freecontrib.org/plf dapper free non-free


```


first, I "aptitude update" the system:

```

root@simone-desktop:~# aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:4 http://archive.ubuntu.com dapper-backports Release.gpg [189B]
Ign http://packages.freecontrib.org dapper Release.gpg
Hit http://archive.ubuntu.com dapper Release
Get:5 http://security.ubuntu.com dapper-security Release [30.9kB]
Ign http://packages.freecontrib.org dapper Release
Get:6 http://archive.ubuntu.com dapper-updates Release [30.9kB]
Ign http://packages.freecontrib.org dapper/free Packages
Ign http://packages.freecontrib.org dapper/non-free Packages
Ign http://packages.freecontrib.org dapper/free Sources
Ign http://packages.freecontrib.org dapper/non-free Sources
Hit http://packages.freecontrib.org dapper/free Packages
Hit http://packages.freecontrib.org dapper/non-free Packages
Hit http://packages.freecontrib.org dapper/free Sources
Get:7 http://archive.ubuntu.com dapper-backports Release [19.6kB]
Hit http://packages.freecontrib.org dapper/non-free Sources
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Sources
Get:8 http://security.ubuntu.com dapper-security/main Packages [40.4kB]
Get:9 http://security.ubuntu.com dapper-security/restricted Packages [4275B]
Get:10 http://security.ubuntu.com dapper-security/universe Packages [6951B]
Get:11 http://security.ubuntu.com dapper-security/multiverse Packages [2041B]
Get:12 http://security.ubuntu.com dapper-security/main Sources [9872B]
Get:13 http://security.ubuntu.com dapper-security/restricted Sources [974B]
Get:14 http://security.ubuntu.com dapper-security/universe Sources [902B]
Get:15 http://security.ubuntu.com dapper-security/multiverse Sources [521B]
Hit http://archive.ubuntu.com dapper/multiverse Sources
Get:16 http://archive.ubuntu.com dapper-updates/main Packages [43.0kB]
Get:17 http://archive.ubuntu.com dapper-updates/restricted Packages [14B]
Get:18 http://archive.ubuntu.com dapper-updates/universe Packages [9372B]
Get:19 http://archive.ubuntu.com dapper-updates/multiverse Packages [866B]
Get:20 http://archive.ubuntu.com dapper-updates/main Sources [25.0kB]
Get:21 http://archive.ubuntu.com dapper-updates/restricted Sources [14B]
Get:22 http://archive.ubuntu.com dapper-updates/universe Sources [2224B]
Get:23 http://archive.ubuntu.com dapper-updates/multiverse Sources [427B]
Get:24 http://archive.ubuntu.com dapper-backports/main Packages [14B]
Get:25 http://archive.ubuntu.com dapper-backports/restricted Packages [14B]
Get:26 http://archive.ubuntu.com dapper-backports/universe Packages [14B]
Get:27 http://archive.ubuntu.com dapper-backports/multiverse Packages [14B]
Get:28 http://archive.ubuntu.com dapper-backports/main Sources [14B]
Get:29 http://archive.ubuntu.com dapper-backports/restricted Sources [14B]
Get:30 http://archive.ubuntu.com dapper-backports/universe Sources [14B]
Get:31 http://archive.ubuntu.com dapper-backports/multiverse Sources [14B]
Fetched 229kB in 6s (33.3kB/s)
Reading package lists... Done
root@simone-desktop:~#

```

but when I "aptitude upgrade" I encounter the following error:

```


root@simone-desktop:~# aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have unmet dependencies:
  j2re1.4-mozilla-plugin: Depends: j2re1.4 but it is not installable


```

How can I fix this problem?

Thanks in advance

---

### Post by philippe_carlo on 2006-07-25
Open up synaptic (System->Admin->Synaptic Package Mngr)

Use the search function for finding j2re1.4-mozilla-plugin and mark it for removal. Next, apply.

May I recommend [Easy Ubuntu]("http://easyubuntu.freecontrib.org/") for getting java plugins, media support and such working properly?

---

### Post by simone.brunozzi on 2006-07-25
Thanks, it was so banal I didn't think of it :-)

Cheers!

---

