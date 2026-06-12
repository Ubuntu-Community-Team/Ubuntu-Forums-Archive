---
title: "BadAlloc (insufficient resources for operation)"
date: 2006-06-01
forum: Desktop Environments
---

### Post by edcrfv on 2006-06-01
Repost/update from [http://www.ubuntuforums.org/showthread.php?t=181040](http://www.ubuntuforums.org/showthread.php?t=181040)

I don't know how it's related to Dapper but since I upgraded from breezy I can't read "big" videos anymore with most of the media players. I don't know exactly where the limit is but I can play 480x204 vid but not 480x260 so the limit should be somewhere in between. I can play these big videos with gmplayer and with the mplayer plugin inside Firefox.
My video card is an ATI Rage 128 AIW AGP.

Here are the error messages:
> **"totem/xine"]The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 73 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously said:**
> 

[QUOTE="vlc"]VLC media player 0.8.5 Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85


> **"mplayer"]MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Athlon Thunderbird (Family: 6, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 0 SSE2: 0
Compiled with runtime CPU detection.


91 audio & 204 video codecs
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
Playing test.rm.
REAL file format detected.
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
Stream description: Video Stream
Stream mimetype: video/x-pn-realvideo
Stream mimetype: logical-fileinfo
VIDEO:  [RV40]  640x300  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 name: BA HD vost : "Volver"
 author: AlloCin
 copyright: &#65533 said:**
>  FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 96.5 kbit/6.84% (ratio: 12058->176400)
Selected audio codec: [ffcook] afm: ffmpeg (FFmpeg COOK audio decoder)
==========================================================================
==========================================================================
Opening video decoder: [realvid] RealVideo decoder
opening shared obj '/usr/lib/win32/drvc.so'
Selected video codec: [rv3040] vfm: realvid (Linux RealPlayer 10 RV30/40 decoder)
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 44100 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 640 x 300 (preferred colorspace: Planar I420)
VDec: using Planar I420 as output csp (no 0)
Movie-Aspect is 2.13:1 - prescaling to correct movie aspect.
VO: [xv] 640x300 => 640x300 Planar I420
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
alsa-uninit: pcm closed


> **"realplay"]The program 'realplay.bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 35 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously said:**
> 

[QUOTE="kaffeine/gstreamer"]ASSERT: "i <= nodes" in /usr/share/qt3/include/qvaluelist.h (373)
DVB 0 : Aucun fichier ou répertoire de ce type
DVB 1 : Aucun fichier ou répertoire de ce type
DVB 2 : Aucun fichier ou répertoire de ce type
DVB 3 : Aucun fichier ou répertoire de ce type
X Error: BadAlloc (insufficient resources for operation) 11
  Major opcode:  141
  Minor opcode:  19
  Resource id:  0x0

The sound plays but no video and the last 4 lines repeats until the end

---

### Post by Chuckaluphagus on 2006-06-02
I'm having a similar but not identical problem withTotem 1.4.1 since I upgraded to Dapper.  if I try and run Totem by clicking "Movie Player" in the Applications->Sound & Video menu, the program appears to load but then crashes out after less than a second with no error message.  If I run totem from a command line, the same crash happens and I get this error message:

```
charles@ubuntu:~$ totem

(totem:9026): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 70 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
charles@ubuntu:~$
```

  Strangely enough, however, If I double-click on any video file on my hard drive or place a DVD in my DVD-ROM drive, totem loads and plays the video just fine.  Once it's open and running a video file, I can load new video, change the preferences, etc.  I simply can't open totem without calling a video file of some sort.  I can still play video, so this isn't even remotely a serious problem, but it is odd and only came about yesterday when I upgraded from Breezy to Dapper through the Update Manager.

  Otherwise, Dapper is sweet.  Thanks to everyone who contributed, you folks do nice work.

---

### Post by edcrfv on 2006-06-02
Probably this is related to your problem
[https://launchpad.net/distros/ubuntu/+source/totem/+bug/35229](https://launchpad.net/distros/ubuntu/+source/totem/+bug/35229)

---

### Post by Chuckaluphagus on 2006-06-02
[QUOTE=edcrfv]Probably this is related to your problem
[https://launchpad.net/distros/ubuntu/+source/totem/+bug/35229](https://launchpad.net/distros/ubuntu/+source/totem/+bug/35229)[/QUOTE]

That looks to be exactly the issue.  I've never tried to play anything terribly high definition through Totem, but the crash behavior described appears to be exactly what's happening.  I'll run through the recommendations during my lunch break and see whether they provide a fix.  If not, I'll post back here (or to the bug report thread).  Thanks for the help.

Update:
edcrfv, I followed the instructions for the workaround in the bug report you linked to.  I resized the graphic totem_logo.png in /usr/share/totem to an 800x640 file and Totem will now load properly without crashing, even without running a video file.  Thanks again for your help.

---

