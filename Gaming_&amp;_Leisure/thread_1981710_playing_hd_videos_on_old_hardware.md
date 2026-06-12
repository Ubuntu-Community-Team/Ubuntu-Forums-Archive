---
title: "playing hd videos on old hardware"
date: 2012-05-17
forum: Gaming &amp; Leisure
---

### Post by bhoopal on 2012-05-17
hi everyone. 
I have an old desktop pc, 2.8 Ghz P4, 1.5Gb ram, NVIDIA geforce 6200 256Mb agp video card. I bought a new screen yesterday, viewsonic 22" led, with 1080p full hd resolution. I re-installed ubuntu 12.04 32 bit, with internet on to install updates and codecs. updated after install. using nvidia version current(recomended) restricted drivers. 
the desktop run ok, a little slower than with crt screen.

1) online video(youtube) lags, even the 240p. on google chrome or firefox.
2) downloaded videos, 
   i tried a 720p video, it played ok on vlc and default movie     player
i tried a 1080p movie, that one lags much on both players(vlc and default movie player and even when played online). even when i switch to ubuntu 2d.

i dont play games. my parent use this pc only to surf, watch online videos, or downloaded videos.

i need help to optimize this old pc. i looked for a codec called coreavc, will it be useful?
my motherboard suports 4gb of ram ddr400. i have 2 pairs of 2slots.i can upgrade my ram from 1.5 to 3gb for $40(for 2 1gb ddr1). Will it be worth, or waste due to bottleneck?

---

### Post by forrestcupp on 2012-05-17
The Geforce 6200 only supports h.264 and VC-1 video with software acceleration, which means you'd have to have a beast of a computer to run them. It also doesn't support HDCP from Blu-rays, which means you'd have to have something to circumvent that to play Blu-rays.

I'd say your best way to spend money would be on a better video card that supports hardware video acceleration for HD video. I'm not sure what's out there in AGP, though. I think there are some cards in the Radeon HD line that are AGP.

---

### Post by regor210 on 2012-05-17
I'm not sure the Nvidia current divers support your NVIDIA geforce 6200 APG. So lets check and see.

Open a terminal, press ctrl+alt+t all at the same time. Cut and paste the following commands into the terminal window one line at a time minus the $.

$ sudo apt-get update
$ sudo apt-get upgrade

$ sudo apt-get install mesa-utils

Now run these and post what you get.

# video driver 3D test FPS
$ glxgears

#video card and driver information
$ lspci -vmk | grep -A 8 -B 2 VGA

---

### Post by bhoopal on 2012-05-17
gajadur@gajadur:~$ #video card and driver information
gajadur@gajadur:~$  lspci -vmk | grep -A 8 -B 2 VGA

Device:	01:00.0
Class:	VGA compatible controller
Vendor:	NVIDIA Corporation
Device:	NV44A [GeForce 6200]
SVendor:	Elitegroup Computer Systems
SDevice:	Device 0302
Rev:	a1
Driver:	nvidia
Module:	nvidia_current
Module:	nouveau

---

### Post by bhoopal on 2012-05-17
gajadur@gajadur:~$ # video driver 3D test FPS
gajadur@gajadur:~$  glxgears
2222 frames in 5.0 seconds = 444.298 FPS
2377 frames in 5.0 seconds = 475.313 FPS
2358 frames in 5.0 seconds = 471.579 FPS
2397 frames in 5.0 seconds = 479.362 FPS
2344 frames in 5.0 seconds = 468.612 FPS
2270 frames in 5.0 seconds = 453.885 FPS
2273 frames in 5.0 seconds = 454.545 FPS
2392 frames in 5.0 seconds = 478.354 FPS
2393 frames in 5.0 seconds = 478.513 FPS
2417 frames in 5.0 seconds = 483.384 FPS
2414 frames in 5.0 seconds = 482.724 FPS
2390 frames in 5.0 seconds = 477.154 FPS
2395 frames in 5.0 seconds = 478.989 FPS
2375 frames in 5.0 seconds = 474.995 FPS
2419 frames in 5.0 seconds = 483.762 FPS
2410 frames in 5.0 seconds = 481.949 FPS
2414 frames in 5.0 seconds = 482.710 FPS
2409 frames in 5.0 seconds = 481.532 FPS
2425 frames in 5.0 seconds = 484.966 FPS
2408 frames in 5.0 seconds = 481.535 FPS
2403 frames in 5.0 seconds = 480.520 FPS
2372 frames in 5.0 seconds = 474.351 FPS
2409 frames in 5.0 seconds = 481.745 FPS
2383 frames in 5.0 seconds = 476.576 FPS
2393 frames in 5.0 seconds = 478.515 FPS
2391 frames in 5.0 seconds = 478.162 FPS
2425 frames in 5.0 seconds = 484.868 FPS
2412 frames in 5.0 seconds = 482.336 FPS
2398 frames in 5.0 seconds = 479.531 FPS
2405 frames in 5.0 seconds = 480.976 FPS
2389 frames in 5.0 seconds = 477.762 FPS
2417 frames in 5.0 seconds = 483.334 FPS
2397 frames in 5.0 seconds = 479.375 FPS
2422 frames in 5.0 seconds = 484.393 FPS
2418 frames in 5.0 seconds = 483.405 FPS
2408 frames in 5.0 seconds = 481.560 FPS
2420 frames in 5.0 seconds = 483.966 FPS
2396 frames in 5.0 seconds = 479.147 FPS
2431 frames in 5.0 seconds = 486.136 FPS
2404 frames in 5.0 seconds = 480.788 FPS
2397 frames in 5.0 seconds = 479.222 FPS
2376 frames in 5.0 seconds = 474.765 FPS
2445 frames in 5.0 seconds = 488.588 FPS
2397 frames in 5.0 seconds = 479.346 FPS
2416 frames in 5.0 seconds = 483.100 FPS
2396 frames in 5.0 seconds = 479.163 FPS
2402 frames in 5.0 seconds = 480.318 FPS
2402 frames in 5.0 seconds = 480.369 FPS
2375 frames in 5.0 seconds = 474.957 FPS
2400 frames in 5.0 seconds = 479.968 FPS
2405 frames in 5.0 seconds = 480.957 FPS
2241 frames in 5.0 seconds = 448.082 FPS
2428 frames in 5.0 seconds = 484.708 FPS
2338 frames in 5.0 seconds = 467.504 FPS
2408 frames in 5.0 seconds = 481.484 FPS
2434 frames in 5.0 seconds = 486.732 FPS
2404 frames in 5.0 seconds = 480.743 FPS
2431 frames in 5.0 seconds = 486.131 FPS
2415 frames in 5.0 seconds = 482.987 FPS
2396 frames in 5.0 seconds = 479.123 FPS
2421 frames in 5.0 seconds = 484.138 FPS
2375 frames in 5.0 seconds = 474.947 FPS
2422 frames in 5.0 seconds = 484.287 FPS
2412 frames in 5.0 seconds = 482.360 FPS
2399 frames in 5.0 seconds = 479.777 FPS
2431 frames in 5.0 seconds = 486.162 FPS
2418 frames in 5.0 seconds = 483.479 FPS
2396 frames in 5.0 seconds = 479.182 FPS
2419 frames in 5.0 seconds = 483.730 FPS
2396 frames in 5.0 seconds = 479.079 FPS
2422 frames in 5.0 seconds = 484.386 FPS
2401 frames in 5.0 seconds = 480.193 FPS
2430 frames in 5.0 seconds = 485.899 FPS
2396 frames in 5.0 seconds = 479.107 FPS
2408 frames in 5.0 seconds = 481.504 FPS
2400 frames in 5.0 seconds = 479.936 FPS
2426 frames in 5.0 seconds = 485.126 FPS
2409 frames in 5.0 seconds = 481.750 FPS
2419 frames in 5.0 seconds = 483.725 FPS
2409 frames in 5.0 seconds = 481.792 FPS
2410 frames in 5.0 seconds = 481.936 FPS
2438 frames in 5.0 seconds = 487.507 FPS
2410 frames in 5.0 seconds = 481.983 FPS
2405 frames in 5.0 seconds = 480.939 FPS
2432 frames in 5.0 seconds = 486.327 FPS
2413 frames in 5.0 seconds = 482.549 FPS
2292 frames in 5.0 seconds = 457.101 FPS
2486 frames in 5.0 seconds = 496.817 FPS
2392 frames in 5.0 seconds = 478.331 FPS
2267 frames in 5.0 seconds = 453.386 FPS
2175 frames in 5.0 seconds = 434.874 FPS
2921 frames in 5.0 seconds = 584.009 FPS
2769 frames in 5.0 seconds = 553.766 FPS
2433 frames in 5.0 seconds = 486.351 FPS
2398 frames in 5.0 seconds = 479.374 FPS
2420 frames in 5.0 seconds = 483.712 FPS
2244 frames in 5.0 seconds = 447.762 FPS
2501 frames in 5.0 seconds = 500.129 FPS
1970 frames in 5.0 seconds = 393.970 FPS
2358 frames in 5.0 seconds = 471.583 FPS
2376 frames in 5.0 seconds = 475.171 FPS
2341 frames in 5.0 seconds = 468.132 FPS
2383 frames in 5.0 seconds = 476.557 FPS
2394 frames in 5.0 seconds = 478.723 FPS
2292 frames in 5.0 seconds = 458.336 FPS
2252 frames in 5.0 seconds = 450.259 FPS
2277 frames in 5.0 seconds = 455.359 FPS
2229 frames in 5.0 seconds = 445.779 FPS
2224 frames in 5.0 seconds = 444.748 FPS
2328 frames in 5.0 seconds = 465.548 FPS
2397 frames in 5.0 seconds = 479.387 FPS
2410 frames in 5.0 seconds = 481.933 FPS
2408 frames in 5.0 seconds = 481.501 FPS
2395 frames in 5.0 seconds = 478.949 FPS
2424 frames in 5.0 seconds = 484.738 FPS
2385 frames in 5.0 seconds = 476.945 FPS
2405 frames in 5.0 seconds = 480.959 FPS
2406 frames in 5.0 seconds = 481.092 FPS
2440 frames in 5.0 seconds = 487.912 FPS
2399 frames in 5.0 seconds = 479.792 FPS
2414 frames in 5.0 seconds = 482.743 FPS
2392 frames in 5.0 seconds = 478.345 FPS
2403 frames in 5.0 seconds = 480.500 FPS
2395 frames in 5.0 seconds = 478.981 FPS
2250 frames in 5.0 seconds = 449.982 FPS
2108 frames in 5.0 seconds = 421.456 FPS
2434 frames in 5.0 seconds = 486.698 FPS
2141 frames in 5.0 seconds = 427.605 FPS
1848 frames in 5.0 seconds = 369.428 FPS
2172 frames in 5.0 seconds = 434.363 FPS
2401 frames in 5.0 seconds = 480.159 FPS
2324 frames in 5.0 seconds = 464.722 FPS
2340 frames in 5.0 seconds = 467.965 FPS
2270 frames in 5.0 seconds = 453.992 FPS
2386 frames in 5.0 seconds = 477.105 FPS
2349 frames in 5.0 seconds = 469.003 FPS
2405 frames in 5.0 seconds = 480.903 FPS
2365 frames in 5.0 seconds = 472.983 FPS
2356 frames in 5.0 seconds = 470.349 FPS
1774 frames in 5.0 seconds = 354.353 FPS
2280 frames in 5.0 seconds = 455.930 FPS

2380 frames in 5.0 seconds = 475.498 FPS
2410 frames in 5.0 seconds = 481.606 FPS
2113 frames in 5.0 seconds = 422.299 FPS
2271 frames in 5.0 seconds = 453.979 FPS
2405 frames in 5.0 seconds = 480.168 FPS
2558 frames in 5.0 seconds = 511.326 FPS
2544 frames in 5.0 seconds = 508.702 FPS
2358 frames in 5.0 seconds = 471.260 FPS
2289 frames in 5.0 seconds = 457.796 FPS
2574 frames in 5.0 seconds = 514.678 FPS
2176 frames in 5.0 seconds = 435.139 FPS
2376 frames in 5.0 seconds = 474.997 FPS
2397 frames in 5.0 seconds = 479.335 FPS
2408 frames in 5.0 seconds = 481.497 FPS
2382 frames in 5.0 seconds = 476.307 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 47 requests (47 known processed) with 0 events remaining.

---

### Post by bhoopal on 2012-05-17
im running the glxgears test again, because i cancelled it the last time, i thought it was never gonna end!

---

### Post by bhoopal on 2012-05-17
and by the way im using DVI cable, not the VGA, if that matters

---

### Post by QIII on 2012-05-17
glxgears will keep going until you stop it.

glxgears is not a good benchmarking tool.  In fact, I would say with those results your playback would be very low quality.

You can drive your glxgears fps through the roof by setting your playback to low quality.

---

### Post by bhoopal on 2012-05-17
ok. there's no way to improve the performance software-wise i guess. i don't i'll buy another graphic card. it'll be bottle-necked by my cpu. i was looking at radeon HD 4670 agp...
i'll rather save the money for a new system in a year or two. I'll manage, as my parents only surf, watch youtube videos, and skype with it. just a question, is there any distribution which will serve me better for these task than ubuntu?
considering my specs
2.8 GHz p4, 40gb ide hhd, 1.5 gb ddr ram, nvidia geforce 6200 256mb ddr2 agp

---

### Post by regor210 on 2012-05-17
Use

$ /usr/bin/nvidia-settings

Then goto OpenGL Settings and push the bar to High Performance.

This will give you a little better performance but probably not what your looking for but worth a try.

---

### Post by forrestcupp on 2012-05-17
> **bhoopal said:**
> is there any distribution which will serve me better for these task than ubuntu?
considering my specs
2.8 GHz p4, 40gb ide hhd, 1.5 gb ddr ram, nvidia geforce 6200 256mb ddr2 agp

No. You could use every Linux distro out there and even Windows, and you will get the same results. The 6200 just can't handle 1080p. It has nothing to do with software, and everything to do with your video card not being able to hardware accelerate the HD video. I hate to say it, but the 6200 was low end even when it was new.

---

### Post by bhoopal on 2012-05-17
i understand. but what im asking is, given that i perform only those particular task on my old system, should i switch to lubuntu, or xubuntu?what matters is performance, and hardware support. and my pc being slow, is it because my screen resolution is 1920x1080p? and even low resolution youtube videos lagging, google chrome has flash inbuit, and hardware acceleration in enabled. may be the spec is too low. I'll try changing the resolution, try a few things and post back. the graphics was a great update for me, from my previous ati radeon 7000, 32 mb :-)
thank anyway:-)

---

### Post by Perfect Storm on 2012-05-17
If you want to benchmark use Heaven; [http://unigine.com/products/heaven/](http://unigine.com/products/heaven/)

---

### Post by forrestcupp on 2012-05-17
> **bhoopal said:**
> i understand. but what im asking is, given that i perform only those particular task on my old system, should i switch to lubuntu, or xubuntu?

It wouldn't hurt to try out Lubuntu. Lowering the resolution can help, too.

---

### Post by mastablasta on 2012-05-18
you could try to get s used card. some older radeons like 9800 and 9600 have good opensoruce driver support. there might be even more arround. 
 
for newer ones they sell here AMD Radeon HD 3650 512 MB, AGP for about 50 EUR, but we do have high prices for computer equipment.... so you might be able to find something similar for much less in your country.

---

### Post by mode7 on 2012-05-18
It's highly unlikely you'll be able to process high definition media if you can't already, but if you are looking to squeeze every last bit of performance on your machine, it's worth a try using XFCE or LXDE (Xubuntu/Lubuntu).
On my old laptop, I got a 15 fps increase in Minecraft when switching to XFCE from Unity. From 15 to ~30 or so.

Edit: Selecting Unity 2D on the login screen instead of Unity will probably improve your general desktop performance as well if you like the Unity shell, or don't want to install other desktop environments.

---

### Post by SeijiSensei on 2012-05-18
Unless the machine has a PCI Express slot, which seems unlikely on a machine with AGP, you're basically out of luck.  I looked at Newegg the other day to see whether any AGP adapters included an NVIDIA chip that supports hardware video acceleration; there were none.  You need at least an NVIDIA 8xxx to support acceleration, and all the cards I've seen with those chips use PCI-X.  Personally I wouldn't even bother exploring older ATI adapters.  Their video support was generally worse than NVIDIA's until fairly recently.

---

### Post by bhoopal on 2012-05-18
yes. i think ill save for a newer system. the buggy online videos is a software bug i think(the 360p). i was having this problem with ubuntu 11.04, i switched to XP(plays online videos well, not the hd). 11.10 was working well, upgraded to 12.04, also ok. then the system crashed( boot init failed), instead of repairing i just performed a fresh install, and this time with my new screen! and ever since, online videos are buggy. i even reduced the resolution from 1920x1080 to 1337x768. I haven't test the skype video call yet. movies on hhd or dvds play well. its only the flash videos. 

i live in mauritius, I bought the nvidia 6200 about $50 last year. and this was among the best card i found, and my best deal, its a second hand.  i know i'll waste if i invest more, though im very attached to this system(my first pc).
 i'll try installing the lxde and xfce and see if i get some speed.

---

### Post by bhoopal on 2012-05-18
the coreavc thing i saw it on this site 
[http://geeknizer.com/1080p-minimum-requirements/](http://geeknizer.com/1080p-minimum-requirements/)

---

### Post by bhoopal on 2012-05-18
[http://ubuntuforums.org/showthread.php?t=839295](http://ubuntuforums.org/showthread.php?t=839295)

---

### Post by forrestcupp on 2012-05-18
> **SeijiSensei said:**
> Personally I wouldn't even bother exploring older ATI adapters.  Their video support was generally worse than NVIDIA's until fairly recently.

Not true. When ATI came out with their HD line, they had hardware acceleration for HD video. Back in the day, I had a Radeon HD 2600, which was a contemporary of nVidia's 6xxx line, which didn't have hardware HD video support. There are plenty of newer model Radeon HD cards that are AGP that would do just fine, aside from AMD/ATI's general crappy Linux support.

But I agree with the OP's notion that it would be wiser just to save for a new system.

---

### Post by bhoopal on 2012-05-20
guys, lubuntu was very bad! had a kernel panic... the install was taking too long, the server was slow(3kbps) to download updates! i skipped the updates, and post-installed them , on a more prefered server(which i let updatemanager to decide), and after update had a kernel panic. i was unable to find a quick solution.also i could not make microsoft lifecam to work with skype!(the preload thing was not working) had a really bad time. tried to switch back to ubuntu, my dvd writers was not booting.. i burned 4 cd's of ubuntu, was not booting... check bios... check iso(followed instruction on ubuntu site) iso was ok. burned with windows 7 default, and nero also..reduced speed... 
i switched back to xp... a pain, had to install all drivers which used to be out of the box in ubuntu! 
however , youtube videos are playing very smooth! and to my surprise!!!!after i followed these instructions [http://www.pcpro.co.uk/blogs/2010/02/18/how-to-play-hd-video-on-a-netbook/](http://www.pcpro.co.uk/blogs/2010/02/18/how-to-play-hd-video-on-a-netbook/)

with latest coreavc3.0.1 , (but i could not set output-DirectShow Video  to EVR,thus i put it to default!) and im now playing 1080p movies, the same that didn't play with ubuntu, and xp (both with vlc) before installing coreavc and Mediaplayerclassic. [http://www.youtube.com/watch?v=YW8p8JO2hQw](http://www.youtube.com/watch?v=YW8p8JO2hQw)

there should be a way to do that in ubuntu. I have a big exam in 2 days, after that i'll try to find and implement it and post back. If anyone ever tried something like that and it worked, post the steps please.

the 1080p plays smooth,almost the same as my laptop with corei5,4gb ram, radeon hd 5650.

i think it uses something called CUDA for nvidia.

---

### Post by bhoopal on 2012-05-20
guys, now i really think there were problems software wise, xp is running without lag. no buggy online videos. im using my screen at 1920x1080. Image quality with microsoft lifecam also better. i think the restricted drivers the company provides for linux is not the same level. i'll stick with xp for a while. i have win 7 on my laptop, which i had nightmare to put ubuntu on. ATI restricted drivers was crashing the computer on install itself... 
the next computer i'll build, it should be an ubuntu compatible!:)

---

### Post by mastablasta on 2012-05-20
> **bhoopal said:**
>  i have win 7 on my laptop, which i had nightmare to put ubuntu on. ATI restricted drivers was crashing the computer on install itself... 


have you tried with latest drivers? if you have hybrid graphics (intel+ati) it just might work. you could try wiht persistant liveUSB and then install drivers to it instead of installing the whole OS to disk....

---

### Post by bhoopal on 2012-05-20
it was last year. ok, i'll try the usb live

---

### Post by mastablasta on 2012-05-21
have a look here for a how to: [http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)
 
still i was told it doesn't work with all combinations.

---

### Post by bhoopal on 2012-05-22
[http://en.wikipedia.org/wiki/CoreAVC](http://en.wikipedia.org/wiki/CoreAVC)

---

