---
title: "Dell D600 monitor problem"
date: 2012-08-10
forum: Desktop Environments
---

### Post by wquatan on 2012-08-10
I installed Xubuntu 12.04 on my Dell D600. On the Dell site I see in the specs

```
**Maximum resolutions**
1024 x 768 at 16.8 million colors (XGA);
1400 x 1050 at 16.8 million colors (SXGA+)
```

and

```
**_Video_** 
**Video type**
64-bit hardware accelerated
**Data bus**
4X AGP
**Video controller**
ATI Mobility RADEON 9000
**Video memory**
32 MB
**LCD interface**
LVDS
**TV support**
NTSC or PAL in S-video and composite modes
```

However, for both the LCD and the external monitor I only can select a max of 1024 x 768 in Display / Screen settings (which is ok for the LCD)

One can imagine that everything looks huuuge on a 26inch !

I can't find a way to have the higher resolutions despite I'm sure I used them before on the same D600 with WinXP

What can I do (in the knowledge that I'm not Linux-expert) ?

---

### Post by wquatan on 2012-08-20
No one ?

---

### Post by vandorjw on 2012-08-21
Hey whats up,

I'm going through all unanswered posts, and see if I can solve them. 

By Dell D600, you mean Dell Latitude D600 right?
If this is right, that means that you have and ATI video card, an older one.

Video ::: Video Controller - ATI® MOBILITY RADEON 9000; Video Memory - 32MB DDR SDRAM; Video Type - 64-bit
hard-ware accelerated, 4X AGP support

In my machine, I have the radeon 9250, so I hope the radeon 9000 is also supported.

To check if the proper "Driver is loaded" can you run to command,
```
 
lsmod | grep radeon

```

> 
basement@Presario-6350CA:~$ lsmod | grep radeon
radeon                737789  2 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197692  4 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon


is what what you should see, if not:

please do this:

```

sudo apt-get install xserver-xorg-video-radeon

```

```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf-backup

```

restart your machine.

if you are running ubuntu 12.10, hit the windows start key when you have restarted and are logged in, and type "displays" and hit enter. You should now be able to set your resolution to whatever it was supposed to be.

Let me know if this didn't work.

Cheers - cc7

**_EDIT: <----- arandr is what you need i think_**

If you do have proper drivers installed, and driver support isn't the problem, then I suggest you install arandr

It will help you configure your external monitor.

---

