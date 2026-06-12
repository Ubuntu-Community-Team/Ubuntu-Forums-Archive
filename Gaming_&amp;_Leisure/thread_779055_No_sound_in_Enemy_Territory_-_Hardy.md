---
title: "No sound in Enemy Territory - Hardy"
date: 2008-05-02
forum: Gaming &amp; Leisure
---

### Post by wadelewis4 on 2008-05-02
what is the deal with the sound issues? lol. 

First it was no sound with Firefox & flash player (resolved),
but now no sound when I installed Wolfenstein: Enemy Territory. 

Anyone else getting this in Hardy?

Lemme know.

---

### Post by Luister on 2008-05-02
check the last post in this thread, might help

[http://ubuntuforums.org/showthread.php?t=767515&page=2](http://ubuntuforums.org/showthread.php?t=767515&page=2)

---

### Post by dannyking on 2008-05-09
The problem is the new pulseaudio sound deamon.

To fix enemy territory do this:

wget -q -O - [http://nullkey.ath.cx/~stuff/et-sdl-sound/et-sdl-sound.gz](http://nullkey.ath.cx/~stuff/et-sdl-sound/et-sdl-sound.gz) | gzip -d > et-sdl-sound && chmod a+x et-sdl-sound

That will download a script that you can run (./et-sdl-sound.gz) which should get the sound working for you once et is installed.

That command was taken from [http://nullkey.ath.cx/~stuff/et-sdl-sound/](http://nullkey.ath.cx/~stuff/et-sdl-sound/)

---

### Post by Ronbo on 2008-05-10
> The problem is the new pulseaudio sound deamon.

To fix enemy territory do this:

wget -q -O - [http://nullkey.ath.cx/~stuff/et-sdl-...t-sdl-sound.gz](http://nullkey.ath.cx/~stuff/et-sdl-...t-sdl-sound.gz) | gzip -d > et-sdl-sound && chmod a+x et-sdl-sound

That will download a script that you can run (./et-sdl-sound.gz) which should get the sound working for you once et is installed.

That command was taken from [http://nullkey.ath.cx/~stuff/et-sdl-sound/](http://nullkey.ath.cx/~stuff/et-sdl-sound/)

Thanks, I was having the same problem and that fixed it.

---

### Post by equity on 2008-06-29
Does not work for me ...

> gzip: compressed data not read from a terminal. Use -f to force decompression.
For help, type: gzip -h
 

---

### Post by lillypop on 2008-06-30
I just exited ET completley  then restarted Et and sound worked happens on windows sometimes too .
That was on a ET 2.60 install i have since done a fresh install with ET 2.55 and had no issues at all.

---

### Post by 1/0 on 2008-08-16
I just did this first and it worked fine:

```
sudo su
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit
```

---

### Post by almostlinux on 2008-08-16
> **1/0 said:**
> I just did this first and it worked fine:

```
sudo su
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit
```

With this, you won't be able to hear anything else when on et. I sometimes prefer background music...

go with the sdl method listed above.

---

