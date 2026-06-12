---
title: "ffmpeg compilation error"
date: 2009-05-31
forum: General Help
---

### Post by ActiveFrost on 2009-05-31
**Tutorial:** [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Now, after *make* have been executed, I get the following error ( *make* failed ) :
```
libavcodec/lcldec.c:136: error: ‘LclDecContext’ has no member named ‘zstream’
libavcodec/lcldec.c:138: error: ‘LclDecContext’ has no member named ‘zstream’
libavcodec/lcldec.c:141: error: ‘LclDecContext’ has no member named ‘zstream’
libavcodec/lcldec.c: In function ‘decode_frame’:
libavcodec/lcldec.c:155: warning: cast discards qualifiers from pointer target type
make: *** [libavcodec/lcldec.o] Error 1
```

Any ideas ?
Was able to compile it a few days ago, but now .. it seems to be broken !

---

### Post by FakeOutdoorsman on 2009-05-31
Did you customize anyting from the tutorial?  Did you follow the **Updating Your Installation** section of the tutorial when you tried to recompile? Show the output of:
```
cd ~/ffmpeg
svn info
```
It could be a problem with the FFmpeg revision that you are trying to compile.

---

### Post by Keith Hedger on 2009-05-31
You need to install the libavcodec dev files from the repos (libavcodec-dev)

---

### Post by ActiveFrost on 2009-05-31
- **FakeOutdoorsman**
I have done this process already 10 or more times - never had any problems, so .. no, I haven't made any customizations. Char by char as shown in the tutorial ..

- **Keith Hedger**
I had it, but .. mh .. seems that I've lost it somewhere :o
```
dainis@suncore:~$ sudo apt-get install libavcodec-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libavcodec-dev: Depends: libavutil-dev (= 3:0.svn20090303-1ubuntu6) but it is not going to be installed
E: Broken packages
```

How to fix this ?

---

### Post by mc4man on 2009-05-31
> It could be a problem with the FFmpeg revision that you are trying to compile. 
Post the info about svn revision

---

### Post by ActiveFrost on 2009-05-31
> **mc4man said:**
> Post the info about svn revision

```
Path: .
URL: svn://svn.ffmpeg.org/ffmpeg/trunk
Repository Root: svn://svn.ffmpeg.org/ffmpeg
Repository UUID: 9553f0bf-9b14-0410-a0b8-cfaf0461ba5b
Revision: 19069
Node Kind: directory
Schedule: normal
Last Changed Author: reimar
Last Changed Rev: 19069
Last Changed Date: 2009-05-31 22:51:21 +0300 (Sun, 31 May 2009)
```

---

### Post by mc4man on 2009-05-31
Well I'd defer to FO concerning his guide but can say there is no problem building 19069 (on intrepid atm

The only lines concerning that

> .............-c -o libavcodec/lcldec.o
libavcodec/lcldec.c
libavcodec/lcldec.c: In function ‘zlib_decomp’:
libavcodec/lcldec.c:136: warning: assignment discards qualifiers from pointer target type
libavcodec/lcldec.c: In function ‘decode_frame’:
libavcodec/lcldec.c:165: warning: cast discards qualifiers from pointer target type

Maybe think about this
> Did you follow the Updating Your Installation section of the tutorial when you tried to recompile?





---

### Post by ActiveFrost on 2009-05-31
> **mc4man said:**
> Well I'd defer to FO concerning his guide but can say there is no problem building 19069 (on intrepid atm

The only lines concerning that



Maybe think about this

Thanks !
About updating instead of recompiling - will try it tomorrow ;)
Regarding *libavcodec-dev* - does anybody know how to fix my problem ?

---

### Post by mc4man on 2009-05-31
First off **no** libav*-dev file is a dependency for building ffmpeg, only for building apps that depend on the ffmpeg libraires

If you followed the guide and the configure posted there then the various header files (the equivalent of installing a -dev package from the repo) would be found in /usr/local/include and the pkg-config files in /usr/local/lib/pkgconfig

If used --prefix=/usr as a configure option then they'd be found in same location but in just /usr

There's no need to add the repo -dev files for ffmpeg if your building your own version (in regards to building apps that depend on them and as stated for ffmpeg itself

---

### Post by ActiveFrost on 2009-05-31
> **mc4man said:**
> First off **no** libav*-dev file is a dependency for building ffmpeg, only for building apps that depend on the ffmpeg libraires

If you followed the guide and the configure posted there then the various header files (the equivalent of installing a -dev package from the repo) would be found in /usr/local/include and the pkg-config files in /usr/local/lib/pkgconfig

If used --prefix=/usr as a configure option then they'd be found in same location but in just /usr

There's no need to add the repo -dev files for ffmpeg if your building your own version (in regards to building apps that depend on them and as stated for ffmpeg itself

Appreciate your help ! Will take a closer look at ffmpeg and how it works ( backend ).

---

### Post by andrew.46 on 2009-05-31
Hi ActiveFrost,

Revisions 19068-9 of FFmpeg dealt with usage of zlib and should be resolved by now. I note that FakeOutdoorsman in his guide gives zlib1g-dev as an optional dependencies so perhaps as insurance you could compile against this library?

Andrew

---

### Post by ActiveFrost on 2009-05-31
> **andrew.46 said:**
> Hi ActiveFrost,

Revisions 19068-9 of FFmpeg dealt with usage of zlib and should be resolved by now. I note that FakeOutdoorsman in his guide gives zlib1g-dev as an optional dependencies so perhaps as insurance you could compile against this library?

Andrew

+1 - no more errors ( .deb is ready to go :) ). Thanks a lot ( saw that notice but never took it serious ) !

---

### Post by andrew.46 on 2009-05-31
Hi ActiveFrost,

> **ActiveFrost said:**
> +1 - no more errors ( .deb is ready to go :) ). Thanks a lot ( saw that notice but never took it serious ) !

Mind you the issue was probably resolved with or without the zlib library but its installation opens up a few possibilities anyway :-). 

You may be interested in looking at the svn FFmpeg logfiles to troubleshoot compilation problems / code changes in the future? It used to be a lot easier with a web interface but a DOS attack convinced the devs to disable it a while back and now there is the cli only. If you change to the FFmpeg source (as you did with 'svn info') and issue the following:

```

andrew@skamandros~/source/ffmpeg/ffmpeg$**[COLOR="Purple"] svn log -l 4[/COLOR]**
------------------------------------------------------------------------
r19071 | ramiro | 2009-06-01 06:19:16 +1000 (Mon, 01 Jun 2009) | 1 line

indent
------------------------------------------------------------------------
r19070 | ramiro | 2009-06-01 06:17:58 +1000 (Mon, 01 Jun 2009) | 1 line

Remove useless if(), leftover from the vhook removal.
------------------------------------------------------------------------
r19069 | reimar | 2009-06-01 05:51:21 +1000 (Mon, 01 Jun 2009) | 3 lines

add #if CONFIG_ZLIB_DECODER around zlib_decomp function.
Fixes compilation when zlib is not available.

------------------------------------------------------------------------
r19068 | reimar | 2009-06-01 04:17:33 +1000 (Mon, 01 Jun 2009) | 5 lines

mszh decompression: add a special case for an all-0 mask, i.e. 32 uncompressed
bytes in a row.
About 15% faster mszh_decomp on an Atom N270 for
http://samples.mplayerhq.hu/V-codecs/mszh-zlib/avimzsh_sample.avi

------------------------------------------------------------------------

```

you can often see what is going on and troubleshoot your own installation. If you want greater details some good-looking man has written a guide:

Linux Basics: A gentle introduction to accessing 'svn' repositories
[http://ubuntuforums.org/showthread.php?t=1167578](http://ubuntuforums.org/showthread.php?t=1167578)

which may be helpful :-).

Andrew

---

### Post by ActiveFrost on 2009-05-31
> **andrew.46 said:**
> Hi ActiveFrost,



Mind you the issue was probably resolved with or without the zlib library but its installation opens up a few possibilities anyway :-). 

You may be interested in looking at the svn FFmpeg logfiles to troubleshoot compilation problems / code changes in the future? It used to be a lot easier with a web interface but a DOS attack convinced the devs to disable it a while back and now there is the cli only. If you change to the FFmpeg source (as you did with 'svn info') and issue the following:

you can often see what is going on and troubleshoot your own installation. If you want greater details some good-looking man has written a guide:

Linux Basics: A gentle introduction to accessing 'svn' repositories
[http://ubuntuforums.org/showthread.php?t=1167578](http://ubuntuforums.org/showthread.php?t=1167578)

which may be helpful :-).

Andrew

Thanks for the link and a bit more information about svn ( actually, I've no clue what it is and what it does ) - definitely will take a look at it ;)

---

### Post by jayaraj313 on 2012-11-27
Please make use of the link below,

[http://allofit.blog.com]("http://allofit.blog.com/")

It covers ffmpeg compilation on ubuntu on a step by step basis. Hope that helps.

---

### Post by mc4man on 2012-11-27
Old thread, should & will be closed.
The ffmpeg compile instructions for ubuntu are maintained/updated as need be in the ffmpeg wiki

[http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

---

### Post by philinux on 2012-11-27
Mc4man is spot on.

Closed.

---

