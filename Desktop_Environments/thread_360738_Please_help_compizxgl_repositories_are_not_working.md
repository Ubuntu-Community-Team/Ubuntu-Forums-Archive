---
title: "Please help compiz/xgl repositories are not working."
date: 2007-02-13
forum: Desktop Environments
---

### Post by jacensolo on 2007-02-13
I'm trying to install something but this is what it says

> Err [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release.gpg
  Could not connect to xgl.compiz.info:80 (195.14.0.203). - connect (111 Connection refused)
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Get:5 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Fetched 5B in 6s (1B/s)
Failed to fetch [http://xgl.compiz.info/dists/dapper/Release.gpg](http://xgl.compiz.info/dists/dapper/Release.gpg)  Could not connect to xgl.compiz.info:80 (195.14.0.203). - connect (111 Connection refused)
Reading package lists... Done


Here's my sources.list
 > 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
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
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main 
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main



What could be the problem?

Thanks for any help.

---

### Post by taurus on 2007-02-13
Edit /etc/apt/sources.list 

```
gksudo gedit /etc/apt/sources.list
```
and put a # in front of the last two lines.  Save it and run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by jacensolo on 2007-02-13
> **taurus said:**
> Edit /etc/apt/sources.list 

```
gksudo gedit /etc/apt/sources.list
```
and put a # in front of the last two lines.  Save it and run

```
sudo aptitude update
sudo aptitude upgrade
```

:confused:  I want that. That's what I'm trying to download.

---

### Post by dannyboy79 on 2007-02-13
i didn't think that compiz and xgl were even around anymore? I thought beryl or whatever took it's place? well at least per this, you can get them from normal repos, you don't get them from the xgl or beerokid repo's anymore.

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29)

---

### Post by muguwmp67 on 2007-02-13
```

deb http://xgl.compiz.info/ dapper main
deb http://www.beerorkid.com/compiz/ dapper main
```

Try editing these so they read:
```

deb http://www.beerorkid.com/compiz/ dapper main aiglx
deb http://xgl.compiz.info/ dapper main aiglx

```

Although, if you aren't trying to use xgl/compiz, do what jacensolo said and comment them out.

---

### Post by jacensolo on 2007-02-13
> **dannyboy79 said:**
> i didn't think that compiz and xgl were even around anymore? I thought beryl or whatever took it's place? well at least per this, you can get them from normal repos, you don't get them from the xgl or beerokid repo's anymore.

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29)
I'll try it.

---

### Post by jacensolo on 2007-02-13
> **jacensolo said:**
> I'll try it.

This is what happened

```
killian@SuperLinux:~$ sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome
Reading package lists... Done
Building dependency tree... Done
libgl1-mesa is already the newest version.
xserver-xorg is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-plugins (>= 0.2) but it is not going to be installed
E: Broken packages

```

---

### Post by jacensolo on 2007-02-13
I can't use Beryl because I can't upgrade to edgy because my wi-fi doesn't work in edgy. Would using aiglx and compiz be a better idea?

---

### Post by jacensolo on 2007-02-14
*bump*

---

