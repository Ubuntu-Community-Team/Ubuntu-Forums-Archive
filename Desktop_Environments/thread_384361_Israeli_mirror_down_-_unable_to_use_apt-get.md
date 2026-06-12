---
title: "Israeli mirror down - unable to use apt-get"
date: 2007-03-14
forum: Desktop Environments
---

### Post by aceblue on 2007-03-14
Hey guys,
I'm kinda new to the linux world, and i started with ubuntu with kubuntu on it for the kde desktop environment.
it was all fine until the israeli server was deleted, out of date, or I don't know what happened to it,
any way, i can't use apt-get for anything, all i get is 404 errors from the israeli mirror, and the process stops.
i've tried to change the mirror in the sources.list file, to eu.archive.ubuntu.com, but some files are still downloaded from the il.archive.ubuntu.com mirror.

adding a printout of my last try of "apt-get update":
```

root@eli-desktop:/home/eli# apt-get update
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Ign http://il.archive.ubuntu.com edgy Release.gpg
Ign http://il.archive.ubuntu.com edgy/universe Translation-en_US
Ign http://il.archive.ubuntu.com edgy-updates Release.gpg
Ign http://il.archive.ubuntu.com edgy-updates/universe Translation-en_US
Ign http://il.archive.ubuntu.com edgy Release
Ign http://il.archive.ubuntu.com edgy-updates Release
Ign http://il.archive.ubuntu.com edgy/universe Packages
Ign http://il.archive.ubuntu.com edgy-updates/universe Packages
Err http://il.archive.ubuntu.com edgy/universe Packages
  404 Not Found [IP: 192.116.202.128 80]
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]
Ign http://security.ubuntu.com edgy-security/main Translation-en_US
Ign http://flomertens.keo.in dapper Release.gpg
Err http://il.archive.ubuntu.com edgy-updates/universe Packages
  404 Not Found [IP: 192.116.202.128 80]
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US
Hit http://security.ubuntu.com edgy-security Release
Ign http://flomertens.keo.in dapper/main Translation-en_US
Hit http://security.ubuntu.com edgy-security/main Packages
Get:2 http://eu.archive.ubuntu.com edgy Release.gpg [191B]
Ign http://eu.archive.ubuntu.com edgy/main Translation-en_US
Ign http://eu.archive.ubuntu.com edgy/restricted Translation-en_US
Hit http://security.ubuntu.com edgy-security/restricted Packages
Hit http://security.ubuntu.com edgy-security/main Sources
Hit http://security.ubuntu.com edgy-security/restricted Sources
Ign http://flomertens.keo.in dapper/main-all Translation-en_US
Hit http://security.ubuntu.com edgy-security/universe Packages
Get:3 http://eu.archive.ubuntu.com edgy-updates Release.gpg [191B]
Ign http://eu.archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://eu.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Get:4 http://eu.archive.ubuntu.com edgy Release [34.7kB]
Ign http://flomertens.keo.in dapper Release
Ign http://flomertens.keo.in dapper/main Packages
Ign http://flomertens.keo.in dapper/main-all Packages
Get:5 http://eu.archive.ubuntu.com edgy-updates Release [38.4kB]
Get:6 http://eu.archive.ubuntu.com edgy/main Packages [940kB]
Hit http://flomertens.keo.in dapper/main Packages
Hit http://flomertens.keo.in dapper/main-all Packages
Get:7 http://archive.ubuntu.com edgy Release.gpg [191B]
Ign http://archive.ubuntu.com edgy/universe Translation-en_US
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_US
Hit http://archive.ubuntu.com edgy Release
Hit http://archive.ubuntu.com edgy/universe Packages
Hit http://archive.ubuntu.com edgy/multiverse Packages
Get:8 http://eu.archive.ubuntu.com edgy/restricted Packages [5974B]
Get:9 http://eu.archive.ubuntu.com edgy/main Sources [274kB]
Get:10 http://eu.archive.ubuntu.com edgy/restricted Sources [1436B]
Get:11 http://eu.archive.ubuntu.com edgy-updates/main Packages [64.5kB]
Get:12 http://eu.archive.ubuntu.com edgy-updates/restricted Packages [14B]
Get:13 http://eu.archive.ubuntu.com edgy-updates/main Sources [19.9kB]
Get:14 http://eu.archive.ubuntu.com edgy-updates/restricted Sources [14B]
Fetched 1379kB in 34s (39.9kB/s)
Failed to fetch http://il.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz  404 Not Found [IP: 192.116.202.128 80]
Failed to fetch http://il.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz  404 Not Found [IP: 192.116.202.128 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

couldn't find anywhere on how to change the mirror other than sources.list which didn't helped me that much as you can see...

any ideas?

thanks a bunch guys.

---

### Post by zvacet on 2007-03-14
If you use Edgy go >system>administration>software repositories(or something like that),and you can choose between local and main server.Try with main.

---

### Post by MasterOfMuppets on 2007-03-14
Or, if you really wanna understand how your box works, you can change stuff in /etc/apt/sources.lst . I changed the Israeli repos to Finland's :D

---

### Post by Kateikyoushi on 2007-03-14
Are you sure the repo is down ? It happens that although apt get can't connect to it you can ping or open it in your browser.
Then you can either change to another server or change your sources.list entries from http to ftp.

---

### Post by MasterOfMuppets on 2007-03-19
Tried that, Finland's repos are faster :)...

---

