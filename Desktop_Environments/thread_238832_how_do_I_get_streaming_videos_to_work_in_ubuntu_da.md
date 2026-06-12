---
title: "how do I get streaming videos to work in ubuntu dapper"
date: 2006-08-18
forum: Desktop Environments
---

### Post by kazuya on 2006-08-18
I still cannot get streaming video content from wwe.com or certain other sites to work in Ubuntu even though these same site videos play fine from Vector soho linux.  I have used automatix to install flash and the remaining multimedia codecs. Still cannot stream those videos from firefox any ideas?

---

### Post by encompass on 2006-08-18
You could ask them how they got the players to read it.  I can read most... but when they stream like that wit windows media... no luck.  I would be interesting to see how they did it.

---

### Post by yopnono on 2006-08-18
I tried this link.
[http://www.wwe.com/superstars/divas/2006divasearch/videos1/](http://www.wwe.com/superstars/divas/2006divasearch/videos1/)
I can view the stream using mplayer and fx plugins
also I have the w32 codecs. The flash they complain about since it's ver 7.

EDIT: if you change the flash ver in the pluginreg.dat file to
Shockwave Flash 9.0 r63:$
Shockwave Flash:$
you will be able to use the flash content aswell

---

### Post by givré on 2006-08-18
You should try mozilla-mplayer plugin in universe
```
sudo apt-get install mozilla-mplayer
```

---

### Post by kazuya on 2006-08-21
thanks guys. I tried all of that. I believe the only thing left for me to try is to reinstall the mplayer-plugin and see what happens. I'll try those steps again.

---

