---
title: "Gmplayer/mplayer crashes"
date: 2005-05-16
forum: Desktop Environments
---

### Post by hena on 2005-05-16
I'm trying to play a dvd. I have installed the decss package as guided in '/usr/share/doc/libdvdread3/README.Debian' file. However the gmplayer seems to crash. When running the disc by mplayer in terminal (command 'mplayer dvd://1') these are the last lines.

DVD successfully opened.
Cache fill:  6.25% (65536 bytes)    MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  8500.0 kbps (1062.5 kbyte/s)
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [liba52] AC3 decoding with liba52
AC3: 2.0 (stereo)  48000 Hz  192.0 kbit/s
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, 16 bit (0x10), ratio: 24000->192000 (192.0 kbit)
Selected audio codec: [a52] afm:liba52 (AC3-liba52)
==========================================================================
vo: X11 running at 1400x1050 with depth 24 and 32 bpp (":0.0" => local display)
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred csp: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm:libmpeg2 (MPEG 1 or 2 (libmpeg2))
==========================================================================
Checking audio filter chain for 48000Hz/2ch/16bit -> 48000Hz/2ch/16bit...
AF_pre: af format: 2 bps, 2 ch, 48000 hz, little endian signed int
AF_pre: 48000Hz 2ch Signed 16-bit (Little-Endian)
alsa-init: got device=0, subdevice=0
alsa-init: 1 soundcard found, using: default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch Signed 16-bit (Little-Endian) (2 bps)
Building audio filter chain for 48000Hz/2ch/16bit -> 48000Hz/2ch/16bit...
Starting playback...


MPlayer interrupted by signal 11 in module: decode_audio
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
alsa-uninit: pcm closed

---

### Post by Sniffer on 2005-05-16
Did you install mplayer from a package or from the source???

---

### Post by hena on 2005-05-17
[QUOTE=Sniffer]Did you install mplayer from a package or from the source???[/QUOTE]
I installed it from the mplayer package in hoary multiverse list.

---

### Post by Sniffer on 2005-05-17
[QUOTE=hena]I installed it from the mplayer package in hoary multiverse list.[/QUOTE]

That's what i thought, i had also issues when installing mplayer from packages, so you can uninstall what you have from synaptic and following this guide you will install mplayer from the source with DVD support.

http://www.ubuntuforums.org/showthread.php?t=31061


It solve my problems.

---

### Post by hena on 2005-05-17
[QUOTE=Sniffer]That's what i thought, i had also issues when installing mplayer from packages, so you can uninstall what you have from synaptic and following this guide you will install mplayer from the source with DVD support.

[http://www.ubuntuforums.org/showthread.php?t=31061](http://www.ubuntuforums.org/showthread.php?t=31061)


It solve my problems.[/QUOTE]
Rather annoying to start compiling from sources. Besides then it would still be missing gmplayer... Oh well, Things are never perfect :). Off to get sources and then compiling.

---

### Post by HardwareBoB on 2005-07-26
[QUOTE=hena]Rather annoying to start compiling from sources. Besides then it would still be missing gmplayer... Oh well, Things are never perfect :). Off to get sources and then compiling.[/QUOTE]
 This is because AC3 support is broken in the current mplayer - I've come across this too. all movies (most notably DVDs, as all of them are AC3) with AC3 will crash mplayer.

---

### Post by stilus on 2005-08-03
Same problem here, gmplayer from ubuntu hoary crashing because of decode_audio failure. But if you compile from sources and do a ./configure --enable-gui, you *can* have gmplayer (which is what I'm after).

---

### Post by push_harder on 2008-01-20
> **HardwareBoB said:**
> This is because AC3 support is broken in the current mplayer - I've come across this too. all movies (most notably DVDs, as all of them are AC3) with AC3 will crash mplayer.

I have the same Problem aswell *sigh* i can't seem to get around it.
I've been trying for the last 2 days straight.
I'm new to Linux and have managed to get most things working fine.
It's just this.

mplayer crashes with any video i try, wether it be a DVD or a downloaded AVI/MPG.
It shows up breifly and then mplayer dissaperes.

I've tried numouris things with codecs and other movie viewing applications.
But i just can't seem to find out what's wrong.
It'd be a great help if anyone has any ideas :)

Thanks!

---

