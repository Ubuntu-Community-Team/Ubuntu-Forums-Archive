---
title: "Cannot Install Xubuntu from Kubuntu Dapper [Resolved]"
date: 2007-01-15
forum: Desktop Environments
---

### Post by snowdonkey on 2007-01-15
Hey.  I'm up running with Kubuntu but I would like to install Xubuntu and use it instead because my PC is an old Pentium III with 550Mhz and 226 RAM.

Every time I try to install Xubuntu here's what I get:

```
<username>:~$ sudo apt-get install xubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xubuntu-desktop
```

I made sure to open Universe and Multiverse repositories in Adept and verified by checking the sources.list file.

Also, when I search for "xfce" or "xubuntu-desktop" or just "desktop" no Xubuntu installation even appears in Adept.  The only package that seems possible is "xfce4"; Description: "installs XFCE4 core and its scripts to set it up"

I would just download an ISO for Xubuntu Live CD but all the servers are in Europe and require 24+ hours for me to download.

Am I missing something?  Thanks for your help.

---

### Post by goatflyer on 2007-01-15
Please post your sources.lst

xubuntu-desktop is definitely in the repos, current version is 1.32

---

### Post by snowdonkey on 2007-01-15
Here's my source.list file:


# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted 
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted 
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main 
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by NeoLithium on 2007-01-15
I found this bare repo list set up from Ubuntuguide.org for you, should work out nicely:

```

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

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

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

```

---

### Post by snowdonkey on 2007-01-15
Still no luck.  

NeoLithium, I replaced the old sources.list with the one you supplied from ubuntuguide.org but still APT still can't find "xubuntu-desktop".  A search for "xubuntu" in Adpet still yields no results at all.

For "Match" I have package name and description checked.  

The Adpet satus bar reads "install 0 upgrade 0 remove 0; 937 installed 0 upgradable 937 available"

Is it possible there was an error during Kubuntu installation?

---

### Post by aysiu on 2007-01-15
After you make a change to your /etc/apt/sources.list, you need to run the command ```
sudo aptitude update
``` before you can take advantage of the change and ```
sudo aptitude install xubuntu-desktop
```

---

### Post by snowdonkey on 2007-01-15
aysiu, it's downloading!  Now I know I have to update the package list every time I edit sources.list.  Makes sense.  :-/

Thanks a lot guys, I really appreciate the fast responses and useful suggestions.

---

### Post by NeoLithium on 2007-01-15
No problemo :)

---

