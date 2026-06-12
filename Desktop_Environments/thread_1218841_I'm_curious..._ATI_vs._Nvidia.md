---
title: "I'm curious... ATI vs. Nvidia"
date: 2009-07-21
forum: Desktop Environments
---

### Post by Paul Miller on 2009-07-21
Since all of my current machines use Nvidia cards, I was wondering, should I choose to build a new system, how well do ATI cards work with Ubuntu compared to Nvidia cards?  I have, in fact, never had a system that used an ATI card, so any information would be quite valuable.

---

### Post by bacil on 2009-07-21
I got ATI in one of my laptops. and 9.04 worked in native resolution form the box. So i would say no problem at all :-)

---

### Post by hblaw on 2009-07-21
Don't mislead others. When you say it works out of the box, you need to give the card information and how well it works. For ATI X1250, it works out of the box but is very slow on 9.04 and I need to switch back to 8.10. That's due to the lack of proprietary drivers.

---

### Post by djbushido on 2009-07-21
I much prefer nVidia cards. In my experience, they work better, personally, and are a bit more open with their drivers. Plus, the corporate drivers are relatively up-to-date. I'm running an older card (GeForce 4) but it works fine, and I would personally recommend against ATI. Plus, green is totally cooler than red. Although that isn't exactly a good reason to not buy ATI...

---

### Post by mhurst102282 on 2009-07-21
> **hblaw said:**
> Don't mislead others. When you say it works out of the box, you need to give the card information and how well it works. For ATI X1250, it works out of the box but is very slow on 9.04 and I need to switch back to 8.10. That's due to the lack of proprietary drivers.
That may be th case in your system, but I have the same card and it works fine for me.

---

### Post by mhurst102282 on 2009-07-21
> **djbushido said:**
> I much prefer nVidia cards. In my experience, they work better, personally, and are a bit more open with their drivers. Plus, the corporate drivers are relatively up-to-date. I'm running an older card (GeForce 4) but it works fine, and I would personally recommend against ATI. Plus, green is totally cooler than red. Although that isn't exactly a good reason to not buy ATI...
ATI has given source code to the linux kernel for there cards meaning you won't need to use a proprietary drivers. Nvidia on the other hand hasn't and wants to keep there code a secret.

---

### Post by powel212 on 2009-07-21
I have 2 machines side by side, one with an ATI Card and one with Nvidia.

The Nvidia graphic support is without a doubt the best. 

The Ati card works quite well out of the box with Jaunty but it would not run at all without serious command line restructuring back when I first used it with Hardy.

I also have machines with intel cards and even old Trident hardware. Of them all Nvidia is the clear winner.

All of the machines I build now get Nvidia cards and I always tell my customers to buy nothing but Nvidia.

This is all of coarse based on personal experience and is only my very humble opinion.

Powel

---

### Post by del_diablo on 2009-07-21
My experience is that the grapic runs quite well with my ATI card.
My only problem is that the propitary driver in the repos is old, but i have a good enough performance to run hard 3D for my card anyway.

---

### Post by mudcat on 2009-07-21
ATI Radeon 9200 ;)

---

### Post by ssri on 2009-07-21
> **mhurst102282 said:**
> ATI has given source code to the linux kernel for there cards meaning you won't need to use a proprietary drivers. Nvidia on the other hand hasn't and wants to keep there code a secret.

Really?  THat's news to me.  I thought ATI merely released documentation for their cards up to R7xx series after lengthy consultation with their legal dept.  It is the work of their in-house devs and open-source volunteers to bring the opensource drivers up to spec.  Sadly, even for R5xx cards, 3D acceleration is not up to snuff quite yet (OpenGL 2.0, GLSL support).  Their lead dev mentioned that they are waiting for gallium3D to be merged into the kernel before releasing any of their commits.

---

### Post by Paul Miller on 2009-07-21
The impression I'm getting is that ATI cards work serviceability well, but if you need tonnes of raw performance, it's nVidia all the way.  Is that correct?

Personally, I don't run anything any more graphics-heavy than compiz (and even that I've gotten away from) and Civilization 4 via wine.  Since I'm used to running Civ on a laptop, I think even if I got a new machine with a mid-range ATI card, it might be okay for me.  

The reason I'm even asking the question to begin with is that I'm considering purchasing an AMD Phenom system, and practically all of them come with ATI cards (duh, of course, because AMD now owns ATI).  So, I suppose the real question I need to answer is: is GPU performance, reliability, and stability enough of a reason to go with an nVidia + Intel platform, or is AMD + ATI a reasonable solution for someone like me who isn't a big 3D gamer?

Your thoughts on this particular issue will be of interest (though I'm also interested in the general question as I first posted it).

---

### Post by krazyd on 2009-07-22
> **Paul Miller said:**
> So, I suppose the real question I need to answer is: is GPU performance, reliability, and stability enough of a reason to go with an nVidia + Intel platform, or is AMD + ATI a reasonable solution for someone like me who isn't a big 3D gamer?
In my experience, the nvidia drivers aren't terribly reliable or stable (suspend still doesn't work on my notebook, and see all the bugs in launchpad), but (when they work) they provide the best 3D and video (VDPAU) performance on linux right now.

On the other hand, the open source ATI drivers are rock solid for everything they support - except they don't support 3D or video decode acceleration (for the HD2xxx, HD3xxx, HD4xxx series). 3D support is coming since AMD has released all the specifications for their cards, but it's not there yet.

So right now, if you don't need 3D and have a fast enough CPU to decode 1080p video (which is nearly all new CPUs), I'd go ATI. Otherwise, nvidia.

Personally, I've got a Radeon HD4850 which works for me since for gaming I just boot vista :P - the games I want to play don't work on linux or wine :(

---

### Post by zakloni on 2009-07-22
I love ati better because i am using it in graphics its better from nivada that i had it before

---

### Post by xzero1 on 2009-07-23
> **Paul Miller said:**
> The impression I'm getting is that ATI cards work serviceability well, but if you need tonnes of raw performance, it's nVidia all the way.  Is that correct?

Personally, I don't run anything any more graphics-heavy than compiz (and even that I've gotten away from) and Civilization 4 via wine.  Since I'm used to running Civ on a laptop, I think even if I got a new machine with a mid-range ATI card, it might be okay for me.  

The reason I'm even asking the question to begin with is that I'm considering purchasing an AMD Phenom system, and practically all of them come with ATI cards (duh, of course, because AMD now owns ATI).  So, I suppose the real question I need to answer is: is GPU performance, reliability, and stability enough of a reason to go with an nVidia + Intel platform, or is AMD + ATI a reasonable solution for someone like me who isn't a big 3D gamer?

Your thoughts on this particular issue will be of interest (though I'm also interested in the general question as I first posted it).

I am currently running Ubuntu 9.04 with a Phemom II mb with an onboard fanless ati 3300IGP using ati catalyst 9.6. Once set up properly there are no issues to report! My previous card was Nvidia and I did have xorg stability issues with both the ati and nvidia *recommended* drivers. Since the graphics is built into the mb I don't get blazing speeds but my favorite games are still very playable usually at lower resolutions. To my surprise the chip also provides gpu accelerated video (AVIVO), full resolution 1080p24 video plays smoothly even when I lock down my cpu speed to 800Mhz. Note that the acceleration does not work in a windowed mode.

---

