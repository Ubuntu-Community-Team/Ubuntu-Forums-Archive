---
title: "cant install avidemux"
date: 2005-05-11
forum: Desktop Environments
---

### Post by binks on 2005-05-11
hi guys hello i just tried to apt-get install avidemux using the repsitories in the starter guide and i get this error

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avidemux: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
            Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
            Depends: libvorbisenc2 (>= 1.1.0) but 1.0.1-1 is to be installed
            Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not going to be installed
E: Broken packages


any ideas cheers binks

---

### Post by qstone on 2005-05-12
[QUOTE=binks]hi guys hello i just tried to apt-get install avidemux using the repsitories in the starter guide and i get this error

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avidemux: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
            Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
            Depends: libvorbisenc2 (>= 1.1.0) but 1.0.1-1 is to be installed
            Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not going to be installed
E: Broken packages


any ideas cheers binks[/QUOTE]
 I had the same trouble with warty.
avidemux is in debian marillat repositories, and seems not to install fine on ubuntu.
Try installing it from the sources, it has few dependencies (and it's well explained at avidemux.sourceforge.net ). You may have to install some "*-dev" packages from synaptic.

---

### Post by mean on 2005-05-12
Try this
[http://fixounet.free.fr/avidemux/win32/avidemux2_ubuntu_minimal.gz](http://fixounet.free.fr/avidemux/win32/avidemux2_ubuntu_minimal.gz)

It is a minimalistic exe built on ubuntu (no xvid, no lame)

It only depends on stuff present in ubuntu
It is obvioulsy not a .deb, just a gzipped exe

What you may need to install, most of them are installed by default on kubuntu

- a52dec
- libmad
- libfreetype (6)
- libarts

That's about it.

It a svn built, you can't get anything fresher :)

---

### Post by binks on 2005-05-12
cheers dudes will try again with it

---

### Post by mean on 2005-05-15
Don't know if it worked for you, but anyway, here is the same stuff
with avidemux 2.0.38 final for ubuntu

[http://fixounet.free.fr/avidemux/win32/avidemux_2.0.38_ubuntu.gz](http://fixounet.free.fr/avidemux/win32/avidemux_2.0.38_ubuntu.gz)

---

### Post by DarchAengel on 2008-03-12
I am having a similar problem but I am installing ver. 2.4 and I have Gutsy.  It says I can't install libqt3.mt-dev and libpq-dev.  Any suggestions on how to get around this?

---

