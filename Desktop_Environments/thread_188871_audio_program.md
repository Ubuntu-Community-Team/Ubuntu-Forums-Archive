---
title: "audio program"
date: 2006-06-04
forum: Desktop Environments
---

### Post by nickdr on 2006-06-04
i installed amarok, looks great, but it wont play any of my .mp3 songs. i installed all the codecs neccessary, and they work for every other player. also why did it install 1.3, if 1.4 is out??

off topic question: can anyone help me get my tv tuner card working?

---

### Post by skymt on 2006-06-04
Middle question first, since it's easy: there isn't currently a stable, well-tested Ubuntu package for 1.4. It's on the way. If you want it now, you need to add the following line to the bottom of /etc/apt/sources.list

```
deb http://kubuntu.org/packages/amarok-14 dapper main
```

That file is owned by root, so you'll need to open a terminal window and enter "sudo gedit /etc/apt/sources.list".

The first question is easy now that I've answered #2: 1.4 should fix that. See? :mrgreen: 

As for your third question, no, I can't. Not without more information about the problems you're having, anyway.

---

### Post by nickdr on 2006-06-04
well for the mp3 files i installed all the codecs neccessary, and programs like banshee and rythmbox play them fine, but amarok just scans my whole library when  i click on a file. 

i did notice though that amarok is using the xine engine (only option) and banshee is using the gstreamer. could this be affecting that?

NOTE: it is still telling me that amarok is at latest release. however when i ran "sudo apt-get upgrade" this came up

Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  amarok amarok-xine
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

how do i get around this

---

### Post by nickdr on 2006-06-04
never mind that now...
i have amarok 1.4, but i am still having playback issues with mp3. the situation described above with the xine and gstreamer is still present too.

---

