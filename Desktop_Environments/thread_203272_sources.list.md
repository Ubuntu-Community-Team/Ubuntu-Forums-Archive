---
title: "sources.list"
date: 2006-06-25
forum: Desktop Environments
---

### Post by azray on 2006-06-25
I went looking in /etc/apt for a sources.list file. The only like file is labeled sources.list.d It appears empty. I did the sudo apt-get update command in terminal and it appeared to work o.k. I don't think I have a legitimate sourses.list filew and it is the probable cause why Add/de;ete doesn't work. Suggestions?

---

### Post by Winblowz on 2006-06-25
Do this... 
```
nano /etc/apt/sources.list
```
You said that there is nothing in your sources.list, so put this in it...
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free 
```
Then...
```
sudo apt-get update
```
Hopefully that'll solve your problem:cool:

---

### Post by hippy4life on 2006-06-25
or you can use this

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

to generate a new sources.list just cut and paste the output to /etc/apt/sources.list and voila

---

### Post by azray on 2006-06-25
yeah team, I now have a sourses.list and add/remove works! Thanks!

---

### Post by hippy4life on 2006-06-26
Wicked!

:D

---

### Post by ubuntu_demon on 2006-06-29
**my recommended Dapper sources.list**
[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

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

## Cipherfunk multimedia packages (GPG key: 33BAC1B3)
## only uncomment it if you need it
## deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main
## deb-src ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

## Dapper PLF
## only uncomment it if you need it
## deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
## deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free

## Bleeding edge (official) wine repository for Dapper
## only uncomment it if you need it
## deb http://wine.budgetdedicated.com/apt dapper main
## deb-src http://wine.budgetdedicated.com/apt dapper main

## skype 
## only uncomment it if you need it
## deb http://download.skype.com/linux/repos/debian/ stable non-free

```

---

