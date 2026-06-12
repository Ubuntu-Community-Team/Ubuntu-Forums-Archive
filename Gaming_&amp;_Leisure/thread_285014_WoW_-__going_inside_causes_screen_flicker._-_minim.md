---
title: "WoW -  going inside causes screen flicker. - minimap fixes?"
date: 2006-10-26
forum: Gaming &amp; Leisure
---

### Post by x01000100 on 2006-10-26
Hey, I have searched the forums but onone didnt really come up with a solution other than that mod that disables minimap inside. But that is very irritating because I cant see where quest ends for example.

So, I basicly need a guide to  fix this damn flickering on screen (my eyes hurts like hell from it :p)

I have AMDD64 3200+
1,5gb ram
GF4 TI 4400
Kubuntu desktop 32bit.


**Edit: finally got it to work, it was really easy!!!**

Download this, a prepatched wine for wow [http://thepiratecove.org/files/wine-0.9.21_wow_i386.deb](http://thepiratecove.org/files/wine-0.9.21_wow_i386.deb) Rightclick it and select install package. Done :). 

Enjoy. Dont know if you get higher FPS, but look at my FPS at 2nd pic, its great. I dont know if i had the same FPS at that point before. Anyways, it great playing with minimap!! :D

Pics:
[http://img183.imageshack.us/my.php?image=wowmm2.jpg](http://img183.imageshack.us/my.php?image=wowmm2.jpg)
[http://img97.imageshack.us/my.php?image=wow1hm8.jpg](http://img97.imageshack.us/my.php?image=wow1hm8.jpg)

---

### Post by Jorenko on 2006-10-26
I just upgraded to edgy, and I'm having the same problem. It was working perfectly in dapper. I've tried with standard edgy wine, with wine's official dapper build (which is what I was using before) and both have the same problem. I tried to build wine 0.9.23, but it segfaulted no matter what I tried to do with it.

Athlon XP 2000+
1 GB ram
GeForce4 Ti4400
Ubuntu Edgy Eft

Hey, we have the same video card. Maybe this is a video driver problem? I had nvidia-glx-dev installed before upgrading to edgy, but it wouldn't let me upgrade til I got rid of it. When I tried to reinstall it later, there were some odd dependancy issues with not having the right version of mesa.

---

### Post by hampton275 on 2006-10-26
I did some looking around. It seems that there is a"flicker" issue with nvidia cards and wine. there is a patch out, but everytime I compile wine and run it I get a consistent segfault, so  am between a rock and a hard place. If anyone figures this out, please post it.

TIA

---

### Post by Jorenko on 2006-10-26
After some research, it looks like [this page](http://appdb.winehq.org/appview.php?iVersionId=5606&iTestingId=6773) has [a fix](http://rapidshare.de/files/36686174/wow_patch_nvidia_flicker_fix_0.9.23.diff.html) for the nvidia flicker and [this bug report](https://launchpad.net/distros/ubuntu/+source/wine/+bug/56965) has a fix for the segfault when building from source (add -fno-stack-protector to your CFLAGS).

I'm building with these now, we'll see if it works in an hour or so.

Edit: It does indeed work. Woohoo!

---

### Post by Ferrat on 2006-10-27
> **Jorenko said:**
> After some research, it looks like [this page](http://appdb.winehq.org/appview.php?iVersionId=5606&iTestingId=6773) has [a fix](http://rapidshare.de/files/36686174/wow_patch_nvidia_flicker_fix_0.9.23.diff.html) for the nvidia flicker and [this bug report](https://launchpad.net/distros/ubuntu/+source/wine/+bug/56965) has a fix for the segfault when building from source (add -fno-stack-protector to your CFLAGS).

I'm building with these now, we'll see if it works in an hour or so.

Edit: It does indeed work. Woohoo!


You are runnig it on Edgy? :) 
Im currently running on Dapper but from what I've heard Edgy gives better preformance, can you verify this? :)

---

