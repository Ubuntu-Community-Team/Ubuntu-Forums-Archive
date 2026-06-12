---
title: "in a nutshell, what's the diff between xine and gstreamer"
date: 2005-05-25
forum: Desktop Environments
---

### Post by epb613 on 2005-05-25
1. What's the difference between them and
2. Which one is better (ie: which one should I use)?

Thanks in advance!

---

### Post by jcooper on 2005-05-26
Xine is an older infrastructure, dating back to the early linux media days. GStreamer is new technology, based on a very clever plugin architecture. It basically means gstreamer is a lot more flexible than xine. 

Use whichever works best for you, or both depending on what you need to achieve. In this case, there is no right or wrong way, though with Nokia now actively coding for GStreamer, it will be the main product in the future.

---

### Post by Alexander Kirillov on 2005-05-26
[QUOTE=epb613]1. What's the difference between them and
2. Which one is better (ie: which one should I use)?

Thanks in advance![/QUOTE]
 For watching videos, xine works much better for me, so I use totme-xine. For audio, definitely use gstreamer.

---

### Post by photismos on 2008-02-03
MUCH thanks for posing the question "Which one should I use, Xine or GStreamer?"  

i appreciated the background context; and I REALLY appreciated the definitive constructive advice to go for Xine....here's why.  

although I noticed almost immediately improved responsiveness just switching from GStreamer to Xine for DVD playback (I too noted that Synaptic Package Manager in Gutsy only let's you have one or the other) it still wasn't perfect (only one of my DVDs played without incident, and I tried a few; all the others couldn't even get to a menu).  That is, until a dialog box from a different program I was attempting to use (dvd::rip) asked me if I'd installed libdvdcss by chance...  

the hunt was on...for a possible solution.  I googled and got it from the videoLAN repositories here:

[http://downloads.videolan.org/pub/](http://downloads.videolan.org/pub/)

(Actually, I followed it all the way to the debian package which was the easiest install for a dummy like me: [http://downloads.videolan.org/pub/libdvdcss/1.2.9/deb/](http://downloads.videolan.org/pub/libdvdcss/1.2.9/deb/))

...and voila! *ALL* my DVD's started playing! =D  I was VERY VERY happy...been looking to ditch Windoze for some time and this is one of the "bigger" hurdles for me, as I look "to make my stand" with ubuntu.  

SO...in shorter summary: I entirely concur as of this date, to get satisfactory DVD playback, Xine but also  this ALL-Important (little-known?) piece of software called "libdvdcss"  seems to have been done the trick completely.   

now I'm wondering if libdvdcss would have worked the same wonders for GStreamer to grant me satisfactory DVD playback so that I wouldn't have to make the audio compromise that we're told here Xine is...  *shrug*  Any thoughts to share addressing that question? 

I guess that info could be in another thread somewhere, but I'm gonna watch a DVD now instead to celebrate a small but significant battle won today in the war I have to fight to free myself from Windows!  :D  thanks to you all!!!!  *REALLY* appreciate it...

---

### Post by Mochabuntu on 2008-02-04
i wouldn't say Xine has any major audio downfall either...pretty sure Amarok is a damn fine example of xine as an audio backend.

I wouldn't mind if the developers of Exaile (a project designed to bring a kind of GNOME native Amarok) enabled the choice between the use of the gstreamer or use of the xine backends (just like Amarok does) My experience with gstreamer is very shaky and most of the audio produced with gstreamer has been quite awful compared to xine. Just my opinion though.

---

### Post by Alexander Kirillov on 2008-02-04
libdvdcss would enable dvd play using totem-gstreamer as well. Last time I chcked, totem-gstreamer couldn't properly deal with menus  - it may have changed. 

Anyway, my solution is using totem-xine for video and rhythmbox (which always uses gstreamer playback) for audio. You can try other combnations. 

BTW, I'd advise you to use medibuntu repository for packages such as libdvdcss, rather tehn downloading directly form videolan - this way, you would be informed of updates. See here 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
and 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

> **photismos said:**
> MUCH thanks for posing the question "Which one should I use, Xine or GStreamer?"  

i appreciated the background context; and I REALLY appreciated the definitive constructive advice to go for Xine....here's why.  

although I noticed almost immediately improved responsiveness just switching from GStreamer to Xine for DVD playback (I too noted that Synaptic Package Manager in Gutsy only let's you have one or the other) it still wasn't perfect (only one of my DVDs played without incident, and I tried a few; all the others couldn't even get to a menu).  That is, until a dialog box from a different program I was attempting to use (dvd::rip) asked me if I'd installed libdvdcss by chance...  

the hunt was on...for a possible solution.  I googled and got it from the videoLAN repositories here:

[http://downloads.videolan.org/pub/](http://downloads.videolan.org/pub/)

(Actually, I followed it all the way to the debian package which was the easiest install for a dummy like me: [http://downloads.videolan.org/pub/libdvdcss/1.2.9/deb/](http://downloads.videolan.org/pub/libdvdcss/1.2.9/deb/))

...and voila! *ALL* my DVD's started playing! =D  I was VERY VERY happy...been looking to ditch Windoze for some time and this is one of the "bigger" hurdles for me, as I look "to make my stand" with ubuntu.  

SO...in shorter summary: I entirely concur as of this date, to get satisfactory DVD playback, Xine but also  this ALL-Important (little-known?) piece of software called "libdvdcss"  seems to have been done the trick completely.   

now I'm wondering if libdvdcss would have worked the same wonders for GStreamer to grant me satisfactory DVD playback so that I wouldn't have to make the audio compromise that we're told here Xine is...  *shrug*  Any thoughts to share addressing that question? 

I guess that info could be in another thread somewhere, but I'm gonna watch a DVD now instead to celebrate a small but significant battle won today in the war I have to fight to free myself from Windows!  :D  thanks to you all!!!!  *REALLY* appreciate it...

---

### Post by manimal347 on 2008-02-04
Gstreamer is only really a staple on Gnome desktops. Lots of great programs like Mplayer and Audacious don't use either backend. I know for sure that my Ubuntu system (server install) has no Gstreamer plugins, and I'm pretty sure it has few or no Xine plugins.

See, older players usually provided their own codec framework, used standard things like libmad and ffmpeg, or borrowed that of another application such as Mplayer. Gnome's a very popular DE, though, so Gstreamer does have a fair bit of support.

---

### Post by Amaroq on 2008-02-05
Mplayer doesn't use either? So that's why it can't do something so simple as to play my videos with the video and audio in sync. Audio is always faster than the video for me when I use mplayer.

Then I accidentally opened one of my videos in totem, and everything was perfect, if a little quieter than mplayer's audio.

My totem is using the gstreamer backend. Haven't tried xine.

---

