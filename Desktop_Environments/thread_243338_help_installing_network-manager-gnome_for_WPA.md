---
title: "help installing network-manager-gnome for WPA"
date: 2006-08-24
forum: Desktop Environments
---

### Post by cerkilr on 2006-08-24
Hello, please forgive me for i am new to ubuntu well (linux in general](*,) ](*,) ](*,) ). Anyways im trying to install, network-manager-gnome so i can attach to my WPA network, however i am getting an error with the apt-get install command, even update. its like is not going talk to the server, and im not sure what to do.

here is what my apt-get config file looks like.

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

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/plf dapper free non-free
deb-src http://packages.freecontrib.org/plf dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

```

even when i use SYSTEM > ADMINISTRATION > SYNAPTIC PACKET MANAGER
i click reload it trys to update, thena  error windows pops up and it says

```

Could not download all repository indexes

[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Connection failed [IP: 195.248.90.23 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Connection failed
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:) Connection failed [IP: 195.248.90.23 80]
[http://packages.freecontrib.org/plf/dists/dapper/Release.gpg:](http://packages.freecontrib.org/plf/dists/dapper/Release.gpg:) Connection failed
[http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg:](http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg:) Connection failed
[http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz:](http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz:) Connection failed
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:) Connection failed
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:) Connection failed
[http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz:) Connection failed
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:) Connection failed
[http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz:) Connection failed
[http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz:) Connection failed
[http://packages.freecontrib.org/plf/dists/dapper/free/source/Sources.gz:](http://packages.freecontrib.org/plf/dists/dapper/free/source/Sources.gz:) Connection failed
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:) Connection failed
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://packages.freecontrib.org/plf/dists/dapper/non-free/source/Sources.gz:](http://packages.freecontrib.org/plf/dists/dapper/non-free/source/Sources.gz:) Connection failed
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:) Connection failed
[http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:) Connection failed
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz:) Connection failed
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/source/Sources.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/source/Sources.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz:) Connection failed [IP: 195.248.90.23 80]

```

i hope this is enough info.
if there is anything else i can provide let me know.
THANKS
Cerkilr

---

### Post by meng on 2006-08-24
Have you got a working internet connection?

---

### Post by cerkilr on 2006-08-24
yes right now i am wired lan till i get this working

---

### Post by meng on 2006-08-24
And your connection is working for other purposes? Just need to make sure that that's not the reason for failing to connect to repositories.

---

### Post by cerkilr on 2006-08-24
yes i am posting to you from the laptop. the internet firefox is working.

---

### Post by meng on 2006-08-24
Then try from CLI
sudo apt-get update
sudo apt-get install network-manager
and see if you get the same error.

---

### Post by cerkilr on 2006-08-24
here is what it says.

```
cerkilr@linux-box:~$ sudo apt-get update
Password:
Err http://archive.canonical.com dapper-commercial Release.gpg
  Connection failed
Err http://security.ubuntu.com dapper-security Release.gpg
  Connection failed
Err http://archive.ubuntu.com dapper Release.gpg
  Connection failed [IP: 195.248.90.23 80]
Err http://packages.freecontrib.org dapper Release.gpg
  Connection failed
Ign http://archive.canonical.com dapper-commercial Release
Ign http://security.ubuntu.com dapper-security Release
Err http://archive.ubuntu.com dapper-updates Release.gpg
  Connection failed [IP: 195.248.90.23 80]
Ign http://packages.freecontrib.org dapper Release
Ign http://archive.canonical.com dapper-commercial/main Packages
Ign http://security.ubuntu.com dapper-security/main Packages
Err http://archive.ubuntu.com dapper-backports Release.gpg
  Connection failed [IP: 195.248.90.23 80]
Ign http://packages.freecontrib.org dapper/free Packages
Err http://archive.canonical.com dapper-commercial/main Packages
  Connection failed
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://archive.ubuntu.com dapper Release
Ign http://packages.freecontrib.org dapper/non-free Packages
Ign http://security.ubuntu.com dapper-security/universe Packages
Ign http://archive.ubuntu.com dapper-updates Release
Ign http://packages.freecontrib.org dapper/free Sources
Ign http://security.ubuntu.com dapper-security/multiverse Packages
Ign http://archive.ubuntu.com dapper-backports Release
Ign http://packages.freecontrib.org dapper/non-free Sources
Ign http://security.ubuntu.com dapper-security/main Sources
Ign http://archive.ubuntu.com dapper/main Packages
Err http://packages.freecontrib.org dapper/free Packages
  Connection failed
Ign http://security.ubuntu.com dapper-security/restricted Sources
Ign http://archive.ubuntu.com dapper/restricted Packages
Err http://packages.freecontrib.org dapper/non-free Packages
  Connection failed
Ign http://security.ubuntu.com dapper-security/universe Sources
Ign http://archive.ubuntu.com dapper/universe Packages
Err http://packages.freecontrib.org dapper/free Sources
  Connection failed
Ign http://security.ubuntu.com dapper-security/multiverse Sources
Ign http://archive.ubuntu.com dapper/multiverse Packages
Err http://packages.freecontrib.org dapper/non-free Sources
  Connection failed
Err http://security.ubuntu.com dapper-security/main Packages
  Connection failed
Ign http://archive.ubuntu.com dapper/main Sources
Err http://security.ubuntu.com dapper-security/restricted Packages
  Connection failed
Ign http://archive.ubuntu.com dapper/restricted Sources
Err http://security.ubuntu.com dapper-security/universe Packages
  Connection failed
Ign http://archive.ubuntu.com dapper/universe Sources
Err http://security.ubuntu.com dapper-security/multiverse Packages
  Connection failed
Ign http://archive.ubuntu.com dapper/multiverse Sources
Err http://security.ubuntu.com dapper-security/main Sources
  Connection failed
Ign http://archive.ubuntu.com dapper-updates/main Packages
Err http://security.ubuntu.com dapper-security/restricted Sources
  Connection failed
Ign http://archive.ubuntu.com dapper-updates/restricted Packages
Err http://security.ubuntu.com dapper-security/universe Sources
  Connection failed
Ign http://archive.ubuntu.com dapper-updates/universe Packages
Err http://security.ubuntu.com dapper-security/multiverse Sources
  Connection failed
Ign http://archive.ubuntu.com dapper-updates/multiverse Packages
Ign http://archive.ubuntu.com dapper-updates/main Sources
Ign http://archive.ubuntu.com dapper-updates/restricted Sources
Ign http://archive.ubuntu.com dapper-updates/universe Sources
Ign http://archive.ubuntu.com dapper-updates/multiverse Sources
Ign http://archive.ubuntu.com dapper-backports/main Packages
Ign http://archive.ubuntu.com dapper-backports/restricted Packages
Ign http://archive.ubuntu.com dapper-backports/universe Packages
Ign http://archive.ubuntu.com dapper-backports/multiverse Packages
Ign http://archive.ubuntu.com dapper-backports/main Sources
Ign http://archive.ubuntu.com dapper-backports/restricted Sources
Ign http://archive.ubuntu.com dapper-backports/universe Sources
Ign http://archive.ubuntu.com dapper-backports/multiverse Sources
Err http://archive.ubuntu.com dapper/main Packages
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper/restricted Packages
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper/universe Packages
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper/multiverse Packages
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper/main Sources
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper/restricted Sources
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper/universe Sources
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper/multiverse Sources
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper-updates/main Packages
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper-updates/restricted Packages
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper-updates/universe Packages
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper-updates/multiverse Packages
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper-updates/main Sources
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper-updates/restricted Sources
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper-updates/universe Sources
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper-updates/multiverse Sources
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper-backports/main Packages
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper-backports/restricted Packages
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper-backports/universe Packages
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper-backports/multiverse Packages
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper-backports/main Sources
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper-backports/restricted Sources
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper-backports/universe Sources
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper-backports/multiverse Sources
  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://packages.freecontrib.org/plf/dists/dapper/Release.gpg  Connection failed
Failed to fetch http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg  Connection failed
Failed to fetch http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz  Connection failed
Failed to fetch http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz  Connection failed
Failed to fetch http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz  Connection failed
Failed to fetch http://packages.freecontrib.org/plf/dists/dapper/free/source/Sources.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz  Connection failed
Failed to fetch http://packages.freecontrib.org/plf/dists/dapper/non-free/source/Sources.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/source/Sources.gz  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/source/Sources.gz  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz  Connection failed [IP: 195.248.90.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz  Connection failed [IP: 195.248.90.23 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
cerkilr@linux-box:~$

```

](*,) ](*,)

---

### Post by meng on 2006-08-24
Argh. It's difficult to find an obvious answer. This may help, or not.
[http://ubuntuforums.org/showthread.php?t=206692](http://ubuntuforums.org/showthread.php?t=206692)

---

### Post by cerkilr on 2006-08-24
thank you very much meng that helped.

---

