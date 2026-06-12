---
title: "Xorg + KDE + NVIDIA + Sony SXRD XBR1 TV"
date: 2006-04-22
forum: Desktop Environments
---

### Post by qpalzm on 2006-04-22
Is anyone using Xorg with a Sony XBR1 HDTV?

My hardware:
Nvidia 5500FX
DVI to HDMI Cable
Sony KDS-R50 XBR1

Everything seems to be working except for one huge problem: Overscan.  If anyone has this tv and is using Xorg through HDMI, your config file would be most helpful.  

Is there a way to set an "underscan" value?  The windows NVIDIA driver has sliders....wish the linux driver had them ](*,)

---

### Post by ltmon on 2006-04-23
From memory:
```

sudo apt-get install nvidia-settings

```
should install a nice nvidia setup utililty with over/underscan settings available.

See this thread: [http://www.gossamer-threads.com/lists/mythtv/users/117623](http://www.gossamer-threads.com/lists/mythtv/users/117623)

Cheers,

L.

---

### Post by MalcomM on 2007-10-25
Hi,

This is the modeline which I'm using for a Sony KDS60A2020 (non-XBR model):

Modeline "1840x1016" 148.5 1840 1966 2004 2206 1016 1052 1057 1125 +hsync +vsync

It works pretty well, as there is no major overscan as there normally is when the resolution is 1920x1080.  Also, there is a 1:1 pixel mapping :)

Hope it helps,
Mal

---

### Post by LoSt180 on 2007-11-14
I have the same TV and need some help. I can't get nvidia-settings or Ubuntu to recognize anything past 720p (1280x720) resolution. I've tweaked it down to 1216x684 to get rid of overscan, has anyone gotten this TV to accept a 1920x1080 signal? 

My Setup:
Nvidia 7600 GS
DVI to HDMI cable
Sony KDS-R50XBR1 TV

I've tried the modeline posted above, but it always goes back to the 1216x684 setting. I've tried the UseEDID=false option, but then it goes to 800x600. 

If someone has it working, can  you post your xorg.conf file? plus what ever else you had to do.. Thanks

My xorg.conf file:

edit: got a working modeline for this tv. see post bellow

---

### Post by xaoslaad on 2008-01-10
MalcomM, I could kiss you. Perfect Modeline for this TV. I am using Fedora 8, with an oboard nvidia 7150, and this works great. I had to do some additional tweaking to the xorg.conf to get it to work just perfect, but this gave me a HUGE headstart.

Thank you for posting it!

---

### Post by MalcomM on 2008-01-25
No worries, glad I could help :)

---

### Post by LoSt180 on 2008-03-06
Finally got a working mode for the SXRD XBR1 TV. The Nvidia Driver from Ubuntu is an older driver (100.xx IIRC). I had to use an application called "Envy" to download and install the latest Nvidia driver. Once version 169.09 was installed, Nvidia immediately recognized my TV as 1080i. I tweaked Malcom's modeline to work, it fits pretty well. There's a slight black bar at the top, if I could shift the screen up about 3-5 pixels it would fit perfectly.

Modeline  	   "1840x1016" 74.2 1840 1966 2004 2206 1016 1052 1057 1125 +hsync +vsync interlace
    ModeLine       "1920x1080" 74.2 1920 2008 2052 2200 1080 1088 1091 1121 +hsync +vsync interlace

I still can't get it to accept a 1080p @60 signal. On a  search for a zone-less DVD player, I found that Helios had a warning that 1080p didn't work on some Sony TVs. Here's their reply when I asked specifically what the problem was:
> h4000 to Sony KDS-R50XBR1

Hi Luis,

We haven't tested KDS-R50XBR1 with our H4000. It might have the same problem as the 60XBR2, it may not. It might be that Sony TV only supports 1080p/24 ( a 1080p format only Sony and some other Japanese brands support) which our DVD player and HTPC only ouputs 1080p/60.

So I'm guessing that Sony assumed people would use 1080p only for movies (which are 24 frames per second). 


My Setup:
Nvidia 7600 GS
DVI to HDMI cable
Sony KDS-R50XBR1 TV

---

