---
title: "anyone ever figure out how to fix flash?"
date: 2005-12-08
forum: General Help
---

### Post by woedend on 2005-12-08
hi, I know flash movies have that stupid sound/video sync issue which gets annoying but i'm not here to whine about that one this time.  This time its with any flash game that I play, the little dumb ones you find all over the internet.  They all have a weird intermittent freeze/lag to them.  The one in question that I find the best example is [http://www.addictinggames.com/kittencannon.html](http://www.addictinggames.com/kittencannon.html).  Kinda sick game yes, but when I shoot the cat about every 3 seconds itll freeze, then continue.  Is it just me?  Fairly fast computer.

---

### Post by jhnphm on 2005-12-08
Try disabling the esd wrapper for firefox and replacing it w/ aoss:

Run:
```
aptitude install alsa-oss
```

Edit:
```
/etc/mozilla-firefox/mozilla-firefoxrc
```

Change the value of:
```
 FIREFOX_DSP="esd"
```

to:
```
FIREFOX_DSP="aoss"
```
Might work with the value of "auto", I dunno- play with it.

---

### Post by 0okami on 2005-12-08
i went straight over to macromedia and got the player they have available for linux there. it seems to have solved my issues here :) 
Raving maids: [http://65.189.185.5/maidrave.html](http://65.189.185.5/maidrave.html)  ^_^

The instructions within the package are quite clear but none the les, if you have issues,  please post. Surely someone will help you. 
[http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

---

