---
title: "Help with graphics cards"
date: 2005-12-18
forum: Gaming &amp; Leisure
---

### Post by gRiMgRaVy014 on 2005-12-18
I am asking for a nvidia gforce 5500 for christmas since they are way cheaper now. Currently I am using Xp but I plan on switching over to linux soon. I am wondering if Ubuntu has corect drivers for this graphics card? I have read and heard that nividia drivers are better then ati drivers on linux.

---

### Post by adwait on 2005-12-18
Yeah, AFAIK, nvidia works fine on a linux with a little trouble initially.

---

### Post by 11hjpphty76lkjj on 2005-12-18
Not sure if this will help, there is an Nvidia driver package:

NVIDIA binary XFree86 4.x/X.Org driver
These XFree86 4.x/X.Org binary drivers provide optimized hardware acceleration
of OpenGL applications via a direct-rendering X Server and support the TNT,
TNT2, TNT Ultra, GeForce, nForce and Quadro chipsets. AGP, TV-out and
flat panel displays are also supported.

I was using a GeForce 440, and it worked great.  So I don't see why your new card shouldn't work. (Only reason I'm not using it now is cause I upgraded.)

Hope this helps.  

Switch today!! Don't wait. :)

---

### Post by Evil Whisper on 2005-12-18
GeForce FX5500's work great in Linux I use one myself all you have to do to install the driver from the repositories is:

```

sudo apt-get install nvidia-glx nvidia-settings

```

then 
```

sudo nvidia-glx-config enable

```

then hit control+alt+backspace to restart X log back in and run:
```

glxgears -printfps

```

if the fps prints out at around 2000 everything is good :-)

---

### Post by gRiMgRaVy014 on 2005-12-18
Well thats good news :) But I"m wondering is this graphics card any good for gaming while I still have Xp and if i get wine or some other program for linux? It's a 256 mb card I would think it would be able to run some graphical games liek guild wars,WoW, and maybe Doom 3 / Half life 2 on my Xp. Is it possible or is it just an old card?

---

### Post by Fibre on 2005-12-18
I would have thought any 256mb card will do. I know with xp they will all work well with that card. Provided you have enough ram, large enough cpu and hard drive space.

Perhaps if you give a full run down of your computer the ppl in the know could give you a better answer.

If you go to those game sites they should give you an idea of the recommended requirements just to be 100% sure as well.

If your a noobie to this like me this is good reading and maybe the way to go correct me if I'm wrong guys plz.
[http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)

There is something though that you can't download if in America - but you can choose not to download it whatever it was?

I also don't know about guild Wars or WoW?

---

### Post by gRiMgRaVy014 on 2005-12-19
My computer is a:
Pentium 4, 3.0 ghz
512 RAM 
80 gig HDD 
if you need anything else just ask.

---

### Post by Biased turkey on 2005-12-19
Isn't the 5500 a little weak ?.
I'm a "medium gamer" mostly playing racing games ( Grand Prix Legends, Richard Burns Rally, or F1 challenge 1999-2002 )  have an Nvidia 6600 ( 128 MB ) and I'm satisfied with it, but wouldn't games such as Halfl life 2 require some even more  powerful video card ?

---

### Post by Evil Whisper on 2005-12-19
*Deleted Sorry*

---

### Post by gRiMgRaVy014 on 2005-12-20
Well I've heard that the card is good but its shader driver is horrible. I don't know if this will effect anything but thats waht I've heard.

---

### Post by Fibre on 2005-12-20
I had the fx5200 128mb card in my Celeron 2.66D with 768ram / 80gb hdd.

I found it just a fraction sluggish, Now I've changed to ATI's 9550 256mb and it's enough for me. It's not cutting edge or anything but it's dirt cheap and does the trick just fine. 

I'd say that if my 5200 could do it with just a little gap here or there, I reckon a 5500 should do the trick no worries at least with doom3 or half life2. I don't know anything about the other games you've mentioned, but I can't imagine it wouldn't be able to do those as well.

It should play them fine, my 5200 was only 128 and it almost was to my liking. Yours is a 256mb card and you've got more cpu power, perhaps a touch more ram wouldn't go astray. 

But the card is a good card, Evil Whisper seems to think so and I reckon you'll have no problems. I was thinking of getting one myself, but this one popped up cheap and I'd never tried ATI before so I got it.

---

### Post by Fibre on 2005-12-20
Here, this might give you an idea

[http://ubuntuforums.org/showthread.php?t=83759](http://ubuntuforums.org/showthread.php?t=83759)

Couple of guys have only 64mb gforce 440 mmx cards and there running Doom3.

---

### Post by gRiMgRaVy014 on 2005-12-20
Well I as leaning for the nvidia card because I have headrd that ati is lacking in ubuntu drivers.But thats good that you guys say it good because right now I"m playing WoW on my intergrated graphics card and its just horrible slow down etc. Just looking to play some of the newest games and good performance and being able to use the card with ubuntu.

---

### Post by lsald on 2005-12-20
[QUOTE=gRiMgRaVy014]Well I as leaning for the nvidia card because I have headrd that ati is lacking in ubuntu drivers.[/QUOTE]

You would be semi-correct. ATI's support is much more obscure IMO. I have found 0 issues with any nVida drivers. The nVidia supplied drivers from their website install and run with perfection.

Best of luck.

---

### Post by Fibre on 2005-12-20
Sorry this was crap so I deleted it.

---

### Post by gRiMgRaVy014 on 2005-12-21
Hey thanks you guys, your a huge help :)

---

### Post by Fibre on 2005-12-25
Check this site out, I had a look at the difference between the card you want and the card I've got - the 9550 256mb vs FX 5500 256mb and man yours should do ok but it does look a bit weak although it did better with quake3 fps. I'm glad i decided to go the ati way now. I just wanted to try out an ATI card for a change but it looks like the lower end card of choice if this is anything to go by the FX5700 looked good though but you probably have to pay more for it than I paid for mine.

quake3 fps
[http://www.tweaktown.com/articles/649/11/value_gpu_shootout_page_11_benchmarks_quake_3/index.html](http://www.tweaktown.com/articles/649/11/value_gpu_shootout_page_11_benchmarks_quake_3/index.html)
unreal 2004 demo fps
[http://www.tweaktown.com/articles/649/9/value_gpu_shootout_page_9_benchmarks_unreal_tournament_2004_demo/index.html](http://www.tweaktown.com/articles/649/9/value_gpu_shootout_page_9_benchmarks_unreal_tournament_2004_demo/index.html)
unreal 2003 fps
[http://www.tweaktown.com/articles/649/8/value_gpu_shootout_page_8_benchmarks_unreal_tournament_2003/index.html](http://www.tweaktown.com/articles/649/8/value_gpu_shootout_page_8_benchmarks_unreal_tournament_2003/index.html)
3d mark ? something
[http://www.tweaktown.com/articles/649/5/value_gpu_shootout_page_5_benchmarks_3dmark_2003/index.html](http://www.tweaktown.com/articles/649/5/value_gpu_shootout_page_5_benchmarks_3dmark_2003/index.html)

If your ok with low resolution in your gameplay, I still think it should be ok as I said before about my fx5200 128mb card. But I'm assuming yours is a 256mb card?

Everything I read about people that bought the card sounded positive but this was at sites that where selling the card so whether it's a true indication of the card?

Good luck with your choice. Check out the site and see what you think.

---

