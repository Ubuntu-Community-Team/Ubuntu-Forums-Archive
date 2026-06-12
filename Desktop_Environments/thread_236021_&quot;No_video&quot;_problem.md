---
title: "&quot;No video&quot; problem"
date: 2006-08-14
forum: Desktop Environments
---

### Post by kloshar on 2006-08-14
After upgrading from breezy to drapper, I cannot play movies anymore. Sound and programs work fine, but there is no picture (just blank screen). . I've tried all programs (Xine, Totem, Mplayer and VLC) for DVD and Divx movies and the problem is the same - sound perfect, but no video.

Any suggestions?

best regards,
Peter

---

### Post by Denis on 2006-08-14
Maybe you can try to get some more information. Run VLC and Mplayer from the terminal and see what the output is. There will probably some kind of error message.

---

### Post by kloshar on 2006-08-14
MPLAYER (DVD PLAYING)

> pzorko@workgroup:~$ mplayer dvd://
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Sempron/Athlon MP/XP Thoroughbred; Duron Applebred ( Family: 6, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


91 audio & 204 video codecs
/usr/share/fonts/truetype/freefont/FreeSans.ttf doesn't look like a font descrip tion, ignoring.
Cannot load font: /usr/share/fonts/truetype/freefont/FreeSans.ttf
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing dvd://.
libdvdread: Using libdvdcss version 1.2.9 for DVD access
Reading disc structure, please wait...
*** Zero check failed in ifo_read.c:324
    for vmgi_mat->zero_3 = 0x00000000010000000000000000000000000000
There are 1 titles on this DVD.
There are 1 chapters in this DVD title.
There are 1 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000118
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00003d02
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
DVD successfully opened.
No matching DVD subtitle language found!

*** libdvdread: CHECK_VALUE failed in nav_read.c:202 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:202 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:202 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:202 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:202 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:202 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:202 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:202 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:202 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:202 ***
*** for dsi->dsi_gi.zero1 == 0 ***

MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  8500.0 kbps (1062.5 kbyte/s)
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 224.0 kbit/14.58% (ratio: 28000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
Starting playback...

*** libdvdread: CHECK_VALUE failed in nav_read.c:202 ***
*** for dsi->dsi_gi.zero1 == 0 ***

VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12
A:   0.7 V:   0.6 A-V:  0.028 ct:  0.038  11/ 11 ??% ??% ??,?% 2 0
*** libdvdread: CHECK_VALUE failed in nav_read.c:202 ***
*** for dsi->dsi_gi.zero1 == 0 ***

A:   1.2 V:   1.2 A-V:  0.009 ct:  0.053  24/ 24 31% 13%  1.3% 2 0
*** libdvdread: CHECK_VALUE failed in nav_read.c:202 ***
*** for dsi->dsi_gi.zero1 == 0 ***

A:   1.6 V:   1.6 A-V:  0.005 ct:  0.057  36/ 36 25% 10%  1.1% 2 0
*** libdvdread: CHECK_VALUE failed in nav_read.c:202 ***


VLC (Divx playing)
> pzorko@workgroup:~/Desktop/Moji prenosi$ vlc -vv Eight\ Below\ cd1.avi
VLC media player 0.8.4 Janus
[00000001] main vlc debug: opening config file /home/pzorko/.vlc/vlcrc
[00000001] main vlc debug: checking builtin modules
[00000001] main vlc debug: checking plugin modules
[00000001] main vlc debug: loading plugins cache file /home/pzorko/.vlc/cache/plugins-04041e.dat
[00000001] main vlc debug: recursively browsing `modules'
[00000001] main vlc debug: recursively browsing `/usr/lib/vlc'
[00000001] main vlc debug: recursively browsing `plugins'
[00000001] main vlc debug: module bank initialized, found 212 modules
[00000001] main vlc debug: opening config file /home/pzorko/.vlc/vlcrc
[00000001] main vlc debug: CPU has capabilities 486 586 MMX 3DNow! MMXEXT SSE FPU
[00000001] main vlc debug: looking for memcpy module: 1 candidate
[00000191] main module debug: using memcpy module "memcpy"
[00000268] main playlist debug: waiting for thread completion
[00000268] main playlist debug: thread 3081685936 (playlist) created at priority 0 (src/playlist/playlist.c:183)
[00000269] main private debug: waiting for thread completion
[00000269] main private debug: thread 3073293232 (preparser) created at priority 0 (src/playlist/playlist.c:205)
[00000270] main interface debug: looking for interface module: 1 candidate
[00000135] main module debug: using interface module "hotkeys"
[00000270] main interface debug: interface initialized
[00000270] main interface debug: thread 3064900528 (interface) created at priority 0 (src/interface/interface.c:211)
[00000272] main interface debug: looking for interface module: 6 candidates
[00000182] main module debug: using interface module "screensaver"
[00000272] main interface debug: interface initialized
[00000272] main interface debug: thread 3056507824 (interface) created at priority 0 (src/interface/interface.c:211)
[00000268] main playlist debug: adding playlist item `Eight Below cd1.avi' ( Eight Below cd1.avi )
[00000274] main interface debug: looking for interface module: 5 candidates
[00000031] main module debug: using interface module "wxwidgets"
[00000274] main interface debug: interface initialized
[00000274] main interface debug: thread 3032812464 (manager) created at priority 0 (src/interface/interface.c:196)
[00000274] wxwidgets interface debug: Using last windows config '(-1,0,0,1280,1024)(0,0,25,560,533)'
[00000274] wxwidgets interface debug: id=0 p=(0,25) s=(560,533)
[00000268] main playlist debug: nothing requested, starting
[00000268] main playlist debug: creating new input thread
[00000277] main input debug: waiting for thread completion
[00000277] main input debug: thread 3008900016 (input) created at priority 0 (src/input/input.c:230)
[00000277] main input debug: `Eight Below cd1.avi' gives access `' demux `' path `Eight Below cd1.avi'
[00000277] main input debug: creating demux: access='' demux='' path='Eight Below cd1.avi'
[00000278] main demuxer debug: looking for access_demux module: 2 candidates
[00000277] main input debug: creating access '' path='Eight Below cd1.avi'
[00000281] main access debug: looking for access2 module: 5 candidates
[00000281] vcd access debug: trying .cue file: Eight Below cd1.cue
[00000281] access_file access debug: opening file `Eight Below cd1.avi'
[00000014] main module debug: using access2 module "access_file"
[00000287] main private debug: pre buffering
[00000287] main private debug: received first data for our buffer
[00000287] main private debug: prebuffering done 1408981 bytes in 0s - 232779 kbytes/s
[00000277] main input debug: creating demux: access='' demux='' path='Eight Below cd1.avi'
[00000288] main demuxer debug: looking for demux2 module: 41 candidates
[00000287] avi private debug: found Chunk fourcc:46464952 (RIFF) size:732796740 pos:0
[00000287] avi private debug: found LIST chunk: 'AVI '
[00000287] avi private debug: <list 'AVI '>
[00000287] avi private debug: found Chunk fourcc:5453494c (LIST) size:8818 pos:12
[00000287] avi private debug: found LIST chunk: 'hdrl'
[00000287] avi private debug: <list 'hdrl'>
[00000287] avi private debug: found Chunk fourcc:68697661 (avih) size:56 pos:24
[00000287] avi private debug: avih: streams:2 flags: HAS_INDEX IS_INTERLEAVED 560x416
[00000287] avi private debug: found Chunk fourcc:5453494c (LIST) size:4244 pos:88
[00000287] avi private debug: found LIST chunk: 'strl'
[00000287] avi private debug: <list 'strl'>
[00000287] avi private debug: found Chunk fourcc:68727473 (strh) size:56 pos:100
[00000287] avi private debug: strh: type:vids handler:0x64697678 samplesize:0 23.98fps
[00000287] avi private debug: found Chunk fourcc:66727473 (strf) size:40 pos:164
[00000287] avi private debug: strf: video:XVID 560x416 planes:1 12bpp
[00000287] avi private debug: found Chunk fourcc:4b4e554a (JUNK) size:4120 pos:212
[00000287] avi private debug: </list 'strl'>
[00000287] avi private debug: found Chunk fourcc:5453494c (LIST) size:4222 pos:4340
[00000287] avi private debug: found LIST chunk: 'strl'
[00000287] avi private debug: <list 'strl'>
[00000287] avi private debug: found Chunk fourcc:68727473 (strh) size:56 pos:4352
[00000287] avi private debug: strh: type:auds handler:0x00000000 samplesize:1 48000.00fps
[00000287] avi private debug: found Chunk fourcc:66727473 (strf) size:18 pos:4416
[00000287] avi private debug: strf: audio:0x2000 channels:6 48000Hz 0bits/sample 375kb/s
[00000287] avi private debug: found Chunk fourcc:4b4e554a (JUNK) size:4120 pos:4442
[00000287] avi private debug: </list 'strl'>
[00000287] avi private debug: found Chunk fourcc:5453494c (LIST) size:260 pos:8570
[00000287] avi private debug: found LIST chunk: 'odml'
[00000287] avi private debug: <list 'odml'>
[00000287] avi private debug: found Chunk fourcc:686c6d64 (dmlh) size:248 pos:8582
[00000287] avi private warning: unknown chunk (not loaded)
[00000287] avi private debug: </list 'odml'>
[00000287] avi private debug: </list 'hdrl'>
[00000287] avi private debug: found Chunk fourcc:5453494c (LIST) size:56 pos:8838
[00000287] avi private debug: found LIST chunk: 'INFO'
[00000287] avi private debug: <list 'INFO'>
[00000287] avi private debug: found Chunk fourcc:54465349 (ISFT) size:44 pos:8850
[00000287] avi private debug: ISFT: software : VirtualDubMod 1.5.10.2 (build 2540/release)
[00000287] avi private debug: </list 'INFO'>
[00000287] avi private debug: found Chunk fourcc:4b4e554a (JUNK) size:1330 pos:8902
[00000287] avi private debug: found Chunk fourcc:5453494c (LIST) size:730019516 pos:10240
[00000287] avi private debug: skipping movi chunk
[00000287] avi private debug: found Chunk fourcc:31786469 (idx1) size:2766976 pos:730029764
[00000287] avi private debug: idx1: index entry:172936
[00000287] avi private debug: </list 'AVI '>
[00000287] avi private debug: found Chunk fourcc:4b4e554a (JUNK) size:172 pos:732796748
[00000287] avi private debug: * LIST-root size:732796928 pos:0
[00000287] avi private debug:      + RIFF-AVI  size:732796740 pos:0
[00000287] avi private debug:      |    + LIST-hdrl size:8818 pos:12
[00000287] avi private debug:      |    |    + avih size:56 pos:24
[00000287] avi private debug:      |    |    + LIST-strl size:4244 pos:88
[00000287] avi private debug:      |    |    |    + strh size:56 pos:100
[00000287] avi private debug:      |    |    |    + strf size:40 pos:164
[00000287] avi private debug:      |    |    |    + JUNK size:4120 pos:212
[00000287] avi private debug:      |    |    + LIST-strl size:4222 pos:4340
[00000287] avi private debug:      |    |    |    + strh size:56 pos:4352
[00000287] avi private debug:      |    |    |    + strf size:18 pos:4416
[00000287] avi private debug:      |    |    |    + JUNK size:4120 pos:4442
[00000287] avi private debug:      |    |    + LIST-odml size:260 pos:8570
[00000287] avi private debug:      |    |    |    + dmlh size:248 pos:8582
[00000287] avi private debug:      |    + LIST-INFO size:56 pos:8838
[00000287] avi private debug:      |    |    + ISFT size:44 pos:8850
[00000287] avi private debug:      |    + JUNK size:1330 pos:8902
[00000287] avi private debug:      |    + LIST-movi size:730019516 pos:10240
[00000287] avi private debug:      |    + idx1 size:2766976 pos:730029764
[00000287] avi private debug:      + JUNK size:172 pos:732796748
[00000288] avi demuxer debug: AVIH: 2 stream, flags  HAS_INDEX IS_INTERLEAVED
[00000288] avi demuxer debug: stream[0] rate:2997 scale:125 samplesize:0
[00000288] avi demuxer debug: stream[0] video(XVID) 560x416 12bpp 23.976000fps
[00000277] main input debug: selecting program id=0
[00000288] avi demuxer debug: stream[1] rate:48000 scale:1 samplesize:1
[00000288] avi demuxer debug: stream[1] audio(0x2000) 6 channels 48000Hz 0bits
[00000288] avi demuxer debug: stream[0] created 86473 index entries
[00000288] avi demuxer debug: stream[1] created 86463 index entries
[00000288] avi demuxer debug: stream[0] length:3606 (based on index)
[00000288] avi demuxer debug: stream[1] length:3606 (based on index)
[00000144] main module debug: using demux2 module "avi"
[00000290] main decoder debug: looking for decoder module: 22 candidates
[00000290] ffmpeg decoder debug: libavcodec initialized (interface 3276800 )
[00000290] ffmpeg decoder debug: postprocessing disabled
[00000290] ffmpeg decoder debug: ffmpeg codec (MPEG-4 Video) started
[00000124] main module debug: using decoder module "ffmpeg"
[00000290] main decoder debug: thread 2974436272 (decoder) created at priority 0 (src/input/decoder.c:159)
[00000317] main decoder debug: looking for decoder module: 22 candidates
[00000095] main module debug: using decoder module "a52"
[00000317] main decoder debug: thread 2966043568 (decoder) created at priority 0 (src/input/decoder.c:159)
[00000277] main input debug: meta information:
[00000277] main input debug:   - 'Setting' = ' HAS_INDEX IS_INTERLEAVED'
[00000277] main input debug: `Eight Below cd1.avi' successfully opened
[00000288] avi demuxer debug: old:0 < new 0
[00000290] main decoder debug: no usable vout present, spawning one
[00000318] main video output debug: window size: 560x416
[00000318] main video output debug: looking for video output module: 9 candidates
[00000318] xvideo video output debug: adaptor 0, port 73, format 0x32315659 (YV12) planar
[00000319] main private debug: Registering subpicture channel, ID: 2
[00000319] main private debug: Registering subpicture channel, ID: 3
[00000319] main private debug: Registering subpicture channel, ID: 4
[00000319] main private debug: Registering subpicture channel, ID: 5
[00000318] xvideo video output debug: Window manager supports NetWM
[00000318] xvideo video output debug: Window manager supports _NET_WM_STATE_FULLSCREEN
[00000318] xvideo video output debug: Window manager supports _NET_WM_STATE_ABOVE
[00000318] xvideo video output debug: Window manager supports _NET_WM_STATE_BELOW
[00000011] main module debug: using video output module "xvideo"
[00000318] main video output debug: waiting for thread completion
[00000317] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
[00000317] main decoder debug: no aout present, spawning one
[00000320] main audio output debug: looking for audio output module: 6 candidates
ALSA lib setup.c:555:(add_elem) Cannot obtain info for CTL elem (MIXER,'IEC958 Playback AC97-SPSA',0,0,0): No such file or directory
[00000320] alsa audio output debug: opening ALSA device `default'
[00000320] main audio output debug: thread 2948541360 (aout) created at priority 0 (alsa.c:663)
[00000266] main module debug: using audio output module "alsa"
[00000320] main audio output debug: output 'fl32' 48000 Hz Stereo frame=1 samples/8 bytes
[00000320] main audio output debug: mixer 'fl32' 48000 Hz Stereo frame=1 samples/8 bytes
[00000320] main audio output debug: no need for any filter
[00000320] main audio output debug: looking for audio mixer module: 3 candidates
[00000081] main module debug: using audio mixer module "trivial_mixer"
[00000320] main audio output debug: input 'a52 ' 48000 Hz 3F2R/LFE frame=1536 samples/1536 bytes
[00000320] main audio output debug: filter(s) 'a52 '->'fl32' 48000 Hz->48000 Hz 3F2R/LFE->Stereo
[00000323] main private debug: looking for audio filter module: 24 candidates
[00000058] main module debug: using audio filter module "a52tofloat32"
[00000320] main audio output debug: found a filter for the whole conversion
[00000320] main audio output debug: filter(s) 'fl32'->'fl32' 52800 Hz->48000 Hz Stereo->Stereo
[00000326] main private debug: looking for audio filter module: 24 candidates
[00000076] main module debug: using audio filter module "bandlimited_resampler"
[00000320] main audio output debug: found a filter for the whole conversion
[00000318] main video output debug: got 8 direct buffer(s)
[00000318] main video output debug: picture in 560x416 (0,0,560x416), chroma I420, ar 96923:72000, sar 1:1
[00000318] main video output debug: picture user 560x416 (0,0,560x416), chroma I420, ar 96923:72000, sar 1:1
[00000318] main video output debug: picture out 560x416 (0,0,560x416), chroma I420, ar 96923:72000, sar 1:1
[00000318] main video output debug: direct render, mapping render pictures 0-6 to system pictures 1-7
[00000318] main video output debug: thread 2956934064 (video output) created at priority 0 (src/video_output/video_output.c:416)
[00000001] main vlc debug: removing all interfaces
[00000274] main interface debug: thread 3032812464 joined (src/interface/interface.c:238)
[00000031] main module debug: unlocking module "wxwidgets"
[00000272] main interface debug: thread 3056507824 joined (src/interface/interface.c:238)
[00000182] main module debug: unlocking module "screensaver"
[00000270] main interface debug: thread 3064900528 joined (src/interface/interface.c:238)
[00000135] main module debug: unlocking module "hotkeys"
[00000001] main vlc debug: removing all playlists
[00000269] main private debug: thread 3073293232 joined (src/playlist/playlist.c:237)
[00000277] main input debug: control type=0
[00000277] main input debug: control: stopping input
[00000277] main input debug: closing input
[00000287] avi private debug: free chunk avih
[00000287] avi private debug: free chunk strh
[00000287] avi private debug: free chunk strf
[00000287] avi private debug: free chunk JUNK
[00000287] avi private debug: free chunk LIST
[00000287] avi private debug: free chunk strh
[00000287] avi private debug: free chunk strf
[00000287] avi private debug: free chunk JUNK
[00000287] avi private debug: free chunk LIST
[00000287] avi private warning: unknown chunk (not unloaded)
[00000287] avi private debug: free chunk LIST
[00000287] avi private debug: free chunk LIST
[00000287] avi private debug: free chunk ISFT
[00000287] avi private debug: free chunk LIST
[00000287] avi private debug: free chunk JUNK
[00000287] avi private debug: free chunk LIST
[00000287] avi private debug: free chunk idx1
[00000287] avi private debug: free chunk RIFF
[00000287] avi private debug: free chunk JUNK
[00000287] avi private debug: free chunk LIST
[00000144] main module debug: unlocking module "avi"
[00000014] main module debug: unlocking module "access_file"
[00000290] ffmpeg decoder debug: ffmpeg codec (MPEG-4 Video) stopped
[00000124] main module debug: unlocking module "ffmpeg"
[00000290] main decoder debug: thread 2974436272 joined (src/input/decoder.c:191)
[00000290] main decoder debug: killing decoder fourcc `XVID', 2 PES in FIFO
[00000290] main decoder debug: cannot find playlist, destroying vout
[00000011] main module debug: unlocking module "xvideo"
[00000318] main video output debug: thread 2956934064 joined (src/video_output/video_output.c:456)
[00000095] main module debug: unlocking module "a52"
[00000317] main decoder debug: thread 2966043568 joined (src/input/decoder.c:191)
[00000317] main decoder debug: killing decoder fourcc `a52 ', 0 PES in FIFO
[00000058] main module debug: unlocking module "a52tofloat32"
[00000076] main module debug: unlocking module "bandlimited_resampler"
[00000320] main audio output debug: thread 2948541360 joined (alsa.c:715)
[00000266] main module debug: unlocking module "alsa"
[00000081] main module debug: unlocking module "trivial_mixer"
[00000277] main input debug: thread 3008900016 joined (src/input/input.c:386)
[00000268] main playlist debug: thread 3081685936 joined (src/playlist/playlist.c:238)
[00000268] main playlist: stopping playback
[00000268] main playlist debug: deleting playlist item `Eight Below cd1.avi'
[00000001] main vlc debug: removing all video outputs
[00000001] main vlc debug: removing all audio outputs
[00000001] main vlc debug: removing announce handler
[00000191] main module debug: unlocking module "memcpy"
[00000001] main vlc debug: opening config file /home/pzorko/.vlc/vlcrc
[00000001] main vlc debug: saving plugins cache file /home/pzorko/.vlc/cache/plugins-04041e.dat
pzorko@workgroup:~/Desktop/Moji prenosi$


---

### Post by kloshar on 2006-08-14
I see no errors. :shock:

---

### Post by kloshar on 2006-08-14
Anybody?

---

### Post by orasis on 2006-08-14
You are having a problem with MP4, you will need to find a codec, your AVI file is not an avi file it seems. - it is an MP4.

---

### Post by orasis on 2006-08-14
And for your DVD problem it seems that you do not have the proper subtitle language support, update your libraries.

---

### Post by kloshar on 2006-08-15
Thank you very much for your answer! Could you give me a little bit more instructions?

---

### Post by kloshar on 2006-08-16
The point is, that I cannot play any movie. Neither avi, neither wmv, neither mov, neither mpg ... And I'm almost sure, that I've downloaded all codecs. That caused linux upgrade (from breezy to drapper).

Please, help me

---

### Post by redmarshall on 2006-08-16
Same thing here!  I have installed and uninstalled MPlayer about 12 times and 12 diffferent ways as well.  I have even done what a proper newbie should do and installed automatix.  I let that do everything for me after i tried everything and I am still getting the same error code when trying to play "wmv" files...

"Cannot find codec matching selected -vo and video format 0x33564d57"

...I do have the newest essetials pack and I have pasted it to /usr/local/lib/codec

Any help would be awesome.](*,)

---

### Post by lazcool on 2006-08-17
I have the same problem with my (divx) avi files - audio but no video. I have the latest w32codecs package installed via synaptic.

Have the proprietry ati driver installed (from memory, flgrx?). Guess I will try to uninstall that and try again. What graphics chipset / driver are you using?

---

### Post by redmarshall on 2006-08-18
just figured it out!
first you need to download "w32codec_1.0_20050412-13_i386.deb" from here 

...[http://dl.atrpms.net/all/w32codec-1.0_20050412-12.at.i386.rpm](http://dl.atrpms.net/all/w32codec-1.0_20050412-12.at.i386.rpm)...

dont know the fancy crap so get the .rpm file to your computer then convert the .rpm to a .deb file...

sudo alien package_file.rpm

...then install the .deb file...

sudo dpkg -i package_file.deb

Once you do this it should automatically create a dir path /usr/lib/win32 and inside win32 should be a bunch of codecs.

restart the browser and you should be golden.  as of right now i'm having some text format issues when the video starts but at least I have video and sound.  let me know if you have any questions.

---

### Post by kloshar on 2006-08-18
Thank you but it doesn't work. In my case works everything just fine, just the video picture space is dark blue. :(

---

### Post by redmarshall on 2006-08-18
> **kloshar said:**
> Thank you but it doesn't work. In my case works everything just fine, just the video picture space is dark blue. :(

what version of dapper do you have?  basically what I did was a last resort before removing it and Compiling an older version.  

I take it you use mozilla firefox as your browser and you've downloaded the plugin from synaptic?  Also be sure that your browser media player is set to /usr/bin/x11/gmplayer.  when I first configure my media manager i made the mistake of setting it to /usr/bin/x11/mplayer and when it was set like that i was getting the dark blue window with sound no video.

---

### Post by kloshar on 2006-08-19
Dapper 6.06
I really don't mind mozilla video playing. I don't play videos over internet. All I need is to get mplayer working normally. Can the problem be connected with ubuntu theme? :-?  The problem is really strange. Everything is just fine: no errors in terminal, the player sets video size normally and everything would be all right if video showed..

---

### Post by kloshar on 2006-08-19
[[IMG]http://img209.imageshack.us/img209/501/screenshotjl1.th.png[/IMG]](http://img209.imageshack.us/my.php?image=screenshotjl1.png),

The screenshot.

---

### Post by kloshar on 2006-08-25
Still no answer? :confused:

---

### Post by kloshar on 2006-08-25
I see the picture with mplayer -vo gl . But the program says my computer is too slow to play videos. :confused: :confused: 

> mplayer -vo gl Robin\ Hood\ -\ Men\ In\  Tights.avi
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Sempron/Athlon MP/XP Thoroughbred; Duron Applebred ( Family: 6, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


91 audio & 204 video codecs
/usr/share/fonts/truetype/freefont/FreeSans.ttf doesn't look like a font descrip tion, ignoring.
Cannot load font: /usr/share/fonts/truetype/freefont/FreeSans.ttf
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing Robin Hood - Men In Tights.avi.
AVI file format detected.
VIDEO:  [DIV3]  576x312  24bpp  25.000 fps  832.8 kbps (101.7 kbyte/s)
dvdsublang...robin hood men in tights si sl slo en eng
dvdsublang...robin hood men in tights si sl slo en eng
dvdsublang...robin hood men in tights si sl slo en eng
dvdsublang...robin hood men in tights si sl slo en eng
dvdsublang...robin hood men in tights si sl slo en eng
dvdsublang...robin hood men in tights si sl slo en eng
dvdsublang...robin hood men in tights si sl slo en eng
dvdsublang...robin hood men in tights si sl slo en eng
SUB: Detected subtitle file format: microdvd
SUB: Read 1268 subtitles.
SUB: added subtitle file (1): ./Robin Hood - Men In Tights.sub
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[gl] using extended formats. Use -vo gl:nomanyfmts if playback fails.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffdivx] vfm: ffmpeg (FFmpeg DivX ;-) (MS MPEG-4 v3))
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 44100 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 576 x 312 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: using unscaled Planar YV12 -> BGRA special converter
VO: [gl] 576x312 => 576x312 BGRA
alsa-space: xrun of at least 33.774 msecs. resetting stream,?% 0 0
No bind found for key 'MOUSE_BTN2'                         1.1% 23 0
alsa-space: xrun of at least 210.313 msecs. resetting stream.4% 49 0
A:   5.9 V:   2.0 A-V:  3.875 ct:  0.200  51/ 51 15% 299%  2.3% 50 0

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

alsa-play: xrun of at least 98.635 msecs. resetting stream 4.1% 64 0
alsa-play: xrun of at least 22.697 msecs. resetting stream10.4% 66 0
alsa-space: xrun of at least 35.225 msecs. resetting stream3.6% 69 0
alsa-space: xrun of at least 306.717 msecs. resetting stream.1% 80 0
alsa-space: xrun of at least 482.265 msecs. resetting stream.6% 85 0
alsa-space: xrun of at least 5.679 msecs. resetting stream10.9% 92 0
alsa-space: xrun of at least 709.358 msecs. resetting stream.4% 98 0
alsa-space: xrun of at least 18.828 msecs. resetting stream0.1% 102 0
alsa-uninit: pcm closed11.458 ct:  0.412 104/104  9% 536% 10.0% 103 0

Exiting... (Quit)



---

### Post by claypole on 2006-09-13
I have the same problem.  If I reinstall the w32codecs and re-boot it seems to work for a bit and then stops again.  I have tried reinstalling various components/apps but to no avail.  It's really frustrating as it will not play any video formats on any players, just sound.  Because I can get it to work occasionally I know it CAN work!

Any help appreciated!

---

### Post by xyz on 2006-09-13
How about trying **crmanski** script...just right-click on the file and watch?
[http://www.ubuntuforums.org/showthread.php?t=62625&highlight=ogm](http://www.ubuntuforums.org/showthread.php?t=62625&highlight=ogm)

---

### Post by claypole on 2006-09-13
Thanks xyz, but it won't play ANY videos files, regardless of what format they are in.

---

### Post by xyz on 2006-09-13
**kloshar** says:
> I see the picture with mplayer -vo gl . But the program says my computer is too slow to play videos
How much RAM to you have? Give us your specs!

How about Automatix to make "sure" you've got all you need!
[www.getautomatix.com](www.getautomatix.com)
or
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by claypole on 2006-09-18
I have finally worked out the problem, which I think will help klosher too.

I am using an ATI driver which had the line below in /etc/X11/xorg.conf

	Option	    "VideoOverlay" "on"

in Section "Device"

I removed this line restarted xserver and everything is fine!!

I hope this helps.

---

