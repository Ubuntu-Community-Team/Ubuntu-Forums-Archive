---
title: "Ubuntu 22.04 and xrandr to solve dual monitor problem"
date: 2022-07-01
forum: Desktop Environments
---

### Post by ckurz7000 on 2022-07-01
Hi y'all! I'm ready to throw in the towel with this obnoxious problem. I've managed to solve this previously (I think on Ubuntu 18.x with the same hardware) but now I'm stomped.

The problem is the display settings on my external monitor (1920x1280) connected via HDMI to my Dell Alienware (HD graphics 530 and NVIDIA 980m) with internal 4k screen (3840x2160). I'm running Ubuntu 20.04 and have tried the nouveau driver as well as the proprietary nvidia-510 driver to resolve the issue.
I have the external monitor to the left of the laptop monitor. First, I tried the display utility with and without fractional scaling. Didn't work. Without fractional scaling, scaling set to 200%, the laptop monitor looks OK but the image on the external one looks 2x too big. So tried fractional scaling, which allows a per-monitor setting. Set external screen to 100% and internal to 200%. Result was that the external screen didn't look any smaller and the cursor got out of sync on the external screen. Also, there seemed to be a "void" between the two screens. However, the placement of the monitors shown in the display utility seemed just like I wanted (two equal sized screens next to each other).
Then I tried xrandr with these options (and a lot of variations of these):

```
$ xrandr --fb7680x2160 \
--output HDMI-1-0 --scale 2x2 --pos 0x0 --mode 1920x1080 \
--output eDP-1 --scale 1x1 --right-of HDMI-1-0 --mode 3840x2160
```

Things didn't get any better. And before you tell me to ditch x11 and go the wayland route -- been there, done that. Wasn't able to get a suitable result either.
Now, I'd simply chalk it up to incompatibility between my nvidia and ubuntu but a few months ago, also under 20.04, same monitors, I was able to have it all work smoothly using xrandr. But for the life of me, I don't seem to be able to recreate this anymore.
Any of the experts have some piece of advice?
Thanks y'all for your time and bandwidth!

---

