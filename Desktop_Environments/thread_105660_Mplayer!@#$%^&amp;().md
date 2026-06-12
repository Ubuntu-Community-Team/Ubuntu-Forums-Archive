---
title: "Mplayer!@#$%^&amp;*()"
date: 2005-12-18
forum: Desktop Environments
---

### Post by rudeboyskunk on 2005-12-18
**Ok, so I'm having a tough time with MPlayer.  When I do ./configure, I get this:**

rudeboyskunk@ashbysucks:~/MPlayer-1.0pre7try2$ ./configure
Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... 4.0.2, bad
Checking for gcc version ... 4.0.2, bad
Checking for gcc-3.4 version ... 3.4.5, ok
Checking for host cc ... gcc-3.4
Checking for CPU vendor ... GenuineIntel (15:1:2)
Checking for CPU type ...  Intel(R) Pentium(R) 4 CPU 1.80GHz
Checking for GCC & CPU optimization abilities ... pentium4
Checking for kernel support of mmx ... yes
Checking for kernel support of mmx2 ... yes
Checking for kernel support of sse ... yes
Checking for kernel support of sse2 ... yes
Checking for mtrr support ... yes
Checking for assembler support of -pipe option ... yes
Checking for assembler (as 2.16.1) ... ok
Checking for Linux kernel version ... 2.6.12-10-386, ok
Checking for mplayer binary name ... mplayer
Checking for awk ... mawk
Checking for extra headers ... none
Checking for extra libs ... none
Checking for -lposix ... no
Checking for -lm ... yes
Checking for i18n ... yes
Checking for iconv ... yes
Checking for langinfo ... yes
Checking for language ... using en (man pages:  en)
Checking for enable sighandler ... yes
Checking for runtime cpudetection ... no
Checking for restrict keyword ... __restrict
Checking for __builtin_expect ... yes
Checking for kstat ... no
Checking for posix4 ... no
Checking for lrintf ... yes
Checking for nanosleep ... yes
Checking for socklib ... yes (using -lnsl)
Checking for inet_pton() ... yes (using -lnsl)
Checking for inttypes.h (required) ... yes
Checking for int_fastXY_t in inttypes.h ... yes
Checking for word size ... 32
Checking for stddef.h ... yes
Checking for malloc.h ... yes
Checking for memalign() ... yes
Checking for alloca.h ... yes
Checking for mman.h ... yes
Checking for dynamic loader ... yes
Checking for dynamic a/v plugins support ... no
Checking for pthread ... yes (using -lpthread)
Checking for sys/soundcard.h ... yes
Checking for sys/dvdio.h ... no
Checking for sys/cdio.h ... no
Checking for linux/cdrom.h ... yes
Checking for dvd.h ... no
Checking for BSDI dvd.h ... no
Checking for HPUX SCSI header ... no
Checking for userspace SCSI headers (Solaris) ... no
Checking for termcap ... yes (using -ltermcap)
Checking for termios ... yes (using sys/termios.h)
Checking for shm ... yes
Checking for linux devfs ... no
Checking for scandir() ... yes
Checking for strsep() ... yes
Checking for strlcpy() ... no
Checking for strlcat() ... no
Checking for fseeko() ... yes
Checking for localtime_r() ... yes
Checking for vsscanf() ... yes
Checking for swab() ... yes
Checking for posix select() ... yes
Checking for gettimeofday() ... yes
Checking for glob() ... yes
Checking for sys/sysinfo.h ... yes
Checking for Mac OS X APIs ... no
Checking for Mac OS X Finder Support ... no
Checking for Mac OS X Bundle file locations ... no
Checking for Samba support (libsmbclient) ... no
Checking for 3dfx ... no
Checking for tdfxfb ... no
Checking for tdfxvid ... no
Checking for tga ... yes
Checking for DirectFB headers presence ... not found
Checking for DirectFB ... no
Checking for X11 headers presence ... yes (using /usr/include)
Checking for X11 libs presence ... yes (using /usr/lib)
Checking for X11 ... yes
Checking for DPMS ... yes (using Xdpms 4)
Checking for Xv ... yes
Checking for XvMC ... no
Checking for Xinerama ... no
Checking for Xxf86vm ... no
Checking for XF86keysym ... yes
Checking for DGA ... no
Checking for OpenGL ... yes
Checking for /dev/mga_vid ... no
Checking for xmga ... no
Checking for GGI ... no
Checking for AA ... yes
Checking for CACA ... no
Checking for SVGAlib ... no
Checking for FBDev ... yes
Checking for DVB ... no (specify path to DVB/ost/include with --with-dvbincdir=DIR)
Checking for DVB HEAD ... yes
Checking for PNG support ... yes
Checking for JPEG support ... yes
Checking for PNM support ... yes
Checking for md5sum support ... yes
Checking for GIF support ... yes
Checking for broken giflib workaround ... disabled
Checking for VESA support ... yes
Checking for SDL ... yes (using sdl-config)
Checking for Windows waveout ... no
Checking for Directx ... no
Checking for NAS ... yes
Checking for DXR2 ... no
Checking for DXR3/H+ ... no
Checking for libmp1e ... no
Checking for libfame ... no
Checking for OSS Audio ... yes
Checking for aRts ... yes
Checking for EsounD ... yes
Checking for esd_get_latency() ... yes
Checking for Polyp ... no
Checking for JACK ... no
Checking for ALSA audio ... yes (using alsa 1.0.x and alsa/asoundlib.h)
Checking for Sun audio ... no
Checking for Sun mediaLib ... no
Checking for SGI audio ... no
Checking for VCD support ... ok
Checking for DVD support (libmpdvdkit) ... yes
Checking for DVD support (libdvdread) ... disabled by libmpdvdkit2
Checking for cdparanoia ... no
Checking for freetype >= 2.0.9 ... yes
Checking for fontconfig ... no
Checking for fribidi with charsets ... no
Checking for ENCA ... no
Checking for zlib ... yes
Checking for RTC ... yes
Checking for external liblzo support ... no
Checking for mad support ... no
Checking for Toolame ... no
Checking for OggVorbis support ... yes (internal Tremor)
Checking for OggTheora support (only the CVS version!) ... no
Checking for mp3lib support ... yes
Checking for liba52 support ... yes
Checking for libdts support ... no
Checking for libmpeg2 support ... yes
Checking for Matroska support ... yes
Checking for internal FAAD2 (AAC) support ... yes
Checking for external FAAD2 (AAC) support ... no
Checking for LADSPA plugin support ... no
Checking for Win32 codec DLL support ... yes (using /usr/local/lib/codecs)
Checking for Win32 loader support ... yes
Checking for DirectShow ... yes
Checking for XAnim DLL ... yes (using /usr/local/lib/codecs)
Checking for RealPlayer DLL ... yes (using /usr/local/lib/codecs)
Checking for LIVE.COM Streaming Media libraries ... no
Checking for FFmpeg libavcodec (static) ... yes
Checking for FFmpeg libavformat (static) ... yes
Checking for amr narrowband ... no
Checking for amr narrowband, fixed point ... no
Checking for amr wideband ... no
Checking for libdv-0.9.5+ ... yes
Checking for zr ... no
Checking for bl ... no
Checking for XviD ... no
Checking for x264 ... no
Checking for DivX4linux/DivX5linux/OpenDivX decore ... DivX5linux (with libdivxdecore.so)
Checking for libmp3lame (for mencoder) ... no
Checking for DivX4linux encore (for mencoder) ... no
Checking for mencoder ... yes
Checking for fastmemcpy ... yes
Checking for UniquE RAR File Library ... yes
Checking for TV interface ... yes
Checking for EDL support ... yes
Checking for *BSD BrookTree 848 TV interface ... no
Checking for Video 4 Linux TV interface ... no
Checking for Video 4 Linux 2 TV interface ... no
Checking for audio select() ... yes
Checking for network ... yes
Checking for ftp ... yes
Checking for vstream client ... no
Checking for byte order ... little-endian
Checking for shared postprocess lib ... no
Checking for OSD menu ... no
Checking for QTX codecs ... yes
Checking for Subtitles sorting ... yes
Checking for XMMS inputplugin support ... no
Checking for inet6 ... yes
Checking for gethostbyname2 ... yes
Checking for GUI ... no
Checking for automatic gdb attach ... no
Checking for compiler support for -fno-PIC ... yes
Checking for ftello() ... yes
Checking for VIDIX ... yes
Checking for joystick ... no
Checking for lirc ... no
Checking for lircc ... no
Creating config.mak
Creating config.h
Creating libvo/config.mak
Creating libao2/config.mak
Creating libaf/config.mak

Config files successfully generated by ./configure !

  Install prefix: /usr/local
  Data directory: /usr/local/share/mplayer
  Config direct.: /usr/local/etc/mplayer

  Byte order: little-endian
  Optimizing for: pentium4 mmx mmx2 sse sse2 mtrr

  Languages:
    Messages/GUI: en
    Manual pages:  en

  Enabled optional drivers:
    Input: ftp network edl tv matroska mpdvdkit2 vcd dvb
    Codecs: qtx divx5linux libdv libavcodec real xanim dshow/dmo win32 faad2(internal) libmpeg2 liba52 mp3lib tremor(internal) gif
    Audio output: alsa esd arts oss nas sdl mpegpes(dvb)
    Video output: xvidix cvidix sdl vesa gif89a md5sum pnm jpeg png mpegpes(dvb) fbdev aa opengl xv x11 xover tga
    Audio filters:
  Disabled optional drivers:
    Input: vstream tv-v4l2 tv-v4l tv-bsdbt848 live.com cdda dvdread smb
    Codecs: divx4linux x264 xvid amr_wb amr_nb libdts libtheora toolame libmad liblzo
    Audio output: sgi sun jack polyp dxr2 dsound win32 macosx
    Video output: winvidix bl zr zr2 dxr3 dxr2 directx svga caca ggi xmga mga dga xvmc directfb tdfx_vid tdfxfb 3dfx quartz
    Audio filters: ladspa

'config.h' and 'config.mak' contain your configuration options.
Note: If you alter theses files (for instance CFLAGS) MPlayer may no longer
      compile *** DO NOT REPORT BUGS if you tweak these files ***

'make' will now compile MPlayer and 'make install' will install it.
Note: On non-Linux systems you might need to use 'gmake' instead of 'make'.

Please check mtrr settings at /proc/mtrr (see DOCS/HTML/en/video.html#mtrr)


Check configure.log if you wonder why an autodetection failed (check whether
the development headers/packages are installed).

If you suspect a bug, please read DOCS/HTML/en/bugreports.html.


**Then I do make, and I get:**

rudeboyskunk@ashbysucks:~/MPlayer-1.0pre7try2$ make
bash: make: command not found
rudeboyskunk@ashbysucks:~/MPlayer-1.0pre7try2$
[B]
Anybody know the solution to this problem?  I have the essential codecs in /usr/local/lib/codecs, am I supposed to have "all" codecs?  I thought there would be a makefile in /usr/local/share/mplayer, but there's no mplayer directory in /usr/local/share, and there's no /usr/local/etc/mplayer either.[/B]

---

### Post by duminas on 2005-12-18
```
sudo aptitude install build-essential
```Then try again.

---

### Post by hoodwink on 2005-12-18
[QUOTE=duminas]```
sudo aptitude install build-essential
```Then try again.[/QUOTE]
That should fix the compile problem. 

The question is: why do you want to compile mplayer? The ubuntu package works just fine (on Breezy and even on Dapper) as long as you have the codecs installed.

Just having fun with compiles?

---

### Post by duminas on 2005-12-19
[QUOTE=hoodwink]The question is: why do you want to compile mplayer?[/QUOTE]I'm not saying it won't work for him, or you, but just chiming in here. ;)

For me, it breaks rather terribly.
1) Font paths are broken on install for some odd reason.
2) I can't "Full screen" the video, since it just puts black bars around it and retains the original size.
3) No OSD at all.
4) (Compiled and from the package) A/V not synched.

This, and the version in the repos has some screwy dependencies. Sure, you can *use* parts of XMMS, but why are you depending on it when they're totally optional? And I'm not sure of dates here, but isn't pre7try2 newer than what's in the repos? This is all with the proper codecs installed, albeit manually since the w32codecs package has disappeared.

Ah, well.

---

### Post by Zonkle on 2005-12-19
Man I had the same annoying process of installing MPlayer.

Look here how I got this issue solved: [http://ubuntuforums.org/showthread.php?t=105479](http://ubuntuforums.org/showthread.php?t=105479)

Cya ;)

---

### Post by Knomefan on 2005-12-19
[QUOTE=duminas]
For me, it breaks rather terribly.
1) Font paths are broken on install for some odd reason.
2) I can't "Full screen" the video, since it just puts black bars around it and retains the original size.
3) No OSD at all.
4) (Compiled and from the package) A/V not synched.
[/QUOTE]
1. Doesn't apt-get install mplayer-fonts fix this?
2. Either allow it to zoom in your config file (/etc/mplayer/mplayer.conf for global options, or ~.mplayer/config for user specific options) with zoom=yes, or use xv as the outpot driver (which is probably the fastest option) with vo=xv
3. No idea
4. Sorry, no idea, but maybe using xv fixes this (Btw., I don't have this problem)

---

### Post by poptones on 2005-12-19
Last time I tried the mplayer in the repos mencoder wasn't even there - when I tried to recompress a vob all I got were "mencoder: command not found." I also had the resize problem mentioned above, not to mention cpu usage was considerably higher than expected.

I always build mplayer when I install a system. It's not too difficult (I wrote a script a long time ago) and when it's done you know you have a decent build system in place.

---

### Post by duminas on 2005-12-19
[QUOTE=Knomefan]1. Doesn't apt-get install mplayer-fonts fix this?
2. Either allow it to zoom in your config file (/etc/mplayer/mplayer.conf for global options, or ~.mplayer/config for user specific options) with zoom=yes, or use xv as the outpot driver (which is probably the fastest option) with vo=xv
3. No idea
4. Sorry, no idea, but maybe using xv fixes this (Btw., I don't have this problem)[/QUOTE]
1) More broken dependencies. If mplayer needs these to not groan at me, why are they not depended upon? ;)
2) Might I ask why in the world did this get changed from how it behaved in every other install I've ever done? Didn't do this in Hoary, Gentoo, or SUSE. In Breezy, Hoary and Gentoo, I used the **exact same** bzip to install from. Config [font=Bitstream Vera Sans Mono]zoom=yes[/font] fixed it, but again, why the pain? If you have any idea, of course (this is why I stayed away from Breezy for so long, and I reccomend Hoary over it to anyone who wants to try Linux).
4) xv did not fix it. It only happens with certain files--that is, my OGM files are fine, but all my AVIs, MKVs, and MP(E)Gs are out of sync. Again, only Breezy exhibits this behaviour.

#4 doesn't happen in xine or totem, but those players don't like MKV for some reason, even with the video codecs installed--audio plays fine, but the video freezes every couple seconds for a split-second, then does like a fast-forward to catch up, freeze, fast-forward...

---

### Post by rob2nd9th on 2005-12-19
Never had any luck with mplayer - I use VLC I think its the best:)

---

### Post by Zonkle on 2005-12-19
[QUOTE=rob2nd9th]Never had any luck with mplayer - I use VLC I think its the best:)[/QUOTE]

VLC might go according to their web site!

---

### Post by holiday on 2005-12-19
I tried apt-get on mplayer without luck, I tried building it and got an error *lecture* on how they don't have the time to upgrade their compiler. Which is fine - but the lecture made me tired of trying to install implayer. That's not the first lecture I've got from the mplayer guys. Sure they do good work and we're all grateful for it, but they should perhaps do less of it if it makes them so grumpy.

---

### Post by rudeboyskunk on 2005-12-19
bah!  you know why i tried to compile mplayer?  because i'm retarded and forgot to uncomment the lines in my sources.list file so i could get vlc and all the other great media stuff.

i was also just hoping mplayer could play wmv's.

---

### Post by poptones on 2005-12-19
You got a "lecture" about the compiler because breezy uses 4.0 and they build for 3.x. That's not a big deal, just install 3.x and let fly.

Here, copy this to a file, stick it in a temp folder in your home directory and run it as root (or do the wgets yourself as user, edit them from the top of the list, and run the remainder). It will build mplayer perfectly on breezy.

```

wget -c http://ftp5.mplayerhq.hu/mplayer/releases/MPlayer-1.0pre7.tar.bz2
wget -c http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20050412.tar.bz2
wget -c http://ftp5.mplayerhq.hu/mplayer/releases/fonts/font-arial-iso-8859-7.tar.bz2
wget -c http://www1.mplayerhq.hu/MPlayer/Skin/Blue-1.4.tar.bz2
apt-get install -y autoconf
apt-get install -y automake
apt-get install -y libtool
apt-get install -y flex
apt-get install -y bison
apt-get install -y gcc-doc
apt-get install -y g++
apt-get install -y gcc-3.4-base
apt-get install -y x-window-system-dev
apt-get install -y libgtk1.2-dev
apt-get install -y libpng12-dev 
apt-get install -y libxxf86vm-dev
tar -xjf essential-20050412.tar.bz2
mkdir -p /usr/lib/win32
cp essential-20050412/* /usr/lib/win32/
rm -rf essential-20050412
tar -xjf MPlayer-1.0pre7.tar.bz2
cd MPlayer-1.0pre7
./configure --enable-gui
make
make install
cd ..
tar -xjf font-arial-iso-8859-7.tar.bz2
cp font-arial-iso-8859-7/font-arial-14-iso-8859-7/* /usr/local/share/mplayer/font/
tar -xjf Blue-1.4.tar.bz2
mkdir -p /usr/local/share/mplayer/Skin/default
cp -r Blue/* /usr/local/share/mplayer/Skin/default/
cp MPlayer-1.0pre7/etc/* /usr/local/etc/mplayer/
/usr/share/doc/libdvdread3/examples/install-css.sh
rm -rf MPlayer-1.0pre7
rm -rf Blue
rm -rf font-arial-iso-8859-7

```

---

### Post by holiday on 2005-12-19
Thank you, you're right I know but...

I know *why* I got a lecture. My problem was like why a *lecture*. A simple techie message would do me just fine ("compilation of mplayer requires" whatever) and I would go on and install the earlier version of the compiler. But the lecture made me feel like I didn't want to use these people's software. I was like feeling bad for even trying to compile the sacred mplayer with a compiler they haven't used yet. 

I mean - come on. Just say No. Don't give me a finger-wagging. 

Sheesh!

---

### Post by poptones on 2005-12-19
Again though, you are looking at this as a "user." Most "users" do not compile software - devs and support techs do. Political messages like that are meant mostly for other "developers." 

Long story short: Ya either believe in free speech or ya don't.

---

### Post by holiday on 2005-12-20
Once again, I must thank you for providing the script and came back here this morning to ensure that I gave you the acknowledgement I feared I had not made in my previous note. 

But now you've raised a point to which I must reply - and I hope the moderators will permit me this one digression from topic: 

Freedom of speech surely permits the freedom to freely comment on the speech that's freely made. I am certainly not advocating that the speech should be muzzled, I was simply saying that I found it abrasive and even insulting, so much so that I didn't want to continue working with them.

I have to say that as someone who's been developing software for a good many years, on a number of platforms, including Linux, that I find the speech of the MPlayer team to be *unusually* harsh. It is not my experience that developers speak to each other with such atttitude. It is far more common that developer-developer speech is either cryptic or too obviously absent. 

Thank you once again for the script. I am very grateful for the effort.

---

### Post by jdong on 2005-12-31
Unsynched A/V at times may be caused by a sound server (ESD, ARTS)... Try turning those off before blaming a media player.

---

