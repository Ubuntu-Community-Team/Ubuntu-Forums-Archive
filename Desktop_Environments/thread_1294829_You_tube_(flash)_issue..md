---
title: "You tube (flash?) issue."
date: 2009-10-18
forum: Desktop Environments
---

### Post by wlraider70 on 2009-10-18
So I have 2 old boxes I'm playing with. Both have new installs of ubuntu. 
They are both acting wierd on YouTube. When I first go there I get the seach plugs an it downloads flash. 


on One box it would not ever play. Just black or a freeze frame. after the lenth of the movie it would go to the suggestions normally. I tried installing every flash related package. No real change. 

On the other it's supper choppy. 

I'm not really sure what to try or where to look.

---

### Post by coldReactive on 2009-10-18
Are you trying to play the videos in fullscreen? That's a big no-no in linux.

---

### Post by stuart.reinke on 2009-10-18
> **coldReactive said:**
> Are you trying to play the videos in fullscreen? That's a big no-no in linux.

I watch videos full screen all the time. I have to disable all desktop effects and I increased my swap partition to 2 Gb.

---

### Post by coldReactive on 2009-10-18
> **stuart.reinke said:**
> I watch videos full screen all the time. **I have to disable all desktop effects** and I increased my swap partition to 2 Gb.

I didn't have to do this last time I checked, but most people do.

---

### Post by ikt on 2009-10-18
> **stuart.reinke said:**
> I watch videos full screen all the time. I have to disable all desktop effects and I increased my swap partition to 2 Gb.

You can watch youtube videos in full screen however it is choppy and often will get out of sync, poor full screen performance is a known issue with flash on linux, and dell has mentioned they're attempting to work with adobe to fix this.

---

### Post by stuart.reinke on 2009-10-18
> **ikt said:**
> You can watch youtube videos in full screen however it is choppy and often will get out of sync, poor full screen performance is a known issue with flash on linux, and dell has mentioned they're attempting to work with adobe to fix this.

Is is an Adobe issue? I always assumed that it was because of my ATI video and fairly low amount of RAM.

---

### Post by clhsharky on 2009-10-18
HI wlraider70

You can check required

RECOMMENDED HARDWARE FOR STANDARD- AND HIGH-DEFINITION (HD) VIDEO PLAYBACK

here [http://www.adobe.com/products/flashplayer/systemreqs/](http://www.adobe.com/products/flashplayer/systemreqs/)

---

### Post by coldReactive on 2009-10-18
> **clhsharky said:**
> HI wlraider70

You can check required

RECOMMENDED HARDWARE FOR STANDARD- AND HIGH-DEFINITION (HD) VIDEO PLAYBACK

here [http://www.adobe.com/products/flashplayer/systemreqs/](http://www.adobe.com/products/flashplayer/systemreqs/)

Strange, OSS and ESD plays flash audio fine for me. o_O

---

### Post by Marlonsm on 2009-10-18
Youtube fullscreen (including HD) works great for me, all I had to do was to change the graphics driver for my nvidia card.

---

### Post by wlraider70 on 2009-10-19
Ok 1. Why no full screen
2.  how do I / should I change the swap to 2 gig
3. I'll go to  that site from my pc tommorrow 
4. One of them is a Dell and it is the one with almost no YouTube ability. 

So what can I do?

---

### Post by coldReactive on 2009-10-19
> **wlraider70 said:**
> Ok 1. Why no full screen
2.  how do I / should I change the swap to 2 gig
3. I'll go to  that site from my pc tommorrow 
4. One of them is a Dell and it is the one with almost no YouTube ability. 

So what can I do?

As for 2, you'll need to resize all your partitions to get a bigger swap size. This might change in the future, as I think it's much better to use a swap file in my opinion, so you don't have to needlessly partition a part of the hdd for swap.

---

### Post by wlraider70 on 2009-10-19
I opened g parted.
I tuned off swap
clicked resize
it said maximum size MiB 1279.

Is there a reason that i can go to 2 gig. its an 80 gig drive.

---

### Post by coldReactive on 2009-10-19
> **wlraider70 said:**
> I opened g parted.
I tuned off swap
clicked resize
it said maximum size MiB 1279.

Is there a reason that i can go to 2 gig. its an 80 gig drive.

Did you make sure to resize your other non-swap partitions smaller so that the swap has enough room to resize or claim unpartioned space?

It's actually better to get a big swap size when you first install Ubuntu so you don't have to do this in the future, as resizing can be dangerous.

---

### Post by ssouthparkk on 2009-10-19
How come I can play full screen?  I don't have any issues...

---

### Post by wlraider70 on 2009-10-19
I didn't shrink the main part, I'm willing to risk it since I'm trying get this computer up and running, right now its not really doing anything. 

how do I shrink the running partition i could re-install if i have to.



HOWEVER, one of my goals was to use hulu. At this point im wondering if it is ever possible to get smooth flash. should i even bother.

---

### Post by coldReactive on 2009-10-19
> **wlraider70 said:**
> how do I shrink the running partition i could re-install if i have to.

You have to boot from the livecd in order to do that.

---

### Post by wlraider70 on 2009-10-19
ok i changed to swap file to 1.98 gig (slight math error on my part)

Hulu desktop applications looks much better, but not quite perfect. does that use flash?

You tube is not any better. 
Hulu.com will not play anything?

could there be a firefox issue?

Any other suggestions?

---

### Post by RJARRRPCGP on 2009-10-24
> **ikt said:**
> You can watch youtube videos in full screen however it is choppy and often will get out of sync, poor full screen performance is a known issue with flash on linux, and dell has mentioned they're attempting to work with adobe to fix this.

The cause of this, appears to be the MTRR not-set-properly bug. 

When I ran a bash script (IIRC) made to correct the MTRR setting, it was fine when I tried YouTube in full screen. 

If doing ```
cat /proc/mtrr
``` shows no write combining, when your graphics hardware is Intel, then that appears to be the problem.

---

### Post by RJARRRPCGP on 2009-10-24
> **wlraider70 said:**
> Ok 1. Why no full screen
2.  how do I / should I change the swap to 2 gig
3. I'll go to  that site from my pc tommorrow 
4. One of them is a Dell and it is the one with almost no YouTube ability. 

So what can I do?

Don't change the swap unless you get an out-of-memory error.

---

### Post by wlraider70 on 2009-10-24
luke@LPCC:~$ cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back
reg01: base=0x03c000000 (  960MB), size=   64MB, count=1: uncachable
reg02: base=0x0e0000000 ( 3584MB), size=   64MB, count=2: write-combining
reg03: base=0x0e4000000 ( 3648MB), size=   64MB, count=1: write-combining


i dont really know what this means?

---

### Post by lordofduct on 2009-10-24
> **wlraider70 said:**
> Ok 1. Why no full screen
2.  how do I / should I change the swap to 2 gig
3. I'll go to  that site from my pc tommorrow 
4. One of them is a Dell and it is the one with almost no YouTube ability. 

So what can I do?

1) there is fullscreen... I use it all the time. I also dev flash and flex apps in Linux every day (my display is 2560x1600 at that). You need good system specs though for full screen, it's just a costly process for flash. Fullscreen can be assisted greatly by hardware rendering (if you have a GPU) but Linux support for this is rather gimp.

2) someone's already helping you with this...

3) That site will tell you min specs they expect you to have. So check there to see if you system meets them... assume you need more for fullscreen. Flash is one hell of a memory hog, it's just the way the object data structure works in memory. JIT compiler and dynamic hash tables are memory beasts.

4) How old of a Dell? What video is on it (I'm suspecting intel integrated video, most cheap older Dell's are). Those specs will help you out.

---

### Post by wlraider70 on 2009-10-24
I did it.

I stopped using the dell so its not fixed.

what happened was somehow swfdeck got installed. ( i may have done it while i was trying to fix it or firefox may have made me). 

anyway i i removed them and made sure that there were other flash plugins in were in and its perfect.

I can do every thing.

THANKS

---

