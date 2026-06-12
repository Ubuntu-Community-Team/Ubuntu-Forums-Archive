---
title: "nvidia performance?"
date: 2017-05-25
forum: Gaming &amp; Leisure
---

### Post by kurja on 2017-05-25
I'm trying to figure out what would cause poor performance in the game Alien: isolation, I'm seeing only 30-50 fps in the game - with lowered resolution and all graphics settings either 'low' or 'off'. Just turning on antialiasing drops the frame rate to the twenties.  For comparison in CS: Source I have ~250fps at 1920x1080 resolution and graphics settings at high detail. I searched for performance tests of this game in Linux/SteamOS and it looks like it's supposed to run just fine, so maybe something's wrong at my end..? Or do I just lack the hardware to run at higher settings/higher fps (not really experienced with modern gaming)?

I have an nvidia gtx560 ti top & nvidia driver 375.66, while the game is running none of my cpu cores max out (viewing with ubuntu system monitor) and there are a couple gigs of unused ram at all times. Ubuntu version 14.04. Thoughts?

---

### Post by mastablasta on 2017-05-25
perhaps the drivers you are using are not optimised for this game. is it possible to upgrade them?

nvidia is known fo rthei optimisaitons for specific games. if they did it well the game runs well, if not, the game runs bad.

---

### Post by kurja on 2017-05-25
I found this: [http://support.feralinteractive.com/docs/en/alienisolation/latest/linux/faqs/#i_linux_graphics_drivers](http://support.feralinteractive.com/docs/en/alienisolation/latest/linux/faqs/#i_linux_graphics_drivers)

Since I have the gtx560, which I believe is "5xx series", that might be the problem - if they're stating that "6xx series" cards are supported I would suppose they're using some feature on those cards to speed things up.

---

### Post by oldrocker99 on 2017-05-25
Try thnis:```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-831
reboot
```

This will install the latest nVidia drivers. The reboot is necessary to boot with them enabled. The 5xx series is certainly supported by the drivers. The Nouveau driver, which is installed by default, is inferior to nVidia's drivers. With ATI cards, it's the opposite. The open source drivers are far superior to ATI's drivers. Go figure.

Good luck!

---

### Post by kurja on 2017-05-25
> **oldrocker99 said:**
> Try thnis:```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-138
reboot
```

This will install the latest nVidia drivers. The reboot is necessary to boot with them enabled. The 5xx series is certainly supported by the drivers. The Nouveau driver, which is installed by default, is inferior to nVidia's drivers. With ATI cards, it's the opposite. The open source drivers are far superior to ATI's drivers. Go figure.

Good luck!
nvidia-138?? Surely that is not the latest driver? Current long-lasting branch being 375, afaik. Anyhow, I obviously have the proprietary driver installed, as I said so in the first post.

---

### Post by oldrocker99 on 2017-05-26
> **kurja said:**
> nvidia-138?? Surely that is not the latest driver? Current long-lasting branch being 375, afaik. Anyhow, I obviously have the proprietary driver installed, as I said so in the first post.

OOPS! I meant nvidia-381[-X

I edited my erroneous post...

---

### Post by oldfred on 2017-05-26
Different games all have different results in comparisons.


 MSI GeForce GT 1030: A $70 Passively-Cooled Graphics Card, Decent With OpenGL/Vulkan/OpenCL/VDPAU
Compare  integrated HD Graphics 630, other nVidia & Radeon on i7-7700K box running Ubuntu 17.04 x86_64
[http://www.phoronix.com/scan.php?page=article&item=nvidia-geforce-1030&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia-geforce-1030&num=1) 
   Mesa 17.1-dev vs. AMDGPU-PRO 16.60 vs. NVIDIA 378 Linux Gaming Tests
[http://www.phoronix.com/scan.php?page=article&item=mesa171-pro60-nvidia&num=1](http://www.phoronix.com/scan.php?page=article&item=mesa171-pro60-nvidia&num=1)
AMDGPU/RadeonSI Linux 4.10 + Mesa 17.1-dev vs. NVIDIA 378.09 Performance
[http://www.phoronix.com/scan.php?page=article&item=nvidia-378-amdgpu&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia-378-amdgpu&num=1)

---

### Post by kurja on 2017-05-27
An observation: increasing the resolution from what the game auto-selected to native 1920x1080 had no detrimental effect to the frame rate, if anything it increased slightly. Turning the detail level, texture filtering etc from off to high had hardly any impact either. Only blurring effects obviously decreased the frame rate.

This is rather curious. What could be the limiting factor?

---

### Post by efflandt on 2017-05-28
I noticed that when I was trying game recording with OBS (on my 7 yr old i5 650) it would do much better recording a 720p window than 1080p full screen. But when I tried to set my display to 720p full screen, it still dropped too many frames and my HDTV still said it was receiving a 1080p signal. So I guess when I dropped the resolution full screen, the Nvidia card was up converting to native resolution and the recording was still trying to record and compress 1080p. SimpleScreenRecorder does a fine job of recording 1080p on my old PC, but file sizes are huge (uncompressed) and would need post processing compression to reasonable file size.

So maybe reducing the resolution actually added processing to up convert to your native resolution. That is something you may not be aware of even if your screen supports the lower resolution. Maybe graphics drivers try to match the native resolution anyway.

---

