---
title: "video playback is uber bright"
date: 2006-06-05
forum: Desktop Environments
---

### Post by stbrenner on 2006-06-05
Hi,

I am trying to get my video to play back correctly.  Whenever I play a video (i've tried DVDs, mpgs, and wmvs), I get the picture...however it is really really bright.  It doesn't look how it is supposed to look at all.  I would describe it as having the brightness and contrast too high (visualizing it yet? :) ).  

I already have all the codecs installed (namely w32codecs).  I don't know what else to do.  The only thing I can think of that may have effected anything is 915resolution.  I had to install it to get my screen to 1280x800.  I'm running a dell xps m140.

PLS HELP!    ](*,)

---

### Post by Wermut on 2006-06-05
I had the same problem and found out that is has something to do with the playback program.
Try using MPlayer (not KMplayer) or VLC player. These two did not have the described problems.

---

### Post by Chuckaluphagus on 2006-06-05
I had the same problem when playing back video (AVI, MPEG or DVD) using Totem ("Movie Player" under Applications -> Sound & Video if you're new to all of this; if you're not, sorry).  For some reason, the default video playback settings make everything look horribly bright and washed out.  

In Totem at least, you can change the video settings in the Preferences menu - click "Edit" on the menu bar, then "Preferences"), then select the "Display" tab at the top of the window that pops up.  On my computer (an Asus Centrino notebook), I was able to solve the problem and get everything looking right by just moving the Contrast slider under "Color Balance" from the middle to about 1/4 of the way from the left end of the bar.  

You can open up that menu and change the settings while video is playing if you want in order to tune it properly to your system.  Good luck, post back if you have any questions.

---

### Post by spira_mirabilis on 2006-06-06
I am also having this problem in Kubuntu 6.06 and both with Kaffeine and Mplayer. Adjusting the contrast and brightness helps a little, but does not produce normal playback. Funny, with the Milestone 7 Dapper there was no problem?

---

### Post by spira_mirabilis on 2006-06-08
The problem I had was fixed by resetting the xorg settings (dpkg-reconfigure). It was funny, I tried to take a screenshot of the shoddy DVD playback to show it on the forum, and the screenshot was perfect, even though the playback was not. 

So I thought maybe the monitor refresh settings might be wrong, even though there was only a problem with the display when playing DVD's. 

I guess that was it. Hope this helps everyone else.

---

### Post by stbrenner on 2006-07-01
i actually resolved my problem by adjusting the saturation/brightness/contrast

it was embarassing  #-o

---

### Post by hellmet on 2006-07-06
[QUOTE=spira_mirabilis]The problem I had was fixed by resetting the xorg settings (dpkg-reconfigure). It was funny, I tried to take a screenshot of the shoddy DVD playback to show it on the forum, and the screenshot was perfect, even though the playback was not. 

So I thought maybe the monitor refresh settings might be wrong, even though there was only a problem with the display when playing DVD's. 

I guess that was it. Hope this helps everyone else.[/QUOTE]
Yeah...the screenshots are perfect..
Hey I even tried Xorg reset..(Me too on 915GAV)
Nothin happens..
May I know what u did??
I mean ur settings

---

### Post by secure bit on 2007-12-21
how to make my videos run brighter ??

---

