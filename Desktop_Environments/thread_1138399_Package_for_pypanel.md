---
title: "Package for pypanel"
date: 2009-04-26
forum: Desktop Environments
---

### Post by Major_Kong on 2009-04-26
Is there a pypanel package avaliable for ubuntu 9.04 ?

---

### Post by Miata-MS on 2009-04-26
> **Major_Kong said:**
> Is there a pypanel package avaliable for ubuntu 9.04 ?

Would love to know this as well. I tried the package in launchpad, but the GDeb package installer didn't want to let it install for some reason.

---

### Post by snova on 2009-04-26
[http://packages.ubuntu.com/search?keywords=pypanel](http://packages.ubuntu.com/search?keywords=pypanel)

Oddly enough, it seems to be in Intrepid, but there are no results for Jaunty.

---

### Post by ivaarsen on 2009-04-26
Well wait a minute!  I want this back!

Another forum-goer was kind enough to introduce me to a nice desktop environment made of OpenBox w/ Conky and Pypanel.  Pretty slick and sleek, and now it's kind of broken!  :(

Will the package work if I try to install the version from Intrpid?

---

### Post by snova on 2009-04-26
> **ivaarsen said:**
> Will the package work if I try to install the version from Intrpid?

[http://packages.ubuntu.com/intrepid/pypanel](http://packages.ubuntu.com/intrepid/pypanel)

Possibly. It doesn't depend on much, so it seems unlikely to me that anything would break.

Anyway, you can't really hurt anything by trying.

---

### Post by ivaarsen on 2009-04-27
> **snova said:**
> [http://packages.ubuntu.com/intrepid/pypanel](http://packages.ubuntu.com/intrepid/pypanel)

Possibly. It doesn't depend on much, so it seems unlikely to me that anything would break.

Anyway, you can't really hurt anything by trying.

Thanks, but...

> **Miata-MS said:**
> Would love to know this as well. I tried the package in launchpad, but the GDeb package installer didn't want to let it install for some reason.

...I got this too.

It's not really a problem -- it was a spare machine anyhoo...  I can wait until (if) it's available / supported.  I suppose I would like to know what the beef is -- why this package / program wasn't included or not allowed with this version?

---

### Post by snova on 2009-04-27
See if dpkg will output something more useful for fixing it. If it's a versioning incompatibility or something, I don't know what to do, but it might be simpler than that.

```
cd Desktop # If you put it on your desktop
sudo dpkg --install *<pypanel_whatever.deb>*
```

Paste the error.

---

### Post by Major_Kong on 2009-04-27
> **snova said:**
> [http://packages.ubuntu.com/search?keywords=pypanel](http://packages.ubuntu.com/search?keywords=pypanel)

Oddly enough, it seems to be in Intrepid, but there are no results for Jaunty.

It seems to have been removed from the repo. Maybe because pypanel is no longer maintained.

I recompiled the package from the 8.10 source in the repos:

[http://rapidshare.com/files/226495131/pypanel_2.4-1.1build1_amd64.deb.html](http://rapidshare.com/files/226495131/pypanel_2.4-1.1build1_amd64.deb.html) (x86-64 version only!)

If you want to recompile just download the source from -> [http://packages.ubuntu.com/source/intrepid/pypanel](http://packages.ubuntu.com/source/intrepid/pypanel), open up a terminal and in the directory type:

dpkg-source -x pypanel_2.4-1.1build1.dsc
cd pypanel-2.4
dpkg-buildpackage -rfakeroot

(watch out for the dependencies)

---

### Post by Cybertroll on 2009-08-07
There is another way to make pypanel work on Ubuntu 9.04.

Get the Intrepid version from [http://packages.ubuntu.com/intrepid/pypanel](http://packages.ubuntu.com/intrepid/pypanel) 

Get python2.5-minimal from the current repository 
```
sudo apt-get install python2.5-minimal
```Then install pypanel with the following command: 
```
sudo dpkg -i --force-depends-version pypanel_2.4-1.1build1_i386.deb
```

Make sure of course you cover the other dependencies. 

Run it with: 

```
python2.5 /usr/bin/pypanel &
```It worked for me. 

PS: It would be wise to edit also /var/lib/dpkg/status and remove from the pypanel entry the python (<< 2.6) on the depends entry (marked bold and red below):
```
Package: pypanel
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 164
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 2.4-1.1build1
Depends: libc6 (>= 2.5-0ubuntu1), libfreetype6 (>= 2.2), libimlib2, libx11-6, libxext6, libxft2 (>> 2.1.1), zlib1g (>= 1:1.2.1), python (>= 2.5), **[COLOR=Red]python (<< 2.6),[/COLOR]** python-xlib (>= 0.12-5.1)
Conffiles:
 /etc/pypanelrc 9f29ac7e6bc2ee4f2756b88ffeb6e168
Description: lightweight panel/taskbar for X11 window managers
 PyPanel is a lightweight panel/taskbar written in Python and C for X11
 window managers. It can be easily customized to match any desktop theme or
 taste. PyPanel works with WindowMaker and EWMH compliant WMs (Kahakai,
 Openbox, PekWM, FVWM, etc).
 .
 Some of the customizable features include:
 .
  o Transparency w/ shading
  o Panel dimensions, location and layout
  o Font type and colors with Xft support
  o Button events/actions
  o Clock and workspace name display
  o System Tray (Notification Area)
 .
  Homepage: http://pypanel.sourceforge.net/
Original-Maintainer: Bartosz Fenski <fenio@debian.org>
Python-Version: 2.5

```

---

### Post by bionnaki on 2009-08-29
bring back pypanel!

---

### Post by ivaarsen on 2009-10-25
> **Cybertroll said:**
> There is another way to make pypanel work on Ubuntu 9.04.

Sorry to everybody for my necromancy of this thread, but I had busted out the machine I referenced earlier in the thread, and again decided to check on my 'pypanel issue.'

I wanted to take the time to thank you for this information.  I didn't have to go through all the steps, I'm guessing because I already had pypanel running before my upgrade to Jaunty.  But with this tip, I once again have pypanel running under Jaunty.  Thanks again, good sir!

---

