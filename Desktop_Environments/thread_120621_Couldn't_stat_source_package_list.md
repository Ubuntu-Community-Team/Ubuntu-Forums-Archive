---
title: "Couldn't stat source package list"
date: 2006-01-23
forum: Desktop Environments
---

### Post by lgmdaniel on 2006-01-23
I keep getting this odd error when I do update and installs, using apt-get.
I guess it means that some of my links to the data reposities could be wrong but I'm not sure what it should be or even where I should look.....

```
daniel@Grinch:~$ sudo apt-get install sensors applet
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package sensors
daniel@Grinch:~$
```

---

### Post by mips on 2006-01-23
You are not the only one, sure we'll figure it out soon enough. 
No time now though as I'm setting up a fresh install of Kubuntu on my PC, got rid of Ubuntu and made some space for OpenBSD & FreeBSD.

---

### Post by towsonu2003 on 2006-01-23
```
sudo apt-get update
``` while online (or have install cd inserted) then try installing those again... 
> stat (2 No such file or directory) says it couldn't find the server (I believe). if apt-get update doesn't help while your online, check your network connection (browse web working?) and try again a couple of hours later. if still not working, attach your sources.list here for people to look at.

---

### Post by mips on 2006-01-23
That does not work and the network is fine.
```

W: Couldn't stat source package list http://za.archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/za.archive
.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://za.archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/za.arc
hive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

```

---

### Post by aysiu on 2006-01-23
Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by mips on 2006-01-23
This only happens for the backport repos. If I change them to the US ones it still does the same.

```
deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb http://za.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://za.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://za.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://za.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://za.archive.ubuntu.com/ubuntu breezy universe
deb-src http://za.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://za.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://za.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

## KDE 3.5
deb http://kubuntu.org/packages/kde35 breezy main
```

---

### Post by aysiu on 2006-01-23
Can you try this?

1. Back up your sources.list ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

2. Edit your sources.list ```
sudo kwrite /etc/apt/sources.list
```

3. Replace your entire sources.list with this instead ```
#deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

## KDE 3.5
deb http://kubuntu.org/packages/kde35 breezy main
``` Then save and ```
sudo apt-get update
``` Any difference?

---

### Post by mips on 2006-01-23
Like I said above it does not matter if I change the repos, it still does it but i tried again anyway and the results were the same....

sudo apt-get update:
```
Fetched 4198kB in 2m12s (31.6kB/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packag                  es.gz  MD5Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz                    MD5Sum mismatch
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```
sudo apt-get upgrade:
```
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
```

Anybody else experiencing this  ???

---

### Post by lgmdaniel on 2006-01-23
Mine apears to be all ok now.. so it must have been a issue with the remote repositries..

---

### Post by bschuteker on 2006-01-24
I am having same exact problem. I followed the instructions from aysiu and still get errors.

bill@ubuntu-bill:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages [2304kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
99% [5 Packages bzip2 4575232] [Waiting for headers]                18.5kB/s 0s
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
  Sub-process bzip2 returned an error code (2)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Fetched 214kB in 43s (4956B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


Any help is appreciated.

---

### Post by aysiu on 2006-01-24
I'm really baffled as to why multiple people are experiencing problems with those sources.

I use those sources on my own computer and *sudo apt-get update* every day and haven't experienced problems for months now connecting to the servers.

Can someone more knowledgeable than I explain what's going on?

---

### Post by Turin Turambar on 2006-01-24
Although I'm using Ubuntu without the K, I have similar problems... :confused: 

```
Get:8 http://us.archive.ubuntu.com breezy-updates/main Packages [25.1kB]
99% [8 Packages gzip 0]
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com breezy-updates/main Packages
  Sub-process gzip returned an error code (1)
Fetched 59.4kB in 26s (2250B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
ivan@ubuntu-ivan:~$
ivan@ubuntu-ivan:~$

```

---

### Post by roach of discord on 2006-01-24
Same problem.  Recently, those sources just stopped working..=(

---

### Post by Turin Turambar on 2006-01-24
I fixed it. Just removed the "us" prefix in the address (it was a mirror) and it works now!

---

### Post by epretorious on 2006-01-25
[QUOTE=Turin Turambar]I fixed it. Just removed the "us" prefix in the address (it was a mirror) and it works now![/QUOTE]
Thanks, Turin. That worked for me too!

---

