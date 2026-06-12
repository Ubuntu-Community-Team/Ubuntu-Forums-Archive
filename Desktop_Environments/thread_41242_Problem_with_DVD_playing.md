---
title: "Problem with DVD playing"
date: 2005-06-12
forum: Desktop Environments
---

### Post by Gandalf on 2005-06-12
Hello guys,
i have a problem, i can't play almost 99% of DVD discs, i made a little error log,


TOTEM
------------------------------------------------------
wael@nasreddine:~$ totem

** (totem:17284): CRITICAL **: totem_pl_parser_parse: assertion `strstr (url, ": //") != NULL' failed
libdvdnav: Using dvdnav version 1.0 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdnav: DVD Title: METALLICA
libdvdnav: DVD Serial Number: 288f2494
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/wael/.dvdnav/METALLICA.map'
libdvdnav: DVD disk reports itself with Region mask 0x00c10000. Regions: 2 3 4 5  6

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000031b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000378
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00017249
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0036d588
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0036d58e
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 126 error_code 11 request_code 142 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)



VLC
---------------------------------------------------
wael@nasreddine:~$ vlc
VLC media player 0.8.1 Janus
libdvdnav: Using dvdnav version 0.1.9 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdnav: DVD Title: METALLICA
libdvdnav: DVD Serial Number: 288f2494
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/wael/.dvdnav/METALLICA.map'
libdvdnav: DVD disk reports itself with Region mask 0x00c10000. Regions: 2 3 4 5 6

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000031b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000378
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00017249
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0036d588
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0036d58e
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
[00000275] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:256000
No accelerated IMDCT transform found
The program '.' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 74 error_code 11 request_code 142 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


DVD lib
----------------------------------
wael@nasreddine:~$ dpkg -l |grep dvd
ii  dvd+rw-tools   5.21.4.10.8-1u DVD+-RW/R tools
ii  dvdrip         0.52.3-0.2     perl front end for transcode
ii  libdvdcss2     1.2.8-woody0.0 Simple foundation for reading DVDs - runtime
ii  libdvdnav4     0.1.9-3        The DVD navigation library
ii  libdvdread3    0.9.4-5        Simple foundation for reading DVDs










what do you think the problem can be?

thank you...

---

### Post by RastaMahata on 2005-06-12
> **Gandalf]Hello guys,
i have a problem, i can't play almost 99% of DVD discs, i made a little error log,


TOTEM
------------------------------------------------------
wael@nasreddine:~$ totem

** (totem:17284): CRITICAL **: totem_pl_parser_parse: assertion `strstr (url, ": //") != NULL' failed
libdvdnav: Using dvdnav version 1.0 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdnav: DVD Title: METALLICA
libdvdnav: DVD Serial Number: 288f2494
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/wael/.dvdnav/METALLICA.map'
libdvdnav: DVD disk reports itself with Region mask 0x00c10000. Regions: 2 3 4 5  6

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000031b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000378
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00017249
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0036d588
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0036d58e
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 126 error_code 11 request_code 142 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously said:**
> http://dvd.sf.net[/url]
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdnav: DVD Title: METALLICA
libdvdnav: DVD Serial Number: 288f2494
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/wael/.dvdnav/METALLICA.map'
libdvdnav: DVD disk reports itself with Region mask 0x00c10000. Regions: 2 3 4 5 6

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000031b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000378
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00017249
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0036d588
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0036d58e
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
[00000275] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:256000
No accelerated IMDCT transform found
The program '.' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 74 error_code 11 request_code 142 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


DVD lib
----------------------------------
wael@nasreddine:~$ dpkg -l |grep dvd
ii  dvd+rw-tools   5.21.4.10.8-1u DVD+-RW/R tools
ii  dvdrip         0.52.3-0.2     perl front end for transcode
ii  libdvdcss2     1.2.8-woody0.0 Simple foundation for reading DVDs - runtime
ii  libdvdnav4     0.1.9-3        The DVD navigation library
ii  libdvdread3    0.9.4-5        Simple foundation for reading DVDs










what do you think the problem can be?

thank you...
 maybe the version of your libdvdcss2...

alvaro@Eleanor:~$ dpkg -l |grep dvd
ii  dvd+rw-tools   5.21.4.10.8-1u DVD+-RW/R tools
ii  graveman       0.3.12-1~5.04u graphical tool to burn dvd and cd, gtk based
ii  libdvdcss2     1.2.8-1~5.04ub portable abstraction library for DVD decrypt
ii  libdvdnav4     0.1.9-3        The DVD navigation library
ii  libdvdread3    0.9.4-5        Simple foundation for reading DVDs

I have the one from backports, and I can play DVDs just fine :S

---

### Post by Gandalf on 2005-06-13
[QUOTE=RastaMahata]maybe the version of your libdvdcss2...

alvaro@Eleanor:~$ dpkg -l |grep dvd
ii  dvd+rw-tools   5.21.4.10.8-1u DVD+-RW/R tools
ii  graveman       0.3.12-1~5.04u graphical tool to burn dvd and cd, gtk based
ii  libdvdcss2     1.2.8-1~5.04ub portable abstraction library for DVD decrypt
ii  libdvdnav4     0.1.9-3        The DVD navigation library
ii  libdvdread3    0.9.4-5        Simple foundation for reading DVDs

I have the one from backports, and I can play DVDs just fine :S[/QUOTE]
 i have install --reinstall the same packages you have

wael@nasreddine:~$ dpkg -l |grep dvd
ii  dvd+rw-tools   5.21.4.10.8-1u DVD+-RW/R tools
rc  dvdrip         0.52.3-0.2     perl front end for transcode
ii  graveman       0.3.12-1~5.04u graphical tool to burn dvd and cd, gtk based
ii  libdvdcss2     1.2.8-1~5.04ub portable abstraction library for DVD decrypt
ii  libdvdnav4     0.1.9-3        The DVD navigation library
ii  libdvdread3    0.9.4-5        Simple foundation for reading DVDs


i still have the problem :'(

---

### Post by gheorghe_pop on 2005-06-13
I have the same problem:
this is what i get with:
mplayer
```
MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Advanced Micro Devices Athlon 4 /Athlon MP/XP Palomino (Family: 6, Stepping: 2)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Playing dvd://.
Reading disc structure, please wait...
libdvdread: Can't open file VIDEO_TS.IFO.
Can't open VMG info!


Exiting... (End of file)

``` 

totem
```
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdread: Can't open file VIDEO_TS.IFO.

```

---

