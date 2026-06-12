---
title: "HOWTO Keep NVIDIA 135M GPU at a low temperature (D630)"
date: 2008-08-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by qwill on 2008-08-06
Hi,

I had to change my D630 motherboard due to the infamous NVIDA overheating Quadro 135M GPU. Using my laptop docked with 2 external screens and Compiz enables keeps the GPU at high frequency making it reach 75-80 C quite often.

Nvidia-Settings doesn't allow the user to set the powermixzer setting of the card; but here is the trick : 

Just add the following lines under the device section of the /etc/X11/xorg.conf file to set the powermizer level to the lowest performance level while on AC or battery.

The GPU scales its frequency down from 400MHZ/600MHZ to 275/300 MHZ and its temperature stays between 40-60 C instead of 60-80 C....
#force Powermizer to a certain level at all times

Using ubuntu with compiz, 2 external display ( therefore a 3200x1200 desktop)  and a lot of effects enabled; I did not notice any difference in the graphic performance of the GPU.

# level 0x1 = highest
# level 0x2 = med
# level 0x3 = lowest
Option "RegistryDwords" "PowerMizerLevelAC=0x3"
Option	"RegistryDwords"	"PowerMizerLevel=0x3"

*/ This is saving my laptop !*/

If its so easy to set the powermizer settings; why do NVIDIA don't release tools to that effects ? 20 C difference in temperature certainly increase the GPU life.

Qwill.

Addition : Another factor that helps keeping the GPU temp at a low level is to set the CPU frequency scaling to "conservative". I noticed that the CPU temperature has a big impact on the GPU temp.

---

### Post by Nicolae on 2008-08-07
Hunh, I hadn't heard of the 135M having heating issues, but I've recently had to have my mobo replaced because of a bad GPU as well. I'll keep an eye on my GPU temps and use this fix if they're getting to be too hot, thanks.

---

### Post by RodrigoAl on 2008-10-06
a Bios update was released by Dell for Nvidia Video Cards, to avoid temperature fluctuations

do you know if this release do something similar???

[http://www.ghacks.net/2008/07/30/dell-releases-bios-updates-for-several-nvidia-video-cards/]("http://www.ghacks.net/2008/07/30/dell-releases-bios-updates-for-several-nvidia-video-cards/")

---

### Post by qwill on 2008-10-31
Nope; the DELL Bios update just fires the fan more often ( they lowered the trigger temperature at which the fans start.)

Qwill

---

### Post by Clockswork on 2008-11-03
I have a 8600m GT (XPS m1530) and dont like my GPU temp, 60 degrees idle. Could this fix, lower my idle temp? Thanks

---

### Post by ookamisan on 2009-02-06
Hello,

I tried the changes in the xorg.conf, in the nVidia tool I can see the new PowerMizer Performance Level, so my GPU is running really slow (169MHz), I am not using any 3D features (Compitz is turned off). Still the GPU is at about 58 degrees Celsius.

I think the temperature was better before I did a BIOS update from A08 to A15. The CPU definitely was. The CPU Temperature rose from about 40 to 50 degrees. (After the BIOS update.) But anyway, the fan is more silent now. Maybe later I will trying some 3D game to try out speed and temperature of GPU.
Before everything sometimes while playing graphics became all garbled. (Think because of hot GPU). The mainboard had been already replaced by a DELL technician because of some heat damage.

---

