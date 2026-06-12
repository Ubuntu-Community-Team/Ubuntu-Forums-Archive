---
title: "xorg sources (easy?)"
date: 2006-07-31
forum: Desktop Environments
---

### Post by leodp on 2006-07-31
Hi all,

first days with (k)ubuntu, first problems, first question:
I need to download the xorg sources for drapper (7.0), to compile the driver for an aiptek 600-U tablet, but don't know how to set correctly my sources.conf

I already followed some guides to config. it for the various multimedia stuff, universe, multiverse, proprietary.....
but couldn't find updated infos on how to  "apt-get source xorg", in order to avoid downloading  one_by_one all the xorg 7.0 source files from xorg website.
Can anybody help?

Thanks, ciao, Leo

---

### Post by cptnapalm on 2006-07-31
Are you sure that it is the xorg sources you need?  If it is a driver, then it should need the kernel headers for the kernel you are using, not to mention the compiler and all that stuff.

I've never heard of a driver which needed xorg source code...

---

### Post by leodp on 2006-08-01
> **cptnapalm said:**
> 
I've never heard of a driver which needed xorg source code...


The Aiptek graphic tablet needs a kernel driver (aiptek) AND an xorg driver (aiptek or aiptek_drv). I already installed the first one, but for the second (the CVS version is updated in respect to that in xorg 7.x) I need xorg sources.
For infos:
[http://aiptektablet.sourceforge.net/](http://aiptektablet.sourceforge.net/)

Leo

---

### Post by RAOF on 2006-08-01
Well, you could always try
```
apt-get source xserver-xorg
```
:)
But there's probably a -dev package that you could install.  Try **aptitude search xorg** and see whether there's a -dev package that seems right.

---

### Post by leodp on 2006-08-01
Well with the search option I get a lot of xorg files, but I think they are not the sources, or am I wrong (see below)?
The driver I need to recompile is already installed and is:
i   xserver-xorg-input-aiptek     - X.Org X server -- Aiptek input driver



The other command returns an error:

# apt-get source xserver-xorg
Reading package lists... Done
Building dependency tree... Done
E: Could not open file /var/lib/apt/lists/cipherfunk.org_pub_packages_ubuntu_dists_dapper_main_source_Sources - open (2 No such file or directory)

I attach below also my source.list

Ciao, Leo

--------------------------------------------------
# aptitude search xorg
p   xorg-build-macros                        - X macros required to bootstrap some X clients.
i   xorg-dev                                 - the X.Org development libraries
i   xorg-driver-fglrx                        - Video driver for ATI graphics accelerators
p   xorg-driver-fglrx-dev                    - Video driver for ATI graphics accelerators (devel f
v   xorg-driver-synaptics                    -
i   xserver-xorg                             - the X.Org X server
p   xserver-xorg-air-core                    - X server with accelerated indirect 3D support
i   xserver-xorg-core                        - X.Org X server -- core server
i   xserver-xorg-dev                         - X.Org X server -- development files
v   xserver-xorg-driver                      -
i   xserver-xorg-driver-all                  - the X.Org X server -- output driver metapackage
i   xserver-xorg-driver-apm                  - X.Org X server -- APM display driver
i   xserver-xorg-driver-ark                  - X.Org X server -- ark display driver
i   xserver-xorg-driver-ati                  - X.Org X server -- ATI display driver
v   xserver-xorg-driver-atimisc              -
i   xserver-xorg-driver-chips                - X.Org X server -- Chips display driver
i   xserver-xorg-driver-cirrus               - X.Org X server -- Cirrus display driver
i   xserver-xorg-driver-cyrix                - X.Org X server -- Cyrix display driver
i   xserver-xorg-driver-dummy                - X.Org X server -- dummy display driver
i   xserver-xorg-driver-fbdev                - X.Org X server -- fbdev display driver
i   xserver-xorg-driver-glint                - X.Org X server -- Glint display driver
i   xserver-xorg-driver-i128                 - X.Org X server -- i128 display driver
i   xserver-xorg-driver-i740                 - X.Org X server -- i740 display driver
i   xserver-xorg-driver-i810                 - X.Org X server -- Intel i8xx, i9xx display driver
i   xserver-xorg-driver-imstt                - X.Org X server -- IMSTT display driver
i   xserver-xorg-driver-mga                  - X.Org X server -- MGA display driver
i   xserver-xorg-driver-neomagic             - X.Org X server -- Neomagic display driver
i   xserver-xorg-driver-newport              - X.Org X server -- Newport display driver
i   xserver-xorg-driver-nsc                  - X.Org X server -- NSC display driver
i   xserver-xorg-driver-nv                   - X.Org X server -- NV display driver
v   xserver-xorg-driver-r128                 -
v   xserver-xorg-driver-radeon               -
i   xserver-xorg-driver-rendition            - X.Org X server -- Rendition display driver
v   xserver-xorg-driver-riva128              -
i   xserver-xorg-driver-s3                   - X.Org X server -- legacy S3 display driver
i   xserver-xorg-driver-s3virge              - X.Org X server -- S3 ViRGE display driver
i   xserver-xorg-driver-savage               - X.Org X server -- Savage display driver
i   xserver-xorg-driver-siliconmotion        - X.Org X server -- SiliconMotion display driver
i   xserver-xorg-driver-sis                  - X.Org X server -- SiS display driver
i   xserver-xorg-driver-sisusb               - X.Org X server -- SiS USB display driver
i   xserver-xorg-driver-tdfx                 - X.Org X server -- tdfx display driver
i   xserver-xorg-driver-tga                  - X.Org X server -- TGA display driver
i   xserver-xorg-driver-trident              - X.Org X server -- Trident display driver
i   xserver-xorg-driver-tseng                - X.Org X server -- Tseng display driver
i   xserver-xorg-driver-v4l                  - X.Org X server -- Video4Linux driver
i   xserver-xorg-driver-vesa                 - X.Org X server -- VESA display driver
i   xserver-xorg-driver-vga                  - X.Org X server -- VGA display driver
i   xserver-xorg-driver-via                  - X.Org X server -- VIA display driver
i   xserver-xorg-driver-vmware               - X.Org X server -- VMware display driver
i   xserver-xorg-driver-voodoo               - X.Org X server -- Voodoo display driver
v   xserver-xorg-input                       -
p   xserver-xorg-input-acecad                - X.Org X server -- AceCad input driver
i   xserver-xorg-input-aiptek                - X.Org X server -- Aiptek input driver
i   xserver-xorg-input-all                   - the X.Org X server -- input driver metapackage
p   xserver-xorg-input-calcomp               - X.Org X server -- Calcomp input driver
p   xserver-xorg-input-citron                - X.Org X server -- Citron input driver
p   xserver-xorg-input-digitaledge           - X.Org X server -- DigitalEdge input driver
p   xserver-xorg-input-dmc                   - X.Org X server -- DMC input driver
p   xserver-xorg-input-dynapro               - X.Org X server -- Dynapro input driver
p   xserver-xorg-input-elo2300               - X.Org X server -- ELO2300 input driver
i   xserver-xorg-input-elographics           - X.Org X server -- ELOGraphics input driver
i   xserver-xorg-input-evdev                 - X.Org X server -- evdev input driver
p   xserver-xorg-input-fpit                  - X.Org X server -- FPIT input driver
p   xserver-xorg-input-hyperpen              - X.Org X server -- HyperPen input driver
p   xserver-xorg-input-jamstudio             - X.Org X server -- JamStudio input driver
p   xserver-xorg-input-joystick              - X.Org X server -- joystick input driver
i   xserver-xorg-input-kbd                   - X.Org X server -- keyboard input driver
p   xserver-xorg-input-magellan              - X.Org X server -- Magellan input driver
p   xserver-xorg-input-magictouch            - X.Org X server -- MagicTouch input driver
p   xserver-xorg-input-microtouch            - X.Org X server -- MicroTouch input driver
i   xserver-xorg-input-mouse                 - X.Org X server -- mouse input driver
p   xserver-xorg-input-mutouch               - X.Org X server -- muTouch input driver
p   xserver-xorg-input-palmax                - X.Org X server -- Palmax input driver
p   xserver-xorg-input-penmount              - X.Org X server -- Penmount input driver
p   xserver-xorg-input-spaceorb              - X.Org X server -- SpaceOrb input driver
p   xserver-xorg-input-summa                 - X.Org X server -- Summa input driver
i   xserver-xorg-input-synaptics             - Synaptics TouchPad driver for X.Org server
p   xserver-xorg-input-tek4957               - X.Org X server -- Tek4957 input driver
p   xserver-xorg-input-ur98                  - X.Org X server -- UR98 input driver
p   xserver-xorg-input-void                  - X.Org X server -- void input driver
i   xserver-xorg-input-wacom                 - X.Org X server -- Wacom input driver



/etc/sources.list:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

## dapper-commercial by canonical

## currently has realplay (realplayer 10) and opera (opera 9)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

## Cipherfunk multimedia packages (GPG key: 33BAC1B3)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main
deb-src [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

## Dapper PLF
## only uncomment it if you need it
 deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
 deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

## Bleeding edge (official) wine repository for Dapper
## only uncomment it if you need it
 deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
 deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

## skype (official)
## only uncomment it if you need it
 deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
 
 
#CINELERRA-CVS
 
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools) ./
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/) ./

---

### Post by RAOF on 2006-08-01
Well, it seems you've got all the relevent -dev packages installed...  If it still needs more, then you'll have to get the xserver-xorg source.

That error you were getting is not related to the "source" bit - if you try **anything** with apt-get you'll probably get the same error.  Comment out the cipherpunk repository, run **sudo apt-get update**, and that should clear the error.

---

### Post by leodp on 2006-08-01
> **RAOF said:**
> Well, it seems you've got all the relevent -dev packages installed...  If it still needs more, then you'll have to get the xserver-xorg source.

That error you were getting is not related to the "source" bit - if you try **anything** with apt-get you'll probably get the same error.  Comment out the cipherpunk repository, run **sudo apt-get update**, and that should clear the error.

Ok, but is there a way of getting the xserver-xorg source with apt-get?

Leo

---

### Post by RAOF on 2006-08-01
> **leodp said:**
> Ok, but is there a way of getting the xserver-xorg source with apt-get?

Leo

Yes.  **apt-get source xserver-xorg**!

---

### Post by leodp on 2006-08-02
> **RAOF said:**
> Yes.  **apt-get source xserver-xorg**!

Sure, apt-get source xserver-xorg!
After commenting out the sources that give error I could do it.
Sorry RAOF, but my head is [a bit] hard.

Thanks guys.
Ciao, Leo

---

