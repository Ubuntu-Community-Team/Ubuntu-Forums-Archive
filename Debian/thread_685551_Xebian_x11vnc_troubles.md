---
title: "Xebian x11vnc troubles"
date: 2008-02-02
forum: Debian
---

### Post by melat0nin on 2008-02-02
Hi all

I've tried getting help with this on Xbox-scene but the forum is far less popular than here so I thought I'd give this a bash.

I've installed Xebian on my Xbox and it appears to be working fine, but I can't install x11vnc.  I get a dependency error:

```
xbox:~# apt-get install x11vnc
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  x11vnc: Depends: libxdamage1 but it is not going to be installed
          Depends: libxfixes3 but it is not going to be installed
          Depends: libxinerama1 but it is not going to be installed
E: Broken packages
```

So I tried downloading the tarball and installing manually, and I got this error:

```
xbox:/usr/x11vnc-0.9.3# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether make sets $(MAKE)... (cached) yes
checking for ranlib... ranlib
checking for ar... /usr/bin/ar
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking thenonexistentheader.h usability... no
checking thenonexistentheader.h presence... no
checking for thenonexistentheader.h... no
checking for X... no
checking for XGetImage in -lX11... no
configure: error:
==========================================================================
*** A working X window system build environment is required to build ***
x11vnc.  Make sure any required X development packages are installed.
If they are installed in non-standard locations, one can use the
--x-includes=DIR and --x-libraries=DIR configure options or set the
CPPFLAGS and LDFLAGS environment variables to indicate where the X
window system header files and libraries may be found.  On 64+32 bit
machines you may need to point to lib64 or lib32 directories to pick up
the correct word size.

If you want to build x11vnc without X support (e.g. for -rawfb use only
or for native Mac OS X), specify the --without-x configure option.
==========================================================================
```

Now I've got Xebian running fine with a GUI (fluxbox) on my TV.  How can there be no X?!

I ran Aptitude to try and install x11vnc from there, and when I tried the upgrade option, I got errors about permission being denied.

I don't know where to look now, can anyone help?  The Xebian install is to the gamesave partition (E:) which means it's contained in a single-file filesystem (I believe).

Any help would be much appreciated :)

---

### Post by melat0nin on 2008-02-02
Can someone try and install x11vnc to check whether the problem is at my end or at the repo end? I've reinstalled Xebian, so it's clean, and run Aptitude. When I search for x11vnc, the following dependencies have problems:

```
Source Package: libvncserver
--\ Depends
  --- libc6 (>= 2.3.6-6) (UNSATISFIED)
  --- libjpeg62
  --- libx11-6
  --- libxdamage1 (UNSATISFIED)
  --- libxext6
  --- libxfixes3 (UNSATISFIED)
  --- libxinerama1 (UNSATISFIED)
  --- libxrandr2
  --- libxtst6
  --- zlib1g (>= 1:1.2.1)
```

Any ideas? I'm inclined to think it's a problem with the repo. Is it possible I don't have the right sources in my sources.list? I've searched for additional x11vnc but I can't find any info suggesting I need more than the standard sources.

Any thoughts?

---

### Post by melat0nin on 2008-02-02
Anyone? This is driving me mad.  Why do the default repos not have something as basic as VNC?

---

### Post by p_quarles on 2008-02-02
The repository has it, as you can see from the error output you posted in the first message. You just don't seem to have all the dependencies. It appears that something is preventing the dependencies from being automatically installed. To get more info on why, try installing the missing deps themselves:
```
#apt-get install libc6 libxdamage1 libxfixes3 libxinerama1
```
If they install without a hitch, try to install vnc again. If it complains about conflicting packages, post the error report.

---

### Post by melat0nin on 2008-02-02
> **p_quarles said:**
> The repository has it, as you can see from the error output you posted in the first message. You just don't seem to have all the dependencies. It appears that something is preventing the dependencies from being automatically installed. To get more info on why, try installing the missing deps themselves:
```
#apt-get install libc6 libxdamage1 libxfixes3 libxinerama1
```
If they install without a hitch, try to install vnc again. If it complains about conflicting packages, post the error report.

Thankyou for the reply :)

I tried your suggestion, but it had the same problem with dependencies:

```
xebian:~# apt-get install libc6 libxdamage1 libxfixes3 libxinerama1
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxdamage1: Depends: x11-common but it is not going to be installed
  libxfixes3: PreDepends: x11-common (>= 1:7.0.0) but it is not going to be installed
  libxinerama1: Depends: x11-common but it is not going to be installed
E: Broken packages

```

Any thoughts?

EDIT:

when I then try and install x11-common, I get the following message (prior to saying Yes to installation, which I haven't yet):

```

xebian:~# apt-get install x11-common
Reading Package Lists... Done
Building Dependency Tree... Done
The following extra packages will be installed:
  coreutils dpkg dpkg-dev fontconfig fontconfig-config gcc-4.1-base libast2
  libc6 libc6-dev libdrm2 libfontconfig1 libfontenc1 libfreetype6 libfs6
  libgcc1 libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa libice6 libpng12-0
  libselinux1 libsepol1 libsm6 libstdc++6 libx11-6 libx11-data libxau6 libxaw7
  libxdmcp6 libxext6 libxfont1 libxi6 libxkbfile1 libxmu6 libxmuu1 libxp6
  libxpm4 libxrandr2 libxss1 libxt6 libxtrap6 libxtst6 libxv1 libxxf86dga1
  libxxf86vm1 locales type-handling tzdata x-window-system xbase-clients
  xbitmaps xcursor-themes xfonts-100dpi xfonts-75dpi xfonts-base
  xfonts-encodings xfonts-scalable xfonts-utils xfs xkb-data xlibmesa-dri
  xlibmesa-gl xlibmesa-glu xlibs-data xnest xorg xprint-common xserver-xfree86
  xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati
  xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-cyrix
  xserver-xorg-video-dummy xserver-xorg-video-fbdev xserver-xorg-video-glint
  xserver-xorg-video-i128 xserver-xorg-video-i740 xserver-xorg-video-i810
  xserver-xorg-video-imstt xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-newport xserver-xorg-video-nsc xserver-xorg-video-nv
  xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-via
  xserver-xorg-video-vmware xserver-xorg-video-voodoo xutils xutils-dev xvfb
Suggested packages:
  lzma debian-keyring glibc-doc libfreetype6-dev mesa-utils libglide3 discover
  mdetect read-edid libglide2 gsynaptics ksynaptics qsynaptics pdksh
Recommended packages:
  laptop-detect xresprobe discover1
The following packages will be REMOVED:
  base-config lbxproxy libdps1 libxft1 proxymngr twm xdm xfree86-common xfwp
  xlibs xprint xprt-xprintorg xserver-common xterm xvkbd
The following NEW packages will be installed:
  fontconfig-config gcc-4.1-base libdrm2 libfontenc1 libfs6 libgl1-mesa-dri
  libgl1-mesa-glx libglu1-mesa libselinux1 libsepol1 libstdc++6 libx11-data
  libxau6 libxdmcp6 libxfont1 libxkbfile1 libxss1 libxxf86dga1 libxxf86vm1
  type-handling tzdata x11-common xbitmaps xcursor-themes xfonts-encodings
  xfonts-utils xkb-data xorg xserver-xorg xserver-xorg-core
  xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-kbd
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-cyrix xserver-xorg-video-dummy
  xserver-xorg-video-fbdev xserver-xorg-video-glint xserver-xorg-video-i128
  xserver-xorg-video-i740 xserver-xorg-video-i810 xserver-xorg-video-imstt
  xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-newport xserver-xorg-video-nsc xserver-xorg-video-nv
  xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-via
  xserver-xorg-video-vmware xserver-xorg-video-voodoo xutils-dev
The following packages will be upgraded:
  coreutils dpkg dpkg-dev fontconfig libast2 libc6 libc6-dev libfontconfig1
  libfreetype6 libgcc1 libice6 libpng12-0 libsm6 libx11-6 libxaw7 libxext6
  libxi6 libxmu6 libxmuu1 libxp6 libxpm4 libxrandr2 libxt6 libxtrap6 libxtst6
  libxv1 locales x-window-system xbase-clients xfonts-100dpi xfonts-75dpi
  xfonts-base xfonts-scalable xfs xlibmesa-dri xlibmesa-gl xlibmesa-glu
  xlibs-data xnest xprint-common xserver-xfree86 xutils xvfb
43 upgraded, 73 newly installed, 15 to remove and 338 not upgraded.
Need to get 60.7MB of archives.
After unpacking 10.9MB of additional disk space will be used.
Do you want to continue? [Y/n]

```

---

### Post by p_quarles on 2008-02-02
You just need to follow the breadcrumbs to get to the bottom of the problem. Install x11-common, and if that gives you another dependency problem, install that. Eventually, I suspect, you will either resolve the issue or find the package that is conflicting with the one you want.

---

### Post by melat0nin on 2008-02-02
When I get to the install portion (after downloading) of x11-common, I get this message.  I'm not sure whether to say yes or no:

```
Reading changelogs... Done
Preconfiguring packages ...
(Reading database ... 35830 files and directories currently installed.)
Removing base-config ...
Selecting previously deselected package tzdata.
(Reading database ... 35722 files and directories currently installed.)
Unpacking tzdata (from .../tzdata_2007j-1etch1_all.deb) ...
Replacing files in old package libc6 ...
Preparing to replace libc6-dev 2.3.2.ds1-22 (using .../libc6-dev_2.3.6.ds1-13etch4_i386.deb) ...
Unpacking replacement libc6-dev ...
Preparing to replace locales 2.3.2.ds1-22 (using .../locales_2.3.6.ds1-13etch4_all.deb) ...
Unpacking replacement locales ...
Preparing to replace libc6 2.3.2.ds1-22 (using .../libc6_2.3.6.ds1-13etch4_i386.deb) ...

Name Service Switch update in the C Library: pre-installation question.

Running services and programs that are using NSS need to be restarted,
otherwise they might not be able to do lookup or authentication any more.
The installation process is able to restart some services (such as ssh or
telnetd), but other programs cannot be restarted automatically.  One such
program that needs manual stopping and restart after the glibc upgrade by
yourself is xdm - because automatic restart might disconnect your active
X11 sessions.

Known packages that need to be stopped before the glibc upgrade are:
        xdm kdm gdm postgresql xscreensaver

This script detected the following installed services which must be
stopped before the upgrade:
        xdm

If you want to interrupt the upgrade now and continue later, please
answer No to the question below.

Do you want to upgrade glibc now? [Y/n]

```

---

### Post by p_quarles on 2008-02-02
Oh, I see what's going on. It needs to replace part of the X server, which can't be done while X is running. 

Try this: switch to a console log-in by pressing ctrl-alt-F1. Then, stop xdm:
```
# /etc/init.d/xdm stop
```
You should now be able to install all dependencies for the VNC app.

---

### Post by melat0nin on 2008-02-02
> **p_quarles said:**
> Oh, I see what's going on. It needs to replace part of the X server, which can't be done while X is running. 

Try this: switch to a console log-in by pressing ctrl-alt-F1. Then, stop xdm:
```
# /etc/init.d/xdm stop
```
You should now be able to install all dependencies for the VNC app.

Right I will give that a try, thanks :)

---

### Post by melat0nin on 2008-02-02
I tried stopping xdm but got this:

```
xebian:~# /etc/init.d/xdm stop
Stopping X display manager: xdm not running (/var/run/xdm.pid not found)
```

When I try to install x11-common I still get the same thing about the xdm service still running.

Any ideas? :S  I'm doing all of this through an SSH session on my PC; but I can see the Xebian desktop on the TV.

---

### Post by p_quarles on 2008-02-02
Hmm. I would just hook up a keyboard and monitor and select "single user mode" from the boot menu. That should be the easiest way to get around these issues.

---

### Post by melat0nin on 2008-02-02
I can't really do that cos I don't have a USB keyboard, and that's all you can connect to the Xbox.

Do I have any other options?  To be fair, I executed the 

/etc/init.d/xdm stop

command from the SSH terminal, not the terminal on the xbox itself - does that make a difference?  I could edit the startup stuff to prevent Xebian from logging in automatically - that leaves it at the login (text) prompt.  Would that have the effect of not starting xdm?

---

### Post by p_quarles on 2008-02-02
It very well could.

How did you manage to install this without a keyboard?

---

### Post by melat0nin on 2008-02-02
Xebian has a live CD which I booted from, and I changed my LAN settings to match the static IP settings of the Live CD (the subnet) then I could immediately SSH into the Live CD in order to run the install script.

I will give my own suggestion (!) a try in the morning.  Thanks for your help so far! It's much appreciated :)

---

### Post by maybeway36 on 2008-02-02
If you can install xorg-dev, you'll probably be able to cpmpile it from source.

---

### Post by krunge on 2008-02-02
Have you verified you don't need to do a dist-upgrade?
```
apt-get dist-upgrade
```

One often needs to do this with debian testing or sid when the packages get rearranged.  Otherwise many packages get stuck.

---

### Post by melat0nin on 2008-02-03
> **krunge said:**
> Have you verified you don't need to do a dist-upgrade?
```
apt-get dist-upgrade
```

One often needs to do this with debian testing or sid when the packages get rearranged.  Otherwise many packages get stuck.

I'm not quite sure what the structure of Xebian is with regard to Debian -- would a dist-upgrade be likely to break the Xebian install?  I know it has a custom-compiled kernel, but I'm not sure how many other parts are customised for the Xbox.

EDIT: a chap here ([http://osdir.com/ml/ports.xbox.user/2004-06/msg00059.html](http://osdir.com/ml/ports.xbox.user/2004-06/msg00059.html)) suggests that a dist-upgrade is not a good idea.  I'm using 1.1.4 (not 1.0.0) but I'm still loathe to try this just in case.

---

### Post by melat0nin on 2008-02-03
Preventing the autologin didn't stop xdm from starting, but I just told the install to kill/restart the service and it seemed go fine.  There were some others too, including adp (?), cron and ssh.

Eventually I got to a stage where I could try and install x11-common, and this is what happened:

```
xebian:~# apt-get install x11-common
Reading Package Lists... Done
Building Dependency Tree... Done
The following extra packages will be installed:
  coreutils dpkg dpkg-dev fontconfig fontconfig-config gcc-4.1-base libast2
  libdrm2 libfontconfig1 libfontenc1 libfreetype6 libfs6 libgcc1
  libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa libice6 libpng12-0 libselinux1
  libsepol1 libsm6 libstdc++6 libx11-6 libx11-data libxau6 libxaw7 libxdmcp6
  libxext6 libxfont1 libxi6 libxkbfile1 libxmu6 libxmuu1 libxp6 libxpm4
  libxrandr2 libxss1 libxt6 libxtrap6 libxtst6 libxv1 libxxf86dga1 libxxf86vm1
  type-handling x-window-system xbase-clients xbitmaps xcursor-themes
  xfonts-100dpi xfonts-75dpi xfonts-base xfonts-encodings xfonts-scalable
  xfonts-utils xfs xkb-data xlibmesa-dri xlibmesa-gl xlibmesa-glu xlibs-data
  xnest xorg xprint-common xserver-xfree86 xserver-xorg xserver-xorg-core
  xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-kbd
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-cyrix xserver-xorg-video-dummy
  xserver-xorg-video-fbdev xserver-xorg-video-glint xserver-xorg-video-i128
  xserver-xorg-video-i740 xserver-xorg-video-i810 xserver-xorg-video-imstt
  xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-newport xserver-xorg-video-nsc xserver-xorg-video-nv
  xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-via
  xserver-xorg-video-vmware xserver-xorg-video-voodoo xutils xutils-dev xvfb
Suggested packages:
  lzma debian-keyring libfreetype6-dev mesa-utils libglide3 discover mdetect
  read-edid libglide2 gsynaptics ksynaptics qsynaptics pdksh
Recommended packages:
  laptop-detect xresprobe discover1
The following packages will be REMOVED:
  lbxproxy libdps1 libxft1 proxymngr twm xdm xfree86-common xfwp xlibs xprint
  xprt-xprintorg xserver-common xterm xvkbd
The following NEW packages will be installed:
  fontconfig-config gcc-4.1-base libdrm2 libfontenc1 libfs6 libgl1-mesa-dri
  libgl1-mesa-glx libglu1-mesa libselinux1 libsepol1 libstdc++6 libx11-data
  libxau6 libxdmcp6 libxfont1 libxkbfile1 libxss1 libxxf86dga1 libxxf86vm1
  type-handling x11-common xbitmaps xcursor-themes xfonts-encodings
  xfonts-utils xkb-data xorg xserver-xorg xserver-xorg-core
  xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-kbd
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-cyrix xserver-xorg-video-dummy
  xserver-xorg-video-fbdev xserver-xorg-video-glint xserver-xorg-video-i128
  xserver-xorg-video-i740 xserver-xorg-video-i810 xserver-xorg-video-imstt
  xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-newport xserver-xorg-video-nsc xserver-xorg-video-nv
  xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-via
  xserver-xorg-video-vmware xserver-xorg-video-voodoo xutils-dev
The following packages will be upgraded:
  coreutils dpkg dpkg-dev fontconfig libast2 libfontconfig1 libfreetype6
  libgcc1 libice6 libpng12-0 libsm6 libx11-6 libxaw7 libxext6 libxi6 libxmu6
  libxmuu1 libxp6 libxpm4 libxrandr2 libxt6 libxtrap6 libxtst6 libxv1
  x-window-system xbase-clients xfonts-100dpi xfonts-75dpi xfonts-base
  xfonts-scalable xfs xlibmesa-dri xlibmesa-gl xlibmesa-glu xlibs-data xnest
  xprint-common xserver-xfree86 xutils xvfb
40 upgraded, 72 newly installed, 14 to remove and 338 not upgraded.
Need to get 0B/48.6MB of archives.
After unpacking 9798kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Reading changelogs... Done
Preconfiguring packages ...
(Reading database ... 35873 files and directories currently installed.)
Preparing to replace libice6 4.3.0.dfsg.1-14 (using .../libice6_1%3a1.0.1-2_i386                                                                                                  .deb) ...
Unpacking replacement libice6 ...
Preparing to replace libsm6 4.3.0.dfsg.1-14 (using .../libsm6_1%3a1.0.1-3_i386.d                                                                                                  eb) ...
Unpacking replacement libsm6 ...
Selecting previously deselected package libxau6.
Unpacking libxau6 (from .../libxau6_1%3a1.0.1-2_i386.deb) ...
Selecting previously deselected package libxdmcp6.
Unpacking libxdmcp6 (from .../libxdmcp6_1%3a1.0.1-2_i386.deb) ...
dpkg: xserver-common: dependency problems, but removing anyway as you request:
 xnest depends on xserver-common.
 xserver-xfree86 depends on xserver-common (>= 4.3.0.dfsg.1-5).
(Reading database ... 35881 files and directories currently installed.)
Removing xserver-common ...
dpkg: xfree86-common: dependency problems, but removing anyway as you request:
 libxt6 depends on xfree86-common.
 proxymngr depends on xfree86-common.
 xfs depends on xfree86-common.
 libxtst6 depends on xfree86-common.
 xlibs-data depends on xfree86-common.
 xnest depends on xfree86-common.
 libxp6 depends on xfree86-common.
 xutils depends on xfree86-common (>> 4.3).
 lbxproxy depends on xfree86-common.
 xlibmesa-gl depends on xfree86-common.
 libx11-6 depends on xfree86-common (>> 4.3.0).
 libxft1 depends on xfree86-common.
 xvfb depends on xfree86-common.
 xlibmesa-dri depends on xfree86-common.
 xfonts-75dpi depends on xfree86-common.
 libxaw7 depends on xfree86-common.
 libxmu6 depends on xfree86-common.
 xfonts-100dpi depends on xfree86-common.
 xfonts-scalable depends on xfree86-common.
 xfonts-base depends on xfree86-common.
 libxi6 depends on xfree86-common.
 libxtrap6 depends on xfree86-common.
 xdm depends on xfree86-common.
 libdps1 depends on xfree86-common.
 libxv1 depends on xfree86-common.
 libxrandr2 depends on xfree86-common.
 twm depends on xfree86-common.
 libxpm4 depends on xfree86-common.
 xterm depends on xfree86-common.
 libxext6 depends on xfree86-common.
 xserver-xfree86 depends on xfree86-common.
 xlibmesa-glu depends on xfree86-common.
 xbase-clients depends on xfree86-common.
 libxmuu1 depends on xfree86-common.
 xfwp depends on xfree86-common.
Removing xfree86-common ...
Selecting previously deselected package libfontenc1.
(Reading database ... 35828 files and directories currently installed.)
Unpacking libfontenc1 (from .../libfontenc1_1%3a1.0.2-2_i386.deb) ...
Selecting previously deselected package gcc-4.1-base.
Unpacking gcc-4.1-base (from .../gcc-4.1-base_4.1.1-21_i386.deb) ...
Preparing to replace libgcc1 1:3.4.3-13 (using .../libgcc1_1%3a4.1.1-21_i386.deb                                                                                                  ) ...
Unpacking replacement libgcc1 ...
Setting up gcc-4.1-base (4.1.1-21) ...

Setting up libgcc1 (4.1.1-21) ...

(Reading database ... 35840 files and directories currently installed.)
Preparing to replace libfreetype6 2.1.7-2.4 (using .../libfreetype6_2.2.1-5+etch                                                                                                  2_i386.deb) ...
Unpacking replacement libfreetype6 ...
Selecting previously deselected package libxfont1.
Unpacking libxfont1 (from .../libxfont1_1%3a1.2.2-2.etch1_i386.deb) ...
dpkg: xserver-xfree86: dependency problems, but removing anyway as you request:
 nv-drv-xbox depends on xserver-xfree86 (>= 4.2.1-1).
 x-window-system-core depends on xserver-xfree86.
(Reading database ... 35842 files and directories currently installed.)
Removing xserver-xfree86 ...
xserver-xfree86 prerm warning: X server provided by xserver-xfree86 package
   is being removed; setting /etc/X11/X to point to /bin/true
xserver-xfree86 prerm warning: run "dpkg-reconfigure xserver-xorg" before
   attempting to start the X server again
E: Sub-process /usr/bin/dpkg exited unexpectedly
xebian:~#

```

Any thoughts?

---

### Post by melat0nin on 2008-02-03
I'm getting stupid errors now.  I don't have a clue what's going on:

```
xebian:~# apt-get -f install
Reading Package Lists... Done
Building Dependency Tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  coreutils dpkg dpkg-dev fontconfig fontconfig-config libast2 libfontconfig1
  libfs6 libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa libpng12-0 libx11-6
  libx11-data libxaw7 libxext6 libxi6 libxkbfile1 libxmu6 libxmuu1 libxp6
  libxpm4 libxrandr2 libxss1 libxt6 libxtrap6 libxtst6 libxv1 libxxf86dga1
  libxxf86vm1 type-handling x-window-system x11-common xbase-clients xbitmaps
  xcursor-themes xfonts-100dpi xfonts-75dpi xfonts-base xfonts-encodings
  xfonts-scalable xfonts-utils xlibmesa-dri xlibmesa-gl xlibmesa-glu
  xlibs-data xorg xprint xserver-xfree86 xserver-xorg xutils xutils-dev
Suggested packages:
  lzma debian-keyring mesa-utils xfs xserver libglide3 discover mdetect
  read-edid libglide2 pdksh
Recommended packages:
  xprint-utils laptop-detect xresprobe discover1
The following packages will be REMOVED:
  libdps1 libxft1 xlibs
The following NEW packages will be installed:
  fontconfig-config libfs6 libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa
  libx11-data libxkbfile1 libxss1 libxxf86dga1 libxxf86vm1 type-handling
  x11-common xbase-clients xbitmaps xcursor-themes xfonts-encodings
  xfonts-utils xorg xprint xserver-xfree86 xserver-xorg xutils xutils-dev
The following packages will be upgraded:
  coreutils dpkg dpkg-dev fontconfig libast2 libfontconfig1 libpng12-0
  libx11-6 libxaw7 libxext6 libxi6 libxmu6 libxmuu1 libxp6 libxpm4 libxrandr2
  libxt6 libxtrap6 libxtst6 libxv1 x-window-system xfonts-100dpi xfonts-75dpi
  xfonts-base xfonts-scalable xlibmesa-dri xlibmesa-gl xlibmesa-glu xlibs-data
29 upgraded, 23 newly installed, 3 to remove and 338 not upgraded.
56 not fully installed or removed.
Need to get 0B/39.1MB of archives.
After unpacking 27.7MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Reading changelogs... Done
Preconfiguring packages ...
Setting up libsepol1 (1.14-2) ...

Setting up libselinux1 (1.32-3) ...

(Reading database ... 35789 files and directories currently installed.)
Unpacking x11-common (from .../x11-common_1%3a7.1.0-19_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/x11-common_1%3a7.1.0-19_i386.deb (--unpack):
 trying to overwrite `/usr/X11R6/bin', which is also in package xtdesktop
Preparing to replace coreutils 5.2.1-2 (using .../coreutils_5.97-5.3_i386.deb) ...
No diversion `any diversion of /usr/share/man/man1/md5sum.textutils.1.gz', none removed
No diversion `any diversion of /usr/bin/md5sum.textutils', none removed
Unpacking replacement coreutils ...
Replacing files in old package dpkg ...
Errors were encountered while processing:
 /var/cache/apt/archives/x11-common_1%3a7.1.0-19_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas at all?

---

### Post by melat0nin on 2008-02-03
I have dumped Xebian and gone with X-dsl instead -- it is working pretty much out of the box.

Thanks for your help guys! :)

---

### Post by Zymous on 2008-08-04
It's too late for the original poster, but if any one else stumbles across this like I did: go to [http://packages.debian.org/search?suite=sarge&searchon=names&keywords=x11vnc  ]("http://packages.debian.org/search?suite=sarge&searchon=names&keywords=x11vnc") and download the Sarge version of the .deb file rather than the Etch version. It installs without a hitch.

-- 
Zym

---

### Post by dylan1055 on 2008-08-08
hey thanx, but how do i do this? can i just apt-get ? im a noob but willing, pls help :)

---

### Post by dylan1055 on 2008-08-08
i got it , works perfect.

for other noobs:

```
wget http://debian.oregonstate.edu/debian/pool/main/libv/libvncserver/x11vnc_0.7-1_i386.deb
dpkg -i x11vnc_0.7-1_i386.deb
su live
x11vnc

```

---

### Post by melat0nin on 2008-08-08
> **dylan1055 said:**
> i got it , works perfect.

for other noobs:

```
wget http://debian.oregonstate.edu/debian/pool/main/libv/libvncserver/x11vnc_0.7-1_i386.deb
dpkg -i x11vnc_0.7-1_i386.deb
su live
x11vnc

```

Hi, thanks for the tips.  It installs fine for me, but when I try to run x11vnc this is the output I get:

```

live@xebian:/root$ x11vnc

Settings:
 display:    null
 authfile:   null
 subwin:     0x0
 rootshift:  0
 flashcmap:  0
 force_idx:  0
 overlay:    0
 ovl_cursor: 1
 visual:     null
 scaling:    0 1.00000
 viewonly:   0
 shared:     0
 conn_once:  1
 inetd:      0
 connect:    null
 connectfile null
 vnc_conn:   1
 allow:      null
 passfile:   null
 accept:     null
 gone:       null
 using_shm:  1
 flipbytes:  0
 onetile:    0
 blackout:   null
 xinerama:   0
 xrandr:     0
 xrandrmode: null
 logfile:    null
 rc_file:    
 norc:       0
 bg:         0
 mod_tweak:  1
 isolevel3:  0
 xkb:        0
 skipkeys:   null
 addkeysyms: 0
 xkbcompat:  0
 clearmods:  0
 remap:      null
 norepeat:   1
 nofb:       0
 watchbell:  1
 watchsel:   1
 watchprim:  1
 cursor:     1
 root_curs:  0
 curs_mode:  null
 xfixes:     1
 cursorshp:  1
 cursorpos:  1
 xwarpptr:   0
 buttonmap:  null
 dragging:   1
 ptr_mode:   2
 inputskip:  10
 debug_ptr:  0
 debug_key:  0
 defer:      30
 waitms:     30
 take_naps:  0
 sb:         60
 sigpipe:    null
 threads:    0
 fs_frac:    0.75
 gaps_fill:  4
 grow_fill:  3
 tile_fuzz:  2
 deny_all:   0
 noremote:   0

08/08/2008 23:21:20 x11vnc version: 0.7pre lastmod: 2004-12-20
08/08/2008 23:21:21 XOpenDisplay failed (null)

```

Any thoughts?

EDIT: got it working. Just had to specify the display using x11vnc -display :0

---

### Post by melat0nin on 2008-08-08
Okay so the next step is to install a Bittorrent client.  I'm not sure how to do this in Xebian, because I don't know if it has any repos enabled.

Any thoughts?  Ideally I'd like to run Deluge with the web interface plugin enabled 24/7, so I can leave the xbox downloading things while I'm out.

EDIT:  I tried installing Transmission using apt-get install, but it wanted to install 70mbs of other stuff (about 60-70 other packages) and when I said yes to this, there was all kinds of bizarre stuff going on a services being stopped and whatnot.  I think it was essentially trying to upgrade to etch.

I'm pretty sure this will have broken my Xebian installation, which isn't a problem because I can reinstate it quite easily.

But how do I go about installing Deluge?  Should I compile from source? The .debs on the Deluge website are for Lenny and SID only so I don't want to try them without proper advice first.

Any help would be much appreciated :)

---

