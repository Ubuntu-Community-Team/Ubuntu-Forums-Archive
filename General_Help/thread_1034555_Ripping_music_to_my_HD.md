---
title: "Ripping music to my HD"
date: 2009-01-08
forum: General Help
---

### Post by imtheguido on 2009-01-08
All right. So now I want to rip some music from my CD's to my Hard Drive. I have tried doing this with the media player that the system provides. No luck. I have tried to do it with Amarok... impossible. So after looking into other programs, I found Sound-Juicer. The only problem is, I have to compile the program from source. I am very aggravated at the moment, considering I literally have no clue how to compile anything. I look at the directions, and they make no sense to me. I don't know all the different commands off the top of my head, and the walk through doesn't give detailed commands for me to put into the terminal, so I am completely and utterly lost. I have one night to do this as I am moving over 1,000 miles away and cannot take these CD's with me, just my external HD. If I could get some help with this, it would be GREATLY appreciated. Thanks.

---

### Post by dcstar on 2009-01-08
> **imtheguido said:**
> All right. So now I want to rip some music from my CD's to my Hard Drive. I have tried doing this with the media player that the system provides. No luck. I have tried to do it with Amarok... impossible. So after looking into other programs, I found Sound-Juicer. The only problem is, I have to compile the program from source. 
.......

There is no need whatsoever to compile anything, all of these are in the repositories.

**Grip** is a handy program for ripping CDs.

---

### Post by imtheguido on 2009-01-08
I installed the sound-juicer from the package manager, and it is giving me an error whenever I try to rip the music from the CD:

```
** (sound-juicer:14291): WARNING **: Error getting media type
```

So I figured I had an old version installed or something.And what is Grip?

---

### Post by logos34 on 2009-01-08
yep, in the repos.  


so do 

sudo apt-get install sound-juicer

get the suggested pkgs too (and restricted stuff for mp3 etc):

sudo apt-get install ubuntu-restricted-extras gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly

[https://help.ubuntu.com/community/CDRipping#Sound%20Juicer](https://help.ubuntu.com/community/CDRipping#Sound%20Juicer)

good luck

> 
Package: sound-juicer
Priority: optional
Section: gnome
Installed-Size: 4892
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Original-Maintainer: Ross Burton <ross@debian.org>
Architecture: 
Version: 2.22.0-1ubuntu2
Depends: gconf2 (>= 2.10.1-2), gstreamer0.10-gnomevfs, gstreamer0.10-plugins-base, gstreamer0.10-plugins-good, hal, libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.20.0), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6 (>= 2.4), libcairo2 (>= 1.5.18), libcdio7, libdbus-1-3 (>= 1.1.1), libdbus-glib-1-2 (>= 0.74), libexpat1 (>= 1.95.8), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libgcc1 (>= 1:4.1.1-21), libgconf2-4 (>= 2.13.5), libglade2-0 (>= 1:2.6.1), libglib2.0-0 (>= 2.16.0), libgnome-media0, libgnome2-0 (>= 2.17.3), libgnomecanvas2-0 (>= 2.11.1), libgnomeui-0 (>= 2.17.1), libgnomevfs2-0 (>= 1:2.17.90), libgnomevfs2-extra, libgstreamer-plugins-base0.10-0 (>= 0.10.3), libgstreamer0.10-0 (>= 0.10.14), libgtk2.0-0 (>= 2.12.0), libhal1, libice6 (>= 1:1.0.0), liblaunchpad-integration1 (>= 0.1.17), libmusicbrainz4c2a (>= 2.1.5), libnautilus-burn4, liborbit2 (>= 1:2.14.10), libpango1.0-0 (>= 1.20.1), libpixman-1-0, libpng12-0 (>= 1.2.13-4), libpopt0 (>= 1.10), libsm6, libstdc++6 (>= 4.1.1-21), libtag1c2a (>= 1.4), libx11-6, libxml2, libxrender1, zlib1g (>= 1:1.2.3.3.dfsg-1)
Recommends: eject
Suggests: gstreamer0.10-plugins-bad, gstreamer0.10-plugins-ugly
Filename: pool/main/s/sound-juicer/sound-juicer_2.22.0-1ubuntu2_amd64.deb
Size: 1176198
MD5sum: f40f350f9c8856c54aa387a3cb0436d8
SHA1: 46660272ef3bc2594075b5a813c4be6101c7fba5
SHA256: 5b83dfd8254fba52ef6a3d9049dd262beafc7b9304ba250161998477adcdc81d
Description: GNOME 2 CD Ripper
 A CD ripper for GNOME 2 which aims to have a simple, clean, easy to use
 interface.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop, edubuntu-desktop, gobuntu-desktop

---

### Post by albinootje on 2009-01-08
> **imtheguido said:**
> I installed the sound-juicer from the package manager, and it is giving me an error whenever I try to rip the music from the CD:

```
** (sound-juicer:14291): WARNING **: Error getting media type
```

So I figured I had an old version installed or something.And what is Grip?

Grip is a cd-ripping program, just like sound-juicer.
Try it:
```

sudo apt-get install grip vorbis-tools

```
For grip, and perhaps sound-juicer it's possible that you need to configure the right cdrom- or dvd-drive in the settings.
/dev/scd0 is a safe bet for the device in those settings.

---

