---
title: "CompizFusion's SkyDome Background Missing on Nvidia's Nforce card"
date: 2007-10-27
forum: Desktop Effects &amp; Customization
---

### Post by Gustbuntu on 2007-10-27
Hi,
I've read the tricks to get Skydome background pics going but I haven't had any success.

I have Ubuntu 7.10 using the CompizFusion that came with Gutsy.

GeForce4 MX Integrated GPU with 64mb of shared video

I got the latest driver through the use of ENVY.

here's a condensed output of my xvinfo.
```
xvinfo
X-Video Extension version 2.2
screen #0
  Adaptor #0: "NV17 Video Texture"
    maximum XvImage size: 2046 x 2046
  Adaptor #1: "NV05 Video Blitter"
    maximum XvImage size: 2046 x 2046

``` 

It seems the the max value is not 2048 but 2046 instead does anyone know how this change will affect the ratio of background pics?

I can get image caps  using the separate plugin, but even a 1024 x 512 picture wont show up on the  skydome.

I've attached a couple of to show the problem, any help would be appreciated.
Gust

---

