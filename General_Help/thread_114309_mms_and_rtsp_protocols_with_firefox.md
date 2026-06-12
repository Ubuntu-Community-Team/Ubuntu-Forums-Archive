---
title: "mms and rtsp protocols with firefox"
date: 2006-01-08
forum: General Help
---

### Post by Zerlinna on 2006-01-08
Hi there,

since a user asked me (see [http://ubuntuforums.org/showthread.php?t=113301&page=3](http://ubuntuforums.org/showthread.php?t=113301&page=3)) how to get the videos of [this site]("http://beelinetv.com/") to work I noticed that I cannot stream  mms protocols with my mplayerplugin in firefox (for other streams it works like a charm) neither rtsp protocols with my realplayer. 

If I want to open such a stream my firefox wants to open it with totem - and as far as I can see, totem cannot handle those streams. 

So I did in about:config in firefox:

network.protocol-handler.app.mms	user set	string /usr/bin/X11/mplayer
network.protocol-handler.external.mms	user set	boolean true

network.protocol-handler.app.rtsp           user set         /usr/bin/X11/realplay
network.protocol-handler.external.rtsp     user set       boolean true

Now the streams open with the right program (mplayer and realplayer) - but is there any way to get them working INSIDE firefox? (plugins)? 

Thanx, Z.

---

### Post by pinguinus on 2007-01-06
Me likes to ask the same question...

Zerlinna's previous advice has worked well (thanks), but how about enabling mms and rtsp media inside Firefox? Has there been some development in this kind of streaming media support? (I haven't followed the subject very closely). Any advice anybody?

---

