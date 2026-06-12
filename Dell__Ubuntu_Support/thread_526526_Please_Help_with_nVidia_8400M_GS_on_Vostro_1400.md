---
title: "Please Help with nVidia 8400M GS on Vostro 1400"
date: 2007-08-15
forum: Dell  Ubuntu Support
---

### Post by plehman on 2007-08-15
Hi All,

I've recently bought the Vostro 1400 with the following specs:

1.6 Core2Duo
1GB RAM
nVidia GeForce 8400M GS w/ 128MB
Intel HDA sound
DVD-Burner
Bluetooth
Intel wifi

I've been reading through alot of the threads on this board, and was able to get Ubuntu 7.04 installed on the machine from the regular installation CD without much issue.  I've been able to get the DVD drive to recognize CDs (thanks speckr), and the wi-fi seems to work fine.

My real problem is with the video.  I'm stuck right now using the "vesa" driver at 1024 x 768, and would love to get the correct driver working at 1280 x 800.  I should also  note that the LCD gets recognized as a "Generic" monitor, and I'm not 100% on whether that's correct or not.

Anyway, like I've said, I've searched through several of the threads that indicate how someone got the nVidia drivers installed, and I seem to have tried most if not all of them.  The closest I got was to get X starting up OK, but then when I open a window, there are no title bars, and the terminal windows I try and open are just blank windows with no text anywhere.  Eventually, the video seems to wig out, so something isn't right...

My real hope is that someone with a machine  with similar specs can post the steps they took (as explicit as possible) from a clean install to get the nVidia drivers working.  After this is done, I hope to tackle the sound and suspend and hibernate.

Any help is greatly appreciated.

---

### Post by saru411 on 2007-08-15
i just received my vostro 1500 with the same specs as yours...im about to install ubuntu on it also. normally you can system>administration>restricted drivers and install the nvidia driver that way. i will let you know more in about an hour

---

### Post by dougfractal on 2007-08-15
I don't normally recommend envy as it can break upgrading, but you need the latest driver
> NVIDIA Linux Display Driver Release 100.14.09
Release Highlights

    * Adds support for new GPUs: GeForce 8600 GTS, GeForce 8600 GT, GeForce 8600M GT, GeForce 8600M GS, GeForce 8500 GT, GeForce 8400 GS, GeForce 8400M GT, GeForce 8400M GS, GeForce 8400M G, GeForce 8300 GS, Quadro FX 1600M, Quadro FX 570M, Quadro FX 360M, Quadro NVS 320M, 

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu7_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu7_all.deb)

---

### Post by aldenhg on 2007-08-16
Use Envy! I can't say it enough. If you've got a relatively fresh install it's the only way to go, especially when other methods have failed you. It can be had lower down on the following page.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by plehman on 2007-08-16
Thanks.  Envy seemed to work.  At least, my xorg.conf is indicating the driver is "nvidia" instead of "vesa".  I have a further question on this, though, and that is getting the display to 1280 x 800 instead of the default 1024 x 768.  Can I just add "1280 x 800" to the other resolution choices in my xorg.conf or do I need to couple that with a change to the "Monitor" section as well?  Currently, the "Monitor" section shows:

Section "Monitor"
    Identifier    "Generic Monitor"
    HorizSync    28.0 - 51.0
    VertRefresh    43.0 - 60.0
    Option    "DPMS"
EndSection

Is that correct for the 14.1" lcds in the Vostros?

Again, thanks for your help.

---

### Post by dougfractal on 2007-08-16
> Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	31.5-80
	Vertrefresh	56-85
EndSection


and >  just add "1280 x 800" to the other resolution choices in my xorg.conf

---

### Post by plehman on 2007-08-16
Awesome.  Thank you all so much.  The altered frequencies really does the trick in sharpening up the display.

---

