---
title: "DVD Playback crashes all Media Players"
date: 2007-12-14
forum: Dell  Ubuntu Support
---

### Post by that1guyty on 2007-12-14
Hi, i'm running Gutsy 7.10 on a Dell Latitude D630, and i'm having troubles playing DVDs.  I downloaded all the lib-dvd-css stuff i can find, installed gxine, vlc player, updates for totem and all that.  what happens is this, 

   -whenever i open up a player and load the dvd, it closes the media player.  there's no error message, no beep, it just closes.  Any help would be greatly appreciated.

---

### Post by Stemp on 2007-12-14
Hi,

With Gutsy I have to watch my DVD with vlc.
If you launch vlc in a terminal do you have any error messages ?

---

### Post by that1guyty on 2007-12-15
this is what i get...

VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: CND0NNW1
libdvdnav: DVD Serial Number: 32d62e06
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/that1guyty/.dvdnav/CND0NNW1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000015d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000022d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000048b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0000093a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000009f5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00000bdb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00000c96
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x000017a1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0000185c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0000417e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00004239
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x000045c4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0000467f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x000b6634
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x000b66ef
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x000c882f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x000c88ea
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x000c89d2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x000fc8a2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x0033d50b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x0033d5c6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x00390220
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x003902db
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x003b2253
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x003b230e
libdvdread: Elapsed time 0
libdvdread: Found 12 VTS's
libdvdread: Elapsed time 0
[00000336] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
No accelerated IMDCT transform found
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85

Thanks for the reply!

---

### Post by Stemp on 2007-12-16
> X Error of failed request: BadAlloc (insufficient resources for operation)
Major opcode of failed request: 140 (XVideo)

Hoho.
Ok try to change the Video Output Module in vlc.
Menu Settings, Preferences, Video, Output Module (click on Advanced Option)...
Choose X11

Restart vlc and try again your DVD

---

### Post by that1guyty on 2007-12-18
Stemp, it worked.  thanks for the help, i really appreciated it!

---

### Post by gdoyel on 2007-12-25
Thanks so much!

---

