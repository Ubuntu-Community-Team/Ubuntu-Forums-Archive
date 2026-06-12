---
title: "DVD Cannot be played or ripped by any program."
date: 2009-04-07
forum: General Help
---

### Post by oleander on 2009-04-07
Hi, all. I am running Ubuntu 8.10 with all the latest updates as of today (April 7, 2009). I do have ubuntu-restricted-extras installed, as well as libdvdread3 and libdvdnav4. I have all of the gstreamer plugins (the good, bad, and the ugly). I have tried playback with a dvd using Totem, Vlc, Ogle, Mplayer, and Xine and none of them worked.

With Mplayer, I got a "seek failed" error.

Here is the output when trying to play the DVD with Totem:
```
 totem
** (totem:11734): DEBUG: Init of Python module
** (totem:11734): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:11734): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:11734): DEBUG: Creating Python plugin instance
** (totem:11734): DEBUG: Init of Python module
** (totem:11734): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:11734): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:11734): DEBUG: Creating Python plugin instance
** Message: no file info
** Message: no file info
Device is now /dev/scd0
libdvdnav: Using dvdnav version 4.1.2 from http://dvd.sf.net
libdvdnav: DVD Title: LEOLO
libdvdnav: DVD Serial Number: 431DAA7A___MVB__
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/one/.dvdnav/LEOLO.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
VTS change
cur audio stream change
NAV packet discont: cur_end_ts 99:99:99.999999999 !=  vobu_start_ptm: 0:00:00.233566666 base 0:00:00.000000000
seek completed. New start TS 0:00:00.233566666 pos 0:00:00.000000000
Pushing stream event
Pushing clut event
Pushing spu_select event
Pushing audio_select event
Discont packet
Pushing highlight event with TS 99:99:99.999999999
demux: got segment update 0 start 233566666 stop -1 time 0
sending new segment: update 0 rate 1 format 3, start: 10000000000, stop: -1, time: 0 scr_adjust: 878979(0:00:09.766433333)
** Message: Error: Could not read from resource.
resindvdsrc.c(827): rsn_dvdsrc_step (): /GstPlayBin:play/RsnDvdBin:source/resinDvdSrc:dvdsrc:
Failed to read next DVD block. Error: Error reading from DVD.

totem: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

```

Totem crashed and I had to "Force Quit" to close the window.

With VLC, I get this: 
```
[00000409] dvdread demux error: read failed for -1/4 blocks at 0x01

```

Nothing seems to work and the DVD isn't of a movie that just came out -- also, the DVD is the same region as my DVD drive (region 1) so that isn't the problem. The movie is "Léolo" from 1992 (which really isn't new at all). Does anyone have any suggestions? Just let me know if you need any more information and I'd be happy to oblige. 

Thanks for any help you can provide ahead of time.

~Oleander

---

### Post by mc4man on 2009-04-07
Is the disk in good shape?, there's no reason it shouldn't play.
Couple of examples (I'm using hardy but the player versions, libraries are similar to Intrepid

> doug@doug-desktop:~/vlc9.9/vlc-0.9.9a$ ./vlc
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--prefix=/usr' '--disable-zvbi' '--enable-flac' '--enable-libass' '--enable-faad' '--disable-kate' '--enable-twolame' '--enable-caca' '--enable-theora' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--with-x264-tree=/usr/include' '--disable-fluidsynth'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: LEOLO
libdvdnav: DVD Serial Number: 431DAA7A___MVB__
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/doug/.dvdnav/LEOLO.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000133
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000198
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000354
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002d5164
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002d519d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002e0f7c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002e0fb5
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[00000677] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: LEOLO
libdvdnav: DVD Serial Number: 431DAA7A___MVB__
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/doug/.dvdnav/LEOLO.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000133
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000198
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000354
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002d5164
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002d519d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002e0f7c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002e0fb5
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[00000711] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
QPainter::begin: Paint device returned engine == 0, type: 1
[00000718] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:224000
[00000722] dts decoder: DTS channels:6 samplerate:48000 bitrate:768000
Stream with high frequencies VQ coding



> doug@doug-desktop:~$ mplayer dvd://1 -channels 6 -aid 138 -sid 0 -really-quiet -fs
MPlayer SVN-r29150-4.2.4 (C) 2000-2009 MPlayer Team
129 audio & 258 video codecs
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
There are 3 titles on this DVD.
There are 1 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000133
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000198
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000354
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002d5164
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002d519d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002e0f7c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002e0fb5
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
audio stream: 0 format: ac3 (5.1) language: fr aid: 128.
audio stream: 1 format: ac3 (stereo) language: fr aid: 129.
audio stream: 2 format: dts (5.1/6.1) language: fr aid: 138.
number of audio channels on disk: 3.
subtitle ( sid ): 0 language: en
number of subtitles on disk: 1
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  7800.0 kbps (975.0 kbyte/s)


it may default to the dts track, maybe you have a problem there?

You could try mplayer specifying either the ac3 5.1 or 2.1 stream
mplayer dvd://1 -aid 128 or mplayer dvd://1 -aid 129 to check on that

to ck. libdvdcss2 open vlc this way, try to play and ck. in home folder for vlc_output file

```
export DVDCSS_VERBOSE=2 && vlc > vlc_output 2>&1
```

(really cool movie, too bad the director is gone

---

### Post by mb_webguy on 2009-04-07
You said you have libdvdread and libdvdnav, but didn't say anything about libdvdcss2, which you'll need to read copy-protected DVDs.

You can get it from the [Medibuntu repository]("https://help.ubuntu.com/community/Medibuntu").

---

### Post by oleander on 2009-04-07
I checked the quality of the DVD and it was fine so I checked out the medibuntu libdvdcss2 library as mb_webguy suggested. It worked, so thank you. :)

It's funny that I played tons of DVDs without libdvdcss2 and they worked but after one of the updates, it just stopped -- I couldn't even play many .flv files anymore (strange).

Anyway, this is solved, so thanks. :D

---

