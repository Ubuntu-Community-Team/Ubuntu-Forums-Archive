---
title: "Xubuntu and MP3 playback - packages?"
date: 2006-06-18
forum: Desktop Environments
---

### Post by asktoby on 2006-06-18
Hi,
Just installed Xubuntu on an old box to donate it to a friend. I'm sure he'll want MP3 playback but it's not enabled as standard (presumably due to patent issues).

I've trawled through synaptic and installed two packages which I thought would solve this problem (added universe and multiverse repositories, and then added libmad0 and mpeglib. I couldn't find W32codecs nor lame).

Still, loading an mp3 into Xfmedia results in a deafening silence!
Ogg Vorbises play fine.

Which package do I need to enable MP3 playback please?

---

### Post by majed on 2006-06-18
Hi,

Get XMMS. :)

[http://www.xmms.org](http://www.xmms.org)

Majed

---

### Post by Ramses de Norre on 2006-06-18
```
echo "deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main"|sudo tee -a /etc/apt/sources.list && sudo aptitude install w32codecs
```

For all codecs and audio layers take a look at [this]("http://wiki.ubuntu.com/RestrictedFormats") wiki page.

---

### Post by dolby on 2006-07-25
xfmedia plays mp3s & videos if u install libxine-extracodecs

---

### Post by videodrome on 2006-07-26
xfmedia crashes a lot for me. Get xmms and the W32 codecs from the aforementioned links.

---

### Post by shawnrgr on 2006-07-26
this post is useless, try searching the forums or google. or just do what i did for you, 3 click from ubuntulinux.com and you get this 

[https://help.ubuntu.com/xubuntu/desktopguide/C/multimedia.html](https://help.ubuntu.com/xubuntu/desktopguide/C/multimedia.html)

---

### Post by dolby on 2006-07-26
having done a standard xubuntu install, all u need for xfmedia to play mp3 (as the topic starter asked) all u need to play mp3s is libxine-extracodecs

your post is more useless than mine cause u suggest installing a bunch of packages most of which are not needed to play mp3s on xubuntu

---

### Post by Thanol on 2006-07-26
I don't know if this applies, but when I installed Xine in Kubuntu to get Mp3s to play I kept getting an error, missing/broken packages, and then I found out, through the terminal,  I had to install libmad0_0.15.1b-2.1_i386.deb .

---

### Post by shawnrgr on 2006-07-26
> **dolby said:**
> having done a standard xubuntu install, all u need for xfmedia to play mp3 (as the topic starter asked) all u need to play mp3s is libxine-extracodecs

your post is more useless than mine cause u suggest installing a bunch of packages most of which are not needed to play mp3s on xubuntu

actually i didn't "suggest" he install anything. my point is with a simple search he would find what he is looking for..

besides. im sure at one point he will need/want to play somthing other than mp3/ogg.aa

---

