---
title: "Muine Install"
date: 2006-01-29
forum: Desktop Environments
---

### Post by torturetheartist on 2006-01-29
I'd like to install Muine but for some reason cannot install the packages.

My initial attempt was with the 'Add Applications' wizard.  When I checked Muine the following message was displayed:

"Cannot install 'muine'

Installing this application would mean that something else needs to be removed. Please use the "Advanced" mode to install 'muine'."

So... I turned to google.  I found a wiki on muine installation.  I began installing the individual packages and couldn't install half of them.  

I would appreciate any help as I am growing increasingly tired of Rhythmbox. :) 

*Note: I am a relatively new Ubuntu user.

---

### Post by psychicdragon on 2006-01-29
Type **sudo apt-get install muine** in the terminal and post the output here.

---

### Post by RAOF on 2006-01-29
Did you try the "advanced mode"?  Alternatively, try the Synaptic Package Manager (System -> Administration -> Synaptic Package Manager).  Search for "muine", check it for installation, and see what it says - particularly what it wants to remove.

---

### Post by torturetheartist on 2006-01-29
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
  muine: Depends: mono-jit (>= 1.0) but it is not installable
         Depends: libdbus-1-cil (>= 0.36.2) but it is not installable
         Depends: libgconf2.0-cil (>= 2.3.90) but it is not going to be installed
         Depends: libgconf2.0-cil (< 2.5.0) but it is not going to be installed
         Depends: libglade2.0-cil (>= 2.3.90) but it is not going to be installed
         Depends: libglib2.0-cil (>= 2.3.90) but it is not going to be installed         Depends: libgnome2.0-cil (>= 2.3.90) but it is not going to be installed
         Depends: libgtk2.0-cil (>= 2.3.90) but it is not going to be installed
         Depends: mono-classlib-1.0 (>= 1.0) but it is not installable
E: Broken packages

---

### Post by torturetheartist on 2006-01-29
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
  muine: Depends: mono-jit (>= 1.0) but it is not installable
         Depends: libdbus-1-cil (>= 0.36.2) but it is not installable
         Depends: libgconf2.0-cil (>= 2.3.90) but it is not going to be installed
         Depends: libgconf2.0-cil (< 2.5.0) but it is not going to be installed
         Depends: libglade2.0-cil (>= 2.3.90) but it is not going to be installed
         Depends: libglib2.0-cil (>= 2.3.90) but it is not going to be installed         Depends: libgnome2.0-cil (>= 2.3.90) but it is not going to be installed
         Depends: libgtk2.0-cil (>= 2.3.90) but it is not going to be installed
         Depends: mono-classlib-1.0 (>= 1.0) but it is not installable
E: Broken packages

---

### Post by RAOF on 2006-01-29
Could you also run "apt-cache show muine"?  Could you post your sources.list?

---

### Post by torturetheartist on 2006-01-29
Package: muine
Priority: optional
Section: universe/gnome
Installed-Size: 1232
Maintainer: Dave Beckett <dajobe@debian.org>
Architecture: i386
Version: 0.8.3-5ubuntu7
Depends: libatk1.0-0 (>= 1.9.0), libbonobo2-0 (>= 2.8.0), libc6 (>= 2.3.4-1), libcairo2 (>= 1.0.0), libflac7, libfontconfig1 (>= 2.3.0), libgconf2-4 (>= 2.9), libgdbm3, libglib2.0-0 (>= 2.8.0), libgnomevfs2-0 (>= 2.11.3), libgstreamer-gconf0.8-0 (>= 0.8.0), libgstreamer0.8-0 (>= 0.8.11), libgtk2.0-0 (>= 2.8.0), libid3tag0 (>= 0.15.1b), libogg0 (>= 1.1.2), liborbit2 (>= 1:2.10.0), libpango1.0-0 (>= 1.10.0), libvorbis0a (>= 1.1.0), libvorbisfile3 (>= 1.1.0), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3, libxi6, libxinerama1, libxml2 (>= 2.6.20), libxrandr2, libxrender1, zlib1g (>= 1:1.2.1), gstreamer0.8-gnomevfs (>= 0.8.0), gconf2 (>= 2.6.2-1), mono-jit (>= 1.0), libdbus-1-cil (>= 0.36.2), libgconf2.0-cil (>= 2.3.90), libgconf2.0-cil (<< 2.5.0), libglade2.0-cil (>= 2.3.90), libglib2.0-cil (>= 2.3.90), libgnome2.0-cil (>= 2.3.90), libgtk2.0-cil (>= 2.3.90), mono-classlib-1.0 (>= 1.0)
Filename: pool/universe/m/muine/muine_0.8.3-5ubuntu7_i386.deb
Size: 246956
MD5sum: 8d1d8fc3e1c605fb51af3b6830f34681
Description: Simple playlist based music player
 Muine is an innovative music player. It has a simple interface designed to
 allow the user to easily construct playlists from albums and/or single songs.
 Its goal is to be simply a music player, not to become a robust music
 management application.  It includes a plugin interface.
 .
 The package includes the CIL assemblies to access the D-BUS interface
 to Muine and to compile plugins for Muine.
 .
 Homepage: [http://muine.gooeylinux.org](http://muine.gooeylinux.org)
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by RAOF on 2006-01-29
Ok.  And your sources.list?  You can find that in /etc/apt/sources.list

---

### Post by torturetheartist on 2006-01-29
I have a feeling I'm having some permission issues (I don't think this is what you want, but it's what I found in sources.list).

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted
## Uncomment the following two lines to fetch updated software from the network
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted

I'm getting better at this, I promise. :)

---

### Post by RAOF on 2006-01-29
That's exactly what I wanted.  It seems fine, though.

Finally, can you try 
```
sudo apt-get update
sudo apt-get install muine

```
just to see if updateing the package lists will help.  If not, I'm not sure what's wrong.  I'm running Dapper, and muine installs fine on that.  Can other people install muine on Breezy?

---

### Post by torturetheartist on 2006-01-29
Same deal:
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
  muine: Depends: mono-jit (>= 1.0) but it is not installable
         Depends: libdbus-1-cil (>= 0.36.2) but it is not installable
         Depends: libgconf2.0-cil (>= 2.3.90) but it is not going to be installed
         Depends: libgconf2.0-cil (< 2.5.0) but it is not going to be installed
         Depends: libglade2.0-cil (>= 2.3.90) but it is not going to be installed
         Depends: libglib2.0-cil (>= 2.3.90) but it is not going to be installed         Depends: libgnome2.0-cil (>= 2.3.90) but it is not going to be installed
         Depends: libgtk2.0-cil (>= 2.3.90) but it is not going to be installed
         Depends: mono-classlib-1.0 (>= 1.0) but it is not installable
E: Broken packages

I haven't heard of anyone else having Muine problems in Breezy.  Everyone seems to enjoy how "easy" it is to install.  

I have a good friend that usually helps me out with stuff like this.  I turned to the forum since he was unavailable.  I'll talk to him about it eventually.  I'm confident that if he can't figure it out, it can't be done.  I'll post results here for anyone who cares.

Thanks for your help :)

---

### Post by Madpilot on 2006-01-29
[QUOTE=RAOF]
just to see if updateing the package lists will help.  If not, I'm not sure what's wrong.  I'm running Dapper, and muine installs fine on that.  Can other people install muine on Breezy?[/QUOTE]

I can't help with the odd installing problem, but I can confirm that Muine installed just fine in Breezy - it's running right now, actually.

In the posted sources.list, I noticed that "breezy multiverse" is listed twice, once with the URL us.archive.ubuntu.com and the second time with just archive.u.c - maybe remove the 2nd listing and see what happens?

Brian.

---

### Post by GreySim on 2006-02-07
I'm having a very similar issue, and I think the problem stems from using a third-party repo for a bit.

'apt-get install muine' gives:
```

The following packages have unmet dependencies:
  muine: Depends: libgconf2.0-cil (>= 2.3.90) but it is not going to be installed
         Depends: libgconf2.0-cil (< 2.5.0) but it is not going to be installed
         Depends: libgnome2.0-cil (>= 2.3.90) but it is not going to be installed

```

And so boggling for a while, I decided to try to figure out *why* those weren't being installed.

```

dennis@Guava:~$ sudo apt-get install libgnome2.0-cil
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
  libgnome2.0-cil: Depends: libgconf2.0-cil (>= 2.3.90) but it is not going to be installed
                   Depends: libgconf2.0-cil (< 2.5.0) but it is not going to be installed
                   Depends: libglade2.0-cil (< 2.5.0) but 2.7.90-0filefind.net-breezy0 is to be installed
                   Depends: libglib2.0-cil (< 2.5.0) but 2.7.90-0filefind.net-breezy0 is to be installed
                   Depends: libgtk2.0-cil (< 2.5.0) but 2.7.90-0filefind.net-breezy0 is to be installed
E: Broken packages

```

So my problem at least, is mixed package sources (though just before posting this, I remembered that the sources.list was already posted, so maybe that point has already been investigated and disproven).  Perhaps to fix the original posters problem, try to install the missing packages and see what bars them from installing.  Not sure though.  I have to get back to installing muine either way though, while I wait for Banshee to get better (which is why I started using a third party repo in the first place :???: )

---

