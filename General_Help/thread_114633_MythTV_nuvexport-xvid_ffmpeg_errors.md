---
title: "MythTV nuvexport-xvid ffmpeg errors"
date: 2006-01-09
forum: General Help
---

### Post by Chubtoad on 2006-01-09
Been reading these forums for about a year now and they have helped endlessly, as a big fan of the search feature I haven't needed to post yet, however I have come across a problem that I can't seem to tackle.

I've gotten mythtv up and running on Breezy using my WinTV PVR-150, and i absolutley love it, however I'd like to get mythtv to auto-transcode the recordings to xvid, cutting out the commercials. My current problem is that my version of ffmpeg doesn't seem to include xvid support. I'm using the nuvexport-xvid program to try to transcode.  I read [here]("http://mysettopbox.tv/phpBB2/viewtopic.php?t=7017&") that a newer version (compiled with xvid support) is available somehow. I tried CVSing ffmpeg and compiling it with xvid support and came across a whole load of errors. Now as that thread says I could use transcode to convert to xvid, however it doesn't recognize mythtv's commercial flag, and it takes a very long time, more than 8 hours for an hour long recording. 

I'm wondering if there is somwhere (an additional apt source maybe) I can find a package of ffmpeg with xvid support already compiled into it. It also seems that when the nuvexport-xvid script calls the yuvdenoise it doesn't like the "-r" flag and throws an error, however I have been disabling the noise clean-up, in order to get to the ffmpeg encoding part of the script, which then throws the "Unknown codec: xvid" error.

I was wondering if anyone has any experience getting past these problems.

---

### Post by Chubtoad on 2006-01-25
Does anyone have experience in compiling ffmpeg from CVS that they could pass along?

---

### Post by SteveGodfrey on 2006-02-23
go here

[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

then down to this section

8.18.2 Reinstall ffmpeg from my binaries

---

### Post by Chubtoad on 2006-02-24
thank you. Thats the guide i had used to install mythtv on ubuntu, but at the time i totally missed hte ffmpeg binaries/instrucitons from how to compile from apt-get.  I actually found that last week while i was fixing my system from almost completely b0rking it. 

its so great, now i get 20-30fps encoding, vs 4-8 i was getting with transcode!

So anyone knows, i believe hyman's binaries are down, but compiling using apt-get source to get ffmpeg sources is pretty easy, it may take a little trial and error on where to add the extra switches to the config file.

In case any stumbles across this and has another problem i had, nuvexport will only cut out commercials that mythtv has flagged if you first copy the Commercial Flags to the cutlist:
mythcommflag --gencutlist -f FILENAME

there are other ways of choosing files too.

---

### Post by clievers on 2007-07-16
Hi, did anyone solve the problem to this?
This weekend I installed the newest Ubuntu and mythtv on it. When I try to do the nuvexport to either xvid or divx, I just get errors. When I run "nuvexport", I see for xvid: "1. Export to XviD (disabled)".
If I choose it, I get the message:
[INDENT]Your ffmpeg installation doesn't support encoding to xvid.
  (It must be compiled with the --enable-xvid option)
Press ENTER to continue.[/INDENT]
I inserted "confflags += --enable-mp3lame --enable-xvid --enable-faad --enable-faac" as per the "http://hyams.webhop.net/mythtv/myth_ubuntu.html" instructions. So this really has me confused.

If I instead try the divx option, I get the following:
[INDENT]Now encoding:  <SHOWNAME>
Encode started:  Mon Jul 16 09:28:20 2007
Waiting for mythtranscode to set up the fifos.
Waiting for mythtranscode to set up the fifos.
Waiting for mythtranscode to set up the fifos.
Starting ffmpeg.
processed:  0 of -17359 frames at 0 fps (~%, eta: unknown)

ffmpeg had critical errors:

Unsupported codec for output stream #0.1

Cleaning up temp files.
Cleaning up child processes.[/INDENT]

So I had all this working on my last installation, an older mythtv and gentoo distro, just having problems with Ubuntu. If anyone has any additional help, I would really appreciate it. Thanks.
Cory.

---

### Post by clievers on 2007-07-16
<just trying to get my autosubscribe going for this thread>

---

### Post by Krikke_wl on 2007-07-17
I recently got to install Ubuntu Feisty too, for a MythTV box and this is what solved my problem to make ffmpeg use xvid and all of the other codecs:

[http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)

Greetz,
Krikke

---

### Post by clievers on 2007-07-17
Thanks for your reply. Should I uninstall ffmpeg first, before doing those steps? Or will it just update it properly?

---

### Post by Krikke_wl on 2007-07-18
it'll update just fine! (in my case it did)

enjoy your ubuntu!

ps: if you find decent encoding settings you may always pass them to me, 'cause I can't seem to find anything decent, nothing that compares to the result I get with Virtualdub in Winblows...

---

### Post by clievers on 2007-07-20
So I followed this guide I found to install ffmpeg another way, but it doesn't finish. It seemingly finishes the first pass, but then gives an error. The settings I used are what I recall using in my previous mythtv environment.

Where would you like to export the files to? [.]
Enable Myth cutlist? [Yes]
Enable noise reduction (slower, but better results)? [No]
Enable deinterlacing? [Yes]
Crop broadcast overscan border (0-5%) ? [1.5]
Audio bitrate? [128]
Variable bitrate video? [Yes]
Multi-pass (slower, but better quality)? [Yes]
Video bitrate? [768] 1200
Default resolution based on requested dimensions.
Width? [512]
Height? [384]

Now encoding: Roast of William Shatner Uncensored: Untitled
Encode started: Thu Jul 19 21:21:50 2007
First pass…
Waiting for mythtranscode to set up the fifos.
Waiting for mythtranscode to set up the fifos.
Waiting for mythtranscode to set up the fifos.
Starting ffmpeg.
processed: 133593 of 133617 frames at 44.58 fps (99.98%, eta: 0s)
audio dump finished.
processed: 133614 of 133617 frames at 44.58 fps (100.00%, eta: 0s)
ffmpeg finished.
processed: 133616 of 133617 frames at 44.58 fps (100.00%, eta: 0s)
mythtranscode finished.
Final pass…
Waiting for mythtranscode to set up the fifos.
Waiting for mythtranscode to set up the fifos.
Waiting for mythtranscode to set up the fifos.
Starting ffmpeg.
processed: 0 of 133617 frames at 0 fps (~%, eta: unknown)

ffmpeg had critical errors:

Error while opening codec for output stream #0.1 – maybe incorrect parameters such as bit_rate, rate, width or height

Cleaning up temp files.
Cleaning up child processes.

---

### Post by Krikke_wl on 2007-07-23
I think it might have to do with your width/height, because if I recall correct the ffmpeg doesn't use this settings for his first pass and only starts considering them in the second pass, that might explain why your second pass fails...

---

### Post by clievers on 2007-07-23
Do you have a suggestion for width/height values that would work well? Thanks.

---

### Post by Krikke_wl on 2007-07-25
I got something like 470x360 for my 16:9 recordings. If I'm not mistaken I think it's best to use a resolution that ends on 0 (like 470 instead of 465) 

keep me informed plz!

---

### Post by clievers on 2007-07-26
Okay, so the way I finally got the ffmpeg to work a bit ago was to use the Medibuntu repository. I found a reference to it on some site.
[http://medibuntu.sos-sts.com/]("http://medibuntu.sos-sts.com/")

Then I started playing around. On my previous setup (old Gentoo distro, mythtv was like 0.18 or something), the setting that worked for me was nuvexport-xvid and all defaults except for the video bitrate, which I used 1200. For my current setup though, the xvid doesn't seem to work for me as it comes out with lots of frames being quite pixelated and jerky. So, reverting to divx to try that one. 

I tried testing a variety of settings, including having the noise reduction on, trying different video bitrates, and different widths.

I found that by turning "on" the noise reduction, it isn't lying, it is definitely slower. Like nearly 5 hours instead of 47 minutes (same recording and same settings, just with that one setting 'on'). So that's not exceptable to me. Converting to avi uses cpu and for that length of time, the nuvexport would be always running.

Trying to go from a video bitrate of the default 960 up to 1200 or more, really seemed to just affect the file size. I didn't really seem to notice much of a quality difference. So, it's not like I'm broadcasting recordings, just archiving to maybe one day watch them again, I think the following settings are going to work for me.

nuvexport-divx
Enable Myth cutlist? [Yes] 
Enable noise reduction (slower, but better results)? [No] 
Enable deinterlacing? [Yes] 
Crop broadcast overscan border (0-5%) ? [1.5] 
Audio bitrate? [128] 
Variable bitrate video? [No] 
Video bitrate? [960] 
Default resolution based on requested dimensions.
Width? [624] 512
Height? [384] 

Oh, and my settings in mythtv, for recording are:
+---------+--------------------------+-----------+
| profile | name                     | value     |
+---------+--------------------------+-----------+
|       5 | autotranscode            | 0         |
|       5 | width                    | 720       |
|       5 | height                   | 480       |
|       5 | rtjpegquality            | 170       |
|       5 | rtjpeglumafilter         | 0         |
|       5 | rtjpegchromafilter       | 0         |
|       5 | mpeg4bitrate             | 2200      |
|       5 | mpeg4maxquality          | 2         |
|       5 | mpeg4minquality          | 15        |
|       5 | mpeg4qualdiff            | 3         |
|       5 | mpeg4scalebitrate        | 1         |
|       5 | mpeg4optionvhq           | 0         |
|       5 | mpeg4option4mv           | 0         |
|       5 | mpeg4optionidct          | 0         |
|       5 | mpeg4optionime           | 0         |
|       5 | hardwaremjpegquality     | 100       |
|       5 | hardwaremjpeghdecimation | 4         |
|       5 | hardwaremjpegvdecimation | 4         |
|       5 | mpeg2streamtype          | MPEG-2 PS |
|       5 | mpeg2aspectratio         | 4:3       |
|       5 | mpeg2bitrate             | 6400      |
|       5 | mpeg2maxbitrate          | 8000      |
|       5 | samplerate               | 32000     |
|       5 | mp3quality               | 7         |
|       5 | volume                   | 90        |
|       5 | mpeg2audtype             | Layer II  |
|       5 | mpeg2audbitratel1        | 448       |
|       5 | mpeg2audbitratel2        | 384       |
+---------+--------------------------+-----------+

Not sure if this helps anyone. Also, if anyone has better settings, please let us know.
Thanks.

---

### Post by Krikke_wl on 2007-07-30
well indeed, the divx gives much better results than the xvid! thanks for that! Nevertheless it is no as good as when I use avidemux or virtualdub under windows... 
Do you succeed in cropping your black borders from your recording automaticaly?? 

Regards,
Krikke

---

