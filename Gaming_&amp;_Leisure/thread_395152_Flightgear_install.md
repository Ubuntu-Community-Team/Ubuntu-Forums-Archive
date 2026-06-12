---
title: "Flightgear install"
date: 2007-03-27
forum: Gaming &amp; Leisure
---

### Post by mr_tubaman2002 on 2007-03-27
Im at a complete loss, what package should i download from flightgear.org and how do I install it.  I am new to linux so the simplest way possible please.

---

### Post by 23meg on 2007-03-27
The simplest way would be to install it from the repositories. Make sure [the Universe repository is enabled]("https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html"), and then copy and paste the command below in a terminal:

```
sudo apt-get install flightgear
```

---

### Post by mr_tubaman2002 on 2007-03-27
I tried the apt-get but this is the message that came up, any suggestions

 
Package flightgear is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flightgear has no installation candidate

---

### Post by 23meg on 2007-03-27
Enable the Universe repository by following the instructions in the page I linked to.

---

### Post by mr_tubaman2002 on 2007-03-27
I have the universal repositories on now but now I get this message

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  flightgear: Depends: fgfs-base (>= 0.9.9) but it is not going to be installed
E: Broken packages

---

### Post by 23meg on 2007-03-27
What version of Ubuntu are you using?

Also post the contents of your /etc/apt/sources.list file.

---

### Post by mr_tubaman2002 on 2007-03-27
Im still running 6.06 (because of network problems with 6.10)

heres the .list


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
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by Perfect Storm on 2007-03-28
Make sure you run this comman after you made changes in your sourcelist;
```
sudo apt-get update
```


Check: [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) for complete sourcelist

Third option download the .deb from Ubuntu package storage:
[http://packages.ubuntu.com/dapper/games/flightgear](http://packages.ubuntu.com/dapper/games/flightgear)

---

### Post by mr_tubaman2002 on 2007-03-29
I did try the sudo apt-get update and still received the message that I stated above

---

### Post by Perfect Storm on 2007-03-30
Then use one of the two last options I shown.

---

