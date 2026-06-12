---
title: "why aoss firefox?"
date: 2006-08-18
forum: Desktop Environments
---

### Post by shoagun on 2006-08-18
Many people have had problems with audio woring in embedded videos in firefox (such as youtube) while another sound program is open.  I have been one of those people.  I have searched through so many forums and I keep finding solutions that don't work.  The closest thing I've found to a solution (I don't consider it a "true" solution) is to open firerox using 
```
aoss firefox
```

I'm just curious as to why this works, but none of the solutions which involve changing settings work?  I have edited /etc/firefox/firefoxrc to set FIREFOX_DSP="aoss".  I have set System>Preferences>Multimedia System Selector  to use ALSA as the defualt audio output.  I have disabled ESD.  

Why is it that the only way to get sound to work properly is to type aoss firefox???  I don't get it.

---

### Post by BitTorrentBuddha on 2006-08-18
Flash pipes audio through OSS, aoss is short for alsa-oss, it forces flash to pipe audio through alsa. Why don't you consider it a true fix?

---

### Post by shoagun on 2006-08-18
I don't consider it a true fix because I have to manually force FF to do something it should be able to do automatically.

---

### Post by aysiu on 2006-08-18
Have you tried [this fix](http://www.ubuntuforums.org/showpost.php?p=1297126&postcount=1)?

---

### Post by shoagun on 2006-08-18
I'm at work right now and I don't have my headphones, so I can't really do sound tests.  I'll try this when I get home.  My point is though, shouldn't it be possible to just set FF to only use aoss and to never use esd?   This might be a stupid question; I don't know all that much about sound.  But I figure, if I can force FF to use aoss on the commandline, there has got to be a way to just make that the default, right?

---

