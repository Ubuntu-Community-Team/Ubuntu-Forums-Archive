---
title: "W: Couldn't stat source package list cdrom:?"
date: 2006-04-11
forum: Desktop Environments
---

### Post by dief-eh? on 2006-04-11
hello

<newbie alert>

sudo apt-get update keeps generating the following error. googling/forum searching isn't showing any hits. can anyone suggest where/how i could search to find out what the error is trying to tell me?

W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

!!! thanks in advance.

---

### Post by taurus on 2006-04-11
You need to comment out the line that has your CD-ROM, usually the first line in /etc/apt/source.list.  Open a terminal, Applications -> Accessories -> Terminal and type
```

sudo gedit /etc/apt/sources.list

```

---

### Post by dief-eh? on 2006-04-11
thank you for your reply. 

[QUOTE=taurus]You need to comment out the line that has your CD-ROM, usually the first line in /etc/apt/source.list.  Open a terminal, Applications -> Accessories -> Terminal and type
```

sudo gedit /etc/apt/sources.list

```[/QUOTE]

$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy Release.gpg [189B]
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27.0kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/main Sources
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [45.7kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/restricted Sources
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [14.0kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [26.1kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [14.5kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [1353B]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Fetched 154kB in 4s (35.4kB/s)
Reading package lists... Done
dfa2@workhorse2:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

... seems to have worked. thanks again.

---

