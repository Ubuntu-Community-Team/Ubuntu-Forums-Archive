---
title: "Ubuntu on USB Performance Help"
date: 2009-04-01
forum: General Help
---

### Post by chrini on 2009-04-01
Greetings fellow Ubuntu enthusiasts!
 
I've recently installed Ubuntu 8.04 on an 8 GB USB pen drive and I am having some issues with performance. A little side note, I used a pen drive because I am only using Ubuntu for "hobbiest" programming and some web surfing, and I still wanted XP to be my main OS on the internal HDD (I am using a laptop in case anyone is wondering). I do have a 120 GB internal HDD that is almostl full, but I am willing to partion a little bit if needed. My other (main) intention of putting Ubuntu on a USB is that I could have XP load up automatically and would have to select "boot from USB" whenever I wanted to run ubuntu... thus eliminating the GRUB loader which I want to do.

Anyways, my main problem is with firefox... it is constantly freezing up for 30+ seconds while loading a web page (I watch as the light on my USB drive goes into a frenzy until firefox un freezes). And with high speed internet this is very frustrating. It seems to do ok with other programs (i.e. Vuze, Open-office, etc.), it seems to only be firefox.

Here is what I was thinking was the problem/fix:

Because the reading/writing is all occurring through USB I'd expect things such as downloading, opening programs, etc. to be a bit slower, but with 3 GB of RAM I figured it wouldn't be too big of an issue using firefox (at least that is how I understand it?). So then I thought that maybe it was because I have a ~3 GB swap partition on the USB and it was doing a lot of reading/writing there and that was taking up all the time... but it is using zero swap (free -m). So my initial idea was to cut down on the swap and use more physical memory, but apparently it already is.

Does any one have any tips, tricks, or suggestions to make the performance a little better on the USB install? Keep in mind that I am willing to partion a little bit of my internal HDD if needed (as a secondary hda). Or if anyone knows of a way to have XP load up automatically without the GRUB loader while also (somehow) having the option of booting into Ubuntu, then that would be great. 

NOTE: I also thought about just doing a LiveCD USB and, in fact, I'm not entirely sure why I didn't choose that route. I guess I wasn't 100% sure how configurable (if at all) the "LiveUSB" would be once I installed it on the USB.

---

