---
title: "Constent Second Life Crash?"
date: 2009-02-08
forum: Gaming &amp; Leisure
---

### Post by Kidfork on 2009-02-08
So heres the deal, i used to play Second Life back in 8.04 but then quit for a bit of time. Then in time 8.10 Came out and i upgraded. I now have the latest Nvidia Graphics Drivers from the Respos 177. And Now what happens is when i play i can play in a populated area for about 5-10Minutes, no lagg. Then out of nowhere everything freezes and I have to CTR+ALT+BACKSPACE to get out of it. I Have set the graphics setting to the lowest possiable to try and resolve this problem but no luck. When i install it through Wine it doesn't crash, but the graphics and preformace decreases a bit. 
My Specs
Ubuntu Partition-10GB
2.4 AMD 32-Bit Processer.
640 MB RAM
Nvidia GeForce 6200 AGP 8X 512MB


NOTE: When i played before Ubuntu was my only operating System, but now its 10GB Ubuntu Partition EXT2. And the other half is Windows.

---

### Post by Naiki Muliaina on 2009-02-08
In Xubuntu 8.10 using Nvidia 177 drivers with a 9800GTX my graphics go to pot and lags incredibly badly after 5-10 minutes of play when i have so much as XFCE compositing on. Works fine if i swap the card for an old ATI Radeon X1950. 

Guessing its a compositing + Nvidia 177 driver issue. :(

---

### Post by simtaalo on 2009-02-08
why don't u get the newer drivers?

[http://ubuntuforums.org/showpost.php?p=6632383&postcount=377](http://ubuntuforums.org/showpost.php?p=6632383&postcount=377)

---

### Post by Kidfork on 2009-02-08
How do i install i click on the "Click Here" from the link you gave me  and i get The Untited about:blank webpage

---

### Post by Naiki Muliaina on 2009-02-08
Either you dont have apturl installed or your using a browser it doesnt work in. The long way of doing thats is:

Open Hardware Drivers and remove any Nvidia drivers you have installed. 

Open synaptic, find Nvidia 180 driver and install it. 

Restart your PC and it should be on.

---

### Post by Kidfork on 2009-02-08
Thank you for the reply. I got it working, but however Second Life Still crashes. Not much has changed. And in the meantime i have tried Moving OpenGL to High-Performance. No luck though. This is killing me on how It works fine through wine but not with Linux Client. (With the exception of Slow Graphics)

---

### Post by Kidfork on 2009-02-08
Also, I ran ./secondlife
through the terminal and found out my average FPS is 25. Is this average and if its not how can i fix?

---

### Post by Naiki Muliaina on 2009-02-09
Well, you could try 2 things. First, checking its not all openGL games. As in try playing Nexuiz or Open Arena or something.

Secound, try downloading the SL client through the repo's to make sure you have all your dependencys. [(Linky to second life repo info)]("http://naiux.wordpress.com/2008/11/30/cracking-news-on-second-life-front/")

---

### Post by janicejan on 2009-02-09
upgrade your computer, get a new driver.. maybe its the new version isn't compatible with the old specs of your computer..

---

