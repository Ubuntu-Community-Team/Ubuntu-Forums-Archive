---
title: "Very low fps new gpu"
date: 2007-12-27
forum: Gaming &amp; Leisure
---

### Post by azexian on 2007-12-27
Hello everyone,
I'm new to these forums, but not to linux, so if you need anymore output, just ask. 

My system specs are as follows: 
AMD Athlon X2 4000
1GB RAM
Gigabyte GA-M61P-S3
Ubuntu Gutsy 7.10 64 bit 

I just got a new Nvidia 7300GS to replace my Geforce Fx 5500 (it had to go!), but the fps for it doesn't seem at all right, I realise that glxgears is not a benchmarking tool, but I think it can be used to show problems if the fps is far too low.

Just to clear up the obvious here is output of glxinfo | grep direct```
direct rendering: Yes
``` I'm using the Nvidia-glx-new driver from the apt, although I have also tried the Nvidia binary, no change.

Games run far slower then I think appropriate too, here's the output of glxgears run at 1280x1024 on 24bit colour depth without compiz:

```
glxgears
8415 frames in 5.0 seconds = 1682.992 FPS
8529 frames in 5.0 seconds = 1705.686 FPS
11194 frames in 5.0 seconds = 2238.702 FPS
15182 frames in 5.0 seconds = 3036.329 FPS
10808 frames in 5.0 seconds = 2161.478 FPS
8206 frames in 5.0 seconds = 1641.192 FPS
8375 frames in 5.0 seconds = 1674.876 FPS
8641 frames in 5.0 seconds = 1728.036 FPS
8721 frames in 5.0 seconds = 1744.131 FPS
8605 frames in 5.0 seconds = 1720.967 FPS
11016 frames in 5.0 seconds = 2203.165 FPS
12998 frames in 5.0 seconds = 2599.444 FPS
12061 frames in 5.0 seconds = 2412.174 FPS
8848 frames in 5.0 seconds = 1769.498 FPS
8313 frames in 5.0 seconds = 1662.578 FPS
8794 frames in 5.0 seconds = 1758.711 FPS
8388 frames in 5.0 seconds = 1677.469 FPS
```

I do have CPU Frequency scaling, but the above was done with it switched off in the bios.

My xorg.conf file is pretty stock:

```

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "nVidia Corporation G71 [GeForce 7300 GS]"
        Driver          "nvidia"
        BusID           "PCI:2:0:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "NEC LCD1760N"
        Option          "DPMS"
        HorizSync       31-81
        VertRefresh     56-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G71 [GeForce 7300 GS]"
        Monitor         "NEC LCD1760N"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

```

The motherboard does have a built in nvidia 6100, but this is disabled.

If i can provide any more information, then please tell me, I hope someone can help.

---

### Post by tgalati4 on 2007-12-27
Try running glxgears with your built-in video card so you can see the difference.  I think your numbers are OK.  The 7300 is an older series card.  There are lots of video card reviews on the web that will give you fps for common games and graphics benchmarks.  

xbench is a comprehensive video performance tester.  My only experience with nVidia is an old TnT card and a new 8600 GT.  It flies.  I don't have the fps figures handy but they were impressive.

You are running the legacy "nvidia" drivers.  I don't know if better drivers exist for your card.  Did you try running envy?

---

### Post by azexian on 2007-12-28
> **tgalati4 said:**
> Try running glxgears with your built-in video card so you can see the difference.  I think your numbers are OK.  The 7300 is an older series card.  There are lots of video card reviews on the web that will give you fps for common games and graphics benchmarks.  

xbench is a comprehensive video performance tester.  My only experience with nVidia is an old TnT card and a new 8600 GT.  It flies.  I don't have the fps figures handy but they were impressive.

You are running the legacy "nvidia" drivers.  I don't know if better drivers exist for your card.  Did you try running envy?

Thank you for your reply, I will look into xbench now, I didn't realise that such a thing was available. The bios for this motherboard works in such a way that you either have it always enabled, or on only when no pci-e card is inserted, I tried the always on option, but nothing appeared on my screen, however, I will remove my pci-e graphics card and see what happens with the inbuilt one.

I did hope it wasn't just a matter of the graphics card actually being that slow, but of course its possible, I think I've seen some people on other people on this forum saying that they got at least 5000fps, so I think I should be able to do better.

One thing I didn't mention before is the possibility of conflict, I wondered when i first saw these figuers on my 32 bit installation (different partition) if it was just because it was 64 bit, so i installed the 64 bit version *and the nvidia binary driver* after this, I wanted to try the apt one, so I just installed it, however since then, i ran nvidia-installer --uninstall, which removed that driver, removed the apt one, and reinstalled it, however the nvidia logo still comes up when X starts, so to be honest, I don't know which one I'm actually using, hopefully the logo is the only remenant of the old driver, I use cedega, which would only claim that I was using 3d when I used the 32 bit driver, or the apt one, and it says its all ok, so fingers crossed.

I wander if someone with the same graphics card could verify their fps, just as a light comparison.

---

### Post by azexian on 2007-12-28
After some searching, I found these:
[http://www.nvnews.net/vbulletin/showthread.php?t=74756](http://www.nvnews.net/vbulletin/showthread.php?t=74756)
[http://forums.gentoo.org/viewtopic-t-478558-highlight-7300gs.html](http://forums.gentoo.org/viewtopic-t-478558-highlight-7300gs.html)
Both comment on a similar issue, and they both list that they get much better performance on windows, both those threads had no solution, which is why I posted here, I tried to find xbench, but as I posted on this thread: [http://ubuntuforums.org/showthread.php?p=4029102](http://ubuntuforums.org/showthread.php?p=4029102) it is not in apt, and there is no debian package for it, it is only avalible in source, which no longer works. 

Is it possible the two drivers are conflicting? (perhaps the old installation of the nvidia binary is still there?) Perhaps it would be worth doing a new install, to make sure that I am definitely only using nvidia-glx-new, although I doubt that this would be the reason.

Any suggestions would be much appreciated,

---

### Post by tgalati4 on 2007-12-29
It's been a while since I used xbench.  I was comparing a Radeon 9600 (in a powerbook G4) versus a real video card.  So, yes, I compiled it from scratch, but it wasn't difficult.  I don't remember what I did on the Ubuntu Dapper side.  I thought it was in the repos, but then I may have compiled that as well.  I needed a benchmark that would work in both.  I even ran it on Damn Small Linux (Omnibook, P1, 166 MHz) comparing native performance on the notebook and as a remote X client.  Interesting results--network bandwidth does not limit xserver performance in most cases.

I would agree that your driver installation/deinstallation may have caused problems.  All it takes is one old library to slow the performance.

---

### Post by azexian on 2007-12-29
> **tgalati4 said:**
> It's been a while since I used xbench.  I was comparing a Radeon 9600 (in a powerbook G4) versus a real video card.  So, yes, I compiled it from scratch, but it wasn't difficult.  I don't remember what I did on the Ubuntu Dapper side.  I thought it was in the repos, but then I may have compiled that as well.  I needed a benchmark that would work in both.  I even ran it on Damn Small Linux (Omnibook, P1, 166 MHz) comparing native performance on the notebook and as a remote X client.  Interesting results--network bandwidth does not limit xserver performance in most cases.

I would agree that your driver installation/deinstallation may have caused problems.  All it takes is one old library to slow the performance.

So would you suggest I do a fresh install?

---

### Post by uwishurockedthishxc on 2007-12-29
thats extremely slow for your gpu because i have a comparable system and here are my results
24932 frames in 5.0 seconds = 4985.015 FPS
24892 frames in 5.0 seconds = 4978.279 FPS
26199 frames in 5.0 seconds = 5239.753 FPS
26005 frames in 5.0 seconds = 5200.963 FPS
26146 frames in 5.0 seconds = 5229.136 FPS
26045 frames in 5.0 seconds = 5208.988 FPS
26097 frames in 5.0 seconds = 5219.221 FPS
25987 frames in 5.0 seconds = 5197.358 FPS
25887 frames in 5.0 seconds = 5177.272 FPS
26108 frames in 5.0 seconds = 5221.473 FPS
26098 frames in 5.0 seconds = 5219.482 FPS
25807 frames in 5.0 seconds = 5161.326 FPS
24482 frames in 5.0 seconds = 4896.378 FPS
24799 frames in 5.0 seconds = 4959.782 FPS
25107 frames in 5.0 seconds = 5021.322 FPS
25067 frames in 5.0 seconds = 5013.319 FPS
24749 frames in 5.0 seconds = 4947.304 FPS

the 7300 series has issue for some people from what i have heard so that may be part of your problem.  ive heard that using envy and the latest beta drivers helps.

---

### Post by azexian on 2007-12-29
> **uwishurockedthishxc said:**
> thats extremely slow for your gpu because i have a comparable system and here are my results
24932 frames in 5.0 seconds = 4985.015 FPS
24892 frames in 5.0 seconds = 4978.279 FPS
26199 frames in 5.0 seconds = 5239.753 FPS
26005 frames in 5.0 seconds = 5200.963 FPS
26146 frames in 5.0 seconds = 5229.136 FPS
26045 frames in 5.0 seconds = 5208.988 FPS
26097 frames in 5.0 seconds = 5219.221 FPS
25987 frames in 5.0 seconds = 5197.358 FPS
25887 frames in 5.0 seconds = 5177.272 FPS
26108 frames in 5.0 seconds = 5221.473 FPS
26098 frames in 5.0 seconds = 5219.482 FPS
25807 frames in 5.0 seconds = 5161.326 FPS
24482 frames in 5.0 seconds = 4896.378 FPS
24799 frames in 5.0 seconds = 4959.782 FPS
25107 frames in 5.0 seconds = 5021.322 FPS
25067 frames in 5.0 seconds = 5013.319 FPS
24749 frames in 5.0 seconds = 4947.304 FPS

the 7300 series has issue for some people from what i have heard so that may be part of your problem.  ive heard that using envy and the latest beta drivers helps.

Thank you very much for your reply, It's relieving to hear I can at least get more then 1500! I haven't tried envy, but I'm researching it now, when you say the beta drivers I assume you mean that envy offers you different drivers?

---

### Post by uwishurockedthishxc on 2007-12-29
to be honest im just using restricted drivers but i have a friend with a 7300 and he told me that in envy it got the drivers for you and that nvidia had a beta release that fixed 7300 problems

btw my results were at 1680x1050

---

### Post by azexian on 2007-12-29
> **uwishurockedthishxc said:**
> to be honest im just using restricted drivers but i have a friend with a 7300 and he told me that in envy it got the drivers for you and that nvidia had a beta release that fixed 7300 problems

btw my results were at 1680x1050

I've just installed and run envy, first I made sure to --purge remove all apt nvidia files, I restarted to check that it wouldn't load, then changed the driver to vesa and continued, running it, it used the 169.07 driver, which I assume must be the beta. It installed lots of new libraries, and also compiled nvidia-new-source and other things, after restart, I got the familiar nvidia logo, but the fps hasn't changed much unfortunately :-s:

```
~$ glxgears 
8806 frames in 5.0 seconds = 1761.085 FPS
8824 frames in 5.0 seconds = 1764.721 FPS
8771 frames in 5.0 seconds = 1754.133 FPS
8812 frames in 5.0 seconds = 1762.220 FPS
8819 frames in 5.0 seconds = 1763.626 FPS

```

Not much change, if anything down a little, envy is a beautiful program, and I highly recommend it, but in my case, it hasn't solved my problem, any suggestions very appreciated.

EDIT: uwishurockedthishxc what resolution and colour depth are you on, perhaps it is only higher as my settings are higher then yours are perhaps, just a thought

---

### Post by uwishurockedthishxc on 2007-12-29
im a complete noob.  how do i set that or find out what i have it set at?
im at 1680x1050 but idk the color depth

---

### Post by azexian on 2007-12-29
> **uwishurockedthishxc said:**
> im a complete noob.  how do i set that or find out what i have it set at?
im at 1680x1050 but idk the color depth

If it's on default it will be 32bit, I really wander how yours is so much higher then mine, I'm envious :p.
Did you do anything at all special, except click on the restricted manager and install? is there any option that you changed in nvidia-settings?  I'm pulling on lose strings here I guess, I think I need to either face that it is how it is for mine, and give up, or try a new installation/my gpu in another system, unless there is something I'm missing, hope someone can help.

---

### Post by uwishurockedthishxc on 2007-12-29
nope i just installed the restricted drivers when they popped up during install.  the only fiddling ive done as far as graphics go is i stuck my refresh rate at 63mhz

---

### Post by azexian on 2007-12-29
> **uwishurockedthishxc said:**
> nope i just installed the restricted drivers when they popped up during install.  the only fiddling ive done as far as graphics go is i stuck my refresh rate at 63mhz

Ok, so nothing significant there, that leaves two options: either my configuration is incorrect, in this case, unless someone comes along and suggests a simple fix, i might reinstall, as this is a very new installation anyway. Or your graphics card is better then mine, perhaps gt and gs are different more then the number suggest?

---

### Post by azexian on 2007-12-29
Doing some research, I found this on wikipedia, it suggests that your graphics card is based on the 7600, here are the specs:

**GeForce 7300 GS**
    * Graphics Bus: PCI Express
    * Memory Interface: 64-bit
    * Memory Bandwidth: 6.5 GB/s
    * Fill Rate: 2.2 billion pixel/s
    * Vertice/s: 413 million
    * Memory Type: DDR-II with TC

**GeForce 7300 GT**
    * Graphics Bus: PCI Express
    * Memory Interface: 128-bit
    * Memory Bandwidth: 10.7 GB/s
    * Fill Rate: 2.8 billion pixel/s
    * Vertice/s: 350 million
    * Memory Type: GDDR3 or DDR-II

As you can see, yours is vastly better then mine in pretty much all aspects, apart from in clock speed, where mine is slightly higher, this does mean that comparing the graphics cards is foolish, as they are so different, thanks for your help anyway, could someone with the same card possibly provide there fps please?

---

### Post by uwishurockedthishxc on 2007-12-29
sorry bout that I always thought that they were both derived from the same core but yours was underclocked

---

### Post by uwishurockedthishxc on 2007-12-29
i did some reading and found that many have this problem.  they get an average of 1600 in glxgears and terrible perfromance compared to their windows installations.  i think you should post this in the hardware incompatability and get the ubuntu guys to relize the problem

---

### Post by azexian on 2007-12-29
> **uwishurockedthishxc said:**
> i did some reading and found that many have this problem.  they get an average of 1600 in glxgears and terrible perfromance compared to their windows installations.  i think you should post this in the hardware incompatability and get the ubuntu guys to relize the problem

Intresting, I didn't find anything quite that explictit, clearly you know how to search! I will try it in the hardware incompatablility forum, and link both ways so people can find it, I hope this can be resolved, as it's a shame to waste good money on a gpu which is not working well, Thank you all your help.:)

---

### Post by azexian on 2007-12-29
> **uwishurockedthishxc said:**
> i did some reading and found that many have this problem.  they get an average of 1600 in glxgears and terrible perfromance compared to their windows installations.  i think you should post this in the hardware incompatability and get the ubuntu guys to relize the problem

Where is the 'hardware incompatibility' section? I can't find anything even similar, do you mean post a bug report?

---

### Post by uwishurockedthishxc on 2007-12-29
[http://ubuntuforums.org/showthread.php?t=361237](http://ubuntuforums.org/showthread.php?t=361237)

---

### Post by azexian on 2007-12-29
> **uwishurockedthishxc said:**
> [http://ubuntuforums.org/showthread.php?t=361237](http://ubuntuforums.org/showthread.php?t=361237)
Ok, posted on that forum, although I'm guessing this is not replied to directly, but instead it might be fixed in future release, if there are no other suggestions from anyone, I think I will try a fresh install, to see if this changes anything.

---

### Post by uwishurockedthishxc on 2007-12-29
im really sorry i couldnt help you out anymore

---

### Post by azexian on 2007-12-30
> **uwishurockedthishxc said:**
> im really sorry i couldnt help you out anymore

:)

---

### Post by gtrtx on 2007-12-30
Hello,

I have a 7200GS.  From what I've read it's very similar to the 7300GS. Also from what I've researched is that it was designed as  a low cost solution for people that wanted to upgrade to Vista but need the GPU to handle all the desktop eyecandy. 

Anyways, my glxgears is very similar to yours:

9163 frames in 5.0 seconds = 1832.521 FPS
9185 frames in 5.0 seconds = 1836.853 FPS
9183 frames in 5.0 seconds = 1836.486 FPS

That's with compiz running, with it turned off:
10362 frames in 5.0 seconds = 2072.340 FPS
10072 frames in 5.0 seconds = 2014.175 FPS
9990 frames in 5.0 seconds = 1997.992 FPS

A bit of an improvement.

From what I have gathered, this card isn't really for real high frame rates. It's more designed for desktop use and occasional games. Now I'm not really a gamer. Every once in a while I'll play some Nexuiz and I get pretty good performance, but that's with everything set to it's lowest. 

For regular desktop usage the card works great for me. Even with desktop effects (which I keep turned on). 

I guess the reason I posted this is just to state that I don't think that high frame rates are possible with this card. Now granted, our cards are different model numbers, but I think they are the same chipset. From reading the comparison chart on the box that the card came in, it appears to have the same basic features of the 7300.

I just hate to see you put to much effort into getting much more performance out of this card if it simply just isn't going to happen. Of course, I could be way off on this and I'll certainly follow this thread as I would love to see you get improved performance if it's possible. 

Just my 2 cents

tx

---

### Post by azexian on 2007-12-30
> **gtrtx said:**
> Hello,

I have a 7200GS.  From what I've read it's very similar to the 7300GS. Also from what I've researched is that it was designed as  a low cost solution for people that wanted to upgrade to Vista but need the GPU to handle all the desktop eyecandy. 

Anyways, my glxgears is very similar to yours:

9163 frames in 5.0 seconds = 1832.521 FPS
9185 frames in 5.0 seconds = 1836.853 FPS
9183 frames in 5.0 seconds = 1836.486 FPS

That's with compiz running, with it turned off:
10362 frames in 5.0 seconds = 2072.340 FPS
10072 frames in 5.0 seconds = 2014.175 FPS
9990 frames in 5.0 seconds = 1997.992 FPS

A bit of an improvement.

From what I have gathered, this card isn't really for real high frame rates. It's more designed for desktop use and occasional games. Now I'm not really a gamer. Every once in a while I'll play some Nexuiz and I get pretty good performance, but that's with everything set to it's lowest. 

For regular desktop usage the card works great for me. Even with desktop effects (which I keep turned on). 

I guess the reason I posted this is just to state that I don't think that high frame rates are possible with this card. Now granted, our cards are different model numbers, but I think they are the same chipset. From reading the comparison chart on the box that the card came in, it appears to have the same basic features of the 7300.

I just hate to see you put to much effort into getting much more performance out of this card if it simply just isn't going to happen. Of course, I could be way off on this and I'll certainly follow this thread as I would love to see you get improved performance if it's possible. 

Just my 2 cents

tx

Hello gtrtx, good to hear from you, looking on wikipedia, this is the specs for both cards (if you trust wiki's :p)

**GeForce 7200 GS**
    * Graphics Bus: PCI Express
    * Memory Interface: 64-bit
    * Memory Bandwidth: 6.4 GB/s
    * Fill Rate: 900 million pixel/s
    * Vertice/s: 225 million
    * Memory Type: DDR-II with TC

**GeForce 7300 GS**
    * Graphics Bus: PCI Express
    * Memory Interface: 64-bit
    * Memory Bandwidth: 6.5 GB/s
    * Fill Rate: 2.2 billion pixel/s
    * Vertice/s: 413 million
    * Memory Type: DDR-II with TC

They are clearly very similar cards, however, if anything, I would expect my score to be slightly higher then yours, as it seem's slightly better, although not by much, of course glxgears is quite un accurate as a benchmark, as I don't know what your system specs are, and tiny things can change it.

I wonder if you could post the framerate of a game, if Nexuiz will show it, then that I can check to see how they proform next to each other.

I will be happy to admit defeat if this is just not a great graphics card, but I first want to make sure that this is not a bug in the driver, on the web there seem to be many pages where people suggest that the 7300gs is preforming far better on windows, then on linux, which makes me think this might well be a driver issue, but, I may just be hoping for something that's just not going to happen.

---

### Post by gtrtx on 2007-12-31
As I mentioned before, I play nexiuz with everything turned low at 800x600.

with this I get around 135 fps

---

### Post by azexian on 2007-12-31
Happy new year everyone! I think this is definitely a bug now, looking at the feedback online, from people who have tried it on both Linux and windows, it seems that Linux is having problems in this area, but no doubt the fix will be there in the next release.

Unfortunately I'm an impatient sort naturally, and until I can figure out enough programing languages to fix it myself (working on it), if no one has already figured it out, or recevied a higher frame rate with the same card, I think I will consider purchasing a new card.

Therefore can someone kindly suggest a better card, which would play the latest games *which work on Linux* at nice frame rates, such as UT3, which will hopefully soon have a client released,I've actually been looking at the Geforce 8600, obviously I'm avoiding ATI, any suggestions much appreciated.

---

### Post by Extreme Coder on 2007-12-31
> **azexian said:**
> Happy new year everyone! I think this is definitely a bug now, looking at the feedback online, from people who have tried it on both Linux and windows, it seems that Linux is having problems in this area, but no doubt the fix will be there in the next release.

Unfortunately I'm an impatient sort naturally, and until I can figure out enough programing languages to fix it myself (working on it), if no one has already figured it out, or recevied a higher frame rate with the same card, I think I will consider purchasing a new card.

Therefore can someone kindly suggest a better card, which would play the latest games *which work on Linux* at nice frame rates, such as UT3, which will hopefully soon have a client released,I've actually been looking at the Geforce 8600, obviously I'm avoiding ATI, any suggestions much appreciated.

I used to have a GeForce 8600 GT, and it worked quite nicely the time I had it. I used to get 11,000+ FPS on glxgears :P

---

### Post by azexian on 2007-12-31
> **Extreme Coder said:**
> I used to have a GeForce 8600 GT, and it worked quite nicely the time I had it. I used to get 11,000+ FPS on glxgears :P

Hello Extreme Coder, If you don't mind me asking, what did you change it in favour of?

---

### Post by azexian on 2008-01-01
Ok, following the suggestion earlier from tgalati4  , I tried the built in graphics card, which is the nvidia 6100, specs of both for comparison follow:

**GeForce 6100**
# Manufacturing process: .09micron (90nm)
# Core Clock: 425 MHz
# Vertex Processors: 1
# Pixel Pipelines: 2
# Shader Model: 3
# DirectX support: v9
# Video playback acceleration: SD video acceleration (HD video acceleration not supported)
# Outputs: VGA only
# Memory: Shared DDR2

**GeForce 7300 GS**
    * Graphics Bus: PCI Express
    * Memory Interface: 64-bit
    * Memory Bandwidth: 6.5 GB/s
    * Fill Rate: 2.2 billion pixel/s
    * Vertice/s: 413 million
    * Memory Type: DDR-II with TC

As you can see, the 7300GS is much better, however look at the fps 
in comparison on glxgears:

**GeForce 6100**
8704 frames in 5.0 seconds = 1740.651 FPS
9410 frames in 5.0 seconds = 1881.862 FPS
9407 frames in 5.0 seconds = 1881.352 FPS
9370 frames in 5.0 seconds = 1873.846 FPS
9274 frames in 5.0 seconds = 1854.636 FPS

**GeForce 7300 GS**
9073 frames in 5.0 seconds = 1814.500 FPS
9088 frames in 5.0 seconds = 1817.444 FPS
9093 frames in 5.0 seconds = 1818.495 FPS
9090 frames in 5.0 seconds = 1817.967 FPS
9056 frames in 5.0 seconds = 1811.124 FPS

They're practically the same, apart from the price of buying something I already have built in! I do not believe for one second that they should be the same, looking at the comparison of specs above, it is clear that something is very wrong here...

---

### Post by Extreme Coder on 2008-01-01
> **azexian said:**
> Hello Extreme Coder, If you don't mind me asking, what did you change it in favour of?
Well, I sold it to someone who was prepared to pay for me more than the price I bought the card with, so I sold it :P
I have a built-in ATI Radeon X1200 in my motherboard. I am using it for now, since it fits my light gaming needs well, for now.
But there is something wierd about the glxgears FPS you get with the 6100, According to Wikipedia, my card is supposed to be a bit faster than your card(see [http://www.tweaktown.com/reviews/1112/12/page_12_benchmarks_prey/index.html](http://www.tweaktown.com/reviews/1112/12/page_12_benchmarks_prey/index.html) for example), but I get lower FPS:
**ATI Radeon X1200:**
5997 frames in 5.0 seconds = 1199.368 FPS

IMO, we should test FPS with a game, that should be a lot better.
May I suggest Savage? A great online FPS/RTS hybrid.
Follow this guide to get it installed:
[http://gaming.gwos.org/doku.php/guides:savage](http://gaming.gwos.org/doku.php/guides:savage)

And post your FPS, and at what settings when you're done.

---

### Post by azexian on 2008-01-01
> **Extreme Coder said:**
> 
IMO, we should test FPS with a game, that should be a lot better.
May I suggest Savage? A great online FPS/RTS hybrid.
Follow this guide to get it installed:
[http://gaming.gwos.org/doku.php/guides:savage](http://gaming.gwos.org/doku.php/guides:savage)

And post your FPS, and at what settings when you're done.

Strange how you've gpt such a low fps even though yours is better... but glxgears is not a good means of finding your fps, so yes a game is a much better idea, Savage looks excellent, I've been looking for a nice new game, perhaps this will be it, I will probably have a result for you in about 20 mins, almost finished downloading now.

---

### Post by azexian on 2008-01-01
fps ranged from about 30 - 60 , most of the time it stayed between 30 - 40, my settings were set to highest, at 1280x1024

---

### Post by tgalati4 on 2008-01-01
It's no secret that the nVidia GS series cards are low-cost substitutes for their more expensive GT and GTX series cards.  It's interesting to see the that the 7300 GS is about the same performance as an on-board 6100.

One test is worth a thousand expert opinions.

---

### Post by azexian on 2008-01-01
> **tgalati4 said:**
> It's no secret that the nVidia GS series cards are low-cost substitutes for their more expensive GT and GTX series cards.  It's interesting to see the that the 7300 GS is about the same performance as an on-board 6100.

One test is worth a thousand expert opinions.

Wish I'd researched before buying now :( Are you sure this is not a bug in the software? Online some people do not that it preforms better on windows, although perhaps they do unfair tests...

---

### Post by Extreme Coder on 2008-01-02
> **azexian said:**
> fps ranged from about 30 - 60 , most of the time it stayed between 30 - 40, my settings were set to highest, at 1280x1024

Is that with the onboard 6100?

---

### Post by azexian on 2008-01-02
> **Extreme Coder said:**
> Is that with the onboard 6100?

No, this is with my 7300gs

---

### Post by Extreme Coder on 2008-01-03
> **azexian said:**
> No, this is with my 7300gs
Then, if you don't mind, can you also give my your FPS with the 6100?

---

### Post by azexian on 2008-02-16
This never was solved, although I tried numerous drivers, I think it is just a rubbish card, I will see if I can grab myself a new one soon, I think I will go for a nVidia 8600GT unless anyone else has got anything that might be better?

Thanks for all your help everyone, very appreciated :)

---

