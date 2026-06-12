---
title: "Desktop power consumption - my findings."
date: 2010-05-16
forum: Desktop Environments
---

### Post by viulian on 2010-05-16
Hello,

I am using power meter "Everflourish EMT707C TL" to asses PC's power consumption using Ubuntu's 9.10.

Conclusions: PC uses less power with GUI up then running in text mode. NVidia drivers were able to clock down the board thus using less power (but to load those drivers, X has to run).

More details:

a) powertop does nothing visible to my PC's power consumption. It is currently sitting at 107w and even if I did run powertop and executed all the suggestions (USB suspend kills my RF mouse anyway), I still see the same power consumption on the meter.

b) ```
Option	"OnDemandVBlankInterrupts" "true"
``` does nothing visible on the power meter.

c) I was able to cut 25W from the power consumption by fiddling with NVidia drivers. To mention, I have an Nvidia 8800GT which is not the most favourable candidate for power usage, but ... the PC was initially built for gaming.
- Driver version 195 from ppa keeps the temperature at 80C (130W). 
- Drivers version 185-190 are better, with the temperature at 70C.
- I am now using 173.14.20 which averages at around 65C and keeps the power at around 115W.

I had then to use nvclock and clock down the video board (8800GT) to 150MHz the GPU and 300MHz the memory (from 600/900 standard).

I've edited the file: /etc/gdm/Init/Default, and just before the last line "exit 0", I've inserted:

```
nvclock -m 300 -n 150
```

With this and driver version 173, the system is now at 107W. Board's temperature is 61C.

I was able to cut 20euros / year from the electricity bill :). Is still cheaper for me to have this PC as backup for my websites, as well as trying fancy stuff - than to rent on-line similar characteristics: E8500 CPU + 2Gb of RAM + 2 x 250GB RAID 0 (fakeraid).

---

### Post by chiwi on 2010-05-17
nice info, but where is that power meter?  is that something you attach to the power socket in the wall ? I've never seen one of those where I live.

or is it a software?

---

### Post by cascade9 on 2010-05-17
Interesting diferences in the drivers from 173/180/190/195. I dont know if I would use the 173 drivers on a 8XXX series nVidia card, I cant recall exactly but I *think* that it was the 8 series cards that made nvidia split the drivers (96.xx for gf4, etc, 173 for FX, 180+ for GF6 and above). 

BTW, you could try a minimal install. I've got a PM from somebody who said that they went from 55watts (xubuntu) to 45watts (minimal install Xfce).

---

### Post by viulian on 2010-05-17
> **chiwi said:**
> nice info, but where is that power meter?  is that something you attach to the power socket in the wall ?

Yep, you can search Google Images using the model I gave above and you will find some images.

> **cascade9 said:**
> I *think* that it was the 8 series cards that made nvidia split the drivers (96.xx for gf4, etc, 173 for FX, 180+ for GF6 and above). 

BTW, you could try a minimal install. I've got a PM from somebody who said that they went from 55watts (xubuntu) to 45watts (minimal install Xfce).

Thanks for the feedback, I didn't know that about the driver versions split. I will give version 96 a try. 

About the minimal install, I cannot :(. I can in fact, but to to redo the boot from fakeraid, recompile drivers for wifi, the encrypted home folders, eeeetc...

---

### Post by cascade9 on 2010-05-17
I really wouldnt try the 96 drivers. They were never made for the Geforce 6 and above cards. 

The same sort of thing that happened with the FX being 173.xx drivers happened with the 96.xx drivers (nvidia made the 96.xx drivers GF4 and (some) earlier cards, the FX moved on and ended up stopping at 173.xx) 

As for the minimal install- yeah, it can be a pain for some people. You could always try removing things you dont need via synaptic, that could drop your power usage as well.

---

### Post by viulian on 2010-05-18
On some more interesting facts:

a) playing an non-hd youtube video -> 4W more consumption (I'm only counting the power input to the PC itself, not the audio sound system / monitor, etc).

The CPU load is 26% when using Flash in Firefox. The CPU is scaled down to 2GHz, seems there's not enough load to make it go to 3.17Ghz - but 25% is enough to drive power usage up with 4W.

b) playing an full-hd youtube video (1080p) -> 20W more usage. I can see the CPU going to 3.17GHz though from time to time. Firefox load average 86%. Full screen means 6W more added.

b) just to keep the PC plugged in but shut down - 3W power usage.

---

### Post by cascade9 on 2010-05-18
> **viulian said:**
> On some more interesting facts:

a) playing an non-hd youtube video -> 4W more consumption (I'm only counting the power input to the PC itself, not the audio sound system / monitor, etc).

The CPU load is 26% when using Flash in Firefox. The CPU is scaled down to 2GHz, seems there's not enough load to make it go to 3.17Ghz - but 25% is enough to drive power usage up with 4W.

b) playing an full-hd youtube video (1080p) -> 20W more usage. I can see the CPU going to 3.17GHz though from time to time. Firefox load average 86%. Full screen means 6W more added.

I'm pretty sure that flash 10.1 is (was?) meant to get GPU video acceleration (i.e. VDPAU). It would be interesting to see if flash 10.1 and the 180.XX+ drivers (which you need for VDPAU) would have a giher, or lower max power consumption if that is the case. 

> **viulian said:**
> b) just to keep the PC plugged in but shut down - 3W power usage.

One reason why I unplug my power when I power down. Not the only reason though, the others are it impossible to get surged if the plug is out, and my speakers have a power birck, that like all power bricks eats power even when not in use.

---

