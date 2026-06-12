---
title: "mplayer how to?"
date: 2005-07-11
forum: Desktop Environments
---

### Post by gnuageux on 2005-07-11
Hi all, just moved away from Gentoo and decided to give Ubu a try, so far I like it. I am having a problem getting mplayer to the point where itll play any avi's etc on my disks. I tried just downloading and building from source and while it installed, when I launch it (I.e mplayer somemovie.avi) all I get is a mplayer window with a blue screen and no sound. I haven't been able to get it installed using apt-get b/c I get the following errors: 

~$ sudo apt-get install mplayer-386
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer-386: Depends: libdirectfb-0.9-20 but it is not installable
               Depends: libggi2 (>= 1:2.0.5) but it is not installable
               Depends: libmad0 (>= 0.15.1b) but it is not installable

I've tried to find the files that it complains about to no avail. It could very well be a codec isssue, however I did install the w32codecs package using apt-get. Im kind of at a loss here, any help would be greatly appreciated!

---

### Post by Xian on 2005-07-11
[QUOTE=gnuageux]I haven't been able to get it installed using apt-get b/c I get the following errors:[/QUOTE]
It might be advisable to ensure that you have the correct repos in your source.list before going too much further. Does your /etc/atp/sources.list appear similar to mine? If not, then append the differences and run another 'apt-get update' session.

```
## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

##Backup Ubuntu Mirrors
#deb http://mirrors.xmission.com/ubuntu hoary-updates main restricted universe multiverse
#deb-src http://mirrors.xmission.com/ubuntu hoary-updates main restricted universe multiverse

##Security Mirrors
deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe

##Backup Security Mirrors
#deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
#deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe

#Kubuntu KDE341 Updates
deb http://kubuntu.org/hoary-kde341 hoary-updates main

##Backports
#deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
#deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted

## Backports (Alternate Mirror)
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

### Post by gnuageux on 2005-07-11
I copied your sources and I was able to download and install it, but when I try to run it now it hangs @: 

$ mplayer Downloads/office_space.avi
mplayer: /usr/local/lib/libpng12.so.0: no version information available (required by mplayer)
MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Intel Pentium 4/Xeon/Celeron Foster (Family: 8, Stepping: 9)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for Debian.


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing Downloads/.LM/office_space.avi.
AVI file format detected.
VIDEO:  [DIV3]  704x336  24bpp  23.976 fps  555.9 kbps (67.9 kbyte/s)
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, 16 bit (0x10), ratio: 12000->192000 (96.0 kbit)
Selected audio codec: [mad] afm:libmad (libMAD MPEG layer 1-2-3)
==========================================================================
vo: X11 running at 1600x1200 with depth 24 and 32 bpp (":0.0" => local display)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffdivx] vfm:ffmpeg (FFmpeg DivX ;-) (MS MPEG-4 v3))
==========================================================================
Checking audio filter chain for 48000Hz/2ch/16bit -> 48000Hz/2ch/16bit...
AF_pre: af format: 2 bps, 2 ch, 48000 hz, little endian signed int
AF_pre: 48000Hz 2ch Signed 16-bit (Little-Endian)
alsa-init: got device=0, subdevice=0
alsa-init: 1 soundcard found, using: default

---

### Post by Xian on 2005-07-11
Did you install all of your [codecs](http://ubuntuguide.org/#codecs)?

---

### Post by gnuageux on 2005-07-12
I sure have, I also removed and reinstalled xine and mplayer after installing and registering the codecs, same deal.

---

### Post by gnuageux on 2005-07-12
Got it figured out. 

1. mplayer 
2. preferences 
3. codecs & demuxer 
4. Set video codec family to "Win32/VfW video codecs" 
5. Set audio codec family to "libmad mpeg audio decoder" 

Restart mplayer & enjoy. Of all the distros ive run this is the 1st time where ive ever ran into this, quirky lil thang.

Thanks for the help guys!!

 (oh, I also removed mplayer-386 and installed mplayer-686)

---

