---
title: "R installation"
date: 2007-03-05
forum: Education &amp; Science
---

### Post by jkirby65 on 2007-03-05
Hi everyone,

I am having trouble installing R.  I have added an appropriate entry into my sources.list file and type, "sudo apt-get install r-base r-recommended".  This is what I get (below).  Any help is much appreciated!! I am new to linux, so any general help on installing/managing software is appreciated too!! Thanks

Jim 

Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  r-base: Depends: r-base-core (>= 2.4.1-1dapper0) but it is not going to be installed
  r-recommended: Depends: r-base-core (>= 2.4.1-1dapper0) but it is not going to be installed
                 Depends: r-cran-boot (>= 1.2.19) but it is not going to be installed
                 Depends: r-cran-cluster (>= 1.9.6-2) but it is not going to be installed
                 Depends: r-cran-foreign (>= 0.7-2) but it is not going to be installed
                 Depends: r-cran-kernsmooth (>= 2.2.14) but it is not going to be installed
                 Depends: r-cran-lattice (>= 0.10.11) but it is not going to be installed
                 Depends: r-cran-mgcv (>= 1.1.5) but it is not going to be installed
                 Depends: r-cran-nlme (>= 3.1.52) but it is not going to be installed
                 Depends: r-cran-rpart (>= 3.1.20) but it is not going to be installed
                 Depends: r-cran-survival (>= 2.13.2-1) but it is not going to be installed
                 Depends: r-cran-vr (>= 7.2.8) but it is not going to be installed

---

### Post by akniss on 2007-03-06
> **jkirby65 said:**
> I have added an appropriate entry into my sources.list file 

What was the line?  Was it a standard Ubuntu repo? or one of the CRAN mirrors?

---

### Post by ubuntu27 on 2007-03-06
try subtituiong apt-get with aptitude

```
sudo aptitude install r-base r-recommended
```

Let's see what you get now.

---

### Post by WW on 2007-03-07
Did you accidentally mix repositories?  It would help to see your sources.list, and also to know which version of Ubuntu you are using.

---

### Post by jkirby65 on 2007-03-07
Thanks for the help!  Apparently, my entries in the sources.list file are not taking--- here is my sources.list file, and the output when I type, "sudo aptitude install r-core r-recommended":

========sources .list file =============
deb [http://www.stathy.com/cran/bin/linux/ubuntu](http://www.stathy.com/cran/bin/linux/ubuntu) edgy/
deb [http://lib.stat.cmu.edu/R/CRAN/bin/linux/ubuntu](http://lib.stat.cmu.edu/R/CRAN/bin/linux/ubuntu)  edgy/
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


======= "sudo aptitude install r-core r-recommended =========
jkirby@jkirby-desktop:/etc/apt$ sudo aptitude install r-core r-recommended
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "r-core"
Couldn't find any package whose name or description matched "r-recommended"
The following packages have been automatically kept back:
  linux-image-2.6.17-10-generic linux-image-generic linux-restricted-modules-2.6.17-10-generic linux-restricted-modules-common 
  linux-restricted-modules-generic 
The following packages have been kept back:
  app-install-data-commercial avahi-daemon bind9-host capplets-data dbus dbus-1-utils dnsutils ekiga evince firefox firefox-gnome-support gdm gimp 
  gimp-data gimp-python gnome-applets gnome-applets-data gnome-control-center gnome-games gnome-games-data gnome-netstatus-applet gnome-panel 
  gnome-panel-data gnome-system-tools gnupg info language-pack-en language-pack-gnome-en libavahi-client3 libavahi-common-data libavahi-common3 
  libavahi-core4 libavahi-glib1 libbind9-0 libc6 libc6-i686 libdbus-1-3 libdns21 libgimp2.0 libgnome-window-settings1 libgnomeprintui2.2-0 
  libgnomeprintui2.2-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgsf-1-114 libgsf-1-common libgtk2.0-0 
  libgtk2.0-bin libgtk2.0-common libgtop2-7 libgtop2-common libisc11 libisccc0 libisccfg1 libkrb53 liblwres9 libmagick9 libmono-cairo1.0-cil 
  libmono-corlib1.0-cil libmono-data-tds1.0-cil libmono-security1.0-cil libmono-sharpzip0.84-cil libmono-sqlite1.0-cil libmono-system-data1.0-cil 
  libmono-system-web1.0-cil libmono-system1.0-cil libmono0 libmono1.0-cil libnspr4 libnss3 libpanel-applet2-0 libpng12-0 libpoppler1 libpoppler1-glib 
  libsmbclient libsoup2.2-8 libtotem-plparser1 libvolumeid0 linux-generic linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic linux-headers-generic 
  mono-common mono-gac mono-jit mono-runtime openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core 
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-java-common 
  openoffice.org-math openoffice.org-style-default openoffice.org-style-industrial openoffice.org-writer poppler-utils python-uno samba-common screen 
  slocate smbclient system-tools-backends tar tcpdump totem totem-gstreamer totem-mozilla ttf-opensymbol tzdata ubuntu-docs udev vino volumeid w3m 
  x11-common xbase-clients xorg xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-video-all xutils 
0 packages upgraded, 0 newly installed, 0 to remove and 135 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by akniss on 2007-03-08
Try removing the following two lines in your sources.list:
> **jkirby65 said:**
> 
deb ]http://www.stathy.com/cran/bin/linux/ubuntu edgy/
deb [http://lib.stat.cmu.edu/R/CRAN/bin/linux/ubuntu](http://lib.stat.cmu.edu/R/CRAN/bin/linux/ubuntu)  edgy/

And replace them with these two lines:
```
## CRAN mirrors as repos to get latest R version
deb http://rh-mirror.linux.iastate.edu/CRAN/bin/linux/ubuntu/ edgy/

```

Then paste the following into the terminal:
```
sudo aptitude update
sudo aptitude install r-recommended
```

---

### Post by akniss on 2007-03-08
One more question: in your first post, there is an error about a dapper version not being installed, but your sources.list all have edgy...   Which version are you currently running?

---

### Post by jkirby65 on 2007-03-10
> **akniss said:**
> Try removing the following two lines in your sources.list:


And replace them with these two lines:
```
## CRAN mirrors as repos to get latest R version
deb http://rh-mirror.linux.iastate.edu/CRAN/bin/linux/ubuntu/ edgy/

```

Then paste the following into the terminal:
```
sudo aptitude update
sudo aptitude install r-recommended
```

Thanks, I did as you suggested, and it definitely is progress.  Still, not quite there.  Here is what I get now.  Thanks again for your help!!

jkirby@jkirby-desktop:~$ sudo aptitude install r-recommended
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  r-base-core r-base-dev r-cran-cluster r-cran-kernsmooth r-cran-mgcv 
The following NEW packages will be automatically installed:
  build-essential dpkg-dev g++ g++-4.1 g77 g77-3.4 libbz2-dev libg2c0 libg2c0-dev libjpeg62-dev libncurses5-dev libpcre3-dev libpcrecpp0 libpng12-dev 
  libreadline5-dev libstdc++6-4.1-dev r-cran-boot r-cran-foreign r-cran-lattice r-cran-nlme r-cran-rpart r-cran-survival r-cran-vr refblas3 refblas3-dev 
  tcl8.4 tk8.4 zlib1g-dev 
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 g77 g77-3.4 libbz2-dev libg2c0 libg2c0-dev libjpeg62-dev libncurses5-dev libpcre3-dev libpcrecpp0 libpng12-dev 
  libreadline5-dev libstdc++6-4.1-dev r-cran-boot r-cran-foreign r-cran-lattice r-cran-nlme r-cran-rpart r-cran-survival r-cran-vr r-recommended 
  refblas3 refblas3-dev tcl8.4 tk8.4 zlib1g-dev 
0 packages upgraded, 34 newly installed, 0 to remove and 0 not upgraded.
Need to get 26.7MB of archives. After unpacking 92.7MB will be used.
The following packages have unmet dependencies:
  r-cran-mgcv: Depends: libgfortran1 (>= 4.1.1-12) which is a virtual package.
  r-base-dev: Depends: gfortran (>= 4.0.2) which is a virtual package.
  r-cran-kernsmooth: Depends: libgfortran1 (>= 4.1.1-12) which is a virtual package.
  r-base-core: Depends: zlib-bin which is a virtual package.
               Depends: libgfortran1 (>= 4.1.1-12) which is a virtual package.
  r-cran-cluster: Depends: libgfortran1 (>= 4.1.1-12) which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
r-base-core [Not Installed]
r-base-dev [Not Installed]
r-cran-boot [Not Installed]
r-cran-cluster [Not Installed]
r-cran-foreign [Not Installed]
r-cran-kernsmooth [Not Installed]
r-cran-lattice [Not Installed]
r-cran-mgcv [Not Installed]
r-cran-nlme [Not Installed]
r-cran-rpart [Not Installed]
r-cran-survival [Not Installed]
r-cran-vr [Not Installed]
r-recommended [Not Installed]

Score is 107

Accept this solution? [Y/n/q/?] Y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
jkirby@jkirby-desktop:~$

---

### Post by akniss on 2007-03-10
Are you running Dapper or Edgy???  

Post the output from this command:
```
uname -a
```

---

### Post by jkirby65 on 2007-03-15
Sorry it took me so long to get back.  I think I am running edgy.  Here is what I get when I type 'uname -a':

Linux jkirby-desktop 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

Thanks!

Jim

---

### Post by wgrant on 2007-03-16
That'd be Edgy. Is there any particular reason that you're not using the R packages provided in Ubuntu?

---

### Post by jkirby65 on 2007-03-16
No, no reason except my own ignorance.  At first, I tried installing R using the Synaptic Package Manager.  I checked the program box, but got a similar error when I tried installing.  I am new to Ubuntu, and not terribly experienced using R either, so I could easily be doing something stupid.  Any suggestions are welcome!

Jim

---

### Post by akniss on 2007-03-16
fujitsu makes a good point... unless you have a need to use the latest R version, the ubuntu packages should work just fine.  If you are new to R and just learning the syntax, then the R version in the edgy repos should do everything you need.  

Reasons you may need the latest R version:
[LIST=1]
[*]you are trying to squash a bug, and need to know if it is present in the latest stable version
[*] you require the use of a feature in a package that requires the latest version
[/LIST]

I need the latest version because the drc package I use for dose response curve fitting requires 2.4.1 to access the latest features (its still under active development).

---

### Post by wgrant on 2007-03-16
> **jkirby65 said:**
> No, no reason except my own ignorance.  At first, I tried installing R using the Synaptic Package Manager.  I checked the program box, but got a similar error when I tried installing.  I am new to Ubuntu, and not terribly experienced using R either, so I could easily be doing something stupid.  Any suggestions are welcome!

Jim
Try removing the extra non-ubuntu.com lines from your sources.list, opening up Synaptic, reloading package lists, and installing R again. It should work.

---

### Post by nogginhead on 2007-03-27
Hello, all--

I'm in the same boat with JKirby-- new to Ubuntu, new-ish to R.  Edgy.

I tried the same steps recommended here-- changed my sources.list, used apt-get, then used aptitude.  Also tried Synaptic, without my lines in the sources.list (in which case Synaptic does not know R exists) and with, which gets me similar messages as when using apt-get.  

The problem seems to be that r-base-core depends on zlib-bin and on libgfortran1, which can't be installed.

Any help would be much appreciated.

Regards,

Ken

---

### Post by nogginhead on 2007-03-27
D'oh!  I got it.  I had to uncomment the "universe" lines in sources.list.  R installed (via Synaptic) and runs beautifully now.

---

### Post by vanadium on 2007-04-09
I could install R from the Ubuntu repositories, and now using the repository mentionned in this thread. However, I run into th issue that graphics do not work:

* In a terminal, I launch R fine
* From the R-command prompt, typing 
demo(graphics) launches the graphics demo. However, R can produce graphics:

```

> demo(graphics)


        demo(graphics)
        ---- ~~~~~~~~

Type  <Return>   to start : 

> require(datasets)
[1] TRUE

> require(graphics)
[1] TRUE

> opar <- par(ask = dev.interactive(orNone = TRUE))
Error in X11() : could not find any X11 fonts
Check that the Font Path is correct.
> 
>

```

This is a brand new Ubuntu edgy installation. Anyone experienced this? I am very new to Ubuntu, so I would not know where to look to set the Font Path (probably this is an R setting?)

---

### Post by akniss on 2007-04-09
[http://ubuntuforums.org/showpost.php?p=1683538&postcount=14](http://ubuntuforums.org/showpost.php?p=1683538&postcount=14)

See the above post for instructions on how to fix the plotting/fonts issue.

---

### Post by vanadium on 2007-04-10
This is great. Indeed, this resolved the issue! Thank you for providing the link. I did search myself, obviously, but it is not always easy to spot the right information. For R it is in particularly difficult, because simply searching for R returns a lot of hits indeed ;) 

Is this issue known by the Ubuntu developpers? Probably, there is a place where issues can be filled, but I am very  new and didn't discover it yet.

I thank you again. Additionally, I particularly appreciate the high speed by which you helped out.

---

### Post by akniss on 2007-04-10
> **vanadium said:**
> This is great. Indeed, this resolved the issue! Thank you for providing the link. I did search myself, obviously, but it is not always easy to spot the right information. For R it is in particularly difficult, because simply searching for R returns a lot of hits indeed ;) 

Is this issue known by the Ubuntu developpers? Probably, there is a place where issues can be filled, but I am very  new and didn't discover it yet.

I thank you again. Additionally, I particularly appreciate the high speed by which you helped out.

I'm glad it fixed your problem.  Searching these forums for help on 'R' is certainly not very helpful.  I'm not sure whether the problem is known to the Ubuntu devs... we're close enough to Feisty now, I will probably wait and see if its fixed and file a bug report there.

---

### Post by sgsong on 2007-04-23
It will be easier to install from source.

---

### Post by akniss on 2007-04-23
> **sgsong said:**
> It will be easier to install from source.

Seriously??? Since when is installing something from source easier than ```
sudo apt-get install r-recommended
```

---

