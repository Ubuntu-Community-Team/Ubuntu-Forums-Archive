---
title: "INTREPID Turning on NVIDIA gives me low resolution"
date: 2008-10-31
forum: Desktop Environments
---

### Post by helbent forleder on 2008-10-31
I installed Ubuntu Intrepid Ibex 8.10rc and all went fine. For the first time in many releases the log-in screen resolution looked fine and the default resolution in Gnome was even okay.
Despite all this, as soon as I enabled the NVidia driver under System/Administration/Hardware Drivers (173) logged out and back in, the resolution fell to something like 640x400 (I can't remember now).
I had expected the same available resolutions as without the driver enabled. Both the 'Screen Resolution' utility and 'nvidia x-server congig' only offer the same 2 very low resolutions. Shutting off the driver, things return to the normal state and the resolution is fine again. With the driver off, screen resolutions are all there and can be set through the 'Screen Resolution' utility.
My graphics cards is GF 5200fx. Monitor is LG Flatron 776FM.
After seeing info about EDIDs I ran the command xrandr --verbose
and got this info (with the driver disabled)

```
 brian@Kurczak:~$ xrandr --verbose
Screen 0: minimum 320 x 175, current 1024 x 768, maximum 1152 x 864
default connected 1024x768+0+0 (0x88) normal (normal) 0mm x 0mm
 Identifier: 0x84
 Timestamp: 27660
 Subpixel: no subpixels
 Clones:
 CRTC: 0
 CRTCs: 0
  1152x864 (0x85) 74.6MHz
        h: width 1152 start 0 end 0 total 1152 skew 0 clock 64.8KHz
        v: height 864 start 0 end 0 total 864 clock 75.0Hz
  1152x864 (0x86) 69.7MHz
        h: width 1152 start 0 end 0 total 1152 skew 0 clock 60.5KHz
        v: height 864 start 0 end 0 total 864 clock 70.0Hz
  1152x864 (0x87) 59.7MHz
        h: width 1152 start 0 end 0 total 1152 skew 0 clock 51.8KHz
        v: height 864 start 0 end 0 total 864 clock 60.0Hz
  1024x768 (0x88) 66.8MHz *current
        h: width 1024 start 0 end 0 total 1024 skew 0 clock 65.3KHz
        v: height 768 start 0 end 0 total 768 clock 85.0Hz
  1024x768 (0x89) 59.0MHz
        h: width 1024 start 0 end 0 total 1024 skew 0 clock 57.6KHz
        v: height 768 start 0 end 0 total 768 clock 75.0Hz
  1024x768 (0x8a) 55.1MHz
        h: width 1024 start 0 end 0 total 1024 skew 0 clock 53.8KHz
        v: height 768 start 0 end 0 total 768 clock 70.0Hz
  1024x768 (0x8b) 47.2MHz
        h: width 1024 start 0 end 0 total 1024 skew 0 clock 46.1KHz
        v: height 768 start 0 end 0 total 768 clock 60.0Hz
  1024x768 (0x8c) 68.4MHz
        h: width 1024 start 0 end 0 total 1024 skew 0 clock 66.8KHz
        v: height 768 start 0 end 0 total 768 clock 87.0Hz
  832x624 (0x8d) 38.9MHz
        h: width 832 start 0 end 0 total 832 skew 0 clock 46.8KHz
        v: height 624 start 0 end 0 total 624 clock 75.0Hz
  800x600 (0x8e) 40.8MHz
        h: width 800 start 0 end 0 total 800 skew 0 clock 51.0KHz
        v: height 600 start 0 end 0 total 600 clock 85.0Hz
  800x600 (0x8f) 36.0MHz
        h: width 800 start 0 end 0 total 800 skew 0 clock 45.0KHz
        v: height 600 start 0 end 0 total 600 clock 75.0Hz
  800x600 (0x90) 34.6MHz
        h: width 800 start 0 end 0 total 800 skew 0 clock 43.2KHz
        v: height 600 start 0 end 0 total 600 clock 72.0Hz
  800x600 (0x91) 28.8MHz
        h: width 800 start 0 end 0 total 800 skew 0 clock 36.0KHz
        v: height 600 start 0 end 0 total 600 clock 60.0Hz
  800x600 (0x92) 26.9MHz
        h: width 800 start 0 end 0 total 800 skew 0 clock 33.6KHz
        v: height 600 start 0 end 0 total 600 clock 56.0Hz
  840x525 (0x93) 26.5MHz
        h: width 840 start 0 end 0 total 840 skew 0 clock 31.5KHz
        v: height 525 start 0 end 0 total 525 clock 60.0Hz
  700x525 (0x94) 22.1MHz
        h: width 700 start 0 end 0 total 700 skew 0 clock 31.5KHz
        v: height 525 start 0 end 0 total 525 clock 60.0Hz
  640x512 (0x95) 19.7MHz
        h: width 640 start 0 end 0 total 640 skew 0 clock 30.7KHz
        v: height 512 start 0 end 0 total 512 clock 60.0Hz
  720x450 (0x96) 19.4MHz
        h: width 720 start 0 end 0 total 720 skew 0 clock 27.0KHz
        v: height 450 start 0 end 0 total 450 clock 60.0Hz
  640x480 (0x97) 26.1MHz
        h: width 640 start 0 end 0 total 640 skew 0 clock 40.8KHz
        v: height 480 start 0 end 0 total 480 clock 85.0Hz
  640x480 (0x98) 23.0MHz
        h: width 640 start 0 end 0 total 640 skew 0 clock 36.0KHz
        v: height 480 start 0 end 0 total 480 clock 75.0Hz
  640x480 (0x99) 22.4MHz
        h: width 640 start 0 end 0 total 640 skew 0 clock 35.0KHz
        v: height 480 start 0 end 0 total 480 clock 73.0Hz
  640x480 (0x9a) 20.6MHz
        h: width 640 start 0 end 0 total 640 skew 0 clock 32.2KHz
        v: height 480 start 0 end 0 total 480 clock 67.0Hz
  640x480 (0x9b) 18.4MHz
        h: width 640 start 0 end 0 total 640 skew 0 clock 28.8KHz
        v: height 480 start 0 end 0 total 480 clock 60.0Hz
  720x400 (0x9c) 25.3MHz
        h: width 720 start 0 end 0 total 720 skew 0 clock 35.2KHz
        v: height 400 start 0 end 0 total 400 clock 88.0Hz
  720x400 (0x9d) 20.2MHz
        h: width 720 start 0 end 0 total 720 skew 0 clock 28.0KHz
        v: height 400 start 0 end 0 total 400 clock 70.0Hz
  720x400 (0x9e) 24.5MHz
        h: width 720 start 0 end 0 total 720 skew 0 clock 34.0KHz
        v: height 400 start 0 end 0 total 400 clock 85.0Hz
  680x384 (0x9f) 15.7MHz
        h: width 680 start 0 end 0 total 680 skew 0 clock 23.0KHz
        v: height 384 start 0 end 0 total 384 clock 60.0Hz
  640x400 (0xa0) 21.8MHz
        h: width 640 start 0 end 0 total 640 skew 0 clock 34.0KHz
        v: height 400 start 0 end 0 total 400 clock 85.0Hz
  576x432 (0xa1) 18.7MHz
        h: width 576 start 0 end 0 total 576 skew 0 clock 32.4KHz
        v: height 432 start 0 end 0 total 432 clock 75.0Hz
  576x432 (0xa2) 17.4MHz
        h: width 576 start 0 end 0 total 576 skew 0 clock 30.2KHz
        v: height 432 start 0 end 0 total 432 clock 70.0Hz
  576x432 (0xa3) 14.9MHz
        h: width 576 start 0 end 0 total 576 skew 0 clock 25.9KHz
        v: height 432 start 0 end 0 total 432 clock 60.0Hz
  640x350 (0xa4) 19.0MHz
        h: width 640 start 0 end 0 total 640 skew 0 clock 29.8KHz
        v: height 350 start 0 end 0 total 350 clock 85.0Hz
  512x384 (0xa5) 16.7MHz
        h: width 512 start 0 end 0 total 512 skew 0 clock 32.6KHz
        v: height 384 start 0 end 0 total 384 clock 85.0Hz
  512x384 (0xa6) 14.7MHz
        h: width 512 start 0 end 0 total 512 skew 0 clock 28.8KHz
        v: height 384 start 0 end 0 total 384 clock 75.0Hz
  512x384 (0xa7) 13.8MHz
        h: width 512 start 0 end 0 total 512 skew 0 clock 26.9KHz
        v: height 384 start 0 end 0 total 384 clock 70.0Hz
  512x384 (0xa8) 11.8MHz
        h: width 512 start 0 end 0 total 512 skew 0 clock 23.0KHz
        v: height 384 start 0 end 0 total 384 clock 60.0Hz
  512x384 (0xa9) 17.1MHz
        h: width 512 start 0 end 0 total 512 skew 0 clock 33.4KHz
        v: height 384 start 0 end 0 total 384 clock 87.0Hz
  416x312 (0xaa) 9.7MHz
        h: width 416 start 0 end 0 total 416 skew 0 clock 23.4KHz
        v: height 312 start 0 end 0 total 312 clock 75.0Hz
  400x300 (0xab) 10.2MHz
        h: width 400 start 0 end 0 total 400 skew 0 clock 25.5KHz
        v: height 300 start 0 end 0 total 300 clock 85.0Hz
  400x300 (0xac) 9.0MHz
        h: width 400 start 0 end 0 total 400 skew 0 clock 22.5KHz
        v: height 300 start 0 end 0 total 300 clock 75.0Hz
  400x300 (0xad) 8.6MHz
        h: width 400 start 0 end 0 total 400 skew 0 clock 21.6KHz
        v: height 300 start 0 end 0 total 300 clock 72.0Hz
  400x300 (0xae) 7.2MHz
        h: width 400 start 0 end 0 total 400 skew 0 clock 18.0KHz
        v: height 300 start 0 end 0 total 300 clock 60.0Hz
  400x300 (0xaf) 6.7MHz
        h: width 400 start 0 end 0 total 400 skew 0 clock 16.8KHz
        v: height 300 start 0 end 0 total 300 clock 56.0Hz
  320x240 (0xb0) 6.5MHz
        h: width 320 start 0 end 0 total 320 skew 0 clock 20.4KHz
        v: height 240 start 0 end 0 total 240 clock 85.0Hz
  320x240 (0xb1) 5.8MHz
        h: width 320 start 0 end 0 total 320 skew 0 clock 18.0KHz
        v: height 240 start 0 end 0 total 240 clock 75.0Hz
  320x240 (0xb2) 5.6MHz
        h: width 320 start 0 end 0 total 320 skew 0 clock 17.5KHz
        v: height 240 start 0 end 0 total 240 clock 73.0Hz
  320x240 (0xb3) 4.6MHz
        h: width 320 start 0 end 0 total 320 skew 0 clock 14.4KHz
        v: height 240 start 0 end 0 total 240 clock 60.0Hz
  360x200 (0xb4) 6.1MHz
        h: width 360 start 0 end 0 total 360 skew 0 clock 17.0KHz
        v: height 200 start 0 end 0 total 200 clock 85.0Hz
  320x200 (0xb5) 5.4MHz
        h: width 320 start 0 end 0 total 320 skew 0 clock 17.0KHz
        v: height 200 start 0 end 0 total 200 clock 85.0Hz
  320x175 (0xb6) 4.8MHz
        h: width 320 start 0 end 0 total 320 skew 0 clock 14.9KHz
        v: height 175 start 0 end 0 total 175 clock 85.0Hz

```
Why can't this be something that I can configure easily by myself?

---

### Post by syms on 2008-10-31
As i know Ubuntu 8.10 dont supports nvidia legacy and nvidia glx driver, because nvidia didnt make support for xorg 7.4, this means that proprietary drivers will not work with your video card, and you will not have desktop effects :( . This is nvidia's foult, they were lazy to create support! Luckily, I have ati video card :) In fact if proprietary drivers would not work, you can use open source drivers and effects are working !

---

### Post by helbent forleder on 2008-10-31
I don't really understand. I believe that the driver that I used (173) supports this card. So, I am not sure if what you're saying is correct.
Maybe I'm not getting something though.

---

### Post by evilkastel on 2008-10-31
I'm quite sure syms is wrong. I was running Ibex on propietary drivers, but then I made a fresh install to redo my partitions and now it won't work. My problem is qhen I try to download the driver, the manager crashes.

---

### Post by echostorm on 2008-10-31
> **evilkastel said:**
> I'm quite sure syms is wrong. I was running Ibex on propietary drivers, but then I made a fresh install to redo my partitions and now it won't work. My problem is qhen I try to download the driver, the manager crashes.

I have the same problem, I just made a thread about it, then found yours

---

### Post by helbent forleder on 2008-11-01
Evilkastel: I also didn't have any trouble when I upgraded from Hardy (but to configure everything in Hardy was a pain that I can only equivocate with a dislocated limb). So the long way around would be to install Hardy and upgrade to Intrepid and pray that it works. I am no computer scientist, but I doubt that it would serve you for long (I am guessing that a Kernel update, for example, might send you back to 400x600 city).
I've had trouble on every version since Gutsy, so I've finally just plugged the monitor into the integrated graphics on my motherboard. Much to my surprise it works well enough for the basic compiz effects (not everything, but the cube works and that's the feature I really wanted).
I am wondering if anyone can confirm that ATI cards (has to be AGPx8 or slower) really work trouble free, because they are pretty cheap. Syms says he had no trouble with his.
I can almost believe that he's right about the 173 is a legacy driver - the newest driver 177, doesn't support the 5200fx.:(

---

### Post by azunder on 2008-11-01
> **syms said:**
> As i know Ubuntu 8.10 dont supports nvidia legacy and nvidia glx driver, because nvidia didnt make support for xorg 7.4, this means that proprietary drivers will not work with your video card, and you will not have desktop effects :( . This is nvidia's foult, they were lazy to create support! Luckily, I have ati video card :) In fact if proprietary drivers would not work, you can use open source drivers and effects are working !

What I don't understand is that I downloaded and installed the latest release candidate 5 days ago, the drivers worked fine and my resolution was normal, I was playing computer games under wine perfectly fine.

But today I upgraded to 8.10 fully, and the resolutions and drivers have decided to fail at life.

---

### Post by syms on 2008-11-01
My apologies, this problem is with up to fourth generation geforces, as i see your is fifth

---

### Post by rotary12 on 2008-11-01
every one is having problems with the graphic cards I  tried Kubuntu 8.10, Ubuntu 8.10  about a month (not final) and had the same problems:
Only can get a command prompt
Checking battery state 
can't get my Nvidia card to enable 
now i install 8.10 final release and same problems then i read this: (Ubuntu 8.10 dont supports nvidia legacy and nvidia glx driver, because nvidia didnt make support for xorg 7.4, this means that proprietary drivers will not work) After what Ive seen in the forums its starting to make sense to me. but i could be wrong:(

---

### Post by AaronP_ on 2008-11-01
There's a [beta driver]("http://nvnews.net/vbulletin/showthread.php?t=122139") with support for the kernel and X server shipped in 8.10, but it doesn't look like the packages have been updated yet: [http://packages.ubuntu.com/intrepid/nvidia-glx-96](http://packages.ubuntu.com/intrepid/nvidia-glx-96)

---

### Post by blaze042 on 2008-11-02
I have a somewhat similar issue. I did a fresh install of 8.10 and after the re-boot everything was fine. When adjusting the resolution, the monitor manufacturer was displayed, I set it from 1280x1024 down to 1024x768 and adjusted the refresh rate to 75hz. The settings were applied and all was well. 

Then, I got the alert that there were some new updates (kernel) and performed them. I rebooted the system and now I'm stuck with 800x600 @ 60hz and the system shows "unknown" monitor. This is crazy. That's the highest resolution that I can choose, which just previously I was able to choose up to 1600x1200. At this rate, using the PC is painful. How can I fix it?

Video card as detected by lspci:
VGA compatible controller: nVidia Corporation NV15 [GeForce2 GTS/Pro] (rev a3)

uname -r:
2.6.27-7-generic

---

### Post by helbent forleder on 2008-11-02
So, it looks like Syms was right and sadly my hunch was right too. No old Nvidia cards allowed... or no Kernel updates. Looks like ATI is the way to go. :(

---

### Post by shields on 2009-04-04
Yep. This is an ongoing problem. I am back to 800X600 with no explanation. All I did was restart the computer and now the highest resolution available is 800X600.

And following the suggestions in other threads has been a nightmare. It's resulted in the need for a complete reinstall a few months ago. Who wants to reinstall their OS every few months to fix a video problem that should not exist?

It's very discouraging.

---

