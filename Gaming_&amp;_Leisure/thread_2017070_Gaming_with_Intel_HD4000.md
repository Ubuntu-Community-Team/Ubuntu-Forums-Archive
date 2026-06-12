---
title: "Gaming with Intel HD4000?"
date: 2012-07-04
forum: Gaming &amp; Leisure
---

### Post by 67GTA on 2012-07-04
I was recently kicked in the crotch because of AMD's decision to drop support for my Radeon Mobility HD4570. [http://www.kubuntuforums.net/showthr...9377-AMD-sucks]("http://www.kubuntuforums.net/showthread.php?59377-AMD-sucks") I'm in a pickle at the moment. Because of the Intel bug here [http://partiallysanedeveloper.blogsp...ux-freeze.html]("http://partiallysanedeveloper.blogspot.ca/2012/05/ivy-bridge-hd4000-linux-freeze.html")  I am forced to use 11.04 with this Dell Studio laptop FOREVER because  the ATI driver will never be updated to work with kernel versions that  have the Intel Sandy/Ivy Bridge bug fixed. I can not use the open source  radeon driver in any version of Linux because of heat issues. This has  literally made this $1000 laptop useless with Linux. The past few days I  have been looking at new laptops, and was surprised at how much the  graphics game has changed. AMD IS OUT for sure because of the crappy  support. The only other options are Intel and Nvidia. I wasn't aware of  the new Optimus scheme. I can't find a "new" laptop without the Optimus  hybrid graphics. The hacks/workarounds for it don't look appealing. This  leaves me with Intel. The newer Intel HD4000 reviews have been pretty  good as far as integrated graphics go. It would also be nice to have 3D  work out of the box without installing drivers and making suspend work.  My biggest concern is that the HD4000 will be "just enough", but leave  me wanting a little more compared to AMD/Nvidia equivalents. I don't do a  lot of heavy gaming. Minecraft and sauebraten/cube would be the most  demanding. If you are running the Intel HD4000 graphics, what are your  thoughts?

---

### Post by Dlambert on 2012-07-05
You will always get better performance with a Nvidia card. Intel is almost like a curse word when it comes to PC gaming.

---

### Post by Carborundum on 2012-07-05
> **Dlambert said:**
> You will always get better performance with a Nvidia card. Intel is almost like a curse word when it comes to PC gaming.
Always? Not true. The Intel HD4000 outperforms low-end NVIDIA cards such as GT 620, even if the proprietary NVIDIA driver is matched against Intel's open source driver.

As a point of reference, I can play *Amnesia: The Dark Descent* in 1920x1080 and fairly high settings with my HD4000 powered laptop. I don't think there are any Linux-native games available today that won't work on Ivy Bridge graphics.

For me, the main reason to go with Intel is the excellent out-of-the-box experience, which you won't see on Linux with any card that requires a proprietary driver to function correctly.

---

### Post by 67GTA on 2012-07-05
> For me, the main reason to go with Intel is the excellent out-of-the-box experience, which you won't see on Linux with any card that requires a proprietary driver to function correctly.


This is what I'm thinking. I've always made it a point to buy only laptops with Nvidia, but if I can play moderate games with HD4000 I will be tickled. Intel Haswell is supposed to be out in 2013, and is supposed to improve on the Ivy Bridge performance. I've found tons of Youtube videos with HD4000 tests. It looks like it would be more than enough for what I do with the laptop. The desktop is where I do my gaming with a GeForce GTX 570:guitar:.__

---

### Post by Dlambert on 2012-07-05
Low end is another story. If you can get a moderate Nvidia GPU it will kill Intel.

---

### Post by 67GTA on 2012-07-05
It seems like every new Intel i5/i7 only comes with hybrid graphics. I just didn't want to deal with the bumblebee/ironhide hack to make the Linux side usable. I found several reviews of the HD4000 playing demanding games with medium to low settings. It seems it will be enough for me from the responses I've gotten.
[https://www.youtube.com/watch?v=G41OA0qZiBY](https://www.youtube.com/watch?v=G41OA0qZiBY) My desktop will run BF3 at ultra settings without breaking a sweat with the GeForce GTX 570 and i7.

---

### Post by mastablasta on 2012-07-06
> **67GTA said:**
>  My desktop will run BF3 at ultra settings without breaking a sweat with the GeForce GTX 570 and i7.
 
on windows 7, right?
 
Some laptops with AMD have hybrid support (AMD+Intel) within AMD proprietary drivers.
[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

---

### Post by 67GTA on 2012-07-06
Yes Win7. I've never tried bf3 on Linux. AMD graphics will never happen again in my house. :mad:

---

### Post by Dlambert on 2012-07-06
I stand Corrected: > 
These OpenBenchmarking.org statistics aren't representative of the Linux desktop community as a whole, but tend to be more enthusiast and corporate oriented. It's the enthusiast/corporate/gamer types that are typically installing the Phoronix Test Suite to measure their Linux system(s) performance, many of whom do so when purchasing brand new hardware or considering an upgrade and deciding what component(s) to change. It's also the type of individuals that are generally knowledgeable about the different Linux graphics driver options with their pros and cons. For the overall market, Intel does have a large market-share in the graphics world due to their integrated graphics being quite common to OEM systems. 

As Intel gains ground, the biggest loser is NVIDIA while the ATI/AMD graphics adoption appears stable based upon the OpenBenchmarking.org statistics. 

SOURCE: [http://www.phoronix.com/scan.php?page=news_item&px=MTEzMzg](http://www.phoronix.com/scan.php?page=news_item&px=MTEzMzg)

---

### Post by mastablasta on 2012-07-07
> **67GTA said:**
> Yes Win7. I've never tried bf3 on Linux. AMD graphics will never happen again in my house. :mad:
 
Linus would disagree but ok. :-D nvidia seems to be having issues lately.
 
well i hope you find what you are looking for and let us know how it works out in the gaming area. i too am a bit puzzled by the whole thing. though if i was searchign for laptop now i would probably try to find the previously menitoned hybrid that works with proprietary drivers. especially since AMD is heavilly supporting opensource initiatives. i mean not just because they are supporting it but because their strategy is to give support to open platforms.

---

### Post by Andre-D on 2013-03-09
Running Trine2  in HD resolution, on HD4000 (i7 3770)  - It's very sluggish  (even at the beautiful intro screen - before menu)
nvidia GTX 570 : very smooth- perfect. (Nvidia current drivers)
"High Anti Aliasing , very high detail." for all testes.

Is this expected results on a Ubuntu 12.10 - or - should I get some other Intel drivers somehow ?

---

### Post by TheinsanegamerN on 2013-05-20
> **Andre-D said:**
> Running Trine2  in HD resolution, on HD4000 (i7 3770)  - It's very sluggish  (even at the beautiful intro screen - before menu)
nvidia GTX 570 : very smooth- perfect. (Nvidia current drivers)
"High Anti Aliasing , very high detail." for all testes.

Is this expected results on a Ubuntu 12.10 - or - should I get some other Intel drivers somehow ?

Try running in 1280x720 resolution, as 1080p might be pushing the hd 4000 a little hard. its decent, but it wont work wonders. The other thing i have to ask, is do you have only one memory module in your machine? if you are not running in dual channel, this will severly limit hd 4000 performance (heck, even intel hd 2000 was limited by single channel ram, and hd 4000 is three times faster than hd 2000). also, turn down anti-aliasing. AA eats up system ram, and is pretty demanding on hd 4000. try running it with fxaa and only high detail settings. ill bet your framerate will shoot through the roof from where it is now.

---

### Post by King Dude on 2013-05-20
Welcome to my Hell :twisted:

---

