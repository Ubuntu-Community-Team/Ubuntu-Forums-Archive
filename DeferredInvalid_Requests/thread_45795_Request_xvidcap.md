---
title: "Request: xvidcap"
date: 2005-07-01
forum: Deferred/Invalid Requests
---

### Post by rob martin on 2005-07-01
Hi

I'd like to make some instruction videos/demos/tutorials to encourage the use of FLOSS in a UK qualification.  Unfortunately with the _funny_  libc6 issue and the libavcodec1 requirements mean I cannot install the packages.   Could someone please backport this package (preferably with gvidcap as well  ;-) 

Failing that could someone explain how I could do it myself (without decending into dependency hell) I have a Slackware background so am familiar with ./configure make make install, so compiling the binary isn't a problem, just the package management,  which is, as I'm sure you'll understand, rather new to me   :| 

Thanks

rob

---

### Post by maruchan on 2005-07-12
I really hope this gets done. I'd like to be able to use it, too.

---

### Post by bdamon on 2005-07-17
[QUOTE=maruchan]I really hope this gets done. I'd like to be able to use it, too.[/QUOTE]


Ditto

---

### Post by GeneralZod on 2005-07-18
[QUOTE=bdamon]Ditto[/QUOTE]

Likewise :)

---

### Post by lotusleaf on 2005-07-18
Moo

...

I mean, yeah me too. ;-)

---

### Post by maruchan on 2005-07-18
I was able to get XVidCap working in Hoary by using the latest deb from the XVidCap website, installing libpng2 (or something like that) and using the tips from this website:

[http://dennisgdaniels.com/tiki-index.php?page=xvidcap](http://dennisgdaniels.com/tiki-index.php?page=xvidcap)

Hope that helps.

---

### Post by Osmodia on 2005-07-26
And how? I need to install libavcodec1, but I can't...

Please post your /etc/apt/sources.list

---

### Post by maruchan on 2005-07-26
With pleasure. Hope it helps. It's been nice to have XVidCap running!

> 
## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) ho## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse

##Backup Ubuntu Mirrors
#deb [http://mirrors.xmission.com/ubuntu](http://mirrors.xmission.com/ubuntu) hoary-updates main restricted universe multiverse
#deb-src [http://mirrors.xmission.com/ubuntu](http://mirrors.xmission.com/ubuntu) hoary-updates main restricted universe multiverse

##Security Mirrors
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe

##Backup Security Mirrors
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe

#Kubuntu KDE341 Updates
deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main

##Backports
#deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted
#deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted

## Backports (Alternate Mirror)
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

deb [http://kubuntu.org/hoary-koffice14](http://kubuntu.org/hoary-koffice14) hoary-updates main

#deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
#deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/ary-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse

##Backup Ubuntu Mirrors
#deb [http://mirrors.xmission.com/ubuntu](http://mirrors.xmission.com/ubuntu) hoary-updates main restricted universe multiverse
#deb-src [http://mirrors.xmission.com/ubuntu](http://mirrors.xmission.com/ubuntu) hoary-updates main restricted universe multiverse

##Security Mirrors
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe

##Backup Security Mirrors
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe

#Kubuntu KDE341 Updates
deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main

##Backports
#deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted
#deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted

## Backports (Alternate Mirror)
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

deb [http://kubuntu.org/hoary-koffice14](http://kubuntu.org/hoary-koffice14) hoary-updates main

#deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
#deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

---

### Post by jdong on 2005-07-26
This isn't in Ubuntu....

EDIT: Oh, marillat, nvm

I'll attempt a build.

---

### Post by jdong on 2005-07-26
```

xtoffmpeg.c:1120: warning: passing arg 2 of `av_write_frame' makes pointer from integer without a cast
xtoffmpeg.c:1120: error: too many arguments to function `av_write_frame'
codecs.h:27: warning: unused variable `tCodecNames'
codecs.h:38: warning: unused variable `tCodec2ffmpeg'
xtoffmpeg.c:585: warning: unused variable `i'
xtoffmpeg.c: At top level:
xtoffmpeg.c:1135: warning: return type defaults to `int'
xtoffmpeg.c:1188:25: warning: "/*" within comment
xtoffmpeg.c:134: warning: `audio_grab_format' defined but not used
make[3]: *** [xvidcap-xtoffmpeg.o] Error 1
make[3]: Leaving directory `/home/jdong/ubp-compile-temp/xvidcap-1.1.3/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jdong/ubp-compile-temp/xvidcap-1.1.3'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/jdong/ubp-compile-temp/xvidcap-1.1.3'
make: *** [build-stamp] Error 2
Traceback (most recent call last):
  File "/usr/local/bin/ubp-build.py", line 270, in ?
    build()
  File "/usr/local/bin/ubp-build.py", line 167, in build
    raise Exception("Build command FAILED")
Exception: Build command FAILED

```

Doesn't build.

---

### Post by Osmodia on 2005-07-26
xvidcap works now, but i don't find something to convert my captured jpgs to avi or mpg.

mencoder "mf://*.jpg" -mf fps=25 -o output.avi -ovc lavc

> 
1 duplicate frame(s)!
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
mp_image: Unknown out_fmt: 0x0ps Trem:   0min   0mb  A-V:0,000 [0:0]

1 duplicate frame(s)!
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
mp_image: Unknown out_fmt: 0x0ps Trem:   0min   0mb  A-V:0,000 [0:0]

1 duplicate frame(s)!
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
mp_image: Unknown out_fmt: 0x0ps Trem:   0min   0mb  A-V:0,000 [0:0]

....


???

---

### Post by maruchan on 2005-07-27
Why don't you just capture straight to video? Don't you have any codecs?

---

### Post by strikeforce on 2005-08-09
Bit more feedback for you.

```

marc@ubuntu:~$ sudo dpkg -i xvidcap_1.1.3-p7_i386.deb
dpkg: status database area is locked by another process
marc@ubuntu:~$ sudo dpkg -i xvidcap_1.1.3-p7_i386.deb
Selecting previously deselected package xvidcap.
(Reading database ... 89682 files and directories currently installed.)
Unpacking xvidcap (from xvidcap_1.1.3-p7_i386.deb) ...
dpkg: dependency problems prevent configuration of xvidcap:
 xvidcap depends on libavcodec1 (>= 1:0.4.8); however:
  Package libavcodec1 is not installed.
dpkg: error processing xvidcap (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xvidcap

```

Thats from their new package which is supposedly going to be configured on debian stable.

---

### Post by flosoft on 2005-09-23
[QUOTE=strikeforce]Bit more feedback for you.

```

marc@ubuntu:~$ sudo dpkg -i xvidcap_1.1.3-p7_i386.deb
dpkg: status database area is locked by another process
marc@ubuntu:~$ sudo dpkg -i xvidcap_1.1.3-p7_i386.deb
Selecting previously deselected package xvidcap.
(Reading database ... 89682 files and directories currently installed.)
Unpacking xvidcap (from xvidcap_1.1.3-p7_i386.deb) ...
dpkg: dependency problems prevent configuration of xvidcap:
 xvidcap depends on libavcodec1 (>= 1:0.4.8); however:
  Package libavcodec1 is not installed.
dpkg: error processing xvidcap (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xvidcap

```

Thats from their new package which is supposedly going to be configured on debian stable.[/QUOTE]

Well isn't there anyone who has a correctly building .deb?

---

### Post by eukreign on 2005-10-20
I was able to install the [xvidcap_1.1.3-1_i386.deb](http://www.jarre-de-the.net/computing/debian/dists/stable/main/binary-i386/xvidcap_1.1.3-1_i386.deb) and the program runs, but when i click the record button it crashes with the following error message:

```

lex@hortus:~$ gvidcap
gvidcap: symbol lookup error: gvidcap: undefined symbol: __fixunssfdi

```

Any ideas on what could be causing this? From quickly looking on google __fixunssfdi looks like a gcc/libc thing which makes me wonder if the xvidcap debian package was compiled with a different version of gcc/libc than what I have in Ubuntu 5.10.

Any suggestions would be greatly appreciated.

---

### Post by SilvioTO on 2005-10-22
if you use breezy install istambul for this work.

---

### Post by eukreign on 2005-10-23
[QUOTE=SilvioTO]if you use breezy install istambul for this work.[/QUOTE]

Which repository is this in? This is what I have right now:

```

deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main universe restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main universe restricted

```

---

### Post by joflow on 2005-10-23
[QUOTE=eukreign]Which repository is this in? This is what I have right now:

```

deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main universe restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main universe restricted

```[/QUOTE]


He misspelled it.  Its called istanbul.

I installed it and its not so great.  Kills the CPU even for low res recordings.  Low res recordings look bad.

Any chance of xvidcap ever making it in extras? or does anyone know a repo with xvidcap that works.  I really need this functionality.

---

### Post by eukreign on 2005-10-23
[QUOTE=joflow]He misspelled it.  Its called istanbul.

I installed it and its not so great.  Kills the CPU even for low res recordings.  Low res recordings look bad.

Any chance of xvidcap ever making it in extras? or does anyone know a repo with xvidcap that works.  I really need this functionality.[/QUOTE]

Okay, I thought he ment that if i install istanbul than i would be able to use xvidcap.

---

### Post by eukreign on 2005-10-25
Anyone know if there are plans to add a xvidcap package to Ubuntu yet?

---

### Post by Alexander Grundner on 2006-05-24
[QUOTE=eukreign]I was able to install the [xvidcap_1.1.3-1_i386.deb](http://www.jarre-de-the.net/computing/debian/dists/stable/main/binary-i386/xvidcap_1.1.3-1_i386.deb) and the program runs, but when i click the record button it crashes with the following error message:

```

lex@hortus:~$ gvidcap
gvidcap: symbol lookup error: gvidcap: undefined symbol: __fixunssfdi

```

Any ideas on what could be causing this? From quickly looking on google __fixunssfdi looks like a gcc/libc thing which makes me wonder if the xvidcap debian package was compiled with a different version of gcc/libc than what I have in Ubuntu 5.10.

Any suggestions would be greatly appreciated.[/QUOTE]
I'm going through the same headache with the .deb version of xvidcap. I can record when lauching xvidcap but not with **gvidcap**. You're right, though, the issue is with the libgcc version - [see xvidcap FAQ on how to correct this](http://www.jarre-de-the.net/faq/index.php?aktion=artikel&rubrik=004&id=9&lang=en).

---

### Post by problemdog on 2006-06-18
Hi!

I had the same issue with gvidcap (while xvidcap working) - but now I got the CVS version and managed to compile. And it works! I mean gvidcap. Ubuntu. 6.06. (Still can't believe it).

Check out CVS version (1.1.4+) (see [http://sourceforge.net/cvs/?group_id=81535](http://sourceforge.net/cvs/?group_id=81535)) into some directory of yours.

Enter:
```
./configure --with-gtk2 --with-forced-embedded-ffmpeg --enable-static-libs=libpng
```

then:
```
make gvidcap
```

If all goes well, in the src directory there's a working gvidcap binary.

(Also, I had to install liblame-dev prior to this)

---

### Post by Alexander Grundner on 2006-06-19
Sweet. I'll give it a shot. 

Anyone know if xvidcap is going to be added to the Dapper repository or if it's still under development? I see on the sourceforge project page that the last release was back in Jan. of 2005 (ouch).

---

### Post by Drakx on 2006-07-11
Good news xvidcap has been updated and works fine under dapper you need lame0 and liblame-dev to run then open a terminal and type xvidcap which will bring up the GTK version as the other version is no longer included or you can download the souce and compile like so:
```

./configure --with-gtk2 --with-forced-embedded-ffmpeg --enable-static-libs=libpng
make
make install

```
Ive tryed both the provided deb and source and they work fine for source you will need libgtk2.0-dev and libgnomeui.

Hope this solves any problems, I'd also like to say if xvidcap is not your cuppa tea then take a look here [http://www.demorecorder.com/](http://www.demorecorder.com/) this thing is one of the best utils ive used for linux screencast how ever you've gotta pay for it after 30days.

---

### Post by Alexander Grundner on 2006-07-11
You're right! Xvidcap just got an update to version 1.1.4pre3 (July 7, 2006). Thanks for the heads up. I also checked out DemoRecorder -- very impressive. I'm debating if I should fork out the $79, though. It might be worth it since it gives users the option to save recordings in AVI, FLV, MPEG-2. Plus, the app can set you up with a generic html template and a swf player that you can easily integrate into any webpage.

Update 1: For some reason I'm getting an **unexpected quit notice** when I stop recording. Installed the .deb version and made sure lame0, liblame-dev, libgtk2.0-dev were present beforehand.

Update 2: I'm trying to install from source and I encountered a XML parser perl error during config. Corrected it with *apt-get install libxml-parser-perl*. However, now I'm getting errors about not meeting package requirments that look like they should be covered by *libgtk2.0-dev* as suggested earlier. Any ideas?
```

checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.4.0 libgnome-2.0 libgnomeui-2.0 libglade-2.0 glib-2.0) were not met:

No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'libglade-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

---

### Post by Drakx on 2006-07-12
Hi

Yes i should of said this also but it slipped my mind :) you will also need the following packages

```

sudo apt-get install libgnome2-dev libgnomeui-dev libglade2-dev libxml-parser-perl libgtk2.0-dev libxmu-dev lame liblame-dev

```
OR for a full list of all packages needed and version numbers :)

```

libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.9.0), 
libbonobo2-0 (>= 2.13.0), libbonoboui2-0 (>= 2.5.4), libc6 (>= 2.3.4-1),
libcairo2 (>= 1.0.2-2), libfontconfig1 (>= 2.3.0), libgconf2-4 (>= 2.13.5),
libglade2-0 (>= 1:2.5.1), libglib2.0-0 (>= 2.10.0), 
libgnome-keyring0 (>= 0.4.3), libgnome2-0 (>= 2.8.0), 
libgnomecanvas2-0 (>= 2.11.1), libgnomeui-0 (>= 2.13.0), 
libgnomevfs2-0 (>= 2.13.92-0ubuntu4), libgtk2.0-0 (>= 2.8.0), libice6,
liblame0 (>= 3.96.1-1), liborbit2 (>= 1:2.10.0), 
libpango1.0-0 (>= 1.12.3), libpopt0 (>= 1.7), libsm6, libx11-6, 
libxcursor1 (>> 1.1.2), libxext6, libxfixes3, libxi6, libxinerama1, 
libxml2 (>= 2.6.24), libxmu6, libxrandr2, libxrender1, 
zlib1g (>= 1:1.2.1)
```

Then compile with
```

./configure --with-gtk2 --with-forced-embedded-ffmpeg --enable-static-libs=libpng

make

make install

```

then try a recompile :) and every thing should be fine.

---

### Post by Rever75 on 2006-08-01
Ok I followed all instructions here but am not getting a gvidcap file. All I get is an xvidcap. Yes I use option ./configure --with-gtk2 and still not gvidcap. Please help.

Sorry new command is xvidcap --gui

---

