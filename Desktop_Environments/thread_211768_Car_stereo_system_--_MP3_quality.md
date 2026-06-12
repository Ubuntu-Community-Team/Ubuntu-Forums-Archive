---
title: "Car stereo system -- MP3 quality?"
date: 2006-07-08
forum: Desktop Environments
---

### Post by Kensey on 2006-07-08
I just installed a Kenwood KDC-MP5028 in my car yesterday.  So far I'm loving it -- it's capable of playing MP3s (as well as WMA and unprotected AAC).  My laptop has my MP3 collection and a CD-RW writer, so I'm going to be burning a CD or 3 of my favorite music soon.

To maximize storage, what bitrate is appropriate (i.e. not overkill) for playing on a factory car stereo speaker system?  (It's a '97 Honda Accord, if anyone cares.)  Right now everything I have is 160K -- should I downsample to 128K?  64K?  Lower?  Leave it at 160K?  The stereo unit can handle anything from 8 to 320 Kbps according to the manual.

If I end up downsampling, what's the best way to do it in Ubuntu while preserving decent quality?  I don't want to haul out the source CDs but if there's no alternative I will.

---

### Post by Blankito on 2006-07-08
Anything below 128K will probably give you bad quality. I'd leave it at 160K, should sound nice on that system and you'll get at least 8 lps on a cd, but you could always use lame to decode to wav and then encode to 128K to maximize space, that might be quicker than getting out the source cds.

enjoy the system

---

### Post by LKRaider on 2006-07-08
Take a look at this, it could be useful: [http://puddle.ca/mp3togo/](http://puddle.ca/mp3togo/)

I would go for VBR mp3's set to the range of 32k/128k, this should give pretty good sound, while decreasing filesize on the parts of the songs that require less bitrates.

You could also use VBR 32k/160k, the difference should be minimum.

Or you can try 8k/160k, but there are some issues with bitrates lower than 32k on some players (it may work well on your player, but be unplayable on another...)

If you want to save time, simply copy the ones you have without re-encoding, because it is a very time-consuming process, that may give you little advantadge in storage space. Also, re-encoding from already compressed mp3's is not very good, as it's like saving a jpg picture twice, it is lossy compression applied upon an already lossy compressed source, so you loose ever more quality.

EDIT: another thing I just thought of, is to check what is the higher frequency your car speaker system is capable of, and cut the mp3's at that range (say, cutoff at 19500hz or so), that saves on the size, and if your sound system cannot reproduce it anyways, there's no real loss (and it saves bitrate for compressing the important parts).

---

