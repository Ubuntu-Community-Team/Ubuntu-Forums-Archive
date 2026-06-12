---
title: "Can't update to latest version"
date: 2006-09-01
forum: Desktop Environments
---

### Post by Deramin on 2006-09-01
I'm currently running Breezy Badger on an IBM T42 duel booted with XP. I cannot update to the latest Ubuntu release using the update manager. It suposedly downloads, it looks like some sort of install of message window pops up, but then the window disappears in less than a minute and no install ever happens. I don't even get an error message. Help?

---

### Post by jordanmthomas on 2006-09-01
Try running this in a terminal:

```
sudo apt-get update
sudo apt-get upgrade
```

Then, it will at least tell you why it is quitting.

---

### Post by Deramin on 2006-09-01
[COLOR=Black][I][COLOR=Green]Reading package lists... Done
 Building dependency tree... Done
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
 kat@d123-190:~$ sudo apt-get update
 Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
 Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
 Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release.gpg [189B]
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release
 Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
 Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages [14B]
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/universe Packages
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/multiverse Packages
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
 Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources [14B]
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages
 Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages [14B]
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Sources
 Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Sources [14B]
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Sources
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Sources
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
 Fetched 60B in 1s (42B/s)
 Reading package lists... Done
 kat@d123-190:~$ sudo apt-get upgrade
 Reading package lists... Done
 Building dependency tree... Done
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
 kat@d123-190:~$[/COLOR]
[/I]
That's that I get when I use those comands.[/COLOR]

---

### Post by John.Michael.Kane on 2006-09-01
Copy this soruce.list over your current one
```
sudo gedit /etc/apt/sources.list
```
```

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

```
Save the list then do
```
sudo aptitude update
```
follow by:
```
sudo aptitude dist-upgrade
```

This will get you the current ubuntu version dapper 6.06.1

---

### Post by Deramin on 2006-09-01
did all of the above and got the same results.

[COLOR="Green"][I]kat@d123-190:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Fetched 4B in 0s (4B/s)
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
kat@d123-190:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done[/I][/COLOR]

---

### Post by Deramin on 2006-09-01
ah, nevermind. It didn't save properly and was using the same repositories. Only noticed that after posting. XD

---

### Post by taurus on 2006-09-01
Replace the breezy with dapper in /etc/apt/sources.list!!!  :rolleyes:

---

