---
title: "Mplayer doesn't work at all"
date: 2006-02-28
forum: Desktop Environments
---

### Post by Ramses de Norre on 2006-02-28
I'm having a few problems with mplayer: 
First: it wont play video's, it gives this error: ```
Error opening/initializing the selected video_out (-vo) device.
```
I followed the instructions in the starter guide to configure the video out mode.

Secondly: the volume is always very low, all the system sounds are ten times louder then the music I play. And the volume is at max.

Third: the plugin for firefox makes firefox hang, it never plays and sometimes I need to force quit firefox because it hangs.

In fact nothing works on mplayer, I really need the plugin to work (I use amarok now for music and it works perfect). But I guess the plugin will encounter the other problems too once it works.

---

### Post by sprucio on 2006-02-28
Is this mplayer that you got from Ubuntu or one that you built from source?

I've always preferred to build from source with a software complicated as this.

---

### Post by teleon on 2006-02-28
Have you tried downloading all the codecs from the mplayer home page?

---

### Post by Ramses de Norre on 2006-02-28
I'm trying to compile MPlayer from source but I haven't done this much before and the read me looks pretty difficult to me..
"- ATI cards: Get the GATOS drivers for X11/Xv or use VIDIX." What should I do for this?

Also the output of ./configure doesn't look very good.. But I really don't know what exactely I should do, can someone point me in the direction?
```
ramses@icarus:~/backup/MPlayer-1.0pre7try2$ ./configure --enable-gui
Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... 4.0.2, bad
Checking for gcc version ... 4.0.2, bad
Checking for gcc-3.4 version ... 3.4.5, ok
Checking for host cc ... gcc-3.4
Checking for CPU vendor ... AuthenticAMD (15:39:1)
Checking for CPU type ...  AMD Athlon(tm) 64 Processor 3700+
Checking for GCC & CPU optimization abilities ... athlon-xp
Checking for kernel support of mmx ... yes
Checking for kernel support of mmx2 ... yes
Checking for kernel support of 3dnow ... yes
Checking for kernel support of 3dnowex ... yes
Checking for kernel support of sse ... yes
Checking for kernel support of sse2 ... yes
Checking for mtrr support ... yes
Checking for assembler support of -pipe option ... yes
Checking for assembler (as 2.16.1) ... ok
Checking for Linux kernel version ... 2.6.12-10-k7, ok
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
Checking for termcap ... no
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
Checking for Xinerama ... yes
Checking for Xxf86vm ... no
Checking for XF86keysym ... yes
Checking for DGA ... no
Checking for OpenGL ... yes
Checking for /dev/mga_vid ... no
Checking for xmga ... no
Checking for GGI ... no
Checking for AA ... no
Checking for CACA ... no
Checking for SVGAlib ... no
Checking for FBDev ... yes
Checking for DVB ... no (specify path to DVB/ost/include with --with-dvbincdir=DIR)
Checking for DVB HEAD ... yes
Checking for PNG support ... yes
Checking for JPEG support ... no
Checking for PNM support ... yes
Checking for md5sum support ... yes
Checking for GIF support ... no
Checking for VESA support ... yes
Checking for SDL ... no
Checking for Windows waveout ... no
Checking for Directx ... no
Checking for NAS ... no
Checking for DXR2 ... no
Checking for DXR3/H+ ... no
Checking for libmp1e ... no
Checking for libfame ... no
Checking for OSS Audio ... yes
Checking for aRts ... no
Checking for EsounD ... no
Checking for Polyp ... no
Checking for JACK ... no
Checking for ALSA audio ... no
Checking for Sun audio ... no
Checking for Sun mediaLib ... no
Checking for SGI audio ... no
Checking for VCD support ... ok
Checking for DVD support (libmpdvdkit) ... yes
Checking for DVD support (libdvdread) ... disabled by libmpdvdkit2
Checking for cdparanoia ... no
Checking for freetype >= 2.0.9 ... yes
Checking for fontconfig ... yes
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
Checking for libdv-0.9.5+ ... no
Checking for zr ... no
Checking for bl ... no
Checking for XviD ... no
Checking for x264 ... no
Checking for DivX4linux/DivX5linux/OpenDivX decore ... no
Checking for libmp3lame (for mencoder) ... no
Checking for DivX4linux encore (for mencoder) ... no
Checking for mencoder ... yes
Checking for fastmemcpy ... yes
Checking for UniquE RAR File Library ... yes
Checking for TV interface ... yes
Checking for EDL support ... yes
Checking for *BSD BrookTree 848 TV interface ... no
Checking for Video 4 Linux TV interface ... yes
Checking for Video 4 Linux 2 TV interface ... yes
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
Checking for GUI ... yes
Checking for XShape extension ... yes
Checking for GTK version ...
Error: The GUI requires GTK devel packages (which were not found).

Check "configure.log" if you do not understand why it failed.
ramses@icarus:~/backup/MPlayer-1.0pre7try2$

```
Thanks a lot! I'm still in the beginning of learning how to compile programs from source.

---

### Post by kaamos on 2006-02-28
1) are you using the fglrx driver?

2) if so, add this to the "Device" section of /etc/X11/xorg.conf
```
     Option "VideoOverlay" "on"
     Option "OpenGLOverlay" "off"
```
Save the file, restart X and try the xv output again.

3) if you still wish to compile:
```
sudo apt-get install build-essential debhelper libx11-dev libxv-dev libpng12-0 libpng12-dev checkinstall libavcodec-dev aalib1 libaa1-dev libaa1 caca-utils libcaca-dev libavcodec-dev libavifile-0.7-dev libsdl1.2debian-all libsdl1.2debian libsdl1.2-dev libesd0-dev libfaac-dev libfaad2-dev libgtk2.0-dev liblame-dev libice-dev libjpeg62-dev libmatroska-dev libmad0-dev libmpcdec-dev libmp4v2-dev libmikmod2-dev libogg-dev libtheora-dev libvorbis-dev libxinerama-dev libxv-dev xlibs-dev x-dev cvs libquicktime1 libquicktime-dev libmjpegtools0 fakeroot gnome-core-devel libpostproc-dev
```

---

### Post by Ramses de Norre on 2006-02-28
The options for the xorg.conf worked!
Thx very much:)
And I think I still have much to learn about compiling..

---

