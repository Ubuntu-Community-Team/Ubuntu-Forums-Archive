---
title: "Dell E1505n Screen Resolution"
date: 2007-07-31
forum: Dell  Ubuntu Support
---

### Post by p252 on 2007-07-31
I just got my new Dell Inspiron E1505n Ubuntu Laptop today. Turned it on and was surprised because I was expecting everything to work out of box, but it's not. First was Ubuntu didn't see the sound card but that was resolved with a reboot. Wireless card does work perfect out  of box (hurray!!) and the system is fast/responsive. My only other problem is the screen resolution. It is at 1024 x 768 when I know it is suppose to be 1280 x 800 widescreen. How can I get the proper resolution?

Thanks for all your help

---

### Post by Rocket2DMn on 2007-07-31
This is a common problem, you just need to reconfigure Xorg:
```
sudo dpkg-reconfigure xserver-xorg
```
When you get to the resolution page, use TAB to move around and SPACEBAR to select your monitor's max resolution and everything less.  When you are finished, do CTRL+ALT+BACKSPACE to restart the Xserver.  At this point you should be able to select 1280x800 under Preferences->Screen Resolution.

---

### Post by p252 on 2007-08-01
Ok, that didn't work for me, but at the same time I know next to nothing of x.org or how to configure my monitor so I'm not sure if I answered all the questions it asked me in the right way. . . What should I do?

---

### Post by Rocket2DMn on 2007-08-01
What brand and model video card do you have?  What driver did you enable in the configuration?

---

### Post by jongkind on 2007-08-01
You likely have the Intel integrated chip which uses by default the i810 driver, which does not suport 1280x800 resolution. You can correct this by installing the i915 driver. 
You can follow the instructions in the Wiki.

[https://help.ubuntu.com/community/i915Driver]("https://help.ubuntu.com/community/i915Driver")

---

### Post by ratioswitch on 2007-08-01
Not that this will help, but my E1505n worked, out-of-the-box, with Ubuntu FF 7.0.4 and 1280x800. I did need to do some messing around with preferences and restarts to get Desktop Effects to work, but all is good and has been.

---

### Post by walkerk on 2007-08-01
This will allow 1280x800:
```
sudo apt-get install xserver-xorg-video-intel
```

Reboot or simply restart X.

---

### Post by p252 on 2007-08-01
Sorry it took so long for me to post back, I had to work all night. Anyway's, I wish mine had worked out-of-box but oh well. the card is Intel Integrated Graphics Media Accelerator 950 GM. The only option I had in the x config was i810. I will give all these recommendations a try and post back with the results. Thanks for all your help!

---

### Post by walkerk on 2007-08-01
> **walkerk said:**
> This will allow 1280x800:
```
sudo apt-get install xserver-xorg-video-intel
```

Reboot or simply restart X.

Do this first. It will replace the i810 driver with the Intel driver fo your onboard Intel video 950GM

---

### Post by p252 on 2007-08-01
Installing the xserver-xorg-video-intel worked perfect!! Thank you so much for all the help!! Just made my day

---

### Post by walkerk on 2007-08-01
> **p252 said:**
> Installing the xserver-xorg-video-intel worked perfect!! Thank you so much for all the help!! Just made my day

:)

---

