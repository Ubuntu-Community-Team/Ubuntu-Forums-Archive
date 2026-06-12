---
title: "problems with tvtime"
date: 2005-11-14
forum: Desktop Environments
---

### Post by pclancy on 2005-11-14
I have a KWORLD 883 tv-tuner, and I can't quite get anything working with tvtime.  I can't tune to any channels, because the card isn't being recognized.  tvtime has some information on fixing this for bttv and cx88 modules, but I'm pretty new to linux and I wasn't able to do it.  I believe that all I have to do is tell the module which card and tuner I need to use.  It gives an example of how to update the bttv driver, but I'm having trouble with the cs88 driver (I think).  

When I run dmesg it used to say something about cs88 not finding the driver and that it needed to know which card it was.  I'm using the KWORLD 883, so that is #16.  I tried *modprobe bttv card=16* with no luck, so then I tried to guess a tuner (I guessed #0).  Now it appears that I have screwed something up, and when I run dmesg I get this:

```
etkeycodes e02a <keycode>' to make it known.
[4303622.145000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303622.145000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303622.239000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303622.239000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303622.349000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303622.349000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303622.438000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303622.438000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303622.772000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303622.772000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303622.869000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303622.869000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303623.181000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303623.181000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303623.266000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303623.266000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303623.709000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303623.709000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303623.798000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303623.798000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303623.889000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303623.889000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303623.970000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303623.970000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303624.054000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303624.054000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303624.121000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303624.121000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303624.475000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303624.475000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303624.581000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303624.581000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303624.661000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303624.661000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303624.762000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303624.762000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303625.118000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303625.118000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303625.183000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303625.183000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303625.277000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303625.277000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303625.344000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303625.344000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303625.513000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303625.513000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303625.580000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303625.580000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303625.640000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303625.640000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303625.705000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303625.705000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303625.768000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303625.768000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303625.852000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303625.852000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303625.907000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303625.907000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303625.980000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303625.980000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303663.778000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303663.778000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303664.289000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303664.289000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303664.585000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303664.585000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303664.682000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303664.682000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303790.701000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303790.701000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303790.790000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303790.790000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303790.821000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303790.821000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303790.877000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303790.877000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303790.946000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303790.946000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303790.999000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303790.999000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303791.183000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303791.183000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303791.242000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303791.242000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303791.305000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303791.305000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303791.358000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303791.358000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303791.429000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303791.429000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303791.491000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303791.491000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303791.650000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303791.650000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303791.721000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303791.721000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303792.077000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303792.077000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303792.183000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303792.183000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303794.230000] bttv: driver version 0.9.15 loaded
[4303794.230000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[4303827.447000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303827.447000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303827.520000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303827.520000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303888.230000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303888.230000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303888.351000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303888.351000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303889.144000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303889.144000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303889.260000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303889.260000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303889.772000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303889.772000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303889.889000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303889.889000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303893.284000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303893.284000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303893.425000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303893.425000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303947.626000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303947.626000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303947.717000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303947.717000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303984.767000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303984.767000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303984.814000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303984.814000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303984.819000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303984.819000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303984.865000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303984.865000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303985.083000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303985.083000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303985.257000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303985.257000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303985.863000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303985.863000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303985.999000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303985.999000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303986.630000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303986.630000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303986.732000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303986.732000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303986.828000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303986.828000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303986.942000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303986.942000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303988.407000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303988.407000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303988.528000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303988.528000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4304001.991000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4304001.991000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4304002.086000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4304002.086000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4304179.134000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4304179.134000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4304179.417000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4304179.417000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4304179.508000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4304179.508000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4304179.588000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4304179.588000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4304484.599000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4304484.599000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4304484.679000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4304484.679000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4304534.016000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4304534.016000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4304534.105000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4304534.105000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4304642.432000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4304642.432000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4304642.772000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4304642.772000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4304642.975000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4304642.975000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4304643.083000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4304643.083000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4304668.313000] bttv: driver version 0.9.15 loaded
[4304668.313000] bttv: using 8 buffers with 2080k (520 pages) each for capture

```

Any ideas/suggestions?

---

### Post by oskude on 2005-11-14
hi,

my card was regonized correctly (fbas/s-video input worked), but the "tuner" was not the right one, so i couldnt scan any channels...

i then looked what "card" and "tuner" my miroPCTV is by looking:
[http://www.bttv-gallery.de/](http://www.bttv-gallery.de/) (warning, HUGE page)

then looked the number for my "card" and "tuner"
[http://www.linuxtv.org/v4lwiki/index.php/Cardlist.BTTV](http://www.linuxtv.org/v4lwiki/index.php/Cardlist.BTTV)
[http://www.linuxtv.org/v4lwiki/index.php/Tuners](http://www.linuxtv.org/v4lwiki/index.php/Tuners)

and restarted bttv with right values, for my miroPCTV it looked like this
```
sudo rmmod bttv
sudo rmmod tuner
sudo modprobe bttv card=1 tuner=0
```

but, i dont know if your card is supported by bttv.

cheers
osku[de]

---

### Post by pclancy on 2005-11-14
My card is not supported by bttv.  How do I disable the bttv driver, and enable the cx88 driver?  Also, looking through that list of cards it says this for mine:

> Kworld V-Stream Xpert TV PVR-883

issue date: 2004/3/25
pcb: KW88A_LP Ver:C
tuner: NTSC
connectors: FM,TV, AV-out (8pin fanout: cvid.,audio-L, audio-R, line out), remote
chip: cx23883-19
Here's the lspci -vv for it:
01:06.0 Multimedia video controller: Conexant Winfast TV2000 XP (rev 05)
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+


Does that mean that my tuner is any NTSC tuner, or is there a generic NTSC?  

Thanks for the help.

---

### Post by dc2447 on 2005-11-14
Hope[ this thread helps](http://www.ubuntuforums.org/showthread.php?t=47479)

---

### Post by pclancy on 2005-11-14
I've got it almost completely working.  I'm missing a few channels, but I think I just need to reposition/amplify the antenna I'm using.  As it turns out I was very close to doing what I wanted to before, but I didn't realize that there were two cx88 modules: cx8800 and cx88xx.  So, I scanned through the tuners, and I get the best results using: 
> tuner=2 - Philips NTSC (FI1236,FM1236 and compatibles)

For future reference these are the commands I used:
```

rmmod cx8800
rmmod cx88xx
rmmod bttv
modprobe cx88xx card=16 tuner=2
modprobe cx8800
modprobe bttv
```

Thanks for all of the help!

---

### Post by Akli on 2006-04-01
My card works only with xawtv (but without the sound), I want it to work with tvtime,
I tried to

Pinnacle/Miro DC30+:
* Zoran zr36067 PCI controller
* Zoran zr36050 MJPEG codec
* Zoran zr36016 Video Front End
* Micronas vpx3225d/vpx3220a/vpx3216b TV decoder
* Analog Devices adv7176 TV encoder
Drivers to use: videodev, i2c-core, i2c-algo-bit,
videocodec, vpx3220/vpx3224, adv7175, zr36050, zr36015, zoran
Inputs: Composite, S-video and Internal
Norms: PAL, SECAM (768x576 @ 25 fps), NTSC (640x480 @ 29.97 fps)
Card number: 4

Note: No module for the mse3000 is available yet
Note: No module for the vpx3224 is available yet
Note: use encoder=X or decoder=X for non-default i2c chips (see i2c-id.h)

---

