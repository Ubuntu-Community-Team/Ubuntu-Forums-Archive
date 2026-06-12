---
title: "apt-get error"
date: 2006-03-16
forum: Desktop Environments
---

### Post by ESPOiG on 2006-03-16
wen i try to install the nvidia drivers i get an error msg saying
'Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-settings/nvidia-settings_1.0-3ubuntu_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-settings/nvidia-settings_1.0-3ubuntu_i386.deb) Temporary failure resolving 'au.archive.ubuntu.com'

now this happens alot with things, even though i connected to the net and have enabled the multiverse and universe repositores with the 'etc/apt/sources.list' *i never added text, just removed the # symbol from the front of the location, i hope that is right

it seems to me it is having trouble accessing the australian archive of ubuntu files and things, so i dont know wat is goin on

is it possible to edit my 'sources.list' to some other countries one like the UK or suumthing and see if it happens with that to

my net is 1.5mb ADSL, and i cant access WAP sites (prob doesnt matter but i have noticed that i cant access WAP sites with OPERA, wen my mate who has the same plan and ISP (internet service provider) can, so i dunno if that helps, if anyone needs more info plz reply 

this bugs me :D, ESPOiG

---

### Post by PhoenixP3K on 2006-03-17
You could edit your etc/apt/sources.list and change some of the au.archive.ubuntu.com for archive.ubuntu.com .

It tryed this once because I couldn't get a lock on ca.archive.ubuntu.com So i figured going to the main sub-domain might work. I cannot confirm if this did make it work or the server was just down for a few minutes. Doesn't hurt to try.

---

### Post by ESPOiG on 2006-03-17
ive been to Toronto :P... thx ill try that

---

### Post by ESPOiG on 2006-03-17
k i tried that... it prob works but i think i know wat the main error is now... it is the link for 'security.ubuntu.com' all the error messages that i get wen i try to do 'sudo apt-get update' and do the ubuntu updates, and program say sumtin to do with 'security.ubuntu.com'

one of them that is common is this

'Couldn't stat source package list [http://secuirty.ubuntu.com](http://secuirty.ubuntu.com) breezy-secuirty/universe Packages (var/lib/apt/lists/secuirt/ubuntu.com_ubuntu_dists_breezy-security_universe_binary-1386_Packages) - stat (2 No such file or directory)

the universe value is also sumtimes 'main' as well

do i need this file or directory created and y is this happening it is causing me concern :D

thx, ESPOiG

---

### Post by ESPOiG on 2006-03-17
neone plz cuz i need this fixed :D

it happens on my laptop to :(


> Password:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy Release.gpg
  Temporary failure resolving 'au.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates Release.gpg
  Temporary failure resolving 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-backports Release.gpg
  Temporary failure resolving 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Temporary failure resolving 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  Temporary failure resolving 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg)  Temporary failure resolving 'au.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg)  Temporary failure resolving 'security.ubuntu.com'
Reading package lists... Done
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


---

### Post by ESPOiG on 2006-03-17
neone help ME!!!!!!!!!

---

### Post by PhoenixP3K on 2006-03-17
Are you behind some kind of firewalled router that would block certain ports? I mean none of your sources work. Here is the sources.list of with added repositories
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
## You may replace "us" with your country code to get the closest mirror.

deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## MAJOR BUG FIX UPDATES produced after the final release
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

## UNIVERSE AND MULTIVERSE REPOSITORY (Unsupported by Ubuntu.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf breezy free non-free 
```

My guess is that your **au** mirror is dead. Change it to **us**, slower download perhaps, but might work. In order to replace your sources.list file with the one above use **sudo gedit /etc/apt/sources.list**

---

### Post by claes on 2006-03-18
What does your /etc/resolv.conf look like?
It should have a line like this:
nameserver ip_address

Try and ping the ip_address to me it looks like name resolution that's the problem.

Claes

---

### Post by bonjun on 2006-03-18
maybe you can try this:

make a copy/backup of your source.list
then empty source.list
then do an update by "sudo apt-get update"

then get your source.list backup,, again do an update


it works for me.

---

### Post by ESPOiG on 2006-03-18
i looked at that ip and pinged it... worked fine :D

then i i wiped my sources.list ran 'sudo apt-get update', then put it bak :D... and ran sudo apt-get update again and this is wat happened on my laptop... ill try my desktop in a min :D

> ross@LaptopUbuntu:~$ sudo apt-get update
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Ign [http://www.morphix.org](http://www.morphix.org) ./ Release.gpg
Get:1 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Ign [http://www.morphix.org](http://www.morphix.org) ./ Release
Get:6 [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release [110B]
Get:7 [http://kubuntu.org](http://kubuntu.org) breezy Release [1793B]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release [30.9kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27.0kB]
Ign [http://www.morphix.org](http://www.morphix.org) ./ Packages
Ign [http://kubuntu.org](http://kubuntu.org) breezy Release
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Get:10 [http://www.morphix.org](http://www.morphix.org) ./ Packages
35% [10 Packages gzip 0] [8 Release 10080/30.9kB 32%] [9 Release 8640/27.0kB 31
gzip: stdin: unexpected end of file
Err [http://www.morphix.org](http://www.morphix.org) ./ Packages
  Sub-process gzip returned an error code (1)
Get:11 [http://kubuntu.org](http://kubuntu.org) breezy/main Packages [83.7kB]
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Get:12 [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages [1101B]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [30.9kB]
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [43.9kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources [232kB]
Get:17 [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages [639B]
Get:18 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [13.4kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources [1454B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources [915kB]
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [29.3kB]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [4750B]
Get:26 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Get:27 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Get:28 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages [2304kB]
Get:30 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Get:31 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Get:32 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages [545B]
Get:33 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages [2337B]
Get:34 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources [316B]
Get:35 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources [473B]
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages [585kB]
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages [5061B]
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages [91.6kB]
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages [36.0kB]
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [17.5kB]
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Get:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [14.0kB]
Get:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [26.1kB]
Get:46 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [1353B]
Fetched 4526kB in 38s (117kB/s)
Failed to fetch [http://www.morphix.org/debian/./Packages.gz](http://www.morphix.org/debian/./Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


---

### Post by ESPOiG on 2006-03-18
seemed to be fine this time on the desktop pc... but i still have problems with security.ubuntu.com

and now with archive.ubuntu.com :( this is so shit

---

