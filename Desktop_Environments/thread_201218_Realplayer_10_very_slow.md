---
title: "Realplayer 10 very slow"
date: 2006-06-21
forum: Desktop Environments
---

### Post by Hark on 2006-06-21
I did a fresh install of Dapper on my PC a few weeks ago. I installed RealPlayer from the PLF repositories, like I used to do with previous Ubuntu versions. Unfortunately when I start a stream the stream stops/hangs a while every few seconds. When the stream is stopped, the whole program doesn't respond. After a second or so the stream plays again for a few seconds. I also tried several other RealPlayer 10 versions, even the .bin version from the official website. All had the same problem.

On my laptop I don't have this problem at all. My desktop PC is fast enough (Celeron 1200 MHz, enough CPU left when RealPlayer plays).

I'm not a newbie anymore, and I've really tried to get this working, but I can't. Does anybody know something about this problem?

Because RealPlayer 10 doesn't work I installed Mplayer, totem-xine and the w32codecs. I can view Real streams with it perfectly, but I don't have a (active) progress bar in both Mplayer and totem-xine, so I can't skip forward or backward. Is that normal with the Real codec in the w32codecs?

Thanks a lot!

---

### Post by Hark on 2006-06-23
By coincidence I started RealPlayer with no sound (an esd process was still running). To my surprise RealPlayer worked perfecly now! But, without the sound of course. After killing the esd process and starting RealPlayer for the second time, with sound, it was slow again.

So there must be something wrong with the sound (OSS output). Ideas anyone?

For clearity: the sound does work, but it makes my RealPlayer very slow. This wasn't the case in Breezy.

---

### Post by Hark on 2006-06-24
I found the solution here: [http://ubuntuforums.org/showthread.php?t=7017&page=3](http://ubuntuforums.org/showthread.php?t=7017&page=3)

---

