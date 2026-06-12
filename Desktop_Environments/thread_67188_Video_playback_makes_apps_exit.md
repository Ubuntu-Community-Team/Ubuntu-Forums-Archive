---
title: "Video playback makes apps exit"
date: 2005-09-19
forum: Desktop Environments
---

### Post by flny007 on 2005-09-19
Thanks for looking.
Whenever I playback video, either mpeg4 from harddisk, or dvd from the drive, the player application starts and then exits. It happens the same for VLC, MPlayer, Totem, Ogle. For a split second before the crash, the first frames of the file are displayed, so I know the codecs must be there somewhere.

Any ideas are greatly appreciated!

---

### Post by flny007 on 2005-09-19
I also tried the gstreamer properties tool. I had the default sink set to XWindows with XV, which crashed on test. Then I switched to XWindows (no Xv), and the test worked, but still no playback apps work.

---

### Post by TristanMike on 2005-09-19
Try running the app from the terminal, then post the output when it crashes. I doubt I'll be able to help fully, but at least it gives others something to work with.

---

### Post by flny007 on 2005-09-19
This is what I get with MPlayer opening a DVD:

[INDENT]
MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Advanced Micro Devices Athlon MP/XP/XP-M Barton (Family: 6, Stepping: 0)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE



Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
**Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.**
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /media/cdrom.
Cache fill:  0.00% (0 bytes)    XMMS: found plugin: libmpg123.so (MPEG Layer 1/2/3 Player 1.2.10)
XMMS: found plugin: libwav.so (Wave Player 1.2.10)
XMMS: found plugin: libmikmod.so (MikMod Player 1.2.10)
XMMS: found plugin: libcdaudio.so (CD Audio Player 1.2.10)
XMMS: found plugin: libtonegen.so (Tone Generator 1.2.10)
XMMS: found plugin: libvorbis.so (Ogg Vorbis Player 1.2.10)
XMMS: Closing plugin /usr/lib/xmms/Input/libvorbis.so
XMMS: Closing plugin /usr/lib/xmms/Input/libtonegen.so
XMMS: Closing plugin /usr/lib/xmms/Input/libcdaudio.so
XMMS: Closing plugin /usr/lib/xmms/Input/libmikmod.so
XMMS: Closing plugin /usr/lib/xmms/Input/libwav.so
XMMS: Closing plugin /usr/lib/xmms/Input/libmpg123.so


Exiting... (End of file)

[/INDENT] 

Ok, what is going on here? I don't get the permission denial. Everything should be ok.

---

### Post by flny007 on 2005-09-19
Wait! I think I found something. I tried opening the DVD with VLC, and this is what I got:

[INDENT]
VLC media player 0.8.1 Janus
libdvdnav: Using dvdnav version 0.1.9 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/hdc mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/shane/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000132
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000004c9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000539
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0000054e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00001486
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x000cf68e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x000cfe30
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00344dde
libdvdread: Elapsed time 0
libdvdread: Found 5 VTS's
libdvdread: Elapsed time 0
libdvdnav: Suspected RCE Region Protection!!!
[B]The program '.' received an X Window System error.
This probably reflects a bug in the program.[/B]
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 76 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

[/INDENT] 

That X Window error looks like something. Any suggestions?

---

