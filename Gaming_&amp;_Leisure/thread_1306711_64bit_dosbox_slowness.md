---
title: "64bit dosbox slowness"
date: 2009-10-30
forum: Gaming &amp; Leisure
---

### Post by jworr on 2009-10-30
After upgrading to Karmic the sound in dosbox has become slow and choppy.  Boosting the cpu cycles doesn't help.  I'm running the 32 bit version of karmic with the latest version of dosbox out of the repositories.  I tried rolling back dosbox to the version used in 9.04 but it didn't work either.

Has anyone else had a similar problem?  Does anyone have any suggestions?

---

### Post by jworr on 2009-10-30
Here is the sound part of my dosbox config:

[sblaster]
type = sb16
base = 220
dma = 1
irq = 7
mixer = true

[midi]
intelligent = true
mpu401 = true
device = alsa
config = 128:0

---

### Post by rCXer on 2009-10-30
This is a [known bug](https://bugs.launchpad.net/ubuntu/+source/dosbox/+bug/429373) in Karmic. Someone had the [same problem and fixed it](http://ubuntuforums.org/showthread.php?t=1300669) by setting the sound mixer to "rate=44100" in their config file.  You could also try switching to libsdl-esd as someone else suggested in the bug report.

---

### Post by jworr on 2009-10-30
Thanks that did help some.  It was working perfectly before so it's a shame upgrading broke it.  Pulse audio is really frustrating.

---

### Post by jworr on 2009-10-30
Removing pulseaudio completely fixes the issue.  These two commands will do it:

sudo apt-get install libsdl1.2debian-esd
sudo apt-get remove pulseaudio

---

### Post by automaton26 on 2009-11-01
Changing the mixer rate helped me too, thanks.

I also found that maxing-out these [mixer] values helped a bit more:

```
rate=49716
blocksize=8192
prebuffer=100

```
Although I'm using Kubuntu x64, so I'm not sure whether removing pulseaudio is an option :(

---

### Post by Klaue on 2010-01-11
I had this problem too, but none of the workarounds (like setting rate to another value) worked.

Starting dosbox with
export SDL_AUDIODRIVER=esd;dosbox
did the trick and provided me with perfect sound without any change in the dosbox configuration.

By the way, I did not uninstall pulseaudio and I also don't have libsdl1.2debian-esd installed (which would force me to uninstall PA, as far as I remember). I only have libesd-alsa0 and the gstreamer plugin, but I don't really know if they're neccessary

EDIT: By the way, with what I've found, this problem is not 64bit-exclusive, but still, for the archive: I have 32 bit

---

### Post by mateomiguel on 2010-04-26
> **automaton26 said:**
> Changing the mixer rate helped me too, thanks.

I also found that maxing-out these [mixer] values helped a bit more:

```
rate=49716
blocksize=8192
prebuffer=100

```
Although I'm using Kubuntu x64, so I'm not sure whether removing pulseaudio is an option :(

Maxxing out those values also helped me, and I'm running Ubuntu 10.04 64 bit.  Perfect fix!

---

