---
title: "Loading screen enlarged"
date: 2010-08-03
forum: Desktop Environments
---

### Post by JonasDK on 2010-08-03
Hello everyone

I have Ubuntu 10.04, how big should the loading screen be? The purple one with white letters and the five white loading dots? 

Because I have booted from a USB stick to try it out via Live USB (I already have 10.04 installed, but I had to check something on the USB) and the loading screen there was that purple loading screen but with the white letters MUCH smaller then I have on my normal loading screen (when I boot from my harddrive). When I boot from my harddrive the bootscreen looks enlarged and very pixelated. It also has no glow around it and is quite ugly. My resolution is 1920x1080. I think it should be that small as the bootscreen from USB.

Is this normal? Because it looks kinda ugly. I can take a picture of it to make it more clear if it isn't. :)

Thanks,
Jonas

---

### Post by Yuri sss on 2010-08-03
> **JonasDK said:**
> I have Ubuntu 10.04, how big should the loading screen be? The purple one with white letters and the five white loading dots? 

Because I have booted from a USB stick to try it out via Live USB (I already have 10.04 installed, but I had to check something on the USB) and the loading screen there was that purple loading screen but with the white letters MUCH smaller then I have on my normal loading screen (when I boot from my harddrive). When I boot from my harddrive the bootscreen looks enlarged and very pixelated. It also has no glow around it and is quite ugly. My resolution is 1920x1080. I think it should be that small as the bootscreen from USB.

Is this normal? Because it looks kinda ugly. I can take a picture of it to make it more clear if it isn't. :)

Hi Jonas,
this boot screen issue is quite common. Here's a guide on how to fix the ugly, low-resolution boot screen:
[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

I'm using 1920x1200 and have set the boot screen to 1600x1200. Most cards don't have Vesa framebuffer support for widescreen resolutions, so you'll probably have to use a 4:3 resolution that is no higher than your actual resolution (1080 pixels), e.g. 1400x1050.

---

### Post by JonasDK on 2010-08-04
It's fixed.
Thank you very much!! :D

---

