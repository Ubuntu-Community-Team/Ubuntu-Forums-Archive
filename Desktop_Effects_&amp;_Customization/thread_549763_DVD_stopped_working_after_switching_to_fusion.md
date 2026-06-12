---
title: "DVD stopped working after switching to fusion"
date: 2007-09-13
forum: Desktop Effects &amp; Customization
---

### Post by zabien1970 on 2007-09-13
When I first installed beryl it took me a while to get my DVD player working, can't remember how but I was using totem, now after switching to compiz fusion it doesn't work again.
  Putting a DVD in causes the player to start up, I get the startup screen for a few seconds then it just closes.
  Trying to use MPlayer I get a control box but when I push play it says 'seek failed'
  I have tried several different DVD's with same results

---

### Post by aquavitae on 2007-09-13
Can you post the output of "mplayer -v dvd://1" - it might give some idea of exactly where the problem is.  Can you mount the dvd normally (i.e. open files/folders on it)?

---

### Post by zabien1970 on 2007-09-13
[PHP][PHP]brendon@brendon-laptop:~$ mplayer -v dvd://1
MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1.70GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/brendon/.mplayer/codecs.conf'
Reading /home/brendon/.mplayer/codecs.conf: Can't open '/home/brendon/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
CommandLine: '-v' 'dvd://1'
init_freetype
get_path('font/font.desc') -> '/home/brendon/.mplayer/font/font.desc'
font: can't open file: /home/brendon/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Using nanosleep() timing
get_path('input.conf') -> '/home/brendon/.mplayer/input.conf'
Can't open input config file /home/brendon/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 67 binds
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('1.conf') -> '/home/brendon/.mplayer/1.conf'

Playing dvd://1.
get_path('sub/') -> '/home/brendon/.mplayer/sub/'
URL: dvd://1
Reading disc structure, please wait...
There are 68 titles on this DVD.
There are 25 chapters in this DVD title.
There are 1 angles in this DVD title.
DVD successfully opened.
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
audio stream: 1 format: ac3 (stereo) language: fr aid: 129.
audio stream: 2 format: ac3 (stereo) language: es aid: 130.
audio stream: 3 format: ac3 (stereo) language: en aid: 131.
audio stream: 4 format: ac3 (stereo) language: en aid: 132.
number of audio channels on disk: 5.
subtitle ( sid ): 0 language: en
subtitle ( sid ): 1 language: es
number of subtitles on disk: 2
DVD start cell: 0  pack: 0x0-0x23862  
DVD start=0 end=2074280  
STREAM: [null] dvd://1
STREAM: Description: DVD stream
STREAM: Author: 
STREAM: Comment: 
DVD Seek! lba=0x0  cell=0  packs: 0x0-0x23862  
Angle-seek synced by cell/vob IDN search!  
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
Searching demuxer type for filename dvd://1 ext: (null)
DVD Seek! lba=0x0  cell=0  packs: 0x0-0x23862  
Angle-seek synced by cell/vob IDN search!  
Checking for Nullsoft Streaming Video
DVD Seek! lba=0x0  cell=0  packs: 0x0-0x23862  
Angle-seek synced by cell/vob IDN search!  
Checking for MOV
Checking for VIVO
header block 1 size: 0
AVS: avs_check_file - attempting to open file dvd://1
AVS: File is too big, aborting...
Checking for PVA
Checking for MPEG-TS...
TRIED UP TO POSITION 70264, FOUND 47, packet_size= 0, SEEMS A TS? 0
DVD Seek! lba=0x22  cell=0  packs: 0x0-0x23862  
Angle-seek synced by cell/vob IDN search!  
DVD Seek! lba=0x0  cell=0  packs: 0x0-0x23862  
Angle-seek synced by cell/vob IDN search!  
Checking for LMLM4 Stream Format
Invalid packet in LMLM4 stream: ch=0 size=1140851708
LMLM4 Stream Format not found
system stream synced at 0xD (13)!
==> Found video stream: 0
DVD Seek! lba=0xFD2D9  cell=19  packs: 0xED191-0xFF1BC  
Angle-seek synced by cell/vob IDN search!  
==> Found subtitle: 0
==> Found subtitle: 1
==> Found audio stream: 129
==> Found audio stream: 128
==> Found audio stream: 130
==> Found audio stream: 131
==> Found audio stream: 132
DVD Seek! lba=0x1FA5B3  cell=35  packs: 0x1D4017-0x1FA6A3  
Angle-seek synced by cell/vob IDN search!  
--- END OF CELL !!! ---
DVD next cell: 36  pack: 0x1FA6A4-0x1FA6A8  
--- END OF CELL !!! ---
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)  
DVD Seek! lba=0x0  cell=0  packs: 0x0-0x23862  
Angle-seek synced by cell/vob IDN search!  
MPEG-PS file format detected.
==> Found subtitle: 2
==> Found subtitle: 3
Searching for sequence header... OK!
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  9800.0 kbps (1225.0 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x480  fps:29.97  ftime:=0.0334
get_path('sub/') -> '/home/brendon/.mplayer/sub/'
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1680x1050 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 1920x1088
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Trying filter chain: vo
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale vo
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
dec_audio: Allocating 3840 bytes for input buffer.
dec_audio: Allocating 6144 + 65536 = 71680 bytes for output buffer.
Using SSE optimized IMDCT transform
AC3: 2.0 (dolby)  48000 Hz  192.0 kbit/s
A52 flags before a52_frame: 0x2A
A52 flags after a52_frame: 0xA
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
alsa-init: requested format: 48000 Hz, 2 channels, 9
alsa-init: using ALSA 1.0.13
alsa-init: setup for 1/2 channel(s)
alsa-init: using device default
alsa-init: pcm opend in blocking mode
alsa-init: chunksize set to 1024
alsa-init: fragcount=16
alsa-init: got buffersize=65536
alsa-init: got period size 1024
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
AO: Description: ALSA-0.9.x-1.x audio output
AO: Author: Alex Beregszaszi, Zsolt Barat <joy@streamminister.de>
AO: Comment: under developement
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO Config (720x480->854x480,flags=0,'MPlayer',0x32315659)
VO: [xv] 720x480 => 854x480 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
Xvideo image format: 0x59565955 (UYVY) packed
using Xvideo port 73 for hw scaling
[xv] dx: 0 dy: 0 dw: 1024 dh: 480
*** [vo] Allocating mp_image_t, 720x480x12bpp YUV planar, 518400 bytes
[xv] dx: 0 dy: 0 dw: 1024 dh: 480
*** [vo] Allocating mp_image_t, 720x480x12bpp YUV planar, 518400 bytes
get_path('subfont.ttf') -> '/home/brendon/.mplayer/subfont.ttf'1 0 
Unicode font: 255 glyphs.
*** [vo] Allocating (slices) mp_image_t, 720x480x12bpp YUV planar, 518400 bytes
X11 error: BadAlloc (insufficient resources for operation)?,?% 2 0 
Type: 0, display: 0x8a934c8, resourceid: 5d, serial: 66
Error code: b, request code: 8d, minor code: 13


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
Uninit audio filters...
[libaf] Removing filter dummy 
Uninit audio: liba52
Uninit video: libmpeg2
alsa-uninit: pcm closed
vo: uninit ...
brendon@brendon-laptop:~$[/PHP][/PHP]

---

### Post by zabien1970 on 2007-09-13
I'm still pretty new to linux and have been doing most stuff through guides, I have compiz set to autostart and was wondering if temporarily turning it off may help, just need the command for this unless you don't think it would matter.

---

### Post by aquavitae on 2007-09-13
I don't know compiz-fusion, but usually for that type of app there is an option to disable for certain apps, e.g. mplayer.  From the output you posted it looks like its having trouble with the video out device, i.e. X11.  Since this started when you installed compiz, it indicated that compiz probably applied some settings that are incompatible with movie players.  I know transparency often causes problems, for example.  Look under the options for something about disabling fusion/desltopeffects for certain applications, and add totem and mplayer to the list.  Hope it works!

---

### Post by zabien1970 on 2007-09-13
OK, I found the code ' metacity --replace & ' which got my DVD player working again but I would still like to have it working in compiz if anyone has a solution

---

### Post by hyperair on 2007-09-13
Enable the Video plugin in CompizConfig Settings Manager and see if it works after that?

---

### Post by zabien1970 on 2007-09-13
Video Plugin is enabled

---

### Post by zabien1970 on 2007-09-13
[PHP]brendon@brendon-laptop:~$ mplayer -v dvd://1 
MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1.70GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/brendon/.mplayer/codecs.conf'
Reading /home/brendon/.mplayer/codecs.conf: Can't open '/home/brendon/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
CommandLine: '-v' 'dvd://1'
init_freetype
get_path('font/font.desc') -> '/home/brendon/.mplayer/font/font.desc'
font: can't open file: /home/brendon/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Using nanosleep() timing
get_path('input.conf') -> '/home/brendon/.mplayer/input.conf'
Can't open input config file /home/brendon/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 67 binds
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('1.conf') -> '/home/brendon/.mplayer/1.conf'

Playing dvd://1.
get_path('sub/') -> '/home/brendon/.mplayer/sub/'
URL: dvd://1
Reading disc structure, please wait...
There are 68 titles on this DVD.
There are 25 chapters in this DVD title.
There are 1 angles in this DVD title.
DVD successfully opened.
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
audio stream: 1 format: ac3 (stereo) language: fr aid: 129.
audio stream: 2 format: ac3 (stereo) language: es aid: 130.
audio stream: 3 format: ac3 (stereo) language: en aid: 131.
audio stream: 4 format: ac3 (stereo) language: en aid: 132.
number of audio channels on disk: 5.
subtitle ( sid ): 0 language: en
subtitle ( sid ): 1 language: es
number of subtitles on disk: 2
DVD start cell: 0  pack: 0x0-0x23862  
DVD start=0 end=2074280  
STREAM: [null] dvd://1
STREAM: Description: DVD stream
STREAM: Author: 
STREAM: Comment: 
DVD Seek! lba=0x0  cell=0  packs: 0x0-0x23862  
Angle-seek synced by cell/vob IDN search!  
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
Searching demuxer type for filename dvd://1 ext: (null)
DVD Seek! lba=0x0  cell=0  packs: 0x0-0x23862  
Angle-seek synced by cell/vob IDN search!  
Checking for Nullsoft Streaming Video
DVD Seek! lba=0x0  cell=0  packs: 0x0-0x23862  
Angle-seek synced by cell/vob IDN search!  
Checking for MOV
Checking for VIVO
header block 1 size: 0
AVS: avs_check_file - attempting to open file dvd://1
AVS: File is too big, aborting...
Checking for PVA
Checking for MPEG-TS...
TRIED UP TO POSITION 70264, FOUND 47, packet_size= 0, SEEMS A TS? 0
DVD Seek! lba=0x22  cell=0  packs: 0x0-0x23862  
Angle-seek synced by cell/vob IDN search!  
DVD Seek! lba=0x0  cell=0  packs: 0x0-0x23862  
Angle-seek synced by cell/vob IDN search!  
Checking for LMLM4 Stream Format
Invalid packet in LMLM4 stream: ch=0 size=1140851708
LMLM4 Stream Format not found
system stream synced at 0xD (13)!
==> Found video stream: 0
DVD Seek! lba=0xFD2D9  cell=19  packs: 0xED191-0xFF1BC  
Angle-seek synced by cell/vob IDN search!  
==> Found subtitle: 0
==> Found subtitle: 1
==> Found audio stream: 129
==> Found audio stream: 128
==> Found audio stream: 130
==> Found audio stream: 131
==> Found audio stream: 132
DVD Seek! lba=0x1FA5B3  cell=35  packs: 0x1D4017-0x1FA6A3  
Angle-seek synced by cell/vob IDN search!  
--- END OF CELL !!! ---
DVD next cell: 36  pack: 0x1FA6A4-0x1FA6A8  
--- END OF CELL !!! ---
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)  
DVD Seek! lba=0x0  cell=0  packs: 0x0-0x23862  
Angle-seek synced by cell/vob IDN search!  
MPEG-PS file format detected.
==> Found subtitle: 2
==> Found subtitle: 3
Searching for sequence header... OK!
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  9800.0 kbps (1225.0 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x480  fps:29.97  ftime:=0.0334
get_path('sub/') -> '/home/brendon/.mplayer/sub/'
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1680x1050 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 1920x1088
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Trying filter chain: vo
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale vo
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
dec_audio: Allocating 3840 bytes for input buffer.
dec_audio: Allocating 6144 + 65536 = 71680 bytes for output buffer.
Using SSE optimized IMDCT transform
AC3: 2.0 (dolby)  48000 Hz  192.0 kbit/s
A52 flags before a52_frame: 0x2A
A52 flags after a52_frame: 0xA
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
alsa-init: requested format: 48000 Hz, 2 channels, 9
alsa-init: using ALSA 1.0.13
alsa-init: setup for 1/2 channel(s)
alsa-init: using device default
alsa-init: pcm opend in blocking mode
alsa-init: chunksize set to 1024
alsa-init: fragcount=16
alsa-init: got buffersize=65536
alsa-init: got period size 1024
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
AO: Description: ALSA-0.9.x-1.x audio output
AO: Author: Alex Beregszaszi, Zsolt Barat <joy@streamminister.de>
AO: Comment: under developement
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO Config (720x480->854x480,flags=0,'MPlayer',0x32315659)
VO: [xv] 720x480 => 854x480 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
Xvideo image format: 0x59565955 (UYVY) packed
using Xvideo port 73 for hw scaling
[xv] dx: 0 dy: 0 dw: 1024 dh: 480
*** [vo] Allocating mp_image_t, 720x480x12bpp YUV planar, 518400 bytes
[xv] dx: 0 dy: 0 dw: 1024 dh: 480
*** [vo] Allocating mp_image_t, 720x480x12bpp YUV planar, 518400 bytes
get_path('subfont.ttf') -> '/home/brendon/.mplayer/subfont.ttf'1 0 
Unicode font: 255 glyphs.
*** [vo] Allocating (slices) mp_image_t, 720x480x12bpp YUV planar, 518400 bytes
A:   0.7 V:   0.7 A-V:  0.076 ct:  0.036  16/ 13 ??% ??% ??,?% 6 0 
demux_mpg: 24000/1001fps progressive NTSC content detected, switching framerate.
Uninit audio filters... 0.003 ct:  0.068 161/158 31%  4%  3.3% 6 0 
[libaf] Removing filter dummy 
Uninit audio: liba52
Uninit video: libmpeg2
alsa-uninit: pcm closed
vo: uninit ...

Exiting... (Quit)
brendon@brendon-laptop:~$ 

[/PHP]

Here is the output in metacity, same DVD, the player works here

---

### Post by zabien1970 on 2007-09-13
After comparing the output of both they seem identical until the very end when I get " X11 error: BadAlloc (insufficient resources for operation)?,?% 2 0 " under compiz.
  
  It appears it may be a memory issue, I believe I have 1GB of ram. Hopefully this may help someone diagnose my problem, Once again I'm still fairly new to linux so if you need more info I'll need the command to get it, thanks for all the help so far.

---

### Post by tvrg on 2007-09-13
what card & driver are you using?

---

### Post by zabien1970 on 2007-09-13
I'm on a Dell inspiron 6000 laptop, Integrated intel graphics media accelerator 900 video, not sure on the driver but compiz works flawlessly so far with 3d, except for dvd playing. Pentium M processor 735(1.7GHz, 2MB cache, 400MHz FSB)

---

### Post by aquavitae on 2007-09-13
Could it perhaps be that you don't have enough memory on your graphics card for compiz and mplayer?  Compiz takes quite a bit, and so do dvds.  Dunno - could be way off, but its an idea.

---

### Post by zabien1970 on 2007-09-13
That's kinda what I was wondering in my earlier reply when I referenced the error. This being linux though I was hoping someone would know how to check what memory is being used where and if its possible for the graphics to share some ram. I am running gkrellm and normally only use about half of my 1Gb, I don't think I've ever used the swap. Or some other workaround. This isn't really a necessity since I can get the DVD player to work it just would be nice to have it all. :)

---

### Post by JBAlaska on 2007-09-13
Try launching mplayer with this command; 
XLIB_SKIP_ARGB_VISUALS=1 totem

---

### Post by zabien1970 on 2007-09-14
[PHP]OK, just got home from work, using  "XLIB_SKIP_ARGB_VISUALS=1 totem" I get
 brendon@brendon-laptop:~$ XLIB_SKIP_ARGB_VISUALS=1 totem

(totem:6641): Gtk-WARNING **: Attempting to add `dvd:/' to the list of recently used resources, but not MIME type was defined
libdvdnav: Using dvdnav version 1.1.4 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/brendon/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000226
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000045e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000004a5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00000606
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0002d960
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0002da83
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0005ac49
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0005acea
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00063762
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00063784
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0006ef3b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0006ef59
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0008c64a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x000b8991
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x000f5159
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x000fd473
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x002f7b90
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x00308ad6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x00332766
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x0038d991
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x003b0922
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x003b1a55
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x003b1a72
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_1.VOB at 0x003b2696
libdvdread: Elapsed time 0
libdvdread: Found 16 VTS's
libdvdread: Elapsed time 0
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 72 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
brendon@brendon-laptop:~$ 

[/PHP]

Once again I get an insufficient resource error, I can play DVD's if I turn off compiz so I'm pretty sure compiz is hogging my memory, is there a way to force compiz into my swap during dvd playback? I know this would slow it down but I don't really need desktop effects while watching a movie and it would be alot easier than opening a terminal all the time to manually configure this.

---

### Post by hyperair on 2007-09-14
I know I used to have that problem... Don't remember how I fixed it, or maybe it just fixed itself over the flood of updates that came in between now and the time I had that problem. It's nothing to do with the RAM, but more of Video RAM.

---

### Post by tvrg on 2007-09-14
please post the output of lspci which should look something like this:
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)

and then do lspci $ lspci -v -s 00:02.0 (where the number is the number next to your vid card when you ran lspci

---

### Post by zabien1970 on 2007-09-14
Here is the output of "lspci" 

```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
```


  I see 2 possibilities  00:02.0 and 00:2.1, should I run the command "lspci $ lspci -v -s" for both of these?
  What does the command do?

---

### Post by aquavitae on 2007-09-17
> **zabien1970 said:**
> 
Once again I get an insufficient resource error, I can play DVD's if I turn off compiz so I'm pretty sure compiz is hogging my memory, is there a way to force compiz into my swap during dvd playback? I know this would slow it down but I don't really need desktop effects while watching a movie and it would be alot easier than opening a terminal all the time to manually configure this.
You could do a short script for this - create a file "totem-compiz" and enter the following text```

#!/bin/sh

# Turn off compiz
metacity --replace &

# Start totem.  I think this is right, but you can check it by editing the menu and looking at the command
totem

#Turn on compiz when finished.  Not sure about this either- I'm hoping you'll know
compiz --replace &

```

Then set the file to be executable (under the properties - permissions tab) and change the menu command to point to it instead.  Btw, I'm not at linux atm so I can't check the script.  Let me know if there's anything wrong with it!

---

### Post by tvrg on 2007-09-17
> **zabien1970 said:**
> 
  I see 2 possibilities  00:02.0 and 00:2.1, should I run the command "lspci $ lspci -v -s" for both of these?
  What does the command do?

yup, it shows more details (ie memory) of your card

---

### Post by zabien1970 on 2007-09-17
tvrg: here's the output

```
brendon@brendon-laptop:~$ lspci $ lspci -v -s 00:02.0
Usage: lspci [<switches>]

-v              Be verbose
-n              Show numeric ID's
-nn             Show both textual and numeric ID's (names & numbers)
-b              Bus-centric view (PCI addresses and IRQ's instead of those seen by the CPU)
-x              Show hex-dump of the standard portion of config space
-xxx            Show hex-dump of the whole config space (dangerous; root only)
-xxxx           Show hex-dump of the 4096-byte extended config space (root only)
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]   Show only devices in selected slots
-d [<vendor>]:[<device>]        Show only selected devices
-t              Show bus tree
-m              Produce machine-readable output
-i <file>       Use specified ID database instead of /usr/share/misc/pci.ids.gz
-D              Always show domain numbers
-M              Enable `bus mapping' mode (dangerous; root only)
-P <dir>        Use specified directory instead of /proc/bus/pci
-H <mode>       Use direct hardware access (<mode> = 1 or 2)
-F <file>       Read configuration data from given file
-G              Enable PCI access debugging
brendon@brendon-laptop:~$ lspci $ lspci -v -s 00:02.1
Usage: lspci [<switches>]

-v              Be verbose
-n              Show numeric ID's
-nn             Show both textual and numeric ID's (names & numbers)
-b              Bus-centric view (PCI addresses and IRQ's instead of those seen by the CPU)
-x              Show hex-dump of the standard portion of config space
-xxx            Show hex-dump of the whole config space (dangerous; root only)
-xxxx           Show hex-dump of the 4096-byte extended config space (root only)
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]   Show only devices in selected slots
-d [<vendor>]:[<device>]        Show only selected devices
-t              Show bus tree
-m              Produce machine-readable output
-i <file>       Use specified ID database instead of /usr/share/misc/pci.ids.gz
-D              Always show domain numbers
-M              Enable `bus mapping' mode (dangerous; root only)
-P <dir>        Use specified directory instead of /proc/bus/pci
-H <mode>       Use direct hardware access (<mode> = 1 or 2)
-F <file>       Read configuration data from given file
-G              Enable PCI access debugging
brendon@brendon-laptop:~$ 


```

---

### Post by zabien1970 on 2007-09-17
aquavitae;  could you give me a little more detail on how to do this, ie- how to create the file, where to create the file, etc.  I'm still learning the basics here and would hate to screw it up.

---

### Post by tvrg on 2007-09-17
sorry i made you run the wrong command (lspci is in there twice :)

```
lspci -v -s 00:02.0
```

---

### Post by zabien1970 on 2007-09-17
Also unrelated I am running gkrellm and tried to make it sticky on the right side of my screen, the problem with that setup though is it covers the screen and I have to close it to access things like my shutdown button, is there a way to change my screen size, if youre unfamiliar with this I'll start a new post.

  Thanks for all the help so far, even with the few glitches so far I love this system

---

### Post by zabien1970 on 2007-09-17
```
brendon@brendon-laptop:~$ lspci -v -s 00:02.0
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 0188
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at ec38 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

brendon@brendon-laptop:~$ lspci -v -s 00:02.1
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
        Subsystem: Dell Unknown device 0188
        Flags: bus master, fast devsel, latency 0
        Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>


```

---

### Post by tvrg on 2007-09-17
512k should be enough i suppose

---

### Post by aquavitae on 2007-09-17
> **zabien1970 said:**
> aquavitae;  could you give me a little more detail on how to do this, ie- how to create the file, where to create the file, etc.  I'm still learning the basics here and would hate to screw it up.
Hopefully with all the other help here you won need to do it this way, but its useful to know to I&#314;l try to explain anyway.
As for how to create the file - just open gedit, type up the file contents and save it.  Where to put it is really a matter preference.  What I do it I have a folder ~/bin where I keep any personal scripts.  I'd save it there.  Then either add ~/bin to your PATH, symlink the scripts to something already in your PATH (e.g. /usr/local/bin) or leave it all as is, and just use the full path when referring to the script.

The first options is probably the tidiest, but it meant editing the PATH variable, and I'm not sure how to do that in ubuntu.  The second option (which I use) is fairly easy - open a terminal and type
```
ln -s /usr/local/bin/*<script_name>* ~/bin/*<script_name>*
```
The last option is easiest - when you put it in the menu use the command ~/bin/*<script_name>* instead of just *<script_name>*

The script name itself doesn't matter - just don't use spaces in it.  Technically you can, but it makes life easier if you don't.

Hope this helps!

---

### Post by hyperair on 2007-09-17
The way to modify the PATH:
Add this line somewhere in your ~/.bashrc file (create it if it doesn't exist, ane make sure that the top of your file has the line "#!/bin/sh"):
```
export PATH=~/bin:$PATH
```

Another thing.. I think you meant that you wanted to create a symlink in /usr/local/bin pointing to the script in ~/bin. If that's the case, then it should be:
```

sudo ln -s /home/<username>/bin/<script-name> /usr/local/bin

```

A few things to note (for tvrg's benefit):
sudo - gives you superuser privileges so you can write to /usr/local/bin
usage of ln -s: ln -s <file-to-be-linked> <link location (if directory, then the file name is copied over)>
usage of /home/<username>/bin instead of ~/bin: Only matters if you have more than one user in your computer. If you use the latter, only you can use it.

---

### Post by aquavitae on 2007-09-18
hyperair, thanks for the corrections.  I always get that ln the wrong way round!;)

---

### Post by hyperair on 2007-09-18
No probs. I used to have trouble remembering too. Just remember, the source is always before the destination. Same goes for "cp" and "mv"

---

