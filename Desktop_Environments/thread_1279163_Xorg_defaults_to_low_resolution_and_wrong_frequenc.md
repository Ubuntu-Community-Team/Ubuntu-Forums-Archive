---
title: "Xorg defaults to low resolution and wrong frequency"
date: 2009-09-30
forum: Desktop Environments
---

### Post by Jordanwb on 2009-09-30
I'm trying to get Ubuntu 9.04 amd64 working on a computer I put together. For the most part it works. Whenever Xorg starts up, it ignores the xorg.conf file I made: [http://pastebin.com/f2c1d5a06](http://pastebin.com/f2c1d5a06)

The resolution that Xorg defaults to is 800X600 @ 65 Hz instead of 1440X900 @ 60Hz.

I've installed the binary nvidia driver and this problem occurs. It also occurs with the nv driver. The video chip is an onboard GeForce 6150 LE. I've looked at the HowTo for Nvidia binary drivers.

When xorg initially starts up, it's at the correct resolution and frequency, but then it changes to 800x600 @ 65 Hz.

[In Henry Blake fashion]Why me? Why is it always me?[/] When I went to System->Preferneces->Display it asked me if I wanted to use NVidia's graphics tool. I decided to click on "No" for fun and got the default generic graphics config. I reset it to 1440x900 @ 60Hz, restarted Xorg and it works fine.

---

