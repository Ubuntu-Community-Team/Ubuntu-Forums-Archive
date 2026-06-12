---
title: "E: Package xxxxxxxx has no installation candidate"
date: 2006-03-05
forum: Desktop Environments
---

### Post by mikky on 2006-03-05
I resently installed ubuntu to create a server for various things (fileshare, web, ftp, music...), so pls bare in mind; I'm new

I am very pleased with the apt system, but the last few days every package I try to install, I get:
"E: Package *something* has no installation candidate"
except in those cases where get: 
"*something* is already the newest version."

My sources.list look like this:
-----------------------------
#deb cdrom:[Ubuntu 5.04 _hoary Hedgehog_ - Release i386 (20050407)]/ breezy main restricted

deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
-----------------------------

Please help
/Kim

---

### Post by knalle on 2006-03-05
looks like **dk.archive** is down, try **de.archive** or something

---

### Post by Ramses de Norre on 2006-03-05
Or just take out the dk's.

---

### Post by knalle on 2006-03-05
yeah, smite those danish! :-D

---

### Post by mikky on 2006-03-05
thanks, but it didn't help :(

I removed every reference to dk, and did this:
*kemo@badger:~$* cat /etc/apt/sources.list
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
*kemo@badger:~$* sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Fetched 3B in 3s (1B/s)
Reading package lists... Done
*kemo@badger:~$ sudo apt-get upgrade*
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
*kemo@badger:~$ sudo apt-get install gcc*
Reading package lists... Done
Building dependency tree... Done
Package gcc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gcc has no installation candidate
*kemo@badger:~$*

---

### Post by knalle on 2006-03-05
i think you need to say **gcc-3.4** or **gcc-4.0**, you might also want to add the world **multiverse** after every place it says **universe**

---

### Post by Ramses de Norre on 2006-03-05
sudo apt-get install gcc-3.4 gives the same?

EDIT: too late:)

---

### Post by knalle on 2006-03-05
owned! :-D

---

### Post by mikky on 2006-03-05
Ramses>Yes, its the same with gcc-3.4
[I]
kemo@badger:~$ sudo apt-get install gcc-3.4[/I]
Reading package lists... Done
Building dependency tree... Done
Package gcc-3.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gcc-3.4 has no installation candidate
*kemo@badger:~$*

---

### Post by mikky on 2006-03-05
knalle> I have had a multiverse entry in my sources.list, but removed it while trying to fix this problem. And really, gcc should be in "main"

---

### Post by Ramses de Norre on 2006-03-05
Try using this repo's: [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)
Maybe there is something wrong in your repo's but that's hard to see..

---

### Post by knalle on 2006-03-05
[QUOTE=mikky]knalle> I have had a multiverse entry in my sources.list, but removed it while trying to fix this problem. And really, gcc should be in "main"[/QUOTE]

definitely, i find it very strange that gcc isnt available too you

---

### Post by mikky on 2006-03-05
[QUOTE=Ramses de Norre]Try using this repo's: [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)
Maybe there is something wrong in your repo's but that's hard to see..[/QUOTE]

AHA, that worked!!!
thanks a bunce :)

I of cause was curious to know what the error was, so I did some comparing and we where actually on to something, knalle. gcc is in main, which was exactly what I was missing in my sources.list!!! DOH!!

Thanks again
/Kim

---

### Post by knalle on 2006-03-05
nice, good it worked out for you

---

