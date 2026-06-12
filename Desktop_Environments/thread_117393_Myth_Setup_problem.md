---
title: "Myth Setup problem"
date: 2006-01-14
forum: Desktop Environments
---

### Post by majkmil on 2006-01-14
I was able get into mythtv setup when I was setting up myth. Now I can't. . Here is the error I get.

mark@ubuntu:~$ mythtv setup
2006-01-14 19:50:37.525 New] DB connection, total: 1
Total desktop width=1280, height=1024, numscreens=1
2006-01-14 19:50:37.535 Using screen 0, 1280x1024 at 0,0
2006-01-14 19:50:37.542 Switching to square mode (G.A.N.T.)
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2006-01-14 19:50:38.625 Joystick disabled.
2006-01-14 19:50:38.664 New DB connection, total: 2
2006-01-14 19:50:38.684 Could not open setup. 0 retries remaining.
2006-01-14 19:50:39.187 Unknown state transition: 0 to 0
2006-01-14 19:50:40.191 Changing from None to None

My next problem is [ X or Xv ] I can capture a mpg file but it won't playback.Here is the other error. Whats up with myth and Xv. 

mark@ubuntu:~$ mplayer -vo xv /tmp/test.mpg
MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices Athlon MP/XP Thoroughbred (Family: 6, Stepping: 0)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags: MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE



86 audio & 200 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startupscripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /tmp/test.mpg.
MPEG-PS file format detected.
VIDEO: MPEG2 480x480 (aspect 2) 29.970 fps 6000.0 kbps (750.0 kbyte/s)
================================================== ========================
Trying to force audio codec driver family libmad...
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [mad] afm:libmad (libMAD MPEG layer 1-2-3)
================================================== ========================
vo: X11 running at 1280x1024 with depth 24 and 32 bpp (":0.0" => local display)It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
Error opening/initializing the selected video_out (-vo) device.

I am sorry about the long post. Any help will be appreciated. Thanks

---

