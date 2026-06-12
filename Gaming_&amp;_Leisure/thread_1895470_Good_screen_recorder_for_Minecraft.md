---
title: "Good screen recorder for Minecraft?"
date: 2011-12-14
forum: Gaming &amp; Leisure
---

### Post by jtl999 on 2011-12-14
I need a good Screen Recorder for Minecraft.

Please don't say GtkRecordMyDesktop or xvidcap because it works horribly.
my video card is a 6770 with 1GB of VRam.

Thanks.

---

### Post by frostwork on 2011-12-15
I'm one of the few people still without minecraft, but as it is using opengl you should try apitrace 
[https://github.com/apitrace/apitrace](https://github.com/apitrace/apitrace)
or glc
[https://github.com/nullkey/glc/wiki](https://github.com/nullkey/glc/wiki)

---

### Post by Jay Car on 2011-12-15
I haven't used this service (and I don't do Minecraft), so this may not be an answer for you.  But I read about this service a few days ago and bookmarked it. Even if it isn't exactly what you are asking for, it might be useful for other things. 

It's called [Screencast-O-Matic]("http://www.screencast-o-matic.com/"). 

:)

---

### Post by jtl999 on 2011-12-15
I will test glc later

---

### Post by HolgerB on 2011-12-15
> **jtl999 said:**
> I need a good Screen Recorder for Minecraft.

Please don't say GtkRecordMyDesktop or xvidcap because it works horribly.
my video card is a 6770 with 1GB of VRam.

Thanks.
I have never played Minecraft but for me ffmpeg always worked good for capturing games.

---

### Post by jtl999 on 2011-12-15
With Glc how do I encode?

Also I have a black line on top of video

---

### Post by R3cKL3SS_aM on 2011-12-16
I use recordMyDesktop to record Minecraft gameplay. The only down side is the video file comes out as an .ogv and you can't upload .ogv files to Youtube.

[Sample Video: Click Here!]("http://www.youtube.com/watch?v=SPs3m5uJfcc")

However, you can convert the .ogv file to an .avi so you are able to upload it, if that's you intent.

```
sudo apt-get install mencoder
```This will install the converting software.

```
mencoder -idx "TEXT HERE".ogv -ovc lavc -oac mp3lame -o "TEXT HERE".avi
```Type this command line into terminal (Replace "TEXT HERE" with the file name) and it will convert the .ogv to a .avi

---

### Post by jtl999 on 2011-12-16
Bleh 

I dont like that software

---

### Post by jtl999 on 2011-12-19
I tired WebCamStudio but the its all grainy :(.

---

### Post by doorknob60 on 2011-12-21
Honestly, the only way you will get good quality and good framerate videos is GLC, from my experiences. Here is a Wiki page I wrote about GLC, including some scripts on how to encode the glc videos and stuff. Hope it helps :) [https://wiki.archlinux.org/index.php/GLC](https://wiki.archlinux.org/index.php/GLC)

---

### Post by HolgerB on 2011-12-23
> **doorknob60 said:**
> Honestly, the only way you will get good quality and good framerate videos is GLC, from my experiences. Here is a Wiki page I wrote about GLC, including some scripts on how to encode the glc videos and stuff. Hope it helps :) [https://wiki.archlinux.org/index.php/GLC](https://wiki.archlinux.org/index.php/GLC)
well, honestly I always had issues getting glc to work on my systems !

ffmpeg is often a perfect tool to capture even accelerated games. Higher resolutions might require a more beefy PC (modern quad-core with sufficiently fast HDDs) but in the end you can get good quality. Check out yourself !

[http://www.youtube.com/watch?v=M55sRS-XBm8](http://www.youtube.com/watch?v=M55sRS-XBm8)

This video was captured with ffmpeg.

@R3cKL3SS_aM: your mencoder commandline looks incomplete to me. Usually beside specifying libav as any sort of codec you usually have to set other parameters (such as codec to be used, bitrate and so on). It is better to check out the various examples in the www and do some experiments in order to find out which works best for you.

---

