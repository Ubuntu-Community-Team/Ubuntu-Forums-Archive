---
title: "Music Lagging/skipping while multi tasking"
date: 2009-01-20
forum: General Help
---

### Post by johngreaver on 2009-01-20
Ok im a total linux noob I using fwcutter the other day was a huge accomplishment for me. Heres my question when im web browsing or trying do any multi tasking my media player skips and lags Im using banshee at the moment it does it the least but i have tried amorak, vlc and rythmbox. Im assuming this is due to a lack of system resources but I can stream live video and surf the web in another window whith a chatroom open and it dosent lag on Xp using wmp11. If i understand right ubuntu is suspose to use less resources than Xp.other than this i absoloutly LOVE ubuntu this is just a small extremly anoying problem.any one have an idea for a fox?


GAteway MX6441 laptop
1.8ghz AMD turionx64
512mb ram
80gb hdd 40 intrepid 40xp
64mb ATI xpress 200m
WORKING broadcom wireless adapter (Took me Long enough all hail b43-fwcutter)

---

### Post by FlamingChainsaws on 2009-03-14
I have this same problem. My computer was totally fine playing music, instant messaging, and internet browsing at the same time before this upgrade. Now I can't enjoy music while I do a simple Google search. Any help and/or potential solutions are greatly appreciated.

---

### Post by whitethorn on 2009-03-14
I had something close to that problem once, this fixed it for me

```
sudo /etc/init.d/alsa-utils reset
```

You could also check what your sound settings are set to in Preferences -> Sound.  I have the first 3 set to pulse audio server, the capture device to my usb mic and the mixed to my soundcard.  You could also try changing everything to alsa.

---

