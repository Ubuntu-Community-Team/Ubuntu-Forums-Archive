---
title: "make help"
date: 2006-01-10
forum: Desktop Environments
---

### Post by jaywatkins on 2006-01-10
Hello,

I am trying to do some installs (ClamAV).  I keep getting hung up on the make part.  "The make command is not found", that is what I get.  I tried to obtain it from Add New Programs, but it was not found.  How does one obtain this elusive program?  Is there a system search tool that I could use to find it on my filesystem?

Thanks

- Jason

---

### Post by timfrost on 2006-01-10
There is a meta-package caled build-essential, which pulls in the make program, as well as compiler and other tools.

If you are trying to rebuild clamav from the ubuntu source package, try the following
```

sudo apt-get install buuld-essential 
apt-get source clamav
sudo apt-get install build-dep clamav

```
However, you should not need to build clamav, as it is available in universe

---

### Post by aysiu on 2006-01-10
Applications > Accessories > Terminal ```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by bikeman on 2006-01-10
If make is not installed, you can install it from terminal by typing (enter your user password when prompted to sudo, or switch user to root first and run the follwoing without the "sudo"):

sudo apt-get update
sudo apt-get install make

Daniel

---

### Post by jaywatkins on 2006-01-10
Thanks for the input, but no dice. ClamAV was not found.

---

### Post by carlosqueso on 2006-01-10
make sure you have the universe and multiverse repositories installed.  Go to a terminal and type ```
sudo gedit /etc/apt/sources.lst
``` and it should look like this:```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 
```  This is from Aisu's sig...but is also the one I use (I just couldn't copy mine cause I'm at work. After you change that, save it, and run the following from a terminal ```
sudo apt-get update
sudo apt-get install clamav
``` and you won't have to worry about make or any of that (plus you get automated updates).

---

### Post by aysiu on 2006-01-10
[QUOTE=jaywatkins]Thanks for the input, but no dice. ClamAV was not found.[/QUOTE] I thought you were compiling it from source. If you're trying to install it through apt-get, first get extra repositories (see the first link of my signature). Then, ```
sudo apt-get update
sudo apt-get install clamav
```

---

### Post by jaywatkins on 2006-01-10
Thanks for the suggestions.  I will try them out.

Thanks...

---

### Post by jaywatkins on 2006-01-11
I got ClamAV installed, getting it to parse the clamd.conf file is another matter!

Thanks for all of the suggestions...

---

### Post by jaywatkins on 2006-01-11
Package dependency failed with the Konsole install of ClamAV, updates and scans will not work as well.

Thanks for the suggestions

---

### Post by daschl on 2006-01-11
are you able to post the logfile / output?

maybe

$ command > errorlog


then it will be easier to find out whats wrong and we are able to solve the problem :)

---

