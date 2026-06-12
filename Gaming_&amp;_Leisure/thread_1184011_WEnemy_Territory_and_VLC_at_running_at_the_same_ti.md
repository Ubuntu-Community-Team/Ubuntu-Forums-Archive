---
title: "W:Enemy Territory and VLC at running at the same time."
date: 2009-06-10
forum: Gaming &amp; Leisure
---

### Post by sti11_learning on 2009-06-10
I switched completely to ubuntu a few months ago and have never looked back. 

I have gotten W:ET working on my ubuntu 8.10 install. VLC also runs fine and has done so since I installed it. However, occasionally I like to play music through vlc while I play certain games. Alone, vlc can play whatever I tell it to. Alone, enemy territory can play the game's sound. But, when I run one then the other the application that is **started first** can open [COLOR=red]/dev/dsp[/COLOR] and play sound but, the other can't. So, if I start vlc then W:ET, vlc will play but, enemy territory will be silent. Then, if I start vlc after ET is running enemy territory will continue to play sound but vlc won't play at all. 
Also, I was able to get enemy territory to play sound while I had my psp connected into my computers auxiliary line in and playing the contents of it's memory stick. 

So, any ideas on how to get vlc and Enemy Territory to share [COLOR=red]/dev/dsp[/COLOR]?

---

### Post by CharmyBee on 2009-06-10
This is one of the many griefs of PulseAudio in 8.10. I think 9.04 fixed this, but since I don't know your video hardware (like it could not be a Radeon HDxxxx+) I wouldn't recommend the upgrade.

---

### Post by sti11_learning on 2009-06-10
Thanks for the response. When 9.04 came out I did upgrade but, I lost the ability to use the FGLRX driver with my Xpress 200 series IGP. I am planing to get a new video card in August by which time, most of the bugs in 9.04 should be sorted out. Then I will upgrade.

---

### Post by Gen2ly on 2009-06-13
If you want to OSSv4 should be able to handle both of these audio inputs just fine.  OSSv4 has alot less latency and does a great job of mixing.  ALSA is kinda the default not though and there may be a few programs that just won't work with OSS.

---

