---
title: "VLC no sound with v4l"
date: 2005-07-27
forum: Desktop Environments
---

### Post by karl_kashofer on 2005-07-27
Hi !

I am trying to get VLC to stream TV, but can not get sound to work.
TV works fine in XAWTV, both video and sound.

this is what i get in the log from vlc -vvv when I try to open /dev/video0 and /dev/dsp in vlc

```
VLC media player 0.8.1 Janus
[00000001] main vlc debug: opening config file /home/karl/.vlc/vlcrc
[00000001] main vlc warning: config file /home/karl/.vlc/vlcrc does not exist yet
[00000001] main vlc debug: checking builtin modules
[00000001] main vlc debug: checking plugin modules
[00000001] main vlc debug: loading plugins cache file /home/karl/.vlc/cache/plugins-04041e.dat
[00000001] main vlc debug: recursively browsing `modules'
[00000001] main vlc debug: recursively browsing `/usr/lib/vlc'
[00000001] main vlc debug: recursively browsing `plugins'
[00000001] main vlc debug: module bank initialized, found 185 modules
[00000001] main vlc debug: opening config file /home/karl/.vlc/vlcrc
[00000001] main vlc warning: config file /home/karl/.vlc/vlcrc does not exist yet
[00000000] main root debug: VLC media player - version 0.8.1 Janus - (c) 1996-2004 VideoLAN
[00000000] main root debug: libvlc was configured with ./configure --mandir=/share/man --infodir=/share/info --enable-release --prefix=/usr --disable-gnome --disable-gtk --disable-familiar --disable-fb --enable-ggi --enable-sdl --enable-esd --disable-qt --enable-mad --enable-arts --enable-alsa --enable-lirc --enable-a52 --enable-aa --enable-dvbpsi --enable-xosd --enable-mozilla --disable-kde --enable-mp4 --enable-dvb --enable-dv --disable-satellite --enable-ogg --enable-vorbis --enable-wxwindows --disable-slp --enable-flac --disable-skins --disable-basic-skins --enable-skins2 --enable-freetype --enable-mkv --enable-v4l --enable-pvr --disable-speex --enable-caca --enable-livedotcom --enable-libmpeg2 --enable-dts --enable-fribidi --enable-cdio --enable-mod --enable-theora --enable-modplug --enable-dvdnav --enable-gnutls --enable-ffmpeg --with-ffmpeg-tree=extras/ffmpeg --enable-faad --with-faad-tree=extras/faad2 --enable-x264 --with-x264-tree=extras/x264 --enable-glide --enable-svgalib --enable-dvd --without-dvdcss --no-create --no-recursion
[00000001] main vlc debug: translation test: code is "de"
[00000001] main vlc debug: opening config file /home/karl/.vlc/vlcrc
[00000001] main vlc warning: config file /home/karl/.vlc/vlcrc does not exist yet
[00000001] main vlc debug: checking builtin modules
[00000001] main vlc debug: checking plugin modules
[00000001] main vlc debug: loading plugins cache file /home/karl/.vlc/cache/plugins-04041e.dat
[00000001] main vlc debug: recursively browsing `modules'
[00000001] main vlc debug: recursively browsing `/usr/lib/vlc'
[00000001] main vlc debug: recursively browsing `plugins'
[00000001] main vlc debug: module bank initialized, found 185 modules
[00000001] main vlc debug: opening config file /home/karl/.vlc/vlcrc
[00000001] main vlc warning: config file /home/karl/.vlc/vlcrc does not exist yet
[00000001] main vlc debug: CPU has capabilities 486 586 MMX 3DNow! MMXEXT SSE FPU 
[00000001] main vlc debug: looking for memcpy module
[00000001] main vlc debug: probing 4 candidates
[00000010] main module debug: using memcpy module "memcpymmxext"
[00000234] main playlist debug: creating group Normal with id 1 at position 0
[00000234] main playlist debug: waiting for thread completion
[00000234] main playlist debug: thread -1214829648 (playlist) created at priority 0 (src/playlist/playlist.c:107)
[00000235] main interface debug: looking for interface module
[00000235] main interface debug: probing 1 candidate
[00000114] main module debug: using interface module "hotkeys"
[00000235] main interface debug: interface initialized
[00000235] main interface debug: thread -1223242832 (interface) created at priority 0 (src/interface/interface.c:209)
[00000237] main interface debug: looking for interface module
[00000237] main interface debug: probing 4 candidates
[00000157] main module debug: using interface module "wxwindows"
[00000237] main interface debug: interface initialized
[00000237] main interface debug: thread -1246647376 (manager) created at priority 0 (src/interface/interface.c:194)
[00000237] wxwindows interface debug: accelerator table loaded
[00000234] main playlist debug: adding playlist item `v4l://' ( v4l:// )
[00000234] main playlist debug: creating new input thread
[00000240] main input debug: set input option: v4l-vdev to /dev/video0
[00000240] main input debug: set input option: v4l-adev to /dev/dsp
[00000240] main input debug: waiting for thread completion
[00000240] main input debug: thread -1256305744 (input) created at priority 0 (src/input/input.c:228)
[00000240] main input debug: `v4l://' gives access `v4l' demux `' path `'
[00000240] main input debug: demux2_New: access='v4l' demux='' path=''
[00000241] main demuxer debug: looking for access_demux module
[00000241] main demuxer debug: probing 1 candidate
[00000241] v4l demuxer debug: V4L device BT878 video (Leadtek WinFast 20 4 channels 1 audios 48 < w < 640 32 < h < 576
[00000241] v4l demuxer debug: invalid width 0
[00000241] v4l demuxer debug: invalid height 0
[00000241] v4l demuxer debug: setting channel Television(0) 1 tuners flags=0x3 type=0x1 norm=0x3
[00000241] v4l demuxer debug: will use 384x288
[00000241] v4l demuxer debug: v4l device uses brightness: 32768
[00000241] v4l demuxer debug: v4l device uses colour: 32768
[00000241] v4l demuxer debug: v4l device uses hue: 32768
[00000241] v4l demuxer debug: v4l device uses contrast: 32768
[00000241] v4l demuxer debug: v4l device uses frame size: 442368
[00000241] v4l demuxer debug: v4l device uses chroma: RV32
[00000241] v4l demuxer debug: openened adev=`/dev/dsp' stereo 44100Hz
[00000241] v4l demuxer debug: v4l grabbing started
[00000241] v4l demuxer debug: added new video es RV32 384x288
[00000240] main input debug: Selecting program id=0
[00000241] v4l demuxer debug: new audio es 2 channels 44100Hz
[00000063] main module debug: using access_demux module "v4l"
[00000243] main decoder debug: looking for decoder module
[00000243] main decoder debug: probing 20 candidates
[00000097] main module debug: using decoder module "rawvideo"
[00000243] main decoder debug: thread -1283593296 (decoder) created at priority 0 (src/input/decoder.c:157)
[00000273] main decoder debug: looking for decoder module
[00000273] main decoder debug: probing 20 candidates
[00000273] araw decoder debug: samplerate:44100Hz channels:2 bits/sample:16
[00000099] main module debug: using decoder module "araw"
[00000273] main decoder debug: thread -1291986000 (decoder) created at priority 0 (src/input/decoder.c:157)
[00000240] main input debug: `v4l://' sucessfully opened
[00000243] main decoder debug: no usable vout present, spawning one
[00000274] main video output debug: looking for video output module
[00000274] main video output debug: probing 6 candidates
[00000274] xvideo video output warning: no free XVideo port found for format 0x32335652 (RV32)
[00000274] xvideo video output warning: no free XVideo port found for format 0x32595559 (YUY2)
[00000274] xvideo video output warning: no free XVideo port found for format 0x36315652 (RV16)
[00000275] main private debug: Registering subpicture channel, ID: 2
[00000275] main private debug: Registering subpicture channel, ID: 3
[00000275] main private debug: Registering subpicture channel, ID: 4
[00000275] main private debug: Registering subpicture channel, ID: 5
[00000274] x11 video output debug: Window manager supports NetWM
[00000274] x11 video output debug: Window manager supports _NET_WM_STATE_FULLSCREEN
[00000274] x11 video output debug: Window manager supports _NET_WM_STATE_ABOVE
[00000274] x11 video output debug: Window manager supports _NET_WM_STATE_BELOW
[00000211] main module debug: using video output module "x11"
[00000274] main video output debug: waiting for thread completion
[00000273] main decoder debug: no aout present, spawning one
[00000278] main audio output debug: looking for audio output module
[00000278] main audio output debug: probing 3 candidates
[00000274] main video output debug: got 2 direct buffer(s)
[00000274] main video output debug: picture in 384x288, chroma 0x32335652 (RV32), aspect ratio 4:3
[00000274] main video output debug: picture out 384x288, chroma 0x32335652 (RV32), aspect ratio 4:3
[00000274] main video output debug: direct render, mapping render pictures 0-6 to system pictures 1-7
[00000274] main video output debug: thread -1300923472 (video output) created at priority 0 (src/video_output/video_output.c:443)
[00000278] alsa audio output debug: opening ALSA device `default'
[00000278] alsa audio output warning: The rate 44100 Hz is not supported by your hardware. Using 48000 Hz instead.

[00000278] main audio output debug: thread -1309836368 (aout) created at priority 0 (alsa.c:603)
[00000233] main module debug: using audio output module "alsa"
[00000278] main audio output debug: output 's16l' 48000 Hz Stereo frame=1 samples/4 bytes
[00000278] main audio output debug: mixer 's16l' 48000 Hz Stereo frame=1 samples/4 bytes
[00000278] main audio output debug: filter(s) 'fl32'->'s16l' 48000 Hz->48000 Hz Stereo->Stereo
[00000279] main private debug: looking for audio filter module
[00000279] main private debug: probing 23 candidates
[00000024] main module debug: using audio filter module "float32tos16"
[00000278] main audio output debug: found a filter for the whole conversion
[00000278] main audio output debug: looking for audio mixer module
[00000278] main audio output debug: probing 3 candidates
[00000072] main module debug: using audio mixer module "trivial_mixer"
[00000278] main audio output debug: input 's16l' 44100 Hz Stereo frame=1 samples/4 bytes
[00000278] main audio output debug: filter(s) 's16l'->'fl32' 44100 Hz->44100 Hz Stereo->Stereo
[00000298] main private debug: looking for audio filter module
[00000298] main private debug: probing 23 candidates
[00000033] main module debug: using audio filter module "s16tofloat32"
[00000278] main audio output debug: found a filter for the whole conversion
[00000278] main audio output debug: filter(s) 'fl32'->'fl32' 52800 Hz->48000 Hz Stereo->Stereo
[00000304] main private debug: looking for audio filter module
[00000304] main private debug: probing 23 candidates
[00000042] main module debug: using audio filter module "bandlimited_resampler"
[00000278] main audio output debug: found a filter for the whole conversion
[00000278] main audio output warning: PTS is out of range (59688), dropping buffer
[00000278] main audio output warning: PTS is out of range (36643), dropping buffer

(snip many of these)

[00000278] main audio output warning: PTS is out of range (-37387), dropping buffer
[00000278] main audio output warning: buffer is 40033 in advance, triggering downsampling
[00000278] main audio output warning: timing screwed, stopping resampling
[00000278] main audio output warning: buffer is 51211 in advance, triggering downsampling
[00000278] main audio output warning: timing screwed, stopping resampling
[00000278] main audio output warning: buffer is 86078 in advance, triggering downsampling
[00000278] main audio output warning: audio drift is too big (-128008), clearing out
[00000278] main audio output warning: timing screwed, stopping resampling
[00000278] main audio output warning: mixer start isn't output start (-52586)
[00000278] main audio output debug: audio output is starving (137924), playing silence
[00000278] main audio output warning: buffer is 40142 in advance, triggering downsampling
[00000278] alsa audio output warning: recovered from buffer underrun
[00000278] main audio output warning: timing screwed, stopping resampling
[00000278] main audio output warning: buffer is 60442 in advance, triggering downsampling
[00000278] main audio output warning: timing screwed, stopping resampling
[00000278] main audio output warning: buffer is 90964 in advance, triggering downsampling
[00000278] main audio output warning: audio drift is too big (-122320), clearing out
[00000278] main audio output warning: timing screwed, stopping resampling
[00000278] main audio output warning: mixer start isn't output start (-54738)
[00000278] main audio output warning: buffer is 40037 in advance, triggering downsampling
[00000278] main audio output warning: timing screwed, stopping resampling
[00000278] main audio output warning: buffer is 60148 in advance, triggering downsampling
[00000278] main audio output warning: timing screwed, stopping resampling
[00000278] main audio output warning: buffer is 90437 in advance, triggering downsampling
[00000278] main audio output warning: audio drift is too big (-120026), clearing out
[00000278] main audio output warning: timing screwed, stopping resampling
[00000278] main audio output warning: buffer is 40067 in advance, triggering downsampling
[00000278] main audio output warning: timing screwed, stopping resampling
[00000278] main audio output warning: buffer is 60300 in advance, triggering downsampling
[00000278] main audio output warning: timing screwed, stopping resampling
[00000278] main audio output warning: buffer is 90778 in advance, triggering downsampling
[00000278] main audio output warning: audio drift is too big (-120100), clearing out
[00000278] main audio output warning: timing screwed, stopping resampling

```

After this it dies with "Speicherzugriffsfehler"

It seems the dsp device cant be accessed by vlc, here is my sndstat:

```
Sound Driver:3.8.1a-980706 (ALSA v1.0.6 emulation code)
Kernel: Linux paul-ubuntu 2.6.10-5-386 #1 Fri Jun 24 16:53:01 UTC 2005 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
SiS SI7012 with ALC100/100P at 0xd800, irq 10
Brooktree Bt878 at 0xcbdff000, irq 11

Audio devices:
0: SiS SI7012 (DUPLEX)
1: Bt87x Digital

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: Realtek ALC100/100P rev 38
1: Bt87x

```

and my lsmod:

```
snd_bt87x              12612  0 
snd_intel8x0           29984  2 
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0 
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  4 snd_bt87x,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  9 snd_bt87x,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  2 snd
snd_page_alloc          9604  3 snd_bt87x,snd_intel8x0,snd_pcm

```

Any ideas what is happening here ?

Thanks,
karl

---

### Post by OneSeventeen on 2005-07-28
no idea, but VLC tells me (In the message window) that it cannot open the sound device.

I'm listening to an audio CD at the moment, so audio works elsewhere.

I'm an experienced linux newbie, so stuff like "check out your /var/xorg.0.log" is helpful, but "check out your xorg logs" doesn't... so I'm willing to do my homework to hopefully get this issue resolved, I just need a little nudge in the right direction.

For me, DVD playback is staggered as well, so even if audio was working, the video is always too fast or way too slow.

---

### Post by yyagol on 2005-07-28
Hi 
i had the same prob
if i paly music with Music Player i get sound
but VLC did not.

---

