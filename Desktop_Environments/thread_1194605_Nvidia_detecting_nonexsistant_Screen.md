---
title: "Nvidia detecting nonexsistant Screen"
date: 2009-06-22
forum: Desktop Environments
---

### Post by Heldrex on 2009-06-22
For some reason my dual nvidia 8800's with sli are detecting a screen titled "CRT-0" with a 640x480 resolution. No such screen exists. This wouldn't be an issue if my mouse didn't get glitchy on the side of the screen by thinking another screen was there. I tried to disable it through my NVIDIA setting and it said I needed an xserver restart. I ran 
```
sudo /etc/init.d/gdm stop
``` then
```
sudo /etc/init.d/gdm start
```But the screen is still there. 
I tried saving this to my X Configurationg file and got the error: "unable to remove old X config backup file '/etc/X11/xorg.conf.backup'." How can I get rid of this screen, and what is the correct method?

Edit: Maybe I damaged my xconfig by following [this]("http://ubuntuforums.org/showthread.php?t=1125400&highlight=nvidia+185") when I was having my issue with nvidia drivers.

---

### Post by Heldrex on 2009-06-22
After some exploring I realized that I have one GPU per each screen. I'm running dual nvidia 8800's with sli and they should be working together.

---

