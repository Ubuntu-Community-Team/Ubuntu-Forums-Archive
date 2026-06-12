---
title: "dvd playback problem"
date: 2006-01-05
forum: Desktop Environments
---

### Post by nandasunu on 2006-01-05
Although I can "play" the dvd, it won't let me click the links inside it that choose the chapters etc.

I have this problem in totem & kaffeine

---

### Post by bulldogzerofive on 2006-01-05
Did you install libdvdnav?

Are you using xine or gstreamer for your engine?

---

### Post by nandasunu on 2006-01-05
I have all of those. I was using xine and I tried with gstreamer and still no luck :(

---

### Post by bulldogzerofive on 2006-01-05
Can you run these from a command line and post the error output?

---

### Post by stratotak on 2006-01-05
just wondering..is it with all dvds or just one dvd that this happens??might sound like a stupid obvious question..lol..but i have had times where Mplayer wouldnt play the dvd..but poped it into Xine and it worked,,have you tried to play it using Mplayer and see if it dose the same??

---

### Post by tms on 2006-01-06
[QUOTE=nandasunu]Although I can "play" the dvd, it won't let me click the links inside it that choose the chapters etc.

I have this problem in totem & kaffeine[/QUOTE]

Greetings,

Try running xine-check from the command line and see what it says. It's helped me out in the past.

Later,
TMS.

---

### Post by nandasunu on 2006-01-06
Thank you for your help.

tms: entering "xine-check" into the cl doesn't seem to do aything, it says it doesn't recognise the command.

stratotak: its with all dvds

> Can you run these from a command line and post the error output?

here you go (from kaffeine):
```
nanda@ubuntu:~$ kaffeine
DVB 0 : No such file or directory
DVB 1 : No such file or directory
DVB 2 : No such file or directory
DVB 3 : No such file or directory
nanda@ubuntu:~$ libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: Using dvdnav version 0.1.9 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: MOTHER_GANGA
libdvdnav: DVD Serial Number: 330A992A
libdvdnav: DVD Title (Alternative): MOTHER_GANGA
libdvdnav: Unable to find map file '/home/nanda/.dvdnav/MOTHER_GANGA.map'
libdvdnav: DVD disk reports itself with Region mask 0x00400000. Regions: 1 2 3 4 5 6 8

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000149
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001b8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000aad7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0018aa3e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0018aa8b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001a87b6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001a8803
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x001c0a54
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001c0aa1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x001d79c4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x001d7a11
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x001e8f91
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x001e8fde
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x001fa1aa
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x001fa1f7
libdvdread: Elapsed time 0
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 0

```

It seems to be working now in totem, although the playback could be a little smoother.. (I have dma on). I would rather use kaffeine as totem seems to be a little unstable on kde.

thanks again for the help.

---

### Post by tms on 2006-01-06
[QUOTE=nandasunu]Thank you for your help.

tms: entering "xine-check" into the cl doesn't seem to do aything, it says it doesn't recognise the command.

[/QUOTE]

Hey,

Sorry, I just naturally assumed you were using Xine to watch your DVDs because I'm using it at the moment. It wont recognise the command if you don't have Xine installed of course.

My bad :D

Later,
TMS

---

