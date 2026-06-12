---
title: "Installed 6.06 again and now have dependancy problems"
date: 2006-09-02
forum: Desktop Environments
---

### Post by theslut on 2006-09-02
I put back on 6.06 after the crash last week as it never fully recovered with certain things.

All went great until I tried to compile amarok 1.4.2 when i couldn't get the kde libraries installed because anything i tried complained of lots of dependancy problems (to be honest i've barely seen them since being a ubuntu user for 2-3 months).

I thought this was bad luck with KDE being upgraded but now i'm trying to compile dc++ with scons and I cannot get the gtk dev libs on with the same kind of errors

```

ibgtk2.0-dev:
  Depends: libgtk2.0-0 (=2.8.17-1ubuntu5) but 2.8.20-0ubuntu1 is to be installed
 Depends: libglib2.0-dev but it is not going to be installed
 Depends: libpango1.0-dev but it is not going to be installed
 Depends: libatk1.0-dev but it is not going to be installederrors

```

The only thing I've done to the machine since the reisntall was put on easyubuntu.

---

### Post by taurus on 2006-09-02
Use synaptic and it will take care of other dependencies for you...

---

### Post by theslut on 2006-09-03
I am using synaptic and thats exactly where the problem lies.

---

### Post by bulldog on 2006-09-03
You can try sudo aptitude to solve some problems.
I'm not sure however if you could get things straighten up.

It will come with some solutions and you make the choice what to do.

Example

sudo aptitude update
sudo aptitude dist-upgrade

and see what comes out of it.

---

### Post by theslut on 2006-09-03
it doesn't help at all i'm afraid.

```

No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

when i go to synaptic and try to install libgtk2.0-dev i get this

```

libgtk2.0-dev:
  Depends: libgtk2.0-0 (=2.8.17-1ubuntu5) but 2.8.20-0ubuntu1 is to be installed
 Depends: libglib2.0-dev but it is not going to be installed
 Depends: libpango1.0-dev but it is not going to be installed
 Depends: libatk1.0-dev but it is not going to be installed

```

is my repisitory list broken?  what should it be?

i tried commenting some lines to see if it helped but it didnt

```

#deb http://se.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
#deb http://packages.freecontrib.org/plf/ dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

deb http://se.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
#
# ##deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
##deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb http://se.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
#deb-src http://se.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb http://se.archive.ubuntu.com/ubuntu/ dapper universe
#deb-src http://se.archive.ubuntu.com/ubuntu/ dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://se.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://se.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
#deb http://security.ubuntu.com/ubuntu dapper-security main restricted
#deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
#deb http://security.ubuntu.com/ubuntu dapper-security universe
#deb-src http://security.ubuntu.com/ubuntu dapper-security universe
#deb http://kubuntu.org/packages/kde-354 dapper main

```

I'd rather not reisntall the system if possible,

---

