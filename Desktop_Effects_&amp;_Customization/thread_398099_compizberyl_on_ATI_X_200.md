---
title: "compiz/beryl on ATI X 200"
date: 2007-03-31
forum: Desktop Effects &amp; Customization
---

### Post by ckellner on 2007-03-31
I am sorry to start a new thread on that, but while I did find lots of information in other threads, nothing really helped me so far...

My problem is that I tried to install compiz/beryl in various ways, and I always got it running, but after approx. 30 min it usually freezes- the mouse moves and music continues to play, but no keys work, not even ctr-alt-del or -f1

According to lspci, my AMD 64 laptop has the following graphic card
00:00.0 Host bridge: ATI Technologies Inc ATI Radeon Xpress 200 (RS480/RS482/RX480/RX482) Chipset - Host bridge (rev 01)


Like 2-3 month ago I had installed beryl with xgl, but it generally did not work very well. So i switched to AIGXL and ATI-open source drivers.  Currently, I am using Feisty with Compiz - almost everything worked out of the box, I just added  

Option 	"XAANoOffscreenPixmaps" "true"  to the device section and replaced ati with radeon by suggestions in the forums. 

This workes great, except the random hangup every 30 min +- . 

 I read that ati-open source are really experimental, so i was wondering whether I should try xgl again , as new releases might be more stable- or should I just wait for new developements ? any suggestions? anyone who is running compiz/beryl stable with this card - some sources say it is generally not supported with desktop effects (?!) 

currently, the problem appears both in edgy and feisty beta.

---

### Post by dharmayuvi on 2007-08-14
hi frnd
am also havin the same chipset as urs can u plz tel me how did u install beryl on dat i hv installed al beryl packages and enabled the driver but wen i try to use it its sayin no composite extension available
so kindly help me out wat shud i do now to get beryl effects on my comp

---

### Post by madseason on 2007-08-21
check this link out....it worked great for me. I have amd turion 64 with ati radeon xpress 200m

[http://ubuntuforums.org/showthread.php?t=399643&highlight=beryl+200m+feisty]("http://ubuntuforums.org/showthread.php?t=399643&highlight=beryl+200m+feisty")

---

