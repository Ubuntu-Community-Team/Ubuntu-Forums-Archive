---
title: "Video on Sansa Fuze"
date: 2009-06-13
forum: General Help
---

### Post by hyperdude111 on 2009-06-13
I recently bought a sansa fuze impressed with the advertised Linux support. I successfully added music through usb and moved onto video. The fuze requires a video convert but the official program is only available in windows. 

Does anyone know of a way to add video to a fuze on linux?

---

### Post by hyperdude111 on 2009-06-13
bump

---

### Post by TeoBigusGeekus on 2009-06-13
Could you be a bit more specific about the video format fuze supports?

---

### Post by Gryphen on 2009-06-25
> **TeoBigusGeekus said:**
> Could you be a bit more specific about the video format fuze supports?
Here: [http://www.anythingbutipod.com/forum/showthread.php?t=27460](http://www.anythingbutipod.com/forum/showthread.php?t=27460)

---

### Post by Gryphen on 2009-06-25
I've seen a youtube video of a sansa fuze with rockbox.
Would that solve the problem?

---

### Post by hyperdude111 on 2009-06-26
> **Gryphen said:**
> I've seen a youtube video of a sansa fuze with rockbox.
Would that solve the problem?

Well I have rockbox on mine and it didn't fix it but........I recently put my fuze through the wash while it was in my pocket so i cant see what works anymore.

---

### Post by Gryphen on 2009-08-06
Doesn't any one know to make it work?

---

### Post by Garrovick on 2009-08-06
> **Gryphen said:**
> Doesn't any one know to make it work?

Fuze and Linux "compatibility" means music, never video.  There isn't a Linux compatible converter.  No Drag-n-Drop...

But I suppose some where out there there are several paragraphs of script to put into terminal to get one video at a time loaded.

MP3 players and Linux is like Flash and Linux. Weak and almost useless.

---

### Post by Chronon on 2009-08-06
> MP3 players and Linux is like Flash and Linux. Weak and almost useless.


I wouldn't go that far.  My Rockboxed players just behave as UMS devices.  Rockbox also just plays MPEG-1 or MPEG-2 videos.  You can use WinFF, Mencoder or similar to convert to the proper format, dimensions, etc.

@Gryphen
The Sansa Fuze isn't officially supported by Rockbox yet, but you can find a test build on the Rockbox forums: 
[http://forums.rockbox.org/index.php?topic=22137.0](http://forums.rockbox.org/index.php?topic=22137.0)

If you decide to try that out please provide feedback to the developers.

---

### Post by Gryphen on 2009-08-06
> **Chronon said:**
> I wouldn't go that far.  My Rockboxed players just behave as UMS devices.  Rockbox also just plays MPEG-1 or MPEG-2 videos.  You can use WinFF, Mencoder or similar to convert to the proper format, dimensions, etc.

@Gryphen
The Sansa Fuze isn't officially supported by Rockbox yet, but you can find a test build on the Rockbox forums: 
[http://forums.rockbox.org/index.php?topic=22137.0](http://forums.rockbox.org/index.php?topic=22137.0)

If you decide to try that out please provide feedback to the developers.

I've been wanting to try Rockbox but I have a V2. By the way is Rockbox Linux?

---

### Post by Gryphen on 2009-09-05
Is it possible to install the proper codec on vlc.

---

### Post by OLFP on 2009-09-23
I came across the info below. Maybe a multimedia guy can tell us how to set-up our videos to match this.

> 
This was taken from the video that came with the Fuze from MediaInfo.

Quote:
General #0
Complete name : C:\Users\EnzoTen\Desktop\WAZ.MineToRemember.SansaP layer.avi
Format : AVI
Format/Info : Audio Video Interleave
Format/Family : RIFF
File size : 20.0 MiB
PlayTime : 3mn 26s
Bit rate : 812 Kbps
Writing application : InterVideo

Video #0
Codec : DivX 5
Codec/Family : MPEG-4
Codec profile : Unknown
Codec settings/Packe : No
Codec settings/BVOP : Yes
Codec settings/QPel : No
Codec settings/GMC : 0
Codec settings/Matri : Default
PlayTime : 3mn 26s
Bit rate : 667 Kbps
Width : 224 pixels
Height : 176 pixels
Display Aspect ratio : 1.273
Frame rate : 20.000 fps
Resolution : 8 bits
Interlacement : Progressive

Audio #0
Codec : MPEG-1 Audio layer 3
PlayTime : 3mn 26s
Bit rate : 128 Kbps
Bit rate mode : CBR
Channel(s) : 2 channels
Sampling rate : 44.1 KHz
Resolution : 16 bits
Writing library : Xing (new)

Update: I used avidemux to convert match a video's framerate and picture size. Still nothing.

---

### Post by Gryphen on 2009-09-29
video4fuze works [http://forums.sandisk.com/sansa/board/message?board.id=sansafuse&thread.id=31437](http://forums.sandisk.com/sansa/board/message?board.id=sansafuse&thread.id=31437)

---

### Post by OLFP on 2009-10-01
Great! Thank you.

I haven't had much luck with Wine, but I'll give it a shot.

---

### Post by Gryphen on 2009-11-05
> **OLFP said:**
> Great! Thank you.

I haven't had much luck with Wine, but I'll give it a shot.

Video4fuze is available in a .deb package.

---

### Post by OLFP on 2009-11-07
It didn't work for me. It converted the video, but my fuze still said it was an unsupported media type. I'm going to look into rockbox.

---

### Post by Gryphen on 2009-11-09
> **OLFP said:**
> It didn't work for me. It converted the video, but my fuze still said it was an unsupported media type. I'm going to look into rockbox.
That's weird it works fine for me. Are you using 9.10 because I haven't try'd it on karmic but it worked just fine on jaunty.

---

### Post by soap1 on 2011-08-04
The sansa fuze is sort of strange with video, you need to put the video in a very specific format.  I use video4fuze.  It is a free program that converts video into a format that is recognised by the fuze.

This is the website.
[http://code.google.com/p/video4fuze/](http://code.google.com/p/video4fuze/)
 
This is the download page thing
[http://code.google.com/p/video4fuze/downloads/list](http://code.google.com/p/video4fuze/downloads/list)

Here is a video showing how to install it
[http://www.youtube.com/watch?v=m4-jt3B3Bag](http://www.youtube.com/watch?v=m4-jt3B3Bag)

also, you need to have PyQt4, mencoder, and FFMPEG (when you download the video4fuze everything you need to know will be in the README.txt file thing located at video4fuze --> usr --> share --> video4fuze

---

