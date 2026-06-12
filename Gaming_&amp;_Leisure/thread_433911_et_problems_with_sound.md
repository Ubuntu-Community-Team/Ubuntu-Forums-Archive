---
title: "et problems with sound"
date: 2007-05-05
forum: Gaming &amp; Leisure
---

### Post by themerchant on 2007-05-05
Ok, so I was having problems with Counter strike source in wine, so I had to change some sound options in wine around, so then I go to play et (which isn't in wine) and its sound doesn't work! After using some guides on this, and still not working, I reinstalled the game with the latest version, and still it doesn't work, the sound worked before, why isn't working now? Can anyone help please?

---

### Post by noerrorsfound on 2007-05-12
This might work:
```
sudo killall esd
```
It has solved sound problems for me in the past.

(I was looking through the posts with no responses and when I saw this week-old post I decided to at least try to help you since nobody else has.)

---

### Post by themerchant on 2007-05-12
Nope, didn't work, thanks anyway!

---

### Post by noerrorsfound on 2007-05-12
Can you please post the terminal output of Enemy Territory?

(You must open a terminal and then start ET from the terminal. I believe the command is **et**.)

I also found this:
[http://alsa.opensrc.org/home/w/org/opensrc/alsa/index.php?title=FAQ023](http://alsa.opensrc.org/home/w/org/opensrc/alsa/index.php?title=FAQ023)

---

### Post by saygin on 2007-05-15
thanks a lot! the link you gave worked for me! thanx

---

