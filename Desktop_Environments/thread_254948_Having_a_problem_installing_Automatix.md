---
title: "Having a problem installing Automatix"
date: 2006-09-10
forum: Desktop Environments
---

### Post by Tamacracker on 2006-09-10
Hey guys, I finally mounted my HDD correctly and am able to access my MP3s but the problem is... Amarok with XIne is not working, or atleast not playing my MP3s.

I decided to try Automatix, but come to find out... I can't even install it :-? 

So I go to the Automatix download page, follow the instructions for installtion.. 



tamacracker@tamacracker:~$ **sudo apt-get update**
Password:
E: Type 'http://www.getautomatix.com/apt/dist...pper1_i386.deb' is not known on line 39 in source list /etc/apt/sources.list
tamacracker@tamacracker:~$ wget [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)
--18:55:49--  [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)
           => `automatix-installer'
Resolving [www.getautomatix.com](www.getautomatix.com)... 82.165.194.143
Connecting to www.getautomatix.com|82.165.194.143|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9,256 (9.0K) [text/plain]

100%[====================================>] 9,256         --.--K/s

18:55:49 (108.56 KB/s) - `automatix-installer' saved [9256/9256]

tamacracker@tamacracker:~$ chmod 755 ~/automatix-installer
[B]tamacracker@tamacracker:~$ ./automatix-installer
pub   1024D/521A9C7C 2006-06-04
pub   1024D/437D05B5 2004-09-12
Codename:       dapper
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
E: Type 'http://www.getautomatix.com/apt/dist...pper1_i386.deb' is not known on line 39 in source list /etc/apt/sources.list
E: Type 'http://www.getautomatix.com/apt/dist...pper1_i386.deb' is not known on line 39 in source list /etc/apt/sources.list
E: The list of sources could not be read.
tamacracker@tamacracker:~$
[/B]


When I go to  the Synaptic Package Manager, I get this error:
[B]E: Type 'http://www.getautomatix.com/apt/dist...pper1_i386.deb' is not known on line 41 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.[/B]

---

### Post by croak77 on 2006-09-10
Can you post your /etc/apt/sources.list?

---

### Post by Tamacracker on 2006-09-11
> **croak77 said:**
> Can you post your /etc/apt/sources.list?



deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

#Givre's repository (ntfs-3g & fuse 2.5.3)
deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) dapper main
deb-src [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) dapper main

[B]deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
[/B]

---

