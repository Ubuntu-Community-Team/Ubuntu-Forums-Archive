---
title: "handbrake compile fails"
date: 2006-08-03
forum: Desktop Environments
---

### Post by stmiller on 2006-08-03
Handbrake begins to compile okay, then barfs out this at the end:

```
c libhb/scan.o
Cc libhb/work.o
Cc libhb/decmpeg2.o
Cc libhb/encavcodec.o
Cc libhb/update.o
Cc libhb/demuxmpeg.o
Cc libhb/fifo.o
Cc libhb/render.o
Cc libhb/reader.o
Cc libhb/muxcommon.o
Cc libhb/muxmp4.o
libhb/muxmp4.c:8:17: error: mp4.h: No such file or directory
libhb/muxmp4.c:19: error: syntax error before ‘MP4FileHandle’
libhb/muxmp4.c:19: warning: no semicolon at end of struct or union
libhb/muxmp4.c:23: error: syntax error before ‘}’ token
libhb/muxmp4.c:27: error: syntax error before ‘MP4TrackId’
libhb/muxmp4.c:27: warning: no semicolon at end of struct or union
libhb/muxmp4.c: In function ‘MP4Init’:
libhb/muxmp4.c:37: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:45: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:45: warning: implicit declaration of function ‘MP4Create’
libhb/muxmp4.c:45: error: ‘MP4_DETAILS_ERROR’ undeclared (first use in this function)
libhb/muxmp4.c:45: error: (Each undeclared identifier is reported only once
libhb/muxmp4.c:45: error: for each function it appears in.)
libhb/muxmp4.c:48: error: invalid application of ‘sizeof’ to incomplete type ‘hb_mux_data_t’
libhb/muxmp4.c:55: warning: implicit declaration of function ‘MP4SetTimeScale’
libhb/muxmp4.c:55: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:61: warning: implicit declaration of function ‘MP4SetVideoProfileLevel’
libhb/muxmp4.c:61: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:63: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:63: warning: implicit declaration of function ‘MP4AddH264VideoTrack’
libhb/muxmp4.c:63: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:64: error: ‘MP4_INVALID_DURATION’ undeclared (first use in this function)
libhb/muxmp4.c:70: warning: implicit declaration of function ‘MP4AddH264SequenceParameterSet’
libhb/muxmp4.c:70: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:70: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:72: warning: implicit declaration of function ‘MP4AddH264PictureParameterSet’
libhb/muxmp4.c:72: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:72: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:79: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:79: error: ‘MPEG4_SP_L3’ undeclared (first use in this function)
libhb/muxmp4.c:80: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:80: warning: implicit declaration of function ‘MP4AddVideoTrack’
libhb/muxmp4.c:80: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:82: error: ‘MP4_MPEG4_VIDEO_TYPE’ undeclared (first use in this function)
libhb/muxmp4.c:85: warning: implicit declaration of function ‘MP4SetTrackESConfiguration’
libhb/muxmp4.c:85: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:85: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:93: error: invalid application of ‘sizeof’ to incomplete type ‘hb_mux_data_t’
libhb/muxmp4.c:96: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:96: warning: implicit declaration of function ‘MP4AddAudioTrack’
libhb/muxmp4.c:96: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:97: error: ‘MP4_MPEG4_AUDIO_TYPE’ undeclared (first use in this function)
libhb/muxmp4.c:98: warning: implicit declaration of function ‘MP4SetAudioProfileLevel’
libhb/muxmp4.c:98: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:99: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:99: error: dereferencing pointer to incomplete type
libhb/muxmp4.c: In function ‘MP4Mux’:
libhb/muxmp4.c:109: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:119: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:120: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:125: error: ‘MP4_INVALID_DURATION’ undeclared (first use in this function)
libhb/muxmp4.c:128: warning: implicit declaration of function ‘MP4WriteSample’
libhb/muxmp4.c:128: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:128: error: dereferencing pointer to incomplete type
libhb/muxmp4.c: In function ‘MP4End’:
libhb/muxmp4.c:140: warning: implicit declaration of function ‘MP4Close’
libhb/muxmp4.c:140: error: dereferencing pointer to incomplete type
libhb/muxmp4.c: In function ‘hb_mux_mp4_init’:
libhb/muxmp4.c:155: error: invalid application of ‘sizeof’ to incomplete type ‘hb_mux_object_t’
libhb/muxmp4.c:156: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:157: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:158: error: dereferencing pointer to incomplete type
libhb/muxmp4.c:159: error: dereferencing pointer to incomplete type

gcc -c -o libhb/muxmp4.o -Wall -g -O3 -funroll-loops -I./contrib/include -DSYS_LINUX -DWORDS_BIGENDIAN -DHB_VERSION=\"0.7.1\" -DHB_BUILD=2006022400 -D__LIBHB__ -Ilibhb libhb/muxmp4.c

...failed Cc libhb/muxmp4.o ...
Cc libhb/sync.o
Cc libhb/decsub.o
Cc libhb/deca52.o
Cc libhb/encfaac.o
Cc libhb/declpcm.o
Cc libhb/encx264.o
Cc libhb/decavcodec.o
Cc libhb/encxvid.o
Cc libhb/muxavi.o
Cc libhb/enclame.o
Cc libhb/muxogm.o
libhb/muxogm.c: In function ‘OGMInit’:
libhb/muxogm.c:173: warning: pointer targets in assignment differ in signedness
libhb/muxogm.c:208: warning: pointer targets in assignment differ in signedness
Cc libhb/encvorbis.o
Cc libhb/dvd.o
...skipped libhb.a for lack of libhb.a(muxmp4.o)...
Cc test/test.o
...skipped HBTest for lack of libhb.a...
...failed updating 2 target(s)...
...skipped 2 target(s)...
...updated 54 target(s)...
stmiller@mahler:~/Documents/HandBrake-0.7.1$ 

```


I've tried to figure out why libhb/muxmp4 are not being built and can't figure this out. Thanks for any input.

```
stmiller@mahler:~/Documents/HandBrake-0.7.1$ cat /proc/cpuinfo
processor       : 0
cpu             : 7447A, altivec supported
clock           : 533.333000MHz
revision        : 0.1 (pvr 8003 0101)
bogomips        : 36.73
timebase        : 18432000
machine         : PowerBook6,5
motherboard     : PowerBook6,5 MacRISC3 Power Macintosh
detected as     : 287 (iBook G4)
pmac flags      : 0000001b
L2 cache        : 512K unified
pmac-generation : NewWorld
stmiller@mahler:~/Documents/HandBrake-0.7.1$

```

```
stmiller@mahler:~/Documents/HandBrake-0.7.1$ uname -a
Linux mahler 2.6.15-23-powerpc #1 Tue May 23 13:46:54 UTC 2006 ppc GNU/Linux

```

---

### Post by stmiller on 2006-08-03
Crap, I think I got it. Needed libfaac or similar.

Edit: Well, that led me to this:

```
stmiller@mahler:~/Documents/HandBrake-0.7.1$ jam
...found 303 target(s)...
...using 26 temp target(s)...
...updating 4 target(s)...
LibMp4v2 contrib/lib/libmp4v2.a
SDL appears to be installed
Error - we have detected a version of faac that has libmp4v2 support
and no copy of mpeg4ip-config.  This means faac was built with
faad2 and the libraries will be incompatible.
Please reinstall faac without mp4v2 support

    cd `dirname contrib/mpeg4ip.tar.gz` && CONTRIB=`pwd` &&
    rm -rf mpeg4ip && tar xzf mpeg4ip.tar.gz && cd mpeg4ip &&
    ./bootstrap && make -C lib/mp4v2 libmp4v2.la &&
    cp lib/mp4v2/.libs/libmp4v2.a $CONTRIB/lib &&
    cp mpeg4ip_config.h include/mpeg4ip.h include/mpeg4ip_version.h \
      include/mpeg4ip_win32.h lib/mp4v2/mp4.h $CONTRIB/include &&
    strip -S $CONTRIB/lib/libmp4v2.a

...failed LibMp4v2 contrib/lib/libmp4v2.a ...
Cc libhb/muxmp4.o
libhb/muxmp4.c: In function ‘MP4Init’:
libhb/muxmp4.c:45: error: too few arguments to function ‘MP4Create’
libhb/muxmp4.c:63: warning: implicit declaration of function ‘MP4AddH264VideoTrack’
libhb/muxmp4.c:70: warning: implicit declaration of function ‘MP4AddH264SequenceParameterSet’
libhb/muxmp4.c:72: warning: implicit declaration of function ‘MP4AddH264PictureParameterSet’
libhb/muxmp4.c:79: error: ‘MPEG4_SP_L3’ undeclared (first use in this function)
libhb/muxmp4.c:79: error: (Each undeclared identifier is reported only once
libhb/muxmp4.c:79: error: for each function it appears in.)

gcc -c -o libhb/muxmp4.o -Wall -g -O3 -funroll-loops -I./contrib/include -DSYS_LINUX -DWORDS_BIGENDIAN -DHB_VERSION=\"0.7.1\" -DHB_BUILD=2006022400 -D__LIBHB__ -Ilibhb libhb/muxmp4.c

...failed Cc libhb/muxmp4.o ...
...skipped libhb.a for lack of libhb.a(muxmp4.o)...
...skipped HBTest for lack of libhb.a...
...failed updating 2 target(s)...
...skipped 2 target(s)...
stmiller@mahler:~/Documents/HandBrake-0.7.1$


```


Looks like the ubuntu ppc package of faac doesn't work with handbrake. Yuck.

---

### Post by revfrsanctus on 2006-09-26
I did some hunting on the internet and found this discussion ( [http://handbrake.m0k.org/forum/viewtopic.php?t=549]("http://handbrake.m0k.org/forum/viewtopic.php?t=549")).  It really helped me.

Temporarily removing the old /usr/lib/libmp4v2* and /usr/bin/faac allows handbrake to install.  You can put them back afterwards.  That doesn't really seem very neat, but it worked.

---

### Post by vik.vaughn on 2008-01-28
^ worked for me. thanks!

---

### Post by vik.vaughn on 2008-01-28
by the way, I made the idiot mistake of actually removing the files, which allows handbrake to work perfectly, but breaks avidemux. If you do the same, just use synaptic to re-install faac and libmp4v2.

---

