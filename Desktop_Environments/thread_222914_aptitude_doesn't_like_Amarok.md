---
title: "aptitude doesn't like Amarok"
date: 2006-07-25
forum: Desktop Environments
---

### Post by shane2peru on 2006-07-25
Ok, here is the problem.  **EVERYTIME** I try to run ```
sudo aptitude install Program
``` I always get this problem, no matter what I'm trying to install - ```
The following packages are unused and will be REMOVED:
  amarok amarok-engines amarok-xine libgpod0 synaptic
The following NEW packages will be installed:
  kcalc
0 packages upgraded, 1 newly installed, 5 to remove and 0 not upgraded.
Need to get 189kB of archives. After unpacking 31.6MB will be freed.

```  in the above example I was installing kcalc - a calculator that doesn't have anything to do with Amarok.  I use the ```
sudo apt-get install Program
``` and it installed it without a problem, no matter what program it is.  Is Aptitude really against Amarok?  What is the problem?

Shane

---

### Post by glinsvad on 2006-07-25
Eeh I'd worry more about aptitude trying to remove synaptic, but that's just me. Possibly it's a conflict between aptitude and some basic libraries.

Why don't you just use apt-get? I install everything from the commandline, but I've never needed aptitude...

---

### Post by aysiu on 2006-07-25
*aptitude* tries to be "smart." Most of the time it is. Clearly, here, it's dumb... or you have weird conflicting repositories.

---

### Post by shane2peru on 2006-07-25
Well, that is the point, I read that aptitude was better than apt-get that was the reason that I was using it.  I don't think I have weird sources.list, here it is: ```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
#deb-src ftp://cipherfunk.org/pub/packages/ubuntu dapper main

# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde-latest dapper main

# kubuntu.org packages for the latest KDE version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/kde-latest dapper main

# kubuntu.org packages for the latest Koffice version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/koffice-latest dapper main

# kubuntu.org packages for the latest Koffice version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/koffice-latest dapper main

# kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/amarok-latest dapper main

# kubuntu.org packages for the latest amaroK version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/amarok-latest dapper main

# Bleeding edge wine packages (packages)
deb http://wine.budgetdedicated.com/apt dapper main

# Bleeding edge wine packages (sources)
deb-src http://wine.budgetdedicated.com/apt dapper main

# Sound package
deb http://neogate.homelinux.org/debian/ dapper sound

 # Google Picasa for Linux repository
deb http://dl.google.com/linux/deb/ stable non-free


```  I do have the bleeding-edge amarok source, I don't know if that has anything to do with it.  Thanks for the input though.  I was thinking something was wrong.  I will stick with apt-get.

Shane

---

