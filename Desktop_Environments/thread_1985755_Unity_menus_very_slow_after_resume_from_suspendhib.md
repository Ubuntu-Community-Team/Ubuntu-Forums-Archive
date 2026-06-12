---
title: "Unity menus very slow after resume from suspend/hibernate"
date: 2012-05-23
forum: Desktop Environments
---

### Post by SalsaDoom on 2012-05-23
Hi fellas,

Running Ubuntu 12.04 on my Asus G73 laptop. It runs pretty well, just needed a quick tweak to disable some buggy usb stuff on suspend/hibernate then everything works as expected -- almost. 

This laptop has a Radeon Mobility 5870, I'm using the Open Source drivers because fglrx made suspend/hibernate very unreliable -- but the performance is normally just fine. 

When I resume from a suspend or hibernate the desktop loads up ok except that unity runs very slow, like, software rendering slow. But its not using software rendering, glxinfo shows its direct rendering is fine. glxgears runs at the exact same speed before and after suspend/hibnerate. 

When suspend/hibernate did work with fglrx (about one in three times) it didn't have this issue. You can really tell when you press the super button to bring up the menus, it slowly shows up frame by frame. Logging in and out fixes this problem -- but eliminates the point of suspend. 

Anyone have any suggestions to try?

Cheers!
SD

---

### Post by SalsaDoom on 2012-05-24
Further investigation...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/908268](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/908268)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/767975](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/767975)

So this issue isn't really new or uncommon. I didn't get this bug on ArchLinux using either the OpenSource drivers or fglrx, however, so possibly a very new kernel release may correct the issue.

I'll test with mainline kernels and see what happens, with both the open source and the fglrx stuff.

EDIT: Tested with 3.4 -- no changes for either driver. So its something else causing this. But what?

---

### Post by SalsaDoom on 2012-05-24
I think this may actually be a bug in unity. Running "unity --reset" corrects the issue without having to login/out/reboot. I tried setting that in /etc/pm/sleep.d/ (it would slow resuming, but at least I'd have a functional desktop with any hassle) but it would just crash when I did that.

I'm surprised more people aren't dealing with this bug, or maybe they just gave up?

---

### Post by nozyczek on 2012-05-24
You're not alone. I also get slow Unity after waking up from suspend. I will do more testing and add more details later.

BTW, the bugs you have in your 2nd post describing slightly different issue. We will need to find bugs specific to your topic or open a new one.

Here is some general info for now:

-->lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04 LTS
Release:	12.04
Codename:	precise

-->uname -a
Linux myBox 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

-->dpkg -s unity | grep Version
Version: 5.12-0ubuntu1

-->dpkg -s compiz | grep Version
Version: 1:0.9.7.8-0ubuntu1

-->dpkg -s Xorg | grep Version
Version: 1:7.6+12ubuntu1

-->glxinfo | grep OpenGL
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD JUNIPER
OpenGL version string: 2.1 Mesa 8.0.2
OpenGL shading language version string: 1.20

-->lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Juniper [Radeon HD 5700 Series] [1002:68b8]

Hardware
Motherboard:      Gigabyte GA-P55A-UD4P
Processor:        Intel Core i7-870 Processor
Graphics:         Gigabyte ATI Radeon HD 5770 GV-R577UD-1GD (Batmobile)
Memory:           16GB (4 x 4GB) G.SKILL Ripjaws Series 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800) F3-12800CL9D-8GBRL
SSD Drive:        Crucial 64GB m4 2.5-inch SATA 6GB/s
Monitor:          2x Samsung P2770

---

### Post by nozyczek on 2012-05-25
I did more testing and in my case it does affects FPS. Here are my results.

Fresh boot; before suspend 
-->glxgears 
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
303 frames in 5.0 seconds = 60.440 FPS
300 frames in 5.0 seconds = 59.968 FPS
300 frames in 5.0 seconds = 59.966 FPS
300 frames in 5.0 seconds = 59.970 FPS
300 frames in 5.0 seconds = 59.967 FPS
300 frames in 5.0 seconds = 59.968 FPS

After suspend 
-->glxgears 
Running synchronized to the vertical refresh.  The framerate should be 
approximately the same as the monitor refresh rate. 
188 frames in 5.0 seconds = 37.560 FPS 
194 frames in 5.0 seconds = 38.670 FPS 
196 frames in 5.0 seconds = 39.068 FPS 
198 frames in 5.0 seconds = 39.599 FPS 
201 frames in 5.0 seconds = 40.198 FPS 
200 frames in 5.0 seconds = 39.868 FPS 

After compiz --replace
-->glxgears 
Running synchronized to the vertical refresh.  The framerate should be 
approximately the same as the monitor refresh rate. 
303 frames in 5.0 seconds = 60.457 FPS 
299 frames in 5.0 seconds = 59.797 FPS 
300 frames in 5.0 seconds = 59.997 FPS 
300 frames in 5.0 seconds = 59.999 FPS 
300 frames in 5.0 seconds = 59.998 FPS 
300 frames in 5.0 seconds = 59.998 FPS 
300 frames in 5.0 seconds = 59.998 FPS 
299 frames in 5.0 seconds = 59.798 FPS


I also tried "unity --reset" and it worked. Will need to see what exactly is behind 

unity --reset
and
compiz --replace

Could be compiz issue.

---

### Post by nozyczek on 2012-05-25
It doesn't look like it is only affecting performance when suspend was used. Here is some more details. 

Fresh boot; suspend not used
At first all looks good. Launcher opens and closes quickly but after few minutes of regular use I can see performance degradation when using Launcher. Everything else still works good.


-->glxgears 
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
302 frames in 5.0 seconds = 60.245 FPS[COLOR="red"]<= Launcher closed[/COLOR]
299 frames in 5.0 seconds = 59.798 FPS
301 frames in 5.0 seconds = 60.002 FPS
298 frames in 5.0 seconds = 59.596 FPS
299 frames in 5.0 seconds = 59.799 FPS
102 frames in 5.1 seconds = 20.030 FPS[COLOR="red"]<= pressing &#8220;Super&#8221;; Launcher slowly opens[/COLOR]
30 frames in 5.2 seconds =  5.780 FPS	
30 frames in 5.2 seconds =  5.759 FPS
30 frames in 5.2 seconds =  5.780 FPS
31 frames in 5.2 seconds =  5.962 FPS
32 frames in 5.2 seconds =  6.172 FPS
31 frames in 5.2 seconds =  5.984 FPS
30 frames in 5.2 seconds =  5.788 FPS
105 frames in 5.0 seconds = 20.984 FPS[COLOR="red"]<= pressing ESC; Launcher slowly closes[/COLOR]
299 frames in 5.0 seconds = 59.600 FPS	
299 frames in 5.0 seconds = 59.600 FPS
298 frames in 5.0 seconds = 59.595 FPS
301 frames in 5.0 seconds = 60.001 FPS
300 frames in 5.0 seconds = 59.996 FPS
293 frames in 5.0 seconds = 58.597 FPS
49 frames in 5.2 seconds =  9.438 FPS[COLOR="red"]<= pressing &#8220;Super&#8221;; Launcher slowly opens[/COLOR]
31 frames in 5.2 seconds =  5.961 FPS
34 frames in 5.2 seconds =  6.529 FPS
30 frames in 5.2 seconds =  5.791 FPS
29 frames in 5.2 seconds =  5.595 FPS
33 frames in 5.2 seconds =  6.305 FPS
105 frames in 5.0 seconds = 20.984 FPS[COLOR="Red"]<= pressing ESC; Launcher slowly closes[/COLOR]
299 frames in 5.0 seconds = 59.799 FPS
300 frames in 5.0 seconds = 59.998 FPS
298 frames in 5.0 seconds = 59.599 FPS
300 frames in 5.0 seconds = 59.996 FPS

Everything seems to be very slow when Launcher is open and comes back to normal after Launcher is closed.

Replacing compiz windows:
-->compiz --replace

-->glxgears 
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
303 frames in 5.0 seconds = 60.494 FPS[COLOR="red"]<= Launcher closed[/COLOR]
298 frames in 5.0 seconds = 59.598 FPS
299 frames in 5.0 seconds = 59.797 FPS
291 frames in 5.0 seconds = 58.199 FPS[COLOR="red"]<= pressing &#8220;Super&#8221;; Launcher quickly opens[/COLOR]
299 frames in 5.0 seconds = 59.799 FPS
298 frames in 5.0 seconds = 59.515 FPS
299 frames in 5.0 seconds = 59.679 FPS
300 frames in 5.0 seconds = 59.999 FPS[COLOR="Red"]<= pressing ESC; Launcher quickly closes[/COLOR]
299 frames in 5.0 seconds = 59.798 FPS
297 frames in 5.0 seconds = 59.315 FPS
298 frames in 5.0 seconds = 59.395 FPS
297 frames in 5.0 seconds = 59.399 FPS[COLOR="red"]<= pressing &#8220;Super&#8221;; Launcher quickly opens[/COLOR]
296 frames in 5.0 seconds = 59.089 FPS

This will only work good for few minutes and will go back to degraded performance again.


[COLOR="Red"]New bug opened:[/COLOR]
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1004475](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1004475)

---

