---
title: "no sound in games like q3 and et"
date: 2006-01-24
forum: Desktop Environments
---

### Post by matva on 2006-01-24
ok, i know this is a common problem, but i have yet to find a working solution. i've tried q3jack... that still has latency and gives crackling noises. I tried:
echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss 

&

echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss


but that locks up my system while playing. 

the error produced is:
Could not mmap /dev/dsp

i need a solution that works with PB. thanks!

---

### Post by ACK!! on 2006-01-25
[QUOTE=matva]ok, i know this is a common problem, but i have yet to find a working solution. i've tried q3jack... that still has latency and gives crackling noises. I tried:
...

i need a solution that works with PB. thanks![/QUOTE]

killall esd and then run quake3.  Does it work?

---

### Post by matva on 2006-01-25
havent tried that but read something similar in the q3 readme. I will try it when i get home, thanks.

---

### Post by matva on 2006-01-25
darn, it doesnt work =(

---

### Post by matva on 2006-01-26
Anyone? Should i just give up on it? Will putting in another soundcard fix it?

---

### Post by EPOX123 on 2006-06-28
Try to compile this program it got my m-audio audiophile 2496 to work.

[http://www.craknet.net/joss/](http://www.craknet.net/joss/)

I made a deb pack dont have a place to upload it.

---

