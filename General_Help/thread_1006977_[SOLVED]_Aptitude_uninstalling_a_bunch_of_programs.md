---
title: "[SOLVED] Aptitude uninstalling a bunch of programs"
date: 2008-12-09
forum: General Help
---

### Post by shortylonglegs on 2008-12-09
I am having a problem when I try to run aptitude full-upgrade.  Its trying to remove a bunch of programs.  I don't really know the intracasies of Ubuntu, but this doesn't look right to me.
```
$ sudo aptitude full-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following packages will be REMOVED:
  autoconf{u} autoconf2.13{u} automake1.4{u} automake1.7{u} autotools-dev{u} build-essential{u} cdbs{u} debhelper{u} diffstat{u} dpkg-dev{u} fakeroot{u} fdupes{u}
  gettext{u} html2text{u} intltool{u} intltool-debian{u} libart-2.0-dev{u} libatk1.0-dev{u} libaudiofile-dev{u} libavahi-client-dev{u} libavahi-common-dev{u}
  libavahi-glib-dev{u} libbonobo2-dev{u} libbonoboui2-dev{u} libcairo2-dev{u} libdbus-1-dev{u} libdbus-glib-1-dev{u} libesd0-dev{u} libexpat1-dev{u} libfontconfig1-dev{u}
  libfreetype6-dev{u} libgconf2-dev{u} libgcrypt11-dev{u} libglade2-dev{u} libglib2.0-dev{u} libgnome-keyring-dev{u} libgnome2-dev{u} libgnomecanvas2-dev{u}
  libgnomeui-dev{u} libgnomevfs2-dev{u} libgnutls-dev{u} libgpg-error-dev{u} libgtk2.0-dev{u} libhunspell-dev{u} libice-dev{u} libidl-dev{u} libjpeg62-dev{u}
  libmail-sendmail-perl{u} libnspr4-dev{u} libnss3-dev{u} liborbit2-dev{u} libpango1.0-dev{u} libpixman-1-dev{u} libpng12-dev{u} libpopt-dev{u} libpthread-stubs0{u}
  libpthread-stubs0-dev{u} libselinux1-dev{u} libsepol1-dev{u} libsm-dev{u} libsys-hostname-long-perl{u} libtasn1-3-dev{u} libx11-dev{u} libxau-dev{u}
  libxcb-render-util0-dev{u} libxcb-render0-dev{u} libxcb-xlib0-dev{u} libxcb1-dev{u} libxcomposite-dev{u} libxcursor-dev{u} libxdamage-dev{u} libxdmcp-dev{u}
  libxext-dev{u} libxfixes-dev{u} libxft-dev{u} libxi-dev{u} libxinerama-dev{u} libxml2-dev{u} libxrandr-dev{u} libxrender-dev{u} libxt-dev{u} m4{u} mozilla-devscripts{u}
  orbit2{u} patch{u} patchutils{u} po-debconf{u} quilt{u} sharutils{u} x11proto-composite-dev{u} x11proto-core-dev{u} x11proto-damage-dev{u} x11proto-fixes-dev{u}
  x11proto-input-dev{u} x11proto-kb-dev{u} x11proto-randr-dev{u} x11proto-render-dev{u} x11proto-xext-dev{u} x11proto-xinerama-dev{u} xtrans-dev{u} xulrunner-1.9-dev{u}
  zlib1g-dev{u}
The following packages will be upgraded:
  vinagre
1 packages upgraded, 0 newly installed, 102 to remove and 0 not upgraded.
Need to get 995kB of archives. After unpacking 120MB will be freed.
Do you want to continue? [Y/n/?]

```

Is this right?

---

### Post by DieB on 2008-12-10
why u use "full-upgrade"?

---

### Post by sayakb on 2008-12-10
Did you recently perform an upgrade? These should be the packages that were earlier installed and no longer needed.
Do they also show up when you try:
```
sudo apt-get autoremove
```
and
```
sudo aptitude safe-upgrade
```

---

### Post by shortylonglegs on 2008-12-10
I use full-upgrade because I was told at some point that is better, is safe-upgrade better?

The same set of packages appears with both commands, does this mean they are safe to remove?

---

### Post by bapoumba on 2008-12-10
Have you been using apt-get and aptitude?
They do not share log files, so what you installed with one, the other is not necessarily aware of.
Or there may be something with your sources.list
```
cat /etc/apt/sources.list
```

I use aptitude, and only aptitude, and perform full-upgrades on a regular basis (checks for dependencies more carefully, as apt-get dist-upgrade does).

---

### Post by shortylonglegs on 2008-12-10
I almost never use apt-get, and the only changes I've made to sources.lst was to add the Medibuntu and Wine repositories.

> 
# 
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted

#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse



---

