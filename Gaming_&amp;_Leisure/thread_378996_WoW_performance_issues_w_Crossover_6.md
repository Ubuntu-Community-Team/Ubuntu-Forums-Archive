---
title: "WoW performance issues w/ Crossover 6"
date: 2007-03-08
forum: Gaming &amp; Leisure
---

### Post by SDREnate on 2007-03-08
I just managed to install WoW using Crossover 6 on my laptop (Dell Inspiron 1501). When I was running Windows, WoW ran just fine on it. Now, however, I get choppy sound and video performance. I've been looking for some answers, and I've found a lot of people saying that the ATI drivers aren't very good (I installed the latest fglrx drivers).

Specs:
1 GB RAM
ATI Radeon Xpress 1150
AMD Turion 64 
Ubuntu 6.10

My video card also uses shared memory, and I'm not sure if there's any way to change the amount of memory assigned to the card. So basically, I was just wondering if there's any way to increase performance, of if the ATI cards are just doomed because of crappy drivers.

---

### Post by Sammi on 2007-03-08
I'm not sure how this works for CrossOver, but the first thing one does for Wine is the registry tweak found here:[ https://help.ubuntu.com/community/WorldofWarcraft]("https://help.ubuntu.com/community/WorldofWarcraft")

---

### Post by SDREnate on 2007-03-08
> **Sammi said:**
> I'm not sure how this works for CrossOver, but the first thing one does for Wine is the registry tweak found here:[ https://help.ubuntu.com/community/WorldofWarcraft]("https://help.ubuntu.com/community/WorldofWarcraft")

I reinstalled WoW using wine, following the howto you posted exactly. I also did all the performance tweaks listed in the HowTo. When trying to run WoW in wine now, I get even worse performance than with Crossover. I'm starting to think that the problem lies in the amount of RAM the video card is using (since it uses system memory rather than its own). I'm not sure if there is a way to change it. I couldn't find any options in BIOS, and I haven't been able to locate anything helpful on the web.

edit- I'm also starting to believe that my card doesn't really even support 3d in linux anyway.

---

### Post by Sammi on 2007-03-09
Try some other 3d games to see if 3d works. And then look at this compatibility list:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)

If you don't see your card then please add it and state if it works or not.

EDIT: I must have been very tired when I first wrote this post. It didn't make sense, so I edited it.

---

### Post by SDREnate on 2007-03-11
> **Sammi said:**
> Try some other 3d games to see if 3d works. And them this compatibility list:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)

If you don't see your card then please add it and state if it works or not.

Just an update-

My xorg.conf identifies my card as a Radeon Xpress 200M. I installed Steam and Counter-Strike using Crossover yesterday and it runs flawlessly, so I guess that 3d is supported by this card.

---

