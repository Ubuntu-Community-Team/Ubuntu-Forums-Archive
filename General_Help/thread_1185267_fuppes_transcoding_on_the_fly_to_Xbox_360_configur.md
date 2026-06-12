---
title: "fuppes transcoding on the fly to Xbox 360 configuration"
date: 2009-06-12
forum: General Help
---

### Post by Nixie Pixel on 2009-06-12
Hello, I recently gave up trying to get Twonky working and have moved on to fuppes - only the guide posted in the Ubuntu forums has a broken link to the configuration files.

Does anyone here have fuppes and transcoding working, and willing to share your configuration files?

Thanks!

---

### Post by arc2v on 2009-06-18
What kind of transcoding are you trying to do?

I tested it on a wireless laptop while waiting for my server parts to arrive.

I got straight streaming video working, straight jpeg picture library working, and transcoding flac to mp3 working.

Resizing JPG I could not get working.
I have not tried to transcode video.

I plan on migrating my settings over to the server this weekend.  If it all works, I'll drop my config files here after that.

---

### Post by Nixie Pixel on 2009-06-25
Basically I need to convert a bunch of .mkv files to a format that the Xbox 360 can understand.

I would love to see the files, if you have them - I am having major problems with Twonky and would love to get Fuppes working.

Thanks!

---

### Post by arc2v on 2009-06-25
I'll upload my two config files tonight.  Right now I have FLAC transcoding working with a rudimentary directory structure for audio, and all my pictures in one large container (but resize transcoding not working).

I can play straight video, but have not tried the transcoding.  So not a perfect installation yet, but it might be enough to get you started.

---

### Post by Nixie Pixel on 2009-08-03
Did you ever have a chance to upload your config files?

Thanks!

---

### Post by arc2v on 2009-08-03
Sorry.  He posted a new build and I have been playing with that.  Doesn't seem to fix the ImageMagick problems, but it appears more stable.

I've also been messing with the virtual folders, having 5k pictures in one folder or all my songs/artists in one huge list is not convenient :)

I e-mailed myself a reminder from work.  I will post this as a code snippet here when I get home.  Not complete, but it works for now.

---

### Post by arc2v on 2009-08-03
okay, first attempt at posting a file, so here goes.

He just posted svn 640, which supposedly fixes the exiv2 and ImageMagick issues, but I haven't tested that yet.  These files work with 636 and 638.

Good luck.

---

### Post by jond578 on 2009-08-15
I'm trying to enable transcoding of mkv, as well.  I wrote this config and am at least getting further thru xbox 'play'

    <file ext="mkv">
      <type>VIDEO_ITEM</type>
      <mime_type>video/x-msvideo</mime_type>
      <transcode enabled="true">
        <transcoder>ffmpeg</transcoder>
        <ext>wmv</ext>
        <mime_type>video/x-ms-wmv</mime_type>
        <video_codec>wmv2</video_codec>
        <video_bitrate>1800000</video_bitrate>
        <audio_codec>wmav1</audio_codec>
      </transcode>
    </file>

However, I get this error on fuppes console:

    Stream #0.0(eng): Video: h264, yuv420p, 1280x720, PAR 1:1 DAR 16:9, 24 tbr, 1k tbn, 47.95 tbc
    Stream #0.1(eng): Audio: ac3, 48000 Hz, 5.1, s16
Output #0, asf, to '/tmp/fuppes/0.wmv':
    Stream #0.0: Video: wmv2, yuv420p, 1280x720, q=2-31, 1800 kb/s, 90k tbn, 24 tbc
    Stream #0.1: Audio: wmav1, 48000 Hz, 5.1, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

The audio params are bad ... maybe the 5.1???  I'll keep trying ...

---

### Post by beterhans on 2009-08-24
HI I'm struggle with the same thing.
I have mkv and avi files in my PC.

with some condition 360 won't play whose video files.

1. Audio coded in PCM/Wav format (This means there is no way to stream lossless audio into 360.)
2. Video/Audio in MKV encapsulation.

and looks like that fuppes can't transcode mkv correctly into avi or wmv :(

I tried to transcode a 360 playable AVI(XVID+AC3) into WMV and works ok. but when i try to apply the same config on mkv. it failed. but even the transcode is OK, it's still far from perfect

MKV have multi-Audio track and subtitle tracks.   fuppes don't know which track is your need, and my loss subtitles. :(

for now I've abandon the 360 and turned to HTPC.:lolflag:

---

### Post by neill64 on 2010-02-23
did you get your transcoding working, i am having a similar problem. i have a stack of .mpg files that i want to play to my xbox but cant seem to get them working

---

### Post by endlessracingz on 2010-03-01
Ubuntu 9.1 & fuppes 0.7.2.3

I am also having issues with video transcoding. Hopefully someone can help. My transcoding is going to a PS3, regardless configuring the fuppes.cfg file is the same or very similar.

From the [fuppes wiki]("http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Sony_Playstation_3#Video") they have an example under the device listing for PS3 and mkv files

```

     <file ext="mkv">
        <type>VIDEO_ITEM</type>
        <mime_type>video/x-matroska</mime_type>
        <transcode enabled="true">
          <transcoder>ffmpeg</transcoder>
          <ext>mpg</ext>
          <mime_type>video/mpeg</mime_type>
          <video_codec>mpeg2video</video_codec>
          <video_bitrate>1800000</video_bitrate>
          <audio_codec>mp2</audio_codec>
          <audio_samplerate>44100</audio_samplerate>
          <audio_bitrate>192000</audio_bitrate>
        </transcode>
      </file>

```I have this exact same code placed in fuppes.cfg however when attempting to play the file I receive
```

[matroska @ 0x91819a0]max_analyze_duration reached
[matroska @ 0x91819a0]Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (5994/125) -> 23.98 (24000/1001)
Must supply at least one input file
[NULL @ 0x941d370]Format detected only with low score of 24, misdetection possible!
[mp3 @ 0x940f540]Header missing
[mp3 @ 0x941d370]Could not find codec parameters (Audio: mp3, 0 channels, s16)
[mp3 @ 0x941d370]Estimating duration from bitrate, this may be inaccurate
/home/administrator/movies/.AppleDouble/[HorribleSubs]_Kateikyoushi_Hitman_Reborn_-_172_[480p].mkv: could not find codec parameters
Must supply at least one input file
```from what i can understand there is an issue with the transcoder frame rate. Also I do now know what this "low score" means.  Missing header and lack of codec for mp3...

---

