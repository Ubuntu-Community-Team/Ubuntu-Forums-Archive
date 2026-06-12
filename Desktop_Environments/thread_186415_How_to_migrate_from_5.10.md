---
title: "How to migrate from 5.10"
date: 2006-06-01
forum: Desktop Environments
---

### Post by SwaroopKunduru on 2006-06-01
Hi All,

I installed UBUNTU5.10 a month ago and I wanted to upgrade it to 6.06 and I don't want 5.10 anymore. Please help me how can I do this.

Regards.

Swaroop Kunduru.

---

### Post by aysiu on 2006-06-01
[http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

---

### Post by SwaroopKunduru on 2006-06-01
aysiu,

In the page you posted, in step 1 what is my choice? I am using Gnome.

Regards,

Swaroop Kunduru.

---

### Post by kh4nh on 2006-06-01
sudo aptitude update
sudo aptitude install ubuntu-desktop

---

### Post by SwaroopKunduru on 2006-06-01
sudo aptitude install ubuntu-desktop

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
Initializing package states... Done

..................... IS it done?

---

### Post by SwaroopKunduru on 2006-06-01
in second step it asked to replace breezy. When I give the command below

gksudo gedit /etc/apt/sources.list

It opened an empty file.

Please suggest me what to do now?

Regards,

Swaroop.

---

### Post by SwaroopKunduru on 2006-06-01
gksudo gedit /etc/apt/sources.list

(gedit:8131): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by rcarring on 2006-06-02
Hmmm

try terminal session

try once loaded

sudo nano /etc/apt/sources.list

if you careful:

cd /etc/apt/
ls
sudo cp sources.list sources.list.old
sudo nano sources.list

(do the edit)

Ctrl-O to save
Ctrl-X to quit nano

Why use aptitude? Any good reason?

sudo apt-get dist-upgrade

watch that terminal fly

overwrite all conf files -- hal especially.

---

### Post by kh4nh on 2006-06-02
there should be a sources.list file in /etc/apt directory. If there is none or the file is empty, create one. 

sudo gedit /etc/apt/sources.list,
copy and paste the follwing in

##########################################
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by kh4nh on 2006-06-02
[QUOTE=rcarring]Hmmm

Why use aptitude? Any good reason?

.[/QUOTE]

I heard and read somewhere on this forum that when you install smth and then remove it later on, aptitude will remove the pakage plus all the dependencies for that. apt-get just simply removes the package itself and leaves behind dependencies.

---

### Post by SwaroopKunduru on 2006-06-02
rcarring,

I don't know about aptitude I am following the link in this posts-reply. 

Also I had changed the values in the list file to dapper from breezy still I did not get any result please see the result as follows

 sudo apt-get dist-upgrade

Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

The file have lines starting with # and some lines have ## I did not delete # or ## because I thought they are required.

Regards,

Swaroop Kunduru

---

### Post by kh4nh on 2006-06-02
can you post the content of sources.list file,

---

### Post by SwaroopKunduru on 2006-06-02
See the result. 

sudo apt-get dist-upgrade


Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_dapper-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_dapper-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_dapper-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_dapper-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

---

### Post by SwaroopKunduru on 2006-06-02
My source.list  file


deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by kh4nh on 2006-06-02
ok, check this out [http://www.psychocats.net/ubuntu/sources]("http://www.psychocats.net/ubuntu/sources")

---

