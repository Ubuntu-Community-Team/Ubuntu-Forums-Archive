---
title: "Xubuntu 9.0.4 on a Dell XPS T500Mhz"
date: 2009-07-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by xubu_user on 2009-07-13
Hi all,
 
This is my first posting and I'm a newbie to the Linux world. I have a iMac too. My old Dell XPS T500 w/ 500Mhz CPU and 384MB RAM is collecting dust and I wanted to run Xubuntu on it. Everything is fine except for 2 issues.
 
1. There is absolutely no audio in the system. The system has a Yamaha DS-1 audio card and I tried the sudo aslamixer and increased volume on all available controls and still no go. I previously was running XP on it and the audio was fine but it was crawling.
 
2. Right now, the system seems to be running slow. I can install another PC100 256MB SDRAM. Will this make the system run faster? I watch videos online and it seems that the video are stuttering and wanted to make sure if I add 256MB RAM to get up to 640MB RAM (total), will it help?
 
Appreciate your assistance.

---

### Post by mikewhatever on 2009-07-14
Can you post the output of **aplay -l** command to check if your sound card is recognized.

Adding RAM will make your system snappier and more stable, but I doubt it will noticeably improve flash video playback quality. Flash is simply not a match for a 500Mhz CPU. [http://www.adobe.com/products/flashplayer/systemreqs/](http://www.adobe.com/products/flashplayer/systemreqs/)
Perhaps installing an even lighter system will free some cpu cycles, but I wouldn't expect a lot.

---

