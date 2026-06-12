---
title: "Compiz Fusion broken?"
date: 2010-01-24
forum: Desktop Environments
---

### Post by Eman64 on 2010-01-24
So I used to have fusion working just great. Then Karmic came out, and after my upgrade, I had a ton of problems with things like sound and video. Eventually, my drivers got upgraded to nvidia 195. After this, my desktop effects stopped working.

```
compiz-check
```

```
Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G73 [GeForce 7300 GT] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...
(nvidia-settings:4518): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(nvidia-settings:4518): atk-bridge-WARNING **: IOR not set.

(nvidia-settings:4518): atk-bridge-WARNING **: Could not locate registry
           [ OK ]

```

Anyone want to tell me why I can't run compiz if I get all oks? Is it something to do with my "atk-bridge-WARNING"s?

Thanks

---

### Post by llawwehttam on 2010-01-24
Have you tried re-installing the drivers. That may fix it.

---

### Post by Eman64 on 2010-01-24
Already tried that today. I just fixed the atk thing, so now compiz-check gives me this:

```
Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G73 [GeForce 7300 GT] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


```

---

### Post by llawwehttam on 2010-01-24
Right click on your desktop. Change background >visual effects. then enable them or set to custom if you have a custom setup.

---

### Post by Eman64 on 2010-01-24
Still getting a pop-up window declaring "Desktop effects could not be enabled"

---

### Post by lidex on 2010-01-24
Here is some info for configuring compiz:
[https://help.ubuntu.com/community/CompositeManager/CompizFusion]("https://help.ubuntu.com/community/CompositeManager/CompizFusion")

It sounds like your problem right now is a driver issue. Do you have jockey ("hardware drivers") installed and if so, what does it tell you? What driver do you have installed? Is it vdpau? Did you get it from ppa repository or download from nvidia? Remove any other nvidia drivers and run this command in a terminal:
```
sudo nvidia-xconfig
``` and reboot.

---

### Post by lidex on 2010-01-24
Also have a look here:
[http://www.krishnamoorthy.in/2009/05/ubuntu-904-nvidia-7300-gt-widescreen.html]("http://www.krishnamoorthy.in/2009/05/ubuntu-904-nvidia-7300-gt-widescreen.html")
Scroll down for Karmic.

You may need to roll back the driver.

---

### Post by Eman64 on 2010-01-31
Sorry for the late post. I tried both of your suggestions, lidex, and neither worked. Thanks anyway.

---

### Post by lidex on 2010-01-31
Did you try rolling back the driver to a previous version that worked?

---

### Post by Eman64 on 2010-02-02
Yup. I think I tried 180 and 173. Did not change anything but my resolution.

---

