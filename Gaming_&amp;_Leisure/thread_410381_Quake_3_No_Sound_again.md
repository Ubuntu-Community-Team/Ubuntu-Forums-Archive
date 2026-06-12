---
title: "Quake 3 No Sound again"
date: 2007-04-15
forum: Gaming &amp; Leisure
---

### Post by lucky2 on 2007-04-15
Did anyone get hold of > joss-0.5.tar.gz before the site went down? so far I can only find joss-0.3.tar.gz mirrored and I get compile errors with that so would like to try .5, any help would be really cool, also if anyone has a better/quicker/fix that works please tell me:) Ive tried lots of things.

---

### Post by fakie_flip on 2007-04-19
Get Open Arena and forget about Quake 3. The reason sound doesn't is because Quake 3 is because it is not open source, so the developers can't fix the sound problem. However Open Arena is open source and the sound works without doing anything extra. Open Arena is a Quake clone, and it plays very smooth in Linux.

---

### Post by Christoffer Klang on 2007-04-19
i just got quake3 up and running today with the sound... i used the open source port [http://www.ioquake3.org/](http://www.ioquake3.org/) wich uses open AL for the sound (i think quake from id software uses oss)...

i havent tried it in multiplayer though (i just ran through it in single player ;) ) so i dont know if it can connect to regular servers etc...

---

### Post by noerrorsfound on 2007-04-20
> **Christoffer Klang said:**
> i just got quake3 up and running today with the sound... i used the open source port [http://www.ioquake3.org/](http://www.ioquake3.org/) wich uses open AL for the sound (i think quake from id software uses oss)...

i havent tried it in multiplayer though (i just ran through it in single player ;) ) so i dont know if it can connect to regular servers etc...
You can only connect to servers that have PunkBuster disabled.

---

### Post by lennie2 on 2007-06-19
Do you have any guidelines on how to het ioquake3 runnung ? I cant find a tutorial on it ? Sorry I'm a newbie, got Quake3 running but obviously without sound.

---

### Post by Riel on 2007-07-05
It worked like a charm (the ID-software Quake3 version).
I got ' sound system muted ' all the time.

Installing the OSS-system from [www.opensound.com](www.opensound.com), and using their installation instructions, it worked perfectly!

Had to restart, and set in ' preferences ' the sound at autodetect (otherwise, the sounddrivers were used by another application).

I also needed to install build-essentials, but that was no more than apt-get built-essentials or something like it.

I'm quite new here too, but I am glad I got it all working !

And ALL working, 100%

---

