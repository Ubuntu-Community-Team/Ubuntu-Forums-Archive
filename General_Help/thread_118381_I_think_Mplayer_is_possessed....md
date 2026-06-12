---
title: "I think Mplayer is possessed..."
date: 2006-01-16
forum: General Help
---

### Post by Sparkalo on 2006-01-16
As you may have guessed from the subject, I'm having difficulties with Mplayer : P.

Everything actually works pretty nicely aside from one small issue, sound. You see, whenever I play something, be it a DVD or any other movie, rather than hearing what I'm supposed to, I hear a bunch of garbage that sounds like digital static.  I also get a wonderful little message saying "Couldn't find matching filter/ao format!".  

To combat this, I decided to do something rather profound and opened up the preferences menu, clicked the audio tab, and changed my driver to ALSA. Well, I don't get demon noises, but instead am greeted with the cheery "Could not open/intitialize audio device -> no sound" message...and no sound.

I can use any other program to play my DVDs and other video files flawlessly, but seeing as I'd like to use Mencoder to encode my dvds, I'd like to fix this problem.  So, has anybody else had this problem or does anybody know how to fix it?

Any help would be greatly appreciated ^_^

---

### Post by Sef on 2006-01-16
Are the DVDs encoded?

Read this post from the Documentation:

> Playing DVD's

Most commercial DVDs are encrypted with CSS (the Content Scrambling System). The movie players provided in Ubuntu are capable of reading DVDs that are not encrypted. If it is legal for you to circumvent CSS, then you can enable reading encrypted DVDs in vlc, mplayer, xine and totem-xine by installing libdvdcss2. Type in a terminal: 

sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/examples/install-css.sh

Link: [https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by Sparkalo on 2006-01-17
First of all, let me thank you very  much for your advice.

As much as I was hoping that perhaps I forgot to do that, I am sad to say that yes, my decryption files are all installed and up to date. At the moment, it seems most likely that it's an audio device issue or perhaps an issue with Mplayer.  Some googling has turned up solutions including killing all processes using the audio device.&#12288;Although this doesn't seem all too likely to work, I may try it.  

Any additional help would be greatly appreciated

---

### Post by Sparkalo on 2006-01-17
I figured to help any of you that are interested in excorsizing the demon of Mplayer, I should attatch technical information and junk.  This being said, I ran mplayer from the terminal and copied all of the junk it spewed back hoping that it may help something ;) .  

Below = Mplayer in Terminal, that is, the parts relating to audio

[QUOTE=Terminal Junk]
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'dts' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
No accelerated IMDCT transform found
hwac3: switched to DTS, 768000 bps, 48000 Hz
AUDIO: 48000 Hz, 2 ch, ac3, 768.0 kbit/50.00% (ratio: 96000->192000)
Selected audio codec: [hwdts] afm:hwac3 (DTS through S/PDIF)
==========================================================================
vo: X11 running at 1024x768 with depth 24 and 32 bpp (":0.0" => local display)
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred csp: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm:libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/2ch/ac3 -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: iec958:{CARD 0 AES0 0x02 AES1 0x82 AES2 0x00 AES3 0x02}
ALSA lib setup.c:549:(add_elem) Cannot obtain info for CTL elem (MIXER,'IEC958 Playback Default',0,0,0): No such file or directory
alsa-init: playback open error: No such file or directory
[AO OSS] Can't set audio device /dev/dsp to ac3 output, trying s16le...
AO: [oss] 48000Hz 2ch s16le (2 bps)
Building audio filter chain for 48000Hz/2ch/ac3 -> 48000Hz/2ch/s16le...
[format] Sample format big-endian AC3 not yet supported
[libaf] Reinitialization did not work, audio filter 'format' returned error code -2
Couldn't find matching filter/ao format!
Starting playback...
VDec: vo config request - 720 x 480 (preferred csp: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 854x480 Planar YV12
A:   0.7 V:   0.6 A-V:  0.085 ct:  0.030  12/ 10 ??% ??% ??,?% 5 0 78%
demux_mpg: 24000/1001fps progressive NTSC content detected, switching framerate.No bind found for key MOUSE_BTN0    [/QUOTE]

---

### Post by Sparkalo on 2006-01-17
Ok, the following lines stuck out at me
> Cannot find codec 'dts' in libavcodec...
ADecoder init failed :(

I looked this up and sure enough, I found a similar problem related to this.  The propsed solution was to "Download and install the libdts ([http://ftp.debian.org/debian/pool/main/libd/libdts/libdts_0.0.2-svn.orig.tar.gz](http://ftp.debian.org/debian/pool/main/libd/libdts/libdts_0.0.2-svn.orig.tar.gz)) and re-compile the MPlayer with the --enable-libdts option. "

Can anybody verify that this is, in fact, an advisable solution?  I've tried compling MPlayer before to little avail.  I keep getting the error "libpostproc/postprocess_template.c:2901: error: memory input 4 is not directly addressable"

Input please, I'm close, I can feel it :P

---

### Post by Sparkalo on 2006-01-17
:KS :) :p ;) :smile: ISSUE RESOLVED!! ^____^

I installed mplayer via cvs (instructions found in this thread: [http://www.ubuntuforums.org/showthread.php?t=85190&highlight=compiling+MPlayer](http://www.ubuntuforums.org/showthread.php?t=85190&highlight=compiling+MPlayer) ) with the option --enable-libdts after installing libdts.  Everything works flawlessly at the moment ^_^

---

