---
title: "apt-get configuration error"
date: 2007-08-01
forum: Dell  Ubuntu Support
---

### Post by g0sp3L on 2007-08-01
My PC died, so I decided to install Kubuntu on this old Inspiron 1100 laptop of mine. Pretty much immediately after installing and rebooting, I tried to run Adept to update. It prompted me for my root password and then it gave me this message.

"The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem."

apt-setup gives me "Command Not Found" and using apt-get update gives me this message:

"E: Type 'apt-get' is not known on line 1 in source list /etc/apt/sources.list"

I'm completely new to Linux, so forgive me if this is something simple. :confused:

---

### Post by strabes on 2007-08-01
You have a messed up line in your /etc/apt/sources.list file.

Open a [terminal](http://www.psychocats.net/ubuntu/terminal) and run the following command: ```
kdesu kwrite /etc/apt/sources.list
```

Select everything in that file (Ctrl+A) and replace it with this: ```
# 
# deb cdrom:[Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417)]/ feisty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
```

Save it (Ctrl+S) and close kedit. In the terminal window, run these commands:```
sudo apt-get update
sudo apt-get upgrade
```

You don't really need to use the clumsy gui package manager that comes with kubuntu (adept) to upgrade your packages. Once you become a little more comfortable with the terminal you'll realize how much easier and more efficient it is. Hope this helps.

---

