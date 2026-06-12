---
title: "apt-get fix dependency problem"
date: 2006-01-03
forum: General Help
---

### Post by terriblynice on 2006-01-03
I am trying to install the analog web logfile analysis software but face dependency problems I can't fix.

**apt-get install analog** gives the following output :

Building dependency tree...
You might want to run âapt-get -f installâ to correct these:
The following packages have unmet dependencies:
  alsa-utils: Depends: python but it is not going to be installed
  bicyclerepair: Depends: python (< 2.5) but it is not going to be installed
                 Depends: python (>= 2.4) but it is not going to be installed
  bittorrent: Depends: python (< 2.5) but it is not going to be installed
              Depends: python (>= 2.4) but it is not going to be installed
  gimp-python: Depends: python (< 2.5) but it is not going to be installed
               Depends: python (>= 2.4) but it is not going to be installed
  gnome-app-install: Depends: python but it is not going to be installed
  gnome-btdownload: Depends: python (>= 2.4) but it is not going to be installed
                    Depends: python (< 3) but it is not going to be installed
  gnome-doc-utils: Depends: python (>= 2.4) but it is not going to be installed
                   Depends: python (< 3) but it is not going to be installed
  hal-device-manager: Depends: python (>= 2.4) but it is not going to be installed
                      Depends: python (< 3) but it is not going to be installed
  hplip-base: Depends: python (< 2.5) but it is not going to be installed
              Depends: python (>= 2.4) but it is not going to be installed
  hwdb-client: Depends: python (< 2.5) but it is not going to be installed
               Depends: python (>= 2.4) but it is not going to be installed
  language-selector: Depends: python but it is not going to be installed
  launchpad-integration: Depends: python (< 2.5) but it is not going to be installed
                         Depends: python (>= 2.4) but it is not going to be installed
  mailx: Depends: postfix but it is not going to be installed or
                  mail-transport-agent
  mutt: Depends: postfix but it is not going to be installed or
                 mail-transport-agent
  python-adns: Depends: python (< 2.5) but it is not going to be installed
               Depends: python (>= 2.4) but it is not going to be installed
  python-apt: Depends: python (< 2.5) but it is not going to be installed
              Depends: python (>= 2.4) but it is not going to be installed
  python-cddb: Depends: python (< 2.5) but it is not going to be installed
               Depends: python (>= 2.4) but it is not going to be installed
  python-clientcookie: Depends: python (>= 2.4) but it is not going to be installed
                       Depends: python (< 2.5) but it is not going to be installed
  python-crypto: Depends: python (< 2.5) but it is not going to be installed
                 Depends: python (>= 2.4) but it is not going to be installed
  python-docutils: Depends: python (>= 2.3) but it is not going to be installed
                   Depends: python (< 2.5) but it is not going to be installed
  python-egenix-mxproxy: Depends: python (< 2.5) but it is not going to be installed
                         Depends: python (>= 2.4) but it is not going to be installed
  python-egenix-mxstack: Depends: python (< 2.5) but it is not going to be installed
etc... loats of python- stuff

I try **apt-get -f install** but it suggests installing postfix.  I don't want this as I a have already installed qmail.

# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  postfix python
Suggested packages:
  postfix-mysql postfix-pgsql postfix-ldap postfix-pcre python-doc python-profiler
Recommended packages:
  resolvconf
The following NEW packages will be installed:
  postfix python
0 upgraded, 2 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/1039kB of archives.
After unpacking 2736kB of additional disk space will be used.
Do you want to continue [Y/n]?

Help much appreciated.

---

### Post by rjwood on 2006-01-03
post your ```
sudo gedit /etc/apt/sources.list
```file here.

---

### Post by terriblynice on 2006-01-03
[QUOTE=rjwood]post your ```
sudo gedit /etc/apt/sources.list
```file here.[/QUOTE]

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) breezy universe

---

### Post by ibook-linux on 2006-01-03
[QUOTE=terriblynice]
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) breezy universe[/QUOTE]

Try removing the # from these universe sites then run update. should fix it.

---

### Post by terriblynice on 2006-01-03
[QUOTE=ibook-linux]Try removing the # from these universe sites then run update. should fix it.[/QUOTE]

Changing the apt sources list as you suggest, gives the same error output.

---

### Post by rjwood on 2006-01-03
you may want to uncomment the backports as well. Good luck! You will probably have to remove the "gb" letters in the backport lines also

---

### Post by rjwood on 2006-01-03
try installing the dependencies yourself with apt-get. You don't have to do each one separately. When you enter sudo apt-get install 'name_of_file' just put a space between each file name and that should do it.

BTW in syaptic, you may have to hit the reload button or just do sudo apt-get update----------sudo apt-get upgrade  from a terminal

---

### Post by terriblynice on 2006-01-03
[QUOTE=rjwood]try installing the dependencies yourself with apt-get. You don't have to do each one separately. When you enter sudo apt-get install 'name_of_file' just put a space between each file name and that should do it.
[/QUOTE]

My apologies.  I haven't been very clear.  I am trying to install analog and apt-get is reporting dependency problems which prevent the installation of analog.  For example the python- dependencies noted above.  I don't need the python- things mentioned and therefore installing them to fix this problem seems... daft.

---

### Post by bonzodog on 2006-01-03
seperate hint: also, add the word multiverse to that sources.list, after where it says 'universe' (literally tag the word 'multiverse' to the end of those lines.) then do:

sudo apt-get update

you will find ALOT more software available.

---

