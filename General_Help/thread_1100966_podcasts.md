---
title: "podcasts"
date: 2009-03-19
forum: General Help
---

### Post by shahin on 2009-03-19
Greetings-
   I am trying to listen to podcasts at :   [http://assets.radiojavan.com/images/rj3/download_podcast_button.png?1237488791](http://assets.radiojavan.com/images/rj3/download_podcast_button.png?1237488791) .  I prefer to use VLC .  But it does not work.  What am I doing wrong please?  Can someone else test to see if they can hear it?

---

### Post by andrew.46 on 2009-03-19
Hi,

You have inadvertently given the link only to the download button itself :-). Can you find the link to the stream and I would be happy to test it on my own setup.

Andrew

---

### Post by shahin on 2009-03-19
Hi Andrew,
   Thanks for helping me out.  Here is the link for podcasts:
[http://www.radiojavan.com/onradio/podcasts](http://www.radiojavan.com/onradio/podcasts)
Regards-
Sean

---

### Post by andrew.46 on 2009-03-19
Hi Sean,

> **shahin said:**
> Hi Andrew,
   Thanks for helping me out.  Here is the link for podcasts:
[http://www.radiojavan.com/onradio/podcasts](http://www.radiojavan.com/onradio/podcasts)
Regards-
Sean

I navigated through to the 'Download Podcast' button and could play it with the latest MPlayer:

```

andrew@skamandros~$ [COLOR="Red"]**mplayer http://www.radiojavan.com/onradio/podcasts/get/Norooz1388Mix-DJTaba.mp3**[/COLOR]
MPlayer SVN-r28987-4.2.4 (C) 2000-2009 MPlayer Team

Playing http://www.radiojavan.com/onradio/podcasts/get/Norooz1388Mix-DJTaba.mp3.
Resolving www.radiojavan.com for AF_INET6...
Couldn't resolve name for AF_INET6: www.radiojavan.com
Resolving www.radiojavan.com for AF_INET...
Connecting to server www.radiojavan.com[209.9.238.116]: 80...
Cache size set to 320 KBytes
Cache fill: 17.50% (57344 bytes)   
Audio only file format detected.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  35.2 (35.2) of 3465.0 (57:45.0)  0.5% 46% 

```

and also with the latest vlc, I have attached a screenshot of this in progress. Seems to be an mp3 stream, is your software able to play mp3s?

All the best,

Andrew

---

### Post by shahin on 2009-03-19
Thanks.  It worked with mplayer.

---

