---
title: "Any idea why &quot;wine&quot; wants to remove so many packages?"
date: 2021-09-06
forum: Desktop Environments
---

### Post by scorp123 on 2021-09-06
I'm a bit puzzled by this :confused:

Does anyone have any idea why installing **"wine"** would want to remove so many other packages??

```
> sudo apt --simulate install wine

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  brasero-cdrkit dvdauthor folks-common gconf-service gconf-service-backend
  gconf2 gconf2-common geoip-database gir1.2-champlain-0.12 gir1.2-clutter-1.0
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-geoclue-2.0
  gir1.2-geocodeglib-1.0 gir1.2-gfbgraph-0.2 gir1.2-gtkchamplain-0.12
  gir1.2-gtkclutter-1.0 gir1.2-gweather-3.0 gir1.2-json-1.0 gir1.2-rest-0.7
  gparted-common libamd2 libbabl-0.1-0 libcamd2 libccolamd2
  libchamplain-0.12-0 libchamplain-gtk-0.12-0 libcholmod3 libde265-0
  libevent-2.1-7 libexporter-tiny-perl libfile-readbackwards-perl libfltk1.3
  libfm-extra4 libfolks-eds25 libfolks25 libgconf-2-4 libgegl-0.4-0
  libgegl-common libgeoip1 libgexiv2-2 libgfbgraph-0.2-0 libgimp2.0
  libgmime-3.0-0 libgtkglext1 libgtkmm-2.4-1v5 libhd21 libheif1
  libhttp-parser2.9 libilmbase24 liblist-moreutils-perl libmbedcrypto3
  libmbedtls12 libmbedx509-0 libmenu-cache-bin libmessaging-menu0 libmetis5
  libminizip1 libmypaint-common libnatpmp1 libnetaddr-ip-perl libopenexr24
  libostree-1-1 libpangox-1.0-0 libregexp-assemble-perl libsigsegv2
  libtracker-sparql-2.0-0 libumfpack5 libx86emu2 lightpad
  linux-headers-5.4.0-80 nautilus-extension-brasero transmission-common
  xdg-desktop-portal xdg-desktop-portal-gtk
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  fonts-wine libfaudio0 libgpg-error-l10n libstb0 libvkd3d1 libwine wine64
Suggested packages:
  cups-bsd gstreamer1.0-plugins-bad q4wine winbind winetricks playonlinux
  wine-binfmt dosbox exe-thumbnailer | kio-extras wine64-preloader
Recommended packages:
  libcapi20-3 libodbc1 libosmesa6 wine32
The following packages will be REMOVED:
  aha anydesk apt-file balena-etcher-electron bat brasero brltty
  budgie-clipboard-applet budgie-lightpad-applet chkservice cups-bsd dropbox
  filters flatpak gawk geary geoip-bin gimp gnome-mahjongg gnome-maps go-mtpfs
  google-chrome-stable gparted htop hwinfo inetutils-traceroute inputattach
  kerneloops libapt-pkg-perl libc6-dbg libfltk-images1.3 libgit2-28
  libmenu-cache3 libmng2 libmypaint-1.5-1 libpcre2-32-0 libytnef0
  linux-headers-5.4.0-80-generic mesa-utils ncftp nitrogen nmon nxproxy
  openbox-menu procinfo ripgrep seahorse sg3-utils smartmontools sqlite3
  thunderbird tig tigervnc-standalone-server tigervnc-viewer tint2 tmux
  transmission-gtk ubuntu-budgie-desktop whowatch x2goclient zsys
The following NEW packages will be installed:
  fonts-wine libfaudio0 libgpg-error-l10n libstb0 libvkd3d1 libwine wine
  wine64
0 upgraded, 8 newly installed, 61 to remove and 0 not upgraded.
```

I imagine this must be some kind of bug??   I don't remember **"wine"** doing this before ... ](*,)

---

### Post by rsteinmetz70112 on 2021-09-06
Have you done a release upgrgade recently often after a 
```
$ do-release-upgrade
``` a lot of old packages are left over due to changes in the release. 
Have you routinely used apt autoremove to remove unnecessary packages? These may be left over unremoved packages.
What happens if you;
```
$ sudo apt autoremove --simulate
```?

---

### Post by scorp123 on 2021-09-06
> **rsteinmetz70112 said:**
> Have you done a release upgrgade recently 

No, I'm still on Ubuntu Budgie 20.04.  I never do in-place upgrades, they just never work for me.

```
> cat /etc/lsb-release
 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=20.04
DISTRIB_CODENAME=focal
DISTRIB_DESCRIPTION="Ubuntu 20.04.3 LTS"
```

```
> apt --simulate autoremove

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by deadflowr on 2021-09-06
Does only wine do that or do other packages list so much to remove when trying to install them?
(or when you simulate to install them)

---

### Post by scorp123 on 2021-09-06
> **deadflowr said:**
> Does only wine do that 

Yes. Only wine.

Someone on "Reddit" mentioned installing "aptitude" and trying a
```
sudo aptitude install wine64
```

... as that would generate more useful error messages.

Looks to me like "wine" is unhappy with the version of **libc6** that is installed on my system.

...
```
The following actions will resolve these dependencies:

     Remove the following packages:                                        
1)     libc-dev-bin [2.31-0ubuntu9.3 (now)]                                

     Install the following packages:                                       
2)     libc-dev-bin:i386 [2.31-0ubuntu9.2 (focal-updates)]                 

     Downgrade the following packages:                                     
3)     libc6 [2.31-0ubuntu9.3 (now) -> 2.31-0ubuntu9.2 (focal-updates)]    
4)     libc6-dbg [2.31-0ubuntu9.3 (now) -> 2.31-0ubuntu9.2 (focal-updates)]
5)     libc6-dev [2.31-0ubuntu9.3 (now) -> 2.31-0ubuntu9.2 (focal-updates)]

Accept this solution? [Y/n/q/?]
```

Looks to me like "wine" wants "libc6" to be in version 2.31-0ubuntu9.2 ... but I have 2.31-0ubuntu9.3

```
> apt show -a libc6

Package: libc6
Version: 2.31-0ubuntu9.3
Status: install ok installed
Priority: required
Section: libs
Source: glibc
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
Installed-Size: 13.6 MB
Depends: libgcc-s1, libcrypt1 (>= 1:4.4.10-10ubuntu4)
Recommends: libidn2-0 (>= 2.0.5~)
Suggests: glibc-doc, debconf | debconf-2.0, locales
Conflicts: openrc (<< 0.27-2~)
Breaks: hurd (<< 1:0.9.git20170910-1), iraf-fitsutil (<< 2018.07.06-4), libtirpc1 (<< 0.2.3), locales (<< 2.31), locales-all (<< 2.31), nocache (<< 1.1-1~), nscd (<< 2.31), r-cran-later (<< 0.7.5+dfsg-2), wcc (<< 0.0.2+dfsg-3)
Replaces: libc6-amd64
Homepage: https://www.gnu.org/software/libc/libc.html
Original-Vcs-Browser: https://salsa.debian.org/glibc-team/glibc
Original-Vcs-Git: https://salsa.debian.org/glibc-team/glibc.git
Download-Size: unknown
APT-Manual-Installed: no
APT-Sources: /var/lib/dpkg/status
Description: GNU C Library: Shared libraries
 Contains the standard libraries that are used by nearly all programs on
 the system. This package includes shared versions of the standard C library
 and the standard math library, as well as many others
```

What do you guys get when you try to install "wine"?  And what version of "libc6" is on your system?

---

### Post by ActionParsnip on 2021-09-06
what is the output of:
```

apt-cache policy wine

```

---

### Post by scorp123 on 2021-09-06
Voilà :

```
> apt-cache policy wine
wine:
  Installed: (none)
  Candidate: 5.0-3ubuntu1
  Version table:
     5.0-3ubuntu1 500
        500 [http://ch.archive.ubuntu.com/ubuntu](http://ch.archive.ubuntu.com/ubuntu) focal/universe amd64 Packages
        500 [http://ch.archive.ubuntu.com/ubuntu](http://ch.archive.ubuntu.com/ubuntu) focal/universe i386 Packages
```

---

### Post by scorp123 on 2021-09-06
So I changed my main repositories from the Swiss mirrors (ch.archive.ubuntu.com) to the German mirrors (de.archive.ubuntu.com) because those are often more reliable.

The result is that now I get shown a newer "wine" version:

```
> apt --simulate install wine

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine64 (>= 5.0-3ubuntu1) but it is not going to be installed or
                 wine32 (>= 5.0-3ubuntu1)
        Depends: wine64 (< 5.0-3ubuntu1.1~) but it is not going to be installed or
                 wine32 (< 5.0-3ubuntu1.1~)
```

There was no "wine" version 5.0-3ubuntu1.1 before, only 5.0-3ubuntu1

So when I try to install that it complains about broken dependencies and suggests other packages that need to be installed. In the interest of keeping this post short I will jump to the end, the last command I ended up with trying:

```
> apt --simulate install wine64 libwine wine32 libfaudio0 libvkd3d1 libc6:i386 libwine:i386

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libc6 : Breaks: libc6:i386 (!= 2.31-0ubuntu9.3) but 2.31-0ubuntu9.2 is to be installed
 libc6:i386 : Breaks: libc6 (!= 2.31-0ubuntu9.2) but 2.31-0ubuntu9.3 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

I have no "held" packages:

```
apt-mark showhold
```
... prints nothing.

So this really comes down to "libc6" and "libc6:i386" disagreeing with "wine" about which version needs to be installed.

```
 libc6 : Breaks: libc6:i386 (!= 2.31-0ubuntu9.3) but 2.31-0ubuntu9.2 is to be installed
 libc6:i386 : Breaks: libc6 (!= 2.31-0ubuntu9.2) but 2.31-0ubuntu9.3 is to be installed
```

One package wants to be in version 2.31-0ubuntu9.3... the other wants to be 2.31-0ubuntu9.2. And they mutually break each other?? ](*,)

---

### Post by scorp123 on 2021-09-06
I found the reason.  There's indeed a bug with **libc6** and a faulty patch that has been revoked.

**Bug report:**
[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/1926918]("https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/1926918")

**Solution:**
Downgrade **libc6** back down to version **2.31-0ubuntu9.2** ... it will also remove these packages:

```

build-essential will be removed
g++ will be removed
g++-9 will be removed
libc6-dbg will be removed
libc6-dev will be removed
libexpat1-dev will be removed
libpython3-dev will be removed
libpython3.8-dev will be removed
libstdc++-9-dev will be removed
python3-dev will be removed
python3.8-dev will be removed
zlib1g-dev will be removed
```

... but those are easy to reinstall afterwards.

After this **"wine"** will install without complaining and deleting half the system!

```
> apt --simulate install wine

... output cut ...
The following additional packages will be installed:
... output cut ...

0 upgraded, 264 newly installed, 0 to remove and 0 not upgraded.
```

Yay!!  No more removing totally unrelated packages! :D

---

