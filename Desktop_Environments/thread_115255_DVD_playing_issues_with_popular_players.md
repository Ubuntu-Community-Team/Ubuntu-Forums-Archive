---
title: "DVD playing issues with popular players"
date: 2006-01-10
forum: Desktop Environments
---

### Post by emperon on 2006-01-10
Hello,

I am trying to play my DVD's but i have encountered following issues:

* Kaffeine (gstreamer codec/plugin) - DMA Enabled! :  causes  choppy video, some parts of movie play faster than it has to be, sound is choppy mostly.

* Any player based on Xine plugin(including Kaffeine, Totem, Xine): When i try this option, along with some people in this forum, i get very broken output and the application crahes within few moments.

VLC: Everything is perfect, sound, video. The only problem is i couldn't manage to display subtitles.

Any help or opinions will be appreciated.

Onur

---

### Post by GoldBuggie on 2006-01-10
I recently made a fresh install of latest kubuntu with kde3.5 and when I played a dvd(with dma enabled) with kaffeine I got either choppy playback or some other error msg. With the xine engine I changed the "xine engine param.->video" to xshm. That made it play smooth and nice.

Haven't looked into fixing gstreamer yet since I got a working xine engine at the moment.

---

### Post by bulldogzerofive on 2006-01-11
I had this problem too.  Read the last entry in the thread to see how to fix it.

[http://www.ubuntuforums.org/showthread.php?t=104669](http://www.ubuntuforums.org/showthread.php?t=104669)

---

### Post by emperon on 2006-01-11
[QUOTE=GoldBuggie]I recently made a fresh install of latest kubuntu with kde3.5 and when I played a dvd(with dma enabled) with kaffeine I got either choppy playback or some other error msg. With the xine engine I changed the "xine engine param.->video" to xshm. That made it play smooth and nice.

Haven't looked into fixing gstreamer yet since I got a working xine engine at the moment.[/QUOTE]


This worked for me. Thanks for your posts

---

### Post by bullfrog on 2006-01-11
if others dont work.try totem it works for me on all.    bullfrog

---

### Post by emperon on 2006-01-14
In deed i realiezed that my problem still exists in a limited way. When i start kaffeine,  to play my DVD movie, i have to choose root from DVD menu otherwise it crashes as before. If i choose it on time, then there is no problem at all. It seems i have another linuxish workaround thing on the pile.

---

