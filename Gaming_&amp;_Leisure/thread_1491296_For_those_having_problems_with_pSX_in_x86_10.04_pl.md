---
title: "For those having problems with pSX in x86 10.04 please read..."
date: 2010-05-23
forum: Gaming &amp; Leisure
---

### Post by dfreer on 2010-05-23
Can you try the following and see if it works for you now?:

Download pSX.
```
sudo aptitude install libgtkglext1 libgtkglext1-dev
echo "autospawn = no" > /etc/pulse/client.conf
pkill pulseaudio
./pSX
```

Let me know what output you get if it doesn't work, or if it does work. It's working for me but with crazy sound under runs but I'm using VMWare Workstation to play with it, so I assume thats the problem with its sound (it always had some under runs but not this much).

---

### Post by 7G Operator on 2010-05-31
Try adjusting your screen display to 480x640 to help with the sound underruns. I'm running it on a netbook and it used to sound bloody underrun a alot. A moment of inspiration hit me when i realised that the emulator is actually a faithful replication of the original playstation which runs at 480x640 native default screen res, so it made sense to adjust the screen res on my laptop appropriately. Seemed to of solved my sound underrun woes anyways. Perhaps it will be of use to you also ;) 

- ObiDan Kinobi

---

