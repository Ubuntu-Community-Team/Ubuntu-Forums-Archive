---
title: "installation of ppa wslu for Ubuntu 22.04"
date: 2022-12-11
forum: Desktop Environments
---

### Post by ortollj on 2022-12-11
Hi
I did these commands:

```
wget https://launchpad.net/ubuntu/+archive/primary/+sourcefiles/wslu/3.2.3-0ubuntu3/wslu_3.2.3.orig.tar.gz
wget https://launchpad.net/ubuntu/+archive/primary/+sourcefiles/wslu/3.2.3-0ubuntu3/wslu_3.2.3-0ubuntu3.debian.tar.xz
wget https://launchpad.net/ubuntu/+archive/primary/+sourcefiles/wslu/3.2.3-0ubuntu3/wslu_3.2.3-0ubuntu3.dsc
mkdir wsluPkg
mv wslu_* wsluPkg
ls -ltr wsluPkg
sudo apt-get install dpkg-dev
cd wsluPkg/
dpkg-source -x wslu_3.2.3-0ubuntu3.dsc
cd wslu-3.2.3/
dpkg-buildpackage -rfakeroot -b
```

and I got this:

```
ortollj@DESKTOP-K30FLRP:~/wsluPkg$ dpkg-source -x wslu_3.2.3-0ubuntu3.dsc
gpgv: Signature made Thu Oct  7 12:34:36 2021 CEST
gpgv:                using RSA key D56571B88A8BBAF140BF63D6BD7EAA60778FA6F5
gpgv:                issuer "doko@ubuntu.com"
gpgv: [COLOR="#FF0000"]Can't check signature: No public key[/COLOR]
dpkg-source: warning: cannot verify signature ./wslu_3.2.3-0ubuntu3.dsc
dpkg-source: info: extracting wslu in wslu-3.2.3
dpkg-source: info: unpacking wslu_3.2.3.orig.tar.gz
dpkg-source: info: unpacking wslu_3.2.3-0ubuntu3.debian.tar.xz
ortollj@DESKTOP-K30FLRP:~/wsluPkg$ ls
wslu-3.2.3  wslu_3.2.3-0ubuntu3.debian.tar.xz  wslu_3.2.3-0ubuntu3.dsc  wslu_3.2.3.orig.tar.gz
ortollj@DESKTOP-K30FLRP:~/wsluPkg$ cd wslu-3.2.3/
ortollj@DESKTOP-K30FLRP:~/wsluPkg/wslu-3.2.3$ dpkg-buildpackage -rfakeroot -b
dpkg-buildpackage: info: source package wslu
dpkg-buildpackage: info: source version 3.2.3-0ubuntu3
dpkg-buildpackage: info: source distribution impish
dpkg-buildpackage: info: source changed by Matthias Klose <doko@ubuntu.com>
dpkg-buildpackage: info: host architecture amd64
 dpkg-source --before-build .
dpkg-checkbuilddeps: [COLOR="#FF0000"]error: Unmet build dependencies: bats[/COLOR]
dpkg-buildpackage: warning: build dependencies/conflicts unsatisfied; aborting
dpkg-buildpackage: warning: (Use -d flag to override.)
```

question 1) if no signature can i install it safely or do I have to require a verified signature ? 

question 2) could I install this ppa despite the message :dpkg-checkbuilddeps: error: Unmet build dependencies: bats ?

---

### Post by DuckHook on 2022-12-13
Please use standard fonts and styles in your postings. Large non-standard fonts are considered shouting and offend forum netiquette.
______________

You have me scratching my head here. Though I don't use these utilities, I don't understand the way you are approaching this.

Are you trying to add this PPA to an Ubuntu instance running on WSL in a Windows machine?

[LIST=1]
[*]PPAs are only meant for Ubuntu (and some derivatives that piggyback on Ubuntu's infrastructure). They can't be installed onto anything else.
[*]Any PPA that I'm familiar with already has the binaries precompiled. That's the point of a dev offering a PPA. All of this wget/make/build stuff is not only unnecessary, but misdirected.
[*]Here's the launchpad page for [WSL Utilities]("https://launchpad.net/~wslutilities/+archive/ubuntu/wslu"). Follow the simple two-line instruction to add the PPA to Ubuntu. After that, a simple "sudo apt install wslu" and the utilities you are looking for should just download and install. No need to compile anything.
[/LIST]
If you are trying to do something more complicated that I didn't pick up on, then you should provide the intent and context of your actions and also state your end goals. Others may be able to help you where I can't.

---

### Post by ActionParsnip on 2022-12-13
Which release of Ubuntu are you using
[https://ppa.launchpadcontent.net/wslutilities/wslu/ubuntu/dists/](https://ppa.launchpadcontent.net/wslutilities/wslu/ubuntu/dists/)
Not all PPA support all releases of Ubuntu

---

### Post by ortollj on 2022-12-24
Thanks a lot DuckHook now WSLU is installed on my Ubuntu 22.04 in W11 WSL.

---

