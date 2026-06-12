---
title: "GX280 Video Performance"
date: 2007-08-25
forum: Dell  Ubuntu Support
---

### Post by tekchip on 2007-08-25
I have Edgy installed and rock'n on my GX280. Everything seems to work fine for the most part. I am having some issue with the performance on the video side. I know currently that I'm running under vesa drivers for the video which I'm sure is the reason for the performance issue but I can't seem to find any specific drivers/software for the integrated intel stuff that might improve performance. I can't even watch a divx video in full screen with out the frame rate dropping to 10fps or so. Just did some more research and found that the GX280 is supposed to have an i915 graphics adapter and it's only showing as an i910 currently. Any help or suggestions would be greatly appreciated. Thanks!

---

### Post by angryfirelord on 2007-08-25
```
sudo apt-get install xserver-xorg-video-intel
```
```
sudo dpkg-reconfigure xserver-xorg
```
Select intel as your driver. The defaults will work fine unless you know what you are doing.

---

### Post by tekchip on 2007-08-29
Thanks!

---

