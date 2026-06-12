---
title: "can't run any game on steam, ubuntu 14.04"
date: 2015-05-11
forum: Gaming &amp; Leisure
---

### Post by jimm-garcia on 2015-05-11
so I have a pc that I made to run SteamOS, but the beta isn't that good yet, so I decided to install ubuntu on this one, since it's my favorite distro,
the first thing I did was to install ubuntu 15.04 64 bits, I did it without any problem, I installed steam, installed the drivers of my graphics card and then set up steam to start in bigpicture mode when I turn on my pc, but when I restarted the pc all I got was a black screen and no more,

so I had to reinstall ubuntu, but now 14.04 64bits, I installed Steam once again, installed the libs that steam needed, installed the drivers for my graphics card, but when I run any game after a couple minutes I get a black screen and the only thing I can do is restart the pc, the only game that doesn't do that is Dota 2, but when I try to exit the game it crashes, and the only thing I can do is restart the pc.
here are the specs of my pc
cpu AMD A10 5800k
gpu AMD Radeon R7 250
4gbs Ram kingston
I think that's all the important stuff.

I'm running the drivers from flgrx proprietery

maybe this will help

*-display               
       description: VGA compatible controller
       product: Oland XT [Radeon HD 8670 / R7 250]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:49 memory:c0000000-cfffffff memory:fea00000-fea3ffff ioport:e000(size=256) memory:fea40000-fea5ffff


am I missing some libraries or something? the games I've tried so far are, Metro last light, bioshock infinite, shadow warrior,

---

### Post by R33D3M33R on 2015-05-14
If you can play the games and they crash during playing, this could be a sign of GPU overheating. Try playing with case open if they run better.

---

### Post by jimm-garcia on 2015-05-15
> **R33D3M33R said:**
> If you can play the games and they crash during playing, this could be a sign of GPU overheating. Try playing with case open if they run better.

I don't think so man, I made this a gaming pc, I have 1 front fan, 2 side fans, and a evo 212 as the cpu cooler, I even have a fan controller that shows me the temperature of my cpu and gpu, my pc is always at 23`c and the max that I've seen is 40`c

---

### Post by R33D3M33R on 2015-05-15
Ok, can you try the opensource drivers then? Still black screen? Just properly uninstall (purge) fglrx and reboot.

---

### Post by jimm-garcia on 2015-05-16
for some reason when I use the open source drivers there's no resolution for my 32' screen, the side icons do not appear, cause the screen looks to be zoomed, and it doesn't recognize my graphics card, instead shows the graphics power of my processor

---

