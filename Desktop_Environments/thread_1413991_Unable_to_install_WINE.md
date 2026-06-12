---
title: "Unable to install WINE"
date: 2010-02-23
forum: Desktop Environments
---

### Post by raunhar on 2010-02-23
Ubuntu 9.10
While installing WINE through terminal, I get:
sudo add-apt-repository ppa:ubuntu-wine/ppa
[sudo] password for punnvs: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 883E8688397576B6C509DF495A9A06AEF9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: key F9CB8DB0: "Launchpad PPA for Ubuntu Wine Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1


WHat should be done to install WINE?

Pl. help

---

### Post by realzippy on 2010-02-23
You just added the repo.To install:

[B]sudo apt-get update
sudo apt-get install wine[/B]

---

### Post by raunhar on 2010-02-23
Tried. Got the following:
~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_IN               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_IN
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_IN
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Translation-en_IN
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/universe Translation-en_IN
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/universe Packages
Reading package lists... Done
~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages

---

### Post by realzippy on 2010-02-23
Got the keys?Try:

[B]wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/karmic.list](http://wine.budgetdedicated.com/apt/sources.list.d/karmic.list) -O /etc/apt/sources.list.d/winehq.list

sudo apt-get update
sudo apt-get install wine[/B]


Edit:
See that there is a 404 error...
But you can install the package manually from:

[http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)

---

### Post by raunhar on 2010-02-23
Tried through Synaptec, and selected Wine 1.2  Then it got through.

Thanks

---

