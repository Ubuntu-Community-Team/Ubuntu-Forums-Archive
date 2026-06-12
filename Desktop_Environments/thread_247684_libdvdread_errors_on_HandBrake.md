---
title: "libdvdread errors on HandBrake"
date: 2006-08-31
forum: Desktop Environments
---

### Post by Onos on 2006-08-31
Greetings all...

After much googling and searching and pulling out of hair... I *think* I have HB up and running... that is, typing "handbrake" in the terminal will actually give a response.

My dilemma now turns to the actual reading/ripping of the DVDs I have which I want to port to a smaller file format.

I entered in this command:

```
handbrake -s 1 -c 1 -w 320 -b 192 -r 25 -B 128 -R 44100 -i /media/cdrom-1/VIDEO_TS/ -o ~/encoded_movies/BSG2-5.avi
```

and a flurry of ***several hundred*** iterations of this error message flew through my terminal:

```
*** libdvdread: CHECK_VALUE failed in nav_read.c:207 ***
*** for dsi->dsi_gi.zero1 == 0 ***
```

and was followed by this before finally failing out:

```
+ title 1:
  + vts 1, ttn 1, cells 0->4 (831597 blocks)
  + duration: 00:43:59
  + size: 720x480, aspect: 1.78, 23.976 fps
  + autocrop: 0/2/0/0
  + chapters:
    + 1: cells 0->0, 136443 blocks, duration 00:07:04
    + 2: cells 1->1, 322238 blocks, duration 00:17:21
    + 3: cells 2->2, 110925 blocks, duration 00:05:51
    + 4: cells 3->4, 261991 blocks, duration 00:13:44
  + audio tracks:
    + 80bd, English (AC3) (5 ch), 48000Hz, 448000bps
    + 81bd, English (AC3) (2 ch), 48000Hz, 192000bps
  + subtitle tracks:
    + 20bd, English
    + 21bd, Espanol
[mpeg4 @ 0x8444a88]removing common factors from framerate
No accelerated IMDCT transform found
Encoding: task 1 of 1, 0.15 %Segmentation fault
```

I imagine that ther is something that is probably easily fixed and is practically under my nose... but so far my research on this error messag turns up only result connected to other projects like mencoder.

Any advice would be dearly apprciated...

Thanks!

---

### Post by &lt;&lt;joe&gt;&gt; on 2006-11-23
hi i have done the same as you, and have gotten the same erros 
i was trying to see if i could ripp a dvd humm dont know what i did rong ether but here is the output

*** libdvdread: CHECK_VALUE failed in nav_read.c:207 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:207 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:207 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:207 ***
*** for dsi->dsi_gi.zero1 == 0 ***

+ title 1:
  + vts 10, ttn 1, cells 0->114 (3451897 blocks)
  + duration: 01:59:51
  + size: 720x480, aspect: 1.78, 23.976 fps
  + autocrop: 40/46/0/0
  + chapters:
    + 1: cells 0->0, 94390 blocks, duration 00:03:18
    + 2: cells 1->5, 117078 blocks, duration 00:02:47
    + 3: cells 6->7, 104680 blocks, duration 00:04:17
    + 4: cells 8->9, 67405 blocks, duration 00:02:38
    + 5: cells 10->13, 63149 blocks, duration 00:01:59
    + 6: cells 14->26, 82644 blocks, duration 00:02:39
    + 7: cells 27->36, 112182 blocks, duration 00:03:27
    + 8: cells 37->40, 122864 blocks, duration 00:04:20
    + 9: cells 41->41, 58891 blocks, duration 00:02:30
    + 10: cells 42->51, 288222 blocks, duration 00:06:23
    + 11: cells 52->54, 77500 blocks, duration 00:02:18
    + 12: cells 55->57, 42731 blocks, duration 00:01:35
    + 13: cells 58->61, 101600 blocks, duration 00:03:19
    + 14: cells 62->63, 89014 blocks, duration 00:03:47
    + 15: cells 64->65, 21664 blocks, duration 00:00:54
    + 16: cells 66->66, 84346 blocks, duration 00:03:28
    + 17: cells 67->67, 69076 blocks, duration 00:02:49
    + 18: cells 68->70, 98439 blocks, duration 00:03:05
    + 19: cells 71->75, 117324 blocks, duration 00:03:55
    + 20: cells 76->78, 105997 blocks, duration 00:02:53
    + 21: cells 79->82, 183293 blocks, duration 00:05:04
    + 22: cells 83->86, 124479 blocks, duration 00:03:50
    + 23: cells 87->87, 122117 blocks, duration 00:05:10
    + 24: cells 88->89, 83025 blocks, duration 00:03:21
    + 25: cells 90->91, 78206 blocks, duration 00:03:06
    + 26: cells 92->92, 59796 blocks, duration 00:02:36
    + 27: cells 93->93, 52111 blocks, duration 00:02:11
    + 28: cells 94->99, 169957 blocks, duration 00:05:09
    + 29: cells 100->100, 51634 blocks, duration 00:01:54
    + 30: cells 101->103, 29471 blocks, duration 00:01:07
    + 31: cells 104->104, 99298 blocks, duration 00:03:30
    + 32: cells 105->107, 71508 blocks, duration 00:02:44
    + 33: cells 108->108, 88496 blocks, duration 00:03:24
    + 34: cells 109->109, 128528 blocks, duration 00:04:42
    + 35: cells 110->112, 69753 blocks, duration 00:02:39
    + 36: cells 113->114, 121029 blocks, duration 00:07:03
  + audio tracks:
    + 80bd, English (AC3) (5 ch), 48000Hz, 384000bps
    + 82bd, Espanol (AC3) (2 ch), 48000Hz, 192000bps
    + 83bd, English (AC3) (2 ch), 48000Hz, 192000bps
    + 84bd, English (AC3) (2 ch), 48000Hz, 96000bps
  + subtitle tracks:
    + 21bd, English
    + 23bd, Espanol
    + 25bd, Unknown
    + 27bd, Unknown
[mpeg4 @ 0x8444a88]removing common factors from framerate
No accelerated IMDCT transform found
Encoding: task 1 of 1, 0.01 %Segmentation fault

wish i new

---

### Post by BatteryKing on 2007-08-02
I am seeing the exact same libdvdread error message while ripping under mencoder under Ubuntu 7.04 (both 64-bit and 32-bit).  Under 64-bit Ubuntu I end up with a VOB file that plays for 8.1 seconds and then kicks out with an audio stream checksum error.  Under 32-bit Ubuntu I end up with a VOB file that under mplayer plays all the way through, but with the time index counter recycling every 15 seconds or so throughout the entire hour long video.  When importing into Final Cut Pro on a Mac we are only able to see the first 15 seconds of video out of the entire hour long video.  (The only way we have been able to get the full hour into Final Cut Pro so far is to make a really cheesy looking, off-color video because with every codec tried either Final Cut Pro won't recognize it [most recent codecs] or mencoder either breaks entirely [like trying to do .mov files through win32 codec add-ons] or breaks when we try to do a useful bit rate [like with mpeg2] or burns way too much disk space to complete the job.)

This error so far only occurs with the first business partner we have had to ask for a DVD based video to be included in a joint online business project.  We tried multiple other DVDs laying around irrelevant to business interests and they all worked flawlessly.  According to our business partner this video was first done on VHS and then converted to DVD back in 2000.

---

### Post by spargonaut on 2008-06-09
wierd.

looking at the date of ya'lls posts, it looks as if ya'll were using ver. 0.7

I just recently installed ver 0.9 and i am getting the _exact_ same error.

did anyone find a fix for it?

cheers.
js

---

