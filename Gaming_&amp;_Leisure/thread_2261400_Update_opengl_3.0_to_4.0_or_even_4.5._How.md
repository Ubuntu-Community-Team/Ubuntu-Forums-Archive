---
title: "Update opengl 3.0 to 4.0 or even 4.5. How?"
date: 2015-01-18
forum: Gaming &amp; Leisure
---

### Post by chihwah_li on 2015-01-18
been searching on google tried a few things , but a game keeps telling me it needs opengl 4.0.
with the command glxinfo | grep "OpenGL version" It's telling me I have Opengl 3.0.

But how to update to version 4 or even 4.5???

(If Linux community was more focused than the millions of distro's, Windows would have lost years ago..... Please make installation much easier.... or perhaps I mist it...in that case please tell.)

---

### Post by tokyobadger on 2015-01-19
What GPU are you using?

The install I'm posting from is 15.04 with Nvidia GTX680 running the nvidia-331 driver and in this case OpenGL is provided by the nvidia driver
```
glxinfo | grep "OpenGL version"
OpenGL version string: 4.4.0 NVIDIA 331.113
```

---

### Post by grahammechanical on 2015-01-19
> [COLOR=#000000](If Linux community was more focused than the millions of distro's, Windows would have lost years ago..... Please make installation much easier.... or perhaps I mist it...in that case please tell.)[/COLOR]

If people paid half as much for Linux as they pay for Apple and Microsoft operating systems then maybe the Linux community would be "more focused," as you put it, on what its customers want.

The video card has to support the OpenGL specification as well. I am using Ubuntu 15.04 on an Nvidia GT220 but I only have OpenGL version 3.0. But according to the Nvidia web site the GT220 only supports OpenGL 3.1.

So, that is another reason for not blaming Linux distributors.

Regards

---

### Post by raptir on 2015-01-19
Installation in Linux is actually much easier than in Windows, since the majority of the software you need is available right in the repo.

Anyway, OpenGL support is provided either by mesa or your graphics driver. If you have Intel graphics, you are most likely already using the most up-to-date driver and the issue is likely that your hardware does not support it. If you have Nvidia or AMD graphics, you might need to install the proprietary drivers.

---

### Post by chihwah_li on 2015-01-21
Ok, I have tried this but It tells me that the package is no longer valid. 

[https://ubuntutechnical.wordpress.com/2011/11/20/install-ati-official-drivers-in-ubuntu/](https://ubuntutechnical.wordpress.com/2011/11/20/install-ati-official-drivers-in-ubuntu/)

Does someone know a complete step by step installation for for instance ATI 7770 VGA card?
Let it please be a post that is up to date.

---

### Post by Yellow Pasque on 2015-01-21
[http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Before_you_start](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Before_you_start)
Note that you may have to change the one command to use "--buildpkg Ubuntu/utopic" instead of Ubunty/trusty depending on what Ubuntu version you're running.

---

### Post by deadflowr on 2015-01-21
Have you tried Additional Drivers?
Open the dash menu(super key>> windows icon button) and type "additional drivers".

(I assume you haven't try this, as you haven't mentioned it, if you have tried this, then my apologizes(?, right word?; I'm baffled atm on how to spell it). Or if this isn't an option for you; ie, pride in open-source only, yada yada...)

---

### Post by chihwah_li on 2015-01-21
Thanks. Did not know this screen exists!

In the additional drivers tab the following option is chosen:
Using video driver for the AMD graphics acceleratiors from fglrx (propietary)

> **deadflowr said:**
> Have you tried Additional Drivers?
Open the dash menu(super key>> windows icon button) and type "additional drivers".

(I assume you haven't try this, as you haven't mentioned it, if you have tried this, then my apologizes(?, right word?; I'm baffled atm on how to spell it). Or if this isn't an option for you; ie, pride in open-source only, yada yada...)

I tried the instructions, I have trusty thanks for reminding,  and there are some errors at the last command line instruction:

```
chihwahli@lion:~$ sudo apt-get install cdbs dh-make dkms execstack dh-modaliases linux-headers-generic libqtgui4 xserver-xorg-dev
[sudo] password for chihwahli: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqtgui4 is already the newest version.
linux-headers-generic is already the newest version.
The following extra packages will be installed:
  autoconf automake autotools-dev dh-translations intltool libmirclient-dev
  libmirclient7 libmirclientplatform-mesa libmirprotobuf-dev libmirprotobuf0
  libpciaccess-dev libpixman-1-dev libprotobuf-dev libprotobuf-lite8
  libsigsegv2 libxkbfile-dev libxml-parser-perl m4 mircommon-dev python-scour
  x11proto-dri3-dev x11proto-fonts-dev x11proto-present-dev x11proto-randr-dev
  x11proto-render-dev x11proto-resource-dev x11proto-scrnsaver-dev
  x11proto-video-dev x11proto-xf86bigfont-dev x11proto-xf86dri-dev
  x11proto-xinerama-dev
Suggested packages:
  autoconf2.13 autoconf-archive gnu-standards autoconf-doc libtool devscripts
  python-rsvg
The following NEW packages will be installed:
  autoconf automake autotools-dev cdbs dh-make dh-modaliases dh-translations
  dkms execstack intltool libmirclient-dev libmirclient7
  libmirclientplatform-mesa libmirprotobuf-dev libmirprotobuf0
  libpciaccess-dev libpixman-1-dev libprotobuf-dev libprotobuf-lite8
  libsigsegv2 libxkbfile-dev libxml-parser-perl m4 mircommon-dev python-scour
  x11proto-dri3-dev x11proto-fonts-dev x11proto-present-dev x11proto-randr-dev
  x11proto-render-dev x11proto-resource-dev x11proto-scrnsaver-dev
  x11proto-video-dev x11proto-xf86bigfont-dev x11proto-xf86dri-dev
  x11proto-xinerama-dev xserver-xorg-dev
0 upgraded, 37 newly installed, 0 to remove and 53 not upgraded.
Need to get 3244 kB of archives.
After this operation, 15,3 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main libmirprotobuf0 amd64 0.1.8+14.04.20140411-0ubuntu1 [75,2 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main libmirclientplatform-mesa amd64 0.1.8+14.04.20140411-0ubuntu1 [23,9 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main libmirclient7 amd64 0.1.8+14.04.20140411-0ubuntu1 [147 kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main libsigsegv2 amd64 2.10-2 [15,0 kB]
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main m4 amd64 1.4.17-2ubuntu1 [195 kB]
Get:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main autoconf all 2.69-6 [322 kB]
Get:7 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main autotools-dev all 20130810.1 [44,3 kB]
Get:8 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main automake all 1:1.14.1-2ubuntu1 [510 kB]
Get:9 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main libxml-parser-perl amd64 2.41-1build3 [294 kB]
Get:10 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main intltool all 0.50.2-2 [52,0 kB]
Get:11 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main dh-translations all 121 [21,6 kB]
Get:12 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main python-scour all 0.26-3build1 [40,5 kB]
Get:13 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main cdbs all 0.4.122ubuntu2 [42,1 kB]
Get:14 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main dh-make all 0.63 [37,6 kB]
Get:15 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main dh-modaliases all 1:0.2.91.4 [8118 B]
Get:16 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main dkms all 2.2.0.3-1.1ubuntu5 [64,4 kB]
Get:17 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main execstack amd64 0.0.20090925-8 [72,2 kB]
Get:18 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main libprotobuf-lite8 amd64 2.5.0-9ubuntu1 [52,7 kB]
Get:19 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main libprotobuf-dev amd64 2.5.0-9ubuntu1 [421 kB]
Get:20 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main libmirprotobuf-dev amd64 0.1.8+14.04.20140411-0ubuntu1 [4556 B]
Get:21 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main mircommon-dev amd64 0.1.8+14.04.20140411-0ubuntu1 [25,1 kB]
Get:22 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main libmirclient-dev amd64 0.1.8+14.04.20140411-0ubuntu1 [7888 B]
Get:23 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main libpixman-1-dev amd64 0.30.2-2ubuntu1 [242 kB]
Get:24 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main libxkbfile-dev amd64 1:1.0.8-1 [89,4 kB]
Get:25 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main x11proto-dri3-dev all 1.0-1 [5996 B]
Get:26 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main x11proto-fonts-dev all 2.1.2-1 [69,7 kB]
Get:27 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main x11proto-present-dev all 1.0-1 [10,1 kB]
Get:28 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main x11proto-randr-dev all 1.4.0+git20120101.is.really.1.4.0-0ubuntu1 [32,9 kB]
Get:29 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main x11proto-render-dev all 2:0.11.1-2 [20,1 kB]
Get:30 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main x11proto-resource-dev all 1.2.0-3 [10,7 kB]
Get:31 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main x11proto-scrnsaver-dev all 1.2.2-1 [25,0 kB]
Get:32 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main x11proto-video-dev all 2.3.2-1 [17,5 kB]
Get:33 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main x11proto-xf86bigfont-dev all 1.2.0-3 [4784 B]
Get:34 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main x11proto-xf86dri-dev all 2.1.1-2 [5630 B]
Get:35 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main x11proto-xinerama-dev all 1.2.1-2 [4966 B]
Get:36 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main libpciaccess-dev amd64 0.13.2-1 [23,6 kB]
Get:37 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main xserver-xorg-dev amd64 2:1.15.1-0ubuntu2 [205 kB]
Fetched 3244 kB in 12s (264 kB/s)                                              
Extracting templates from packages: 100%
Selecting previously unselected package libmirprotobuf0:amd64.
(Reading database ... 420807 files and directories currently installed.)
Preparing to unpack .../libmirprotobuf0_0.1.8+14.04.20140411-0ubuntu1_amd64.deb ...
Unpacking libmirprotobuf0:amd64 (0.1.8+14.04.20140411-0ubuntu1) ...
Selecting previously unselected package libmirclientplatform-mesa:amd64.
Preparing to unpack .../libmirclientplatform-mesa_0.1.8+14.04.20140411-0ubuntu1_amd64.deb ...
Unpacking libmirclientplatform-mesa:amd64 (0.1.8+14.04.20140411-0ubuntu1) ...
Selecting previously unselected package libmirclient7:amd64.
Preparing to unpack .../libmirclient7_0.1.8+14.04.20140411-0ubuntu1_amd64.deb ...
Unpacking libmirclient7:amd64 (0.1.8+14.04.20140411-0ubuntu1) ...
Selecting previously unselected package libsigsegv2:amd64.
Preparing to unpack .../libsigsegv2_2.10-2_amd64.deb ...
Unpacking libsigsegv2:amd64 (2.10-2) ...
Selecting previously unselected package m4.
Preparing to unpack .../m4_1.4.17-2ubuntu1_amd64.deb ...
Unpacking m4 (1.4.17-2ubuntu1) ...
Selecting previously unselected package autoconf.
Preparing to unpack .../autoconf_2.69-6_all.deb ...
Unpacking autoconf (2.69-6) ...
Selecting previously unselected package autotools-dev.
Preparing to unpack .../autotools-dev_20130810.1_all.deb ...
Unpacking autotools-dev (20130810.1) ...
Selecting previously unselected package automake.
Preparing to unpack .../automake_1%3a1.14.1-2ubuntu1_all.deb ...
Unpacking automake (1:1.14.1-2ubuntu1) ...
Selecting previously unselected package libxml-parser-perl.
Preparing to unpack .../libxml-parser-perl_2.41-1build3_amd64.deb ...
Unpacking libxml-parser-perl (2.41-1build3) ...
Selecting previously unselected package intltool.
Preparing to unpack .../intltool_0.50.2-2_all.deb ...
Unpacking intltool (0.50.2-2) ...
Selecting previously unselected package dh-translations.
Preparing to unpack .../dh-translations_121_all.deb ...
Unpacking dh-translations (121) ...
Selecting previously unselected package python-scour.
Preparing to unpack .../python-scour_0.26-3build1_all.deb ...
Unpacking python-scour (0.26-3build1) ...
Selecting previously unselected package cdbs.
Preparing to unpack .../cdbs_0.4.122ubuntu2_all.deb ...
Unpacking cdbs (0.4.122ubuntu2) ...
Selecting previously unselected package dh-make.
Preparing to unpack .../archives/dh-make_0.63_all.deb ...
Unpacking dh-make (0.63) ...
Selecting previously unselected package dh-modaliases.
Preparing to unpack .../dh-modaliases_1%3a0.2.91.4_all.deb ...
Unpacking dh-modaliases (1:0.2.91.4) ...
Selecting previously unselected package dkms.
Preparing to unpack .../dkms_2.2.0.3-1.1ubuntu5_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5) ...
Selecting previously unselected package execstack.
Preparing to unpack .../execstack_0.0.20090925-8_amd64.deb ...
Unpacking execstack (0.0.20090925-8) ...
Selecting previously unselected package libprotobuf-lite8:amd64.
Preparing to unpack .../libprotobuf-lite8_2.5.0-9ubuntu1_amd64.deb ...
Unpacking libprotobuf-lite8:amd64 (2.5.0-9ubuntu1) ...
Selecting previously unselected package libprotobuf-dev:amd64.
Preparing to unpack .../libprotobuf-dev_2.5.0-9ubuntu1_amd64.deb ...
Unpacking libprotobuf-dev:amd64 (2.5.0-9ubuntu1) ...
Selecting previously unselected package libmirprotobuf-dev:amd64.
Preparing to unpack .../libmirprotobuf-dev_0.1.8+14.04.20140411-0ubuntu1_amd64.deb ...
Unpacking libmirprotobuf-dev:amd64 (0.1.8+14.04.20140411-0ubuntu1) ...
Selecting previously unselected package mircommon-dev:amd64.
Preparing to unpack .../mircommon-dev_0.1.8+14.04.20140411-0ubuntu1_amd64.deb ...
Unpacking mircommon-dev:amd64 (0.1.8+14.04.20140411-0ubuntu1) ...
Selecting previously unselected package libmirclient-dev:amd64.
Preparing to unpack .../libmirclient-dev_0.1.8+14.04.20140411-0ubuntu1_amd64.deb ...
Unpacking libmirclient-dev:amd64 (0.1.8+14.04.20140411-0ubuntu1) ...
Selecting previously unselected package libpixman-1-dev.
Preparing to unpack .../libpixman-1-dev_0.30.2-2ubuntu1_amd64.deb ...
Unpacking libpixman-1-dev (0.30.2-2ubuntu1) ...
Selecting previously unselected package libxkbfile-dev:amd64.
Preparing to unpack .../libxkbfile-dev_1%3a1.0.8-1_amd64.deb ...
Unpacking libxkbfile-dev:amd64 (1:1.0.8-1) ...
Selecting previously unselected package x11proto-dri3-dev.
Preparing to unpack .../x11proto-dri3-dev_1.0-1_all.deb ...
Unpacking x11proto-dri3-dev (1.0-1) ...
Selecting previously unselected package x11proto-fonts-dev.
Preparing to unpack .../x11proto-fonts-dev_2.1.2-1_all.deb ...
Unpacking x11proto-fonts-dev (2.1.2-1) ...
Selecting previously unselected package x11proto-present-dev.
Preparing to unpack .../x11proto-present-dev_1.0-1_all.deb ...
Unpacking x11proto-present-dev (1.0-1) ...
Selecting previously unselected package x11proto-randr-dev.
Preparing to unpack .../x11proto-randr-dev_1.4.0+git20120101.is.really.1.4.0-0ubuntu1_all.deb ...
Unpacking x11proto-randr-dev (1.4.0+git20120101.is.really.1.4.0-0ubuntu1) ...
Selecting previously unselected package x11proto-render-dev.
Preparing to unpack .../x11proto-render-dev_2%3a0.11.1-2_all.deb ...
Unpacking x11proto-render-dev (2:0.11.1-2) ...
Selecting previously unselected package x11proto-resource-dev.
Preparing to unpack .../x11proto-resource-dev_1.2.0-3_all.deb ...
Unpacking x11proto-resource-dev (1.2.0-3) ...
Selecting previously unselected package x11proto-scrnsaver-dev.
Preparing to unpack .../x11proto-scrnsaver-dev_1.2.2-1_all.deb ...
Unpacking x11proto-scrnsaver-dev (1.2.2-1) ...
Selecting previously unselected package x11proto-video-dev.
Preparing to unpack .../x11proto-video-dev_2.3.2-1_all.deb ...
Unpacking x11proto-video-dev (2.3.2-1) ...
Selecting previously unselected package x11proto-xf86bigfont-dev.
Preparing to unpack .../x11proto-xf86bigfont-dev_1.2.0-3_all.deb ...
Unpacking x11proto-xf86bigfont-dev (1.2.0-3) ...
Selecting previously unselected package x11proto-xf86dri-dev.
Preparing to unpack .../x11proto-xf86dri-dev_2.1.1-2_all.deb ...
Unpacking x11proto-xf86dri-dev (2.1.1-2) ...
Selecting previously unselected package x11proto-xinerama-dev.
Preparing to unpack .../x11proto-xinerama-dev_1.2.1-2_all.deb ...
Unpacking x11proto-xinerama-dev (1.2.1-2) ...
Selecting previously unselected package libpciaccess-dev:amd64.
Preparing to unpack .../libpciaccess-dev_0.13.2-1_amd64.deb ...
Unpacking libpciaccess-dev:amd64 (0.13.2-1) ...
Selecting previously unselected package xserver-xorg-dev.
Preparing to unpack .../xserver-xorg-dev_2%3a1.15.1-0ubuntu2_amd64.deb ...
Unpacking xserver-xorg-dev (2:1.15.1-0ubuntu2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
Processing triggers for doc-base (0.10.5) ...
Processing 2 added doc-base files...
Registering documents with scrollkeeper...
Setting up libmirprotobuf0:amd64 (0.1.8+14.04.20140411-0ubuntu1) ...
Setting up libsigsegv2:amd64 (2.10-2) ...
Setting up m4 (1.4.17-2ubuntu1) ...
Setting up autoconf (2.69-6) ...
Setting up autotools-dev (20130810.1) ...
Setting up automake (1:1.14.1-2ubuntu1) ...
update-alternatives: using /usr/bin/automake-1.14 to provide /usr/bin/automake (automake) in auto mode
Setting up libxml-parser-perl (2.41-1build3) ...
Setting up intltool (0.50.2-2) ...
Setting up dh-translations (121) ...
Setting up python-scour (0.26-3build1) ...
Setting up cdbs (0.4.122ubuntu2) ...
Setting up dh-make (0.63) ...
Setting up dh-modaliases (1:0.2.91.4) ...
Setting up dkms (2.2.0.3-1.1ubuntu5) ...
Setting up execstack (0.0.20090925-8) ...
Setting up libprotobuf-lite8:amd64 (2.5.0-9ubuntu1) ...
Setting up libprotobuf-dev:amd64 (2.5.0-9ubuntu1) ...
Setting up libmirprotobuf-dev:amd64 (0.1.8+14.04.20140411-0ubuntu1) ...
Setting up mircommon-dev:amd64 (0.1.8+14.04.20140411-0ubuntu1) ...
Setting up libpixman-1-dev (0.30.2-2ubuntu1) ...
Setting up libxkbfile-dev:amd64 (1:1.0.8-1) ...
Setting up x11proto-dri3-dev (1.0-1) ...
Setting up x11proto-fonts-dev (2.1.2-1) ...
Setting up x11proto-present-dev (1.0-1) ...
Setting up x11proto-randr-dev (1.4.0+git20120101.is.really.1.4.0-0ubuntu1) ...
Setting up x11proto-render-dev (2:0.11.1-2) ...
Setting up x11proto-resource-dev (1.2.0-3) ...
Setting up x11proto-scrnsaver-dev (1.2.2-1) ...
Setting up x11proto-video-dev (2.3.2-1) ...
Setting up x11proto-xf86bigfont-dev (1.2.0-3) ...
Setting up x11proto-xf86dri-dev (2.1.1-2) ...
Setting up x11proto-xinerama-dev (1.2.1-2) ...
Setting up libpciaccess-dev:amd64 (0.13.2-1) ...
Setting up libmirclient7:amd64 (0.1.8+14.04.20140411-0ubuntu1) ...
Setting up libmirclient-dev:amd64 (0.1.8+14.04.20140411-0ubuntu1) ...
Setting up xserver-xorg-dev (2:1.15.1-0ubuntu2) ...
Setting up libmirclientplatform-mesa:amd64 (0.1.8+14.04.20140411-0ubuntu1) ...
update-alternatives: using /usr/lib/x86_64-linux-gnu/mir/clientplatform/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_mirclientplatform.conf (x86_64-linux-gnu_mirclientplatform_conf) in auto mode
Processing triggers for libc-bin (2.19-0ubuntu6.4) ...
chihwahli@lion:~$ sudo apt-get install lib32gcc1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 lib32gcc1 : Depends: gcc-4.9-base (= 4.9-20140406-0ubuntu1) but 4.9.1-0ubuntu1 is to be installed
             Depends: libc6-i386 (>= 2.2.4) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
chihwahli@lion:~$ mkdir catalyst14.12 && cd catalyst14.12
chihwahli@lion:~/catalyst14.12$ wget --referer='http://support.amd.com/en-us/download/desktop?os=Linux+x86' [http://www2.ati.com/drivers/linux/amd-catalyst-omega-14.12-linux-run-installers.zip](http://www2.ati.com/drivers/linux/amd-catalyst-omega-14.12-linux-run-installers.zip)
--2015-01-21 23:47:44--  [http://www2.ati.com/drivers/linux/amd-catalyst-omega-14.12-linux-run-installers.zip](http://www2.ati.com/drivers/linux/amd-catalyst-omega-14.12-linux-run-installers.zip)
Resolving www2.ati.com (www2.ati.com)... 23.36.153.7
Connecting to www2.ati.com (www2.ati.com)|23.36.153.7|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 155616187 (148M) [application/zip]
Saving to: ‘amd-catalyst-omega-14.12-linux-run-installers.zip’

100%[======================================>] 155.616.187 1,01MB/s   in 2m 27s 

2015-01-21 23:50:11 (1,01 MB/s) - ‘amd-catalyst-omega-14.12-linux-run-installers.zip’ saved [155616187/155616187]

chihwahli@lion:~/catalyst14.12$ unzip amd-catalyst-omega-14.12-linux-run-installers.zip
Archive:  amd-catalyst-omega-14.12-linux-run-installers.zip
   creating: fglrx-14.501.1003/
   creating: fglrx-14.501.1003/doc/
  inflating: fglrx-14.501.1003/doc/issues.html  
   creating: fglrx-14.501.1003/doc/articles/
  inflating: fglrx-14.501.1003/doc/articles/4470.html  
  inflating: fglrx-14.501.1003/doc/articles/no3d-kt400.html  
  inflating: fglrx-14.501.1003/doc/articles/dualheadvideo.html  
  inflating: fglrx-14.501.1003/doc/articles/4461.html  
  inflating: fglrx-14.501.1003/doc/articles/4481.html  
  inflating: fglrx-14.501.1003/doc/articles/r420blankdisplay.html  
  inflating: fglrx-14.501.1003/doc/articles/corruptstereo.html  
  inflating: fglrx-14.501.1003/doc/articles/xrestartpcie.html  
  inflating: fglrx-14.501.1003/doc/articles/4479.html  
  inflating: fglrx-14.501.1003/doc/articles/rv280dviblankdisplay.html  
  inflating: fglrx-14.501.1003/doc/articles/4480.html  
  inflating: fglrx-14.501.1003/doc/articles/xvsatshift.html  
  inflating: fglrx-14.501.1003/doc/articles/doom3corrupt.html  
  inflating: fglrx-14.501.1003/doc/articles/4482.html  
  inflating: fglrx-14.501.1003/doc/articles/4469.html  
  inflating: fglrx-14.501.1003/doc/articles/4484.html  
  inflating: fglrx-14.501.1003/doc/articles/dga3dhang.html  
  inflating: fglrx-14.501.1003/doc/articles/1gbhang.html  
  inflating: fglrx-14.501.1003/doc/articles/4483.html  
  inflating: fglrx-14.501.1003/doc/articles/4478.html  
  inflating: fglrx-14.501.1003/doc/articles/4463.html  
  inflating: fglrx-14.501.1003/doc/articles/laptopsuspend.html  
  inflating: fglrx-14.501.1003/doc/articles/rv350springdale.html  
  inflating: fglrx-14.501.1003/doc/articles/xf86_enodev.html  
  inflating: fglrx-14.501.1003/doc/articles/4462.html  
  inflating: fglrx-14.501.1003/doc/articles/devshm.html  
  inflating: fglrx-14.501.1003/doc/articles/no3d-aiw8500dv.html  
  inflating: fglrx-14.501.1003/doc/articles/corruptvtswitch.html  
  inflating: fglrx-14.501.1003/doc/articles/secondheadcorruption.html  
  inflating: fglrx-14.501.1003/doc/articles/4475.html  
  inflating: fglrx-14.501.1003/doc/articles/4464.html  
  inflating: fglrx-14.501.1003/doc/articles/4485.html  
  inflating: fglrx-14.501.1003/doc/articles/mousecursorhang.html  
  inflating: fglrx-14.501.1003/doc/articles/missingdrmheaders.html  
  inflating: fglrx-14.501.1003/doc/articles/nomembercount.html  
  inflating: fglrx-14.501.1003/doc/articles/pcie3dmemoryleak.html  
   creating: fglrx-14.501.1003/doc/user-manual/
  inflating: fglrx-14.501.1003/doc/user-manual/index.html  
  inflating: fglrx-14.501.1003/doc/user-manual/AMD_Linux_Driver_Specification.pdf  
  inflating: fglrx-14.501.1003/doc/configure.html  
  inflating: fglrx-14.501.1003/doc/LICENSE.TXT  
  inflating: fglrx-14.501.1003/doc/index.html  
  inflating: fglrx-14.501.1003/doc/tips-linux.html  
  inflating: fglrx-14.501.1003/doc/driverfaq.html  
  inflating: fglrx-14.501.1003/doc/linuxfaq.html  
  inflating: fglrx-14.501.1003/doc/installer.html  
   creating: fglrx-14.501.1003/doc/examples/
   creating: fglrx-14.501.1003/doc/examples/etc/
   creating: fglrx-14.501.1003/doc/examples/etc/init.d/
  inflating: fglrx-14.501.1003/doc/examples/etc/init.d/atieventsd.sh  
   creating: fglrx-14.501.1003/doc/examples/etc/acpi/
   creating: fglrx-14.501.1003/doc/examples/etc/acpi/events/
  inflating: fglrx-14.501.1003/doc/examples/etc/acpi/events/a-lid-aticonfig  
  inflating: fglrx-14.501.1003/doc/examples/etc/acpi/events/a-ac-aticonfig  
  inflating: fglrx-14.501.1003/doc/examples/etc/acpi/ati-powermode.sh  
  inflating: fglrx-14.501.1003/check.sh  
  inflating: fglrx-14.501.1003/amd-driver-installer-14.501.1003-x86.x86_64.run  
chihwahli@lion:~/catalyst14.12$ sudo ./fglrx-14.501.1003/amd-driver-installer-14.501.1003-x86.x86_64.run --buildpkg Ubuntu/trusty
Created directory fglrx-install.yoxZN0
Verifying archive integrity... All good.
Uncompressing AMD Catalyst(TM) Proprietary Driver-14.501.1003..........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/trusty
Package /home/chihwahli/catalyst14.12/fglrx-core_14.501-0ubuntu1_amd64.deb has been successfully generated
Package /home/chihwahli/catalyst14.12/fglrx_14.501-0ubuntu1_amd64.deb has been successfully generated
Package /home/chihwahli/catalyst14.12/fglrx-dev_14.501-0ubuntu1_amd64.deb has been successfully generated
Package /home/chihwahli/catalyst14.12/fglrx-amdcccle_14.501-0ubuntu1_amd64.deb has been successfully generated
Removing temporary directory: fglrx-install.yoxZN0
chihwahli@lion:~/catalyst14.12$ dpkg-deb -R fglrx-core_14.501-0ubuntu1_amd64.deb fglrx-core

chihwahli@lion:~/catalyst14.12$ sed -ri 's/(Conflicts|Provides).*/\1: fglrx-driver-core/' fglrx-core/DEBIAN/control
chihwahli@lion:~/catalyst14.12$ sudo dpkg-deb -b fglrx-core/ fglrx-core_14.501-0ubuntu1_amd64.deb
dpkg-deb: building package `fglrx-core' in `fglrx-core_14.501-0ubuntu1_amd64.deb'.
chihwahli@lion:~/catalyst14.12$ sudo dpkg -i fglrx*.deb
Selecting previously unselected package fglrx.
(Reading database ... 421855 files and directories currently installed.)
Preparing to unpack fglrx_14.501-0ubuntu1_amd64.deb ...
Unpacking fglrx (2:14.501-0ubuntu1) ...
Selecting previously unselected package fglrx-amdcccle.
Preparing to unpack fglrx-amdcccle_14.501-0ubuntu1_amd64.deb ...
Unpacking fglrx-amdcccle (2:14.501-0ubuntu1) ...
Selecting previously unselected package fglrx-core.
Preparing to unpack fglrx-core_14.501-0ubuntu1_amd64.deb ...
Unpacking fglrx-core (2:14.501-0ubuntu1) ...
Selecting previously unselected package fglrx-dev.
Preparing to unpack fglrx-dev_14.501-0ubuntu1_amd64.deb ...
Unpacking fglrx-dev (2:14.501-0ubuntu1) ...
dpkg: dependency problems prevent configuration of fglrx-core:
 fglrx-core depends on lib32gcc1; however:
  Package lib32gcc1 is not installed.
 fglrx-core depends on libc6-i386; however:
  Package libc6-i386 is not installed.

dpkg: error processing package fglrx-core (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx:
 fglrx depends on fglrx-core; however:
  Package fglrx-core is not configured yet.

dpkg: error processing package fglrx (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.

dpkg: error processing package fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx-core | fglrx; however:
  Package fglrx-core is not configured yet.
  Package fglrx is not configured yet.

dpkg: error processing package fglrx-dev (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 fglrx-core
 fglrx
 fglrx-amdcccle
 fglrx-dev
chihwahli@lion:~/catalyst14.12$ 


```

> **Temüjin said:**
> [http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Before_you_start](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Before_you_start)
Note that you may have to change the one command to use "--buildpkg Ubuntu/utopic" instead of Ubunty/trusty depending on what Ubuntu version you're running.

Restarted Ubuntu 14.04 , tried running Metro 2033 Redux, but I get a warning that I have to install OPENGL 4.0 or higher. Thanks so far. (I did execute the extra commands ,because I am using WINE)

---

### Post by Yellow Pasque on 2015-01-21
```
The following packages have unmet dependencies:
lib32gcc1 : Depends: gcc-4.9-base (= 4.9-20140406-0ubuntu1) but 4.9.1-0ubuntu1 is to be installed
```

I'm not really sure what's going on there, other than maybe you have not kept your system updated. Give the output from the second command:
```
sudo apt-get update
apt-cache policy lib32gcc1
```

---

### Post by chihwah_li on 2015-01-22
The output is:

> chihwahli@lion:~$ apt-cache policy lib32gcc1
lib32gcc1:
  Installed: (none)
  Candidate: 1:4.9-20140406-0ubuntu1
  Version table:
     1:4.9-20140406-0ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages



Output from the command : Sudo apt-get update

```
chihwahli@lion:~$ sudo apt-get update
[sudo] password for chihwahli: 
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1347 B]                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Sources               
Get:3 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1219 B]                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam amd64 Packages                  
Get:4 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1212 B]                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam i386 Packages                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                           
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted amd64 Packages        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release [15,1 kB]                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main amd64 Packages                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe amd64 Packages                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse amd64 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe i386 Packages        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse i386 Packages                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [17,9 kB]
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [17,9 kB]             
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en [11,2 kB]            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en_US                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en_US     
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en_US
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Fetched 66,4 kB in 5s (12,8 kB/s)
W: Failed to fetch [http://ppa.launchpad.net/boost-latest/ppa/ubuntu/dists/trusty/main/source/Sources](http://ppa.launchpad.net/boost-latest/ppa/ubuntu/dists/trusty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/boost-latest/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/boost-latest/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/boost-latest/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/boost-latest/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu/dists/trusty/main/source/Sources](http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu/dists/trusty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pali/graphics-drivers-stable/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/pali/graphics-drivers-stable/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pali/graphics-drivers-stable/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/pali/graphics-drivers-stable/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/gvfs-libmtp/ubuntu/dists/trusty/main/source/Sources](http://ppa.launchpad.net/webupd8team/gvfs-libmtp/ubuntu/dists/trusty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/gvfs-libmtp/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/webupd8team/gvfs-libmtp/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/gvfs-libmtp/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/webupd8team/gvfs-libmtp/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

Package manager suggested I execute, but still problems:

> chihwahli@lion:~$ sudo  apt-get install -f
[sudo] password for chihwahli: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  fglrx fglrx-amdcccle fglrx-core fglrx-dev
0 upgraded, 0 newly installed, 4 to remove and 54 not upgraded.
4 not fully installed or removed.
After this operation, 368 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 422129 files and directories currently installed.)
Removing fglrx-amdcccle (2:14.501-0ubuntu1) ...
Removing fglrx-dev (2:14.501-0ubuntu1) ...
Removing fglrx (2:14.501-0ubuntu1) ...
Removing fglrx-core (2:14.501-0ubuntu1) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for libc-bin (2.19-0ubuntu6.4) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-40-generic



---

### Post by tokyobadger on 2015-01-22
> **chihwah_li said:**
> Restarted Ubuntu 14.04 , tried running Metro 2033 Redux, but I get a warning that I have to install OPENGL 4.0 or higher. Thanks so far. (I did execute the extra commands ,because I am using WINE)
Your card supports up to OpenGL 4.2. Unless I missed it, you did not show us the out put of
```
glxinfo | grep OpenGL
```

I wonder if the WINE environment might not be an additional factor - don't use it so can't advise

---

### Post by deadflowr on 2015-01-22
From the output of your apt-get update
> E: Some index files failed to download. They have been ignored, or old ones used instead.

Those ppa listings do not have versions for trusty, so you need to disable them.
Open the program Software and Updates.
Go to the tab marked "Other Software"
and disable/uncheck the entries for the boost,pali,langdalepl, and webupd8 ppas.
Then close and re-run the apt-get update command.
Then try running the apt-get install -f command again.

Post the output if any thing weird happens...
If not, you can proceed with whatever it was you were going to do or try...

---

### Post by chihwah_li on 2015-01-24
I removed the PPA's boost,pali,langdalepl, and webupd8 ppas. 
Then executed sudo apt-get update, the results are ok, no error.

Executed and there are errors:
> chihwahli@lion:~$ sudo apt-get install lib32gcc1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 lib32gcc1 : Depends: gcc-4.9-base (= 4.9-20140406-0ubuntu1) but 4.9.1-0ubuntu1 is to be installed
             Depends: libc6-i386 (>= 2.2.4) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.



In the manual: [http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Before_you_start](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Before_you_start)
I have to execute above command first because I am using a 64 bit CPU and Linux OS. right?

---

### Post by Yellow Pasque on 2015-01-26
I think I would just use the pre-built version found in "Additional Drivers" dialog. Something odd is going on with 32-bit package version.

---

### Post by chihwah_li on 2015-01-26
The output of commands glxinfo | grep OpenGL:
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD CAPE VERDE
OpenGL core profile version string: 3.1 (Core Profile) Mesa 10.1.3
OpenGL core profile shading language version string: 1.40
OpenGL core profile context flags: (none)
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 10.1.3
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 10.1.3
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.0
OpenGL ES profile extensions:



> **tokyobadger said:**
> Your card supports up to OpenGL 4.2. Unless I missed it, you did not show us the out put of
```
glxinfo | grep OpenGL
```

I wonder if the WINE environment might not be an additional factor - don't use it so can't advise

I reinstalled Ubuntu 14.0.4, and selected the proprietary driver in System settings --> Software & updates --> tab additional drivers --> selected option Using video driver for AMD graphics accelerator for fglrx(proprietary)
Default Ubuntu installs Mesa OPENGL version 10.1.3, which only supports OPENGL 3.0 as far as I can understand.

I tried to run the game Metro 2033 redux, and again the message came that I need a OPENGL 4.0 driver.
I guess I have to switch to proprietary....?

I am also trying to update the Mesa drivers, but I get stuck at the command ./configure. It says I lack glproto package. Where can that package be found?

```
cc@cc-MS-7641:~/Downloads/Mesa-10.4.3$ ls
aclocal.m4         CleanSpec.mk  docs                      m4           src
Android.common.mk  common.py     doxygen                   Makefile.am  VERSION
Android.mk         config.log    include                   Makefile.in
autogen.sh         configure     install-gallium-links.mk  scons
bin                configure.ac  install-lib-links.mk      SConstruct
cc@cc-MS-7641:~/Downloads/Mesa-10.4.3$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking whether make supports nested variables... (cached) yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc understands -c and -o together... yes
checking dependency style of gcc... gcc3
checking for ar... ar
checking the archiver (ar) interface... ar
checking how to run the C preprocessor... gcc -E
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking whether gcc understands -c and -o together... (cached) yes
checking dependency style of gcc... (cached) gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking dependency style of gcc... gcc3
checking for GNU make... make
checking for python2... python2
checking for a sed that does not truncate output... /bin/sed
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking how to print strings... printf
checking for a sed that does not truncate output... (cached) /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for a working dd... /bin/dd
checking how to truncate binary pipes... /bin/dd bs=4096 count=1
checking for mt... mt
checking if mt is a manifest tool... no
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for bison... no
checking for byacc... no
checking if bison is the parser generator... no
checking for flex... no
checking for lex... no
checking if flex is the lexer generator... no
checking for indent... cat
checking if compiling with clang... no
checking whether gcc version is sufficient... yes
checking for __builtin_bswap32... yes
checking for __builtin_bswap64... yes
checking for __builtin_clz... yes
checking for __builtin_clzll... yes
checking for __builtin_ctz... yes
checking for __builtin_expect... yes
checking for __builtin_ffs... yes
checking for __builtin_ffsll... yes
checking for __builtin_popcount... yes
checking for __builtin_popcountll... yes
checking for __builtin_unreachable... yes
checking for __attribute__((flatten))... yes
checking for __attribute__((format))... yes
checking for __attribute__((malloc))... yes
checking for __attribute__((packed))... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking whether gcc supports -Werror=missing-prototypes... yes
checking whether gcc supports -fvisibility=hidden... yes
checking whether g++ supports -fvisibility=hidden... yes
checking if ld supports -Bsymbolic... yes
checking whether ld supports --gc-sections... yes
checking if the linker supports version-scripts... yes
checking if the linker supports --dynamic-list... yes
checking whether to enable assembly... yes, x86_64
checking xlocale.h usability... yes
checking xlocale.h presence... yes
checking for xlocale.h... yes
checking for strtof... yes
checking for dlopen... no
checking for dlopen in -ldl... yes
checking for dladdr... yes
checking for clock_gettime... yes
checking for posix_memalign... yes
checking for the pthreads library -lpthreads... no
checking whether pthreads work without any flags... no
checking whether pthreads work with -Kthread... no
checking whether pthreads work with -kthread... no
checking for the pthreads library -llthread... no
checking whether pthreads work with -pthread... yes
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE
checking if more special flags are required for pthreads... no
checking for PTHREAD_PRIO_INHERIT... no
checking for LIBDRM... no
checking for LIBUDEV... no
checking for GLPROTO... no
configure: error: Package requirements (glproto >= 1.4.14) were not met:

No package 'glproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLPROTO_CFLAGS
and GLPROTO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


```

sudo apt-get install x11proto-gl-dev

./configure (mesa)
Result: configure: error: Direct rendering requires libdrm >= 2.4.38

sudo apt-get install libdrm-dev

apt-cache search dri3proto
searched for dri3proto and result: x11proto-dri3-dev - X11 DRI3 extension wire protocol


sudo apt-get install x11proto-dri3-dev

---

### Post by Yellow Pasque on 2015-01-30
> nd again the message came that I need a OPENGL 4.0 driver. I guess I have to switch to proprietary....? 
For now, yes. Mesa/Gallium drivers are making good progress on OpenGL 4.x and hopefully, there will be 4.2 support soon. [http://cgit.freedesktop.org/mesa/mesa/tree/docs/GL3.txt](http://cgit.freedesktop.org/mesa/mesa/tree/docs/GL3.txt)

Oh, don't even try to compile mesa if you're not familiar with building software. It won't get you OpenGL 4.x, and you're reinventing the wheel because mesa is built fresh in this PPA: [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

---

### Post by monkeybrain20122 on 2015-01-30
> **Temüjin said:**
> Oh, don't even try to compile mesa if you're not familiar with building software. It won't get you OpenGL 4.x, and you're reinventing the wheel because mesa is built fresh in this PPA: [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

There seem to be some regressions lately so I suggest holding off adding the ppa and wait  [http://www.phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers/page146&](http://www.phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers/page146&)

I guess those regressions affect only very new cards (such as OP's?) My hardware is 3 + years old and I don't experience any problem.

---

### Post by chihwah_li on 2015-01-30
I restarted Ubuntu and the proprietary worked in Metro 2033 redux.... hmm ok. Not sure now if I had or had not restarted when installing proprietary drivers.
Thanks people

---

