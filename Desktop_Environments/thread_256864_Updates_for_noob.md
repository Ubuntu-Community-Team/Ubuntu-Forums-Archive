---
title: "Updates for noob"
date: 2006-09-13
forum: Desktop Environments
---

### Post by alleykat on 2006-09-13
It says I have two updates ready but when I tried to install them it gives error message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

I installed automatrix, or tried to anyway, could this be the problem. I need help fast on this please.

---

### Post by lamego on 2006-09-13
Automatix does cause problems specially if you interrupt it.
First make sure you have a clean /etc/apt/sources.list :
```

# Automatically generated sources.list
# ftp://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb ftp://pt.archive.ubuntu.com/ubuntu dapper main restricted
deb ftp://pt.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb ftp://pt.archive.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src ftp://pt.archive.ubuntu.com/ubuntu dapper main restricted
deb-src ftp://pt.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src ftp://pt.archive.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb ftp://pt.archive.ubuntu.com/ubuntu dapper universe multiverse
deb ftp://pt.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb ftp://pt.archive.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src ftp://pt.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src ftp://pt.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src ftp://pt.archive.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src ftp://pt.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src ftp://pt.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src ftp://pt.archive.ubuntu.com/ubuntu dapper-security universe multiverse
```

Then open a terminal and run:
```
sudo apt-get update
sudo dpkg --configure -a
```

---

### Post by alleykat on 2006-09-13
Thank you for the reply, I am a total noob to this. Could you walk me thru it, I am not good with linux yet. I am trying to get off windoze.

---

### Post by alleykat on 2006-09-13
Plinked away till I think I have it working correctly. Thanks for the direction.

---

### Post by alleykat on 2006-09-13
OK guess it is not completely fixed, still get this error message when trying to update:

W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_multiverse_binary-i386_Packages)


So how do I fix this problem?

---

### Post by nrwilk on 2006-09-13
> **alleykat said:**
> So how do I fix this problem?

First, issue this command into your terminal:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

This command will backup your sources.list file in case we accidentally bork the changes we make.

now, open the sources.list file in gedit by issuing this commend:
```
sudo gedit /etc/apt/sources.list
```

When gedit opens, you can get rid of everything in the file and replace it with the following text.  Just copy and paste this stuff over whatever is in the file:
```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

## dapper-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

Save that file and close gedit.

Now issue this command again:
```
sudo aptitude update
```

You should not receive any further errors. :D 

nrwilk

---

### Post by alleykat on 2006-09-13
Thanks, I will give it a try and report back :)

---

### Post by alleykat on 2006-09-13
that seems to have fixed it..Thanks :)

---

### Post by nrwilk on 2006-09-13
> **alleykat said:**
> that seems to have fixed it..Thanks :)
No problem at all. :) 

You have also now enabled the universe and multiverse repositories, which gives you access to much more software.  This sources.list file should give you no problems at all.

nrwilk :D

---

