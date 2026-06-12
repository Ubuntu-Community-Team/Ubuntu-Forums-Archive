---
title: "Synaptic--DVD::RIP--Firestarter"
date: 2006-03-13
forum: Desktop Environments
---

### Post by eriefisher on 2006-03-13
I just finished downloading DVD::RIP about two hours ago. It took me over two hours to get including all dependencies and associated packages. I'm on dial up. Now I just tried to download Firestarter and it wants to remove DVD::RIP and Transcode. What could possibly be the association here? I can't see how these two programs could conflict with one another. Some insight would be welcomed.

eriefisher

---

### Post by puddpunk on 2006-03-13
```
chris@detritus:~$ sudo apt-cache show dvdrip
Package: dvdrip
Priority: optional
Section: multiverse/graphics
Installed-Size: 1656
Maintainer: Christian Marillat <marillat@debian.org>
Architecture: i386
Source: video-dvdrip
Version: 1:0.52.5-0.0
Depends: perl (>= 5.6.0-16), transcode (>= 2:0.6.14), perl-modules (>= 5.8.1-1) | libstorable-perl, libgtk-perl, libgtk-pixbuf-perl, imagemagick, fping, libevent-perl, liblocale-gettext-perl, libintl-perl, eject
Recommends: xine-ui, subtitleripper, dvdrip-doc
Suggests: mjpegtools, ogmtools (>= 0.972), cdrdao, mkisofs, cdrecord, vcdimager, mplayer, rar-2.80
**Conflicts: video-dvdrip (<= 0.50.18-0.0)**
Filename: pool/multiverse/v/video-dvdrip/dvdrip_0.52.5-0.0_i386.deb
Size: 374608
MD5sum: ee288334257ebec5f14f3d1c74db6c72
Description: perl front end for transcode
 dvd::rip is a full featured DVD copy program written in Perl. It provides
 an easy to use but feature-rich Gtk+ GUI to control almost all aspects of
 the ripping and transcoding process. It uses the widely known video
 processing swissknife transcode and many other Open Source tools.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

chris@detritus:~$ sudo apt-get install firestarter -s
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  firestarter
0 upgraded, 1 newly installed, 0 to remove and 52 not upgraded.
Inst firestarter (1.0.3-1.1ubuntu1 Ubuntu:5.10/breezy)
Conf firestarter (1.0.3-1.1ubuntu1 Ubuntu:5.10/breezy)
```

I have no conflict here... dialup eh? Try an apt-get update and get back to us in a week or so :D Just kidding.

Could you please paste the output of apt-cache show firestarter to see if it has any restrictions? The exact output of your apt-get install firestarter command would be helpful too.

---

### Post by eriefisher on 2006-03-14
It looks like a conflict with the version of libfame0.9 so this is what I get:


```
eriefisher@ubuntubox:~$ sudo apt-get install firestarter
Password:
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  transcode: Depends: libfame-0.9 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
eriefisher@ubuntubox:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libfame-0.9
The following NEW packages will be installed:
  libfame-0.9
0 upgraded, 1 newly installed, 0 to remove and 146 not upgraded.
25 not fully installed or removed.
Need to get 0B/77.7kB of archives.
After unpacking 319kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 88687 files and directories currently installed.)
Unpacking libfame-0.9 (from .../libfame-0.9_0.9.0-0.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libfame-0.9_0.9.0-0.1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libfame-0.9.so.0.0.0', which is also in package libfame0
Errors were encountered while processing:
 /var/cache/apt/archives/libfame-0.9_0.9.0-0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
eriefisher@ubuntubox:~$

```

How can I correct this conflict?

eriefisher

---

### Post by eriefisher on 2006-03-14
It looks like a version conflict with libfame. it seems the dvdrip wants a early version than whats already installed and now synaptic wants to remove it.

Can I have both?

eriefisher

---

### Post by eriefisher on 2006-03-14
Suggestions anyone??? I'm sure theres a simple solution here.

eriefisher

---

### Post by gingermark on 2006-03-15
[QUOTE=eriefisher]Suggestions anyone??? I'm sure theres a simple solution here.

eriefisher[/QUOTE]
Can you post the contents of you sources.list file (in /etc/apt) please? I have dvd:rip installed, and marked Firestarter without anything needing removing. I'm guessing you might have a debian repository messing things up.

Otherwise, whilst I appreciate you're on dial up, you could always try Guarddog. Guarddog and Firestarter are both graphical frontends for iptables, and Guarddog will look a bit better in KDE too.

---

### Post by eriefisher on 2006-03-15
Well here's my list, tell me what you think.

```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://ca.archive.ubuntu.com/ubuntu breezy main restricted
deb http://ca.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://ca.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://ca.archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://ca.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://ca.archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

# Seveas' packages (packages, GPG key: 1135D466)
deb http://mirror3.ubuntulinux.nl breezy-seveas all

# Seveas' packages (sources, GPG key: 1135D466)
deb-src http://mirror3.ubuntulinux.nl breezy-seveas all

# Ubuntu backports project (packages, GPG key: 437D05B5)
deb http://ca.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

# Ubuntu backports project (sources, GPG key: 437D05B5)
deb-src http://ca.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ breezy main

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
deb-src ftp://cipherfunk.org/pub/packages/ubuntu breezy main

# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde-latest breezy main

# kubuntu.org packages for the latest KDE version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/kde-latest breezy main

# kubuntu.org packages for the latest Koffice version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/koffice-latest breezy main

# kubuntu.org packages for the latest Koffice version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/koffice-latest breezy main

# kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/amarok-latest breezy main

# kubuntu.org packages for the latest amaroK version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/amarok-latest breezy main

# Penguin Liberation Front (packages)
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

# Penguin Liberation Front (sources)
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

# Bleeding edge wine packages (packages)
deb http://wine.sourceforge.net/apt/ binary/

# Bleeding edge wine packages (sources)
deb-src http://wine.sourceforge.net/apt/ source/

# OpenOffice.org 2 final packages (packages)
deb http://people.ubuntu.com/~doko/OOo2/ ./
```

Some insight would be welcomed.

eriefisher

---

### Post by Q4U on 2006-03-17
This is not exactly what you ask for, but I thought I would post my experience.

Firestarter is a GTK front-end to iptables, so if you want to install it on your Kubuntu, you will have to download a whole load of GTK related packages. 

When I did it, it caused a marked speed degradation and assorted wierdness, so I went to look for a QT front-end for Iptables. 

I found that Guarddog is very similar in function to Firestarter and plays much more nicely with Kubuntu.

Anyway, good luck with your problem. Q

---

### Post by gingermark on 2006-03-19
OK, your sources.list doesn't have any debian repositories in it. Damn. I have no idea what is causing the problem you are experiencing, as I can't reproduce the error on my system.

As far as your sources.list file goes, the one bit of advice I would give would be not to use the "all" section of Seveas' repository (see [https://wiki.ubuntu.com/SeveasPackages](https://wiki.ubuntu.com/SeveasPackages) for more info). Use the individual sections that you think you'll need.

Sorry I cannot provide an answer for your problem though.

---

