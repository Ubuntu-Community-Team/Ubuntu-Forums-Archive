---
title: "Vostro 1400 w intel graphics, ipw3945 - modem and wireless working HOW-TO"
date: 2008-01-15
forum: Dell  Ubuntu Support
---

### Post by Orion2000za on 2008-01-15
Before you read any further: the actions in this post/thread involves messing with your kernel and could absolutely break your system.

That said, I have finally managed to solve 2 problems I had since first install with my Dell Vostro 1400 notebook: built-in Conexant HDA modem now works and the Intel 3945 ABG wireless is stable.

Also the FN-buttons for brightness control of LCD screen started working. Volume buttons already work but MUTE is not working.

Everything else I have tried works: dvd/cd, wired network, sound etc.

Configuration:
Dell Vostro 1400 w Core2 Duo T7250 Intel, 2Gb RAM
Intel 3945 ABG wireless
Broadcomm wired interface
Intel X3100 graphics (or is it X4100?)

As you can see as much Intel as possible, a conscious choice.
S/W: Kubuntu 7.10 Gutsy
WICD (wicd.sourceforge.net) instead of (K)Networkmanager
Otherwise nothing much outside KDE/Kubuntu standard

Problem from day 1 was modem not working. Tried drivers both from Dell and Conexant with no luck. Sound also not working but fix is simple and found elsewhere in this forum. 

The "core" of the problem seemed to be that the kernel in Gutsy do not "see" the modem (earlier kernels could, I checked via Knoppix Live CD). 

Solution, found after trying to compile ALSA drivers and you name it all to no avail:

1. Replace Gutsy kernel with Hardy kernel 
2. Update alsa-base and alsa-utils to Hardy packages
3. Update gcc compiler to Hardy packages
4. fix sound not working
5. Install Dell-supplied Conexant modem driver

First follow this thread on how to upgrade to Hardy kernel and update gcc compiler:
[http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)

However, having updated the gcc compiler DO NOT remove the "hardy source list" just yet as advised but first do:
```
sudo apt-get install alsa-base
sudo apt-get install alsa-utils
```

then remove the extra hardy source in your sources list as advised in the thread.

Reboot. Note that, at least for me, the wireless interface changed from "eth1" to "wlan0", had to change that in wicd to get it to work. All problems with "yo-yo"-behaviour from ipw3945 is gone, it now keeps the connection stable. Disadvantage: the iw-LED at the front does not work.

Sound is gone, to get it back:
```
sudo nano /etc/modprobe.d/alsa-base

```
add this line at the end:
```
options snd-hda-intel model=5stack
```
NOTE: not 3stack as in other threads, then the modem goes missing again.

Reboot (maybe not necessary but to check that sound is back)

Then download conexant modem drivers from Dell here:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/New_Conexant_Modem_Driver](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/New_Conexant_Modem_Driver)

All I needed to do was to click on it in Konqueror (Nautilius for Ubuntu users I guess) and it installed nicely. Modem found at /dev/ttySHSF0 and seems to be working as expected.

I guess this might give problems with updates until Hardy is released but for me it is a better solution than to wait for Hardy to get things working. I will just not update until then...

:lolflag: Sinclair

---

