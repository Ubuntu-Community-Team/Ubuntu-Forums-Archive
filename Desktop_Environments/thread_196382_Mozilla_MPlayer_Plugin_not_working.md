---
title: "Mozilla MPlayer Plugin not working"
date: 2006-06-14
forum: Desktop Environments
---

### Post by rjcube on 2006-06-14
When I try to view a video in MPlayer using firefox, it just shows the gray screen with the logo and says "playing http://*" and there is the progress bar at the bottom and I can hear sound, but no video. 

What is causing this and how can I fix it?

---

### Post by FredB on 2006-06-14
Adding win32 codecs ?

More infos on them :

[http://www1.mplayerhq.hu/design7/codecs.html](http://www1.mplayerhq.hu/design7/codecs.html)

I don't know to install the good way (using synaptic), because I installed them manually :(

---

### Post by phorque on 2006-06-14
You've got to download those codecs (dll files) and put them somewhere like /usr/lib/win32/ or something like that.

You can also check out your mplayer preferences and try changing the video output to X11, xv or gl to see if any of those offer an improvement.

---

### Post by rjcube on 2006-06-14
changing the video output did not do anything, and i cant figure out where to put the codecs. Although I do not think that is the problem because I had the player working at one time then all the sudden it stopped working.

---

### Post by Chris03 on 2006-06-14
For Win32 codecs, [go here]("http://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/") and get the 0.4.deb, which is currently the latest one. Then, you can double click on the .deb to install the package.

That feature rocks!

---

### Post by rjcube on 2006-06-14
[QUOTE=Chris03]For Win32 codecs, [go here]("http://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/") and get the 0.4.deb, which is currently the latest one. Then, you can double click on the .deb to install the package.

That feature rocks![/QUOTE]

Indeed it does! That did the trick, thanks everyone.

---

