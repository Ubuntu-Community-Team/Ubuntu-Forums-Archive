---
title: "3D games lag a lot on Ubuntu"
date: 2010-03-23
forum: Gaming &amp; Leisure
---

### Post by superarthur on 2010-03-23
My computer has a really crap Mobile Intel(R) 965 Express Chipset Family video card.
However, I could still play older 3D games like Morrowind, Sims 2, Hitman: Contracts, Fable and Medieval 2 Total War. (In medium-low qualities, but they still look quite good)
In Ubuntu, I tried to play games like Nexuiz and Lincity NG on Ubuntu, they seems to lag quite a lot.
If I can run better looking games on Windows smoothly, why do I experience lagging on worse looking games on Ubuntu?

(I don't know if lag is the right word, since some people uses lag for online games only. But some people also use it for impaired computer functionality resulting from poor hardware. :P)

---

### Post by _h_ on 2010-03-23
Integrated intel cards have..well, horrible 3D support in Linux, sadly.

I've got the same card as you, and I had troubles with alot of games in 9.10. I think it may be a bad driver, as I went full install of Lucid beta 1 and I can play alot more games now (but still cant seem to play WoW right, even in opengl without the hardware patch). :(

---

### Post by Perfect Storm on 2010-03-23
+1 what _h_ said.

You can't do much with that card. If it's a Desktop you should look for a nvidia/ati card (at current time a nvidia card). It doesn't have to be a top notch expensive one.

---

### Post by _h_ on 2010-03-23
> **Artificial Intelligence said:**
> +1 what _h_ said.

You can't do much with that card. If it's a Desktop you should look for a nvidia/ati card (at current time a nvidia card).

I'd definitely go for an nVidia, as ATI as just a few feet in front of Intel for 3D graphics support from what I can tell by reading the forums.

nVidia > ATI > Intel. Having the short stick sucks. :(

---

### Post by Perfect Storm on 2010-03-23
Yep, nvidia diffidently. I was just afraid to sound too biased towards nvidia, as some of our members says that the ATI driver have improved a lot and I have no way to test this. I only go for nvidia cards for my computer and the computers at my work.

---

### Post by Ferrat on 2010-03-23
> **Artificial Intelligence said:**
> Yep, nvidia diffidently. I was just afraid to sound too biased towards nvidia, as some of our members says that the ATI driver have improved a lot and I have no way to test this. I only go for nvidia cards for my computer and the computers at my work.

They have improved a lot the last year or two since AMD took over and made a pledge to improve the linux drivers they have made big strides, but from what I've see they have a few more things to work out before they are close to nVIDIA on the Linux front but they are getting better and compared to before that they are good, before they where almost as bad as Intel drivers are today. 

From what I understand they are more or less re-writing the drivers from scratch but doing it part by part so there are some issues that make them unstable in some cases as old and new parts have to interact, at least that my understanding of it, but when they have finally updated the entire driver it should work great just like nVIDIA's but that may be a year off or so.

---

### Post by superarthur on 2010-03-23
> **Artificial Intelligence said:**
> +1 what _h_ said.

You can't do much with that card. If it's a Desktop you should look for a nvidia/ati card (at current time a nvidia card). It doesn't have to be a top notch expensive one.

I use a laptop, and I don't think I can switch the video card. As a student, I have to travel around quite often, so I can't own a desktop.

But I think it's a bit ridiculous that even Lincity NG lagged with only a few buildings.

---

### Post by _h_ on 2010-03-23
> **superarthur said:**
> I use a laptop, and I don't think I can switch the video card. As a student, I have to travel around quite often, so I can't own a desktop.

But I think it's a bit ridiculous that even Lincity NG lagged with only a few buildings.

It's pretty much impossible to switch an integrated graphics card like we have, it would basically take a whole brand new mother board to even replace it.

Lincity-NG has some high end 3D effects (from what I could tell), of which our integrated Intel can't seem to handle.

---

### Post by superarthur on 2010-03-23
> **_h_ said:**
> It's pretty much impossible to switch an integrated graphics card like we have, it would basically take a whole brand new mother board to even replace it.

Lincity-NG has some high end 3D effects (from what I could tell), of which our integrated Intel can't seem to handle.

But it doesn't look high end. lol
Buildings in other 3D games I played look much better and still worked.
(I am accepting the fact that Intel video cards aren't supported in Linux. TBH, even in windows, I have to find the the driver support from the manufacturer, not Intel, and the driver is most likely not up-to-date.)

---

### Post by portets on 2010-03-23
lincity-ng is pretty slow on my geforce 9600. i'm pretty sure that it's just the game.

and nexuiz is really demanding requiring a pretty good computer

edit: also, i've heard from quite a few people that the next version of ubuntu improves intel graphics performance by quite a bit.

---

### Post by 3rdalbum on 2010-03-25
> **superarthur said:**
> But it doesn't look high end. lol
Buildings in other 3D games I played look much better and still worked.
(I am accepting the fact that Intel video cards aren't supported in Linux. TBH, even in windows, I have to find the the driver support from the manufacturer, not Intel, and the driver is most likely not up-to-date.)

Nexuiz is an extremely demanding 3D game. I don't know about your Lincity-NG problem; try turning off Compiz.

---

### Post by mastablasta on 2010-03-25
Especially oldder Intel chips were really crappy (concerning 3d) and should be used for office work mostly. Even today they are about half as good as the similar built in graphics card (ATI or Nvidia).

---

### Post by del_diablo on 2010-03-25
> **3rdalbum said:**
> Nexuiz is an extremely demanding 3D game. I don't know about your Lincity-NG problem; try turning off Compiz

With a good engine, I can run it with Mobility Radeon 3460 using the open drivers(which will get proper performance by summer, i guess) getting good GFX and framerate.
And since this is Ubuntu: ATI is super supported, to the point where its the only distro which ATI/AMD activly supports quite well(as in bother to make drivers for the latest X it ships).

---

### Post by _h_ on 2010-03-25
> **3rdalbum said:**
> Nexuiz is an extremely demanding 3D game. I don't know about your Lincity-NG problem; try turning off Compiz.

It's not that demanding if you play with the settings correctly.

On Karmic I couldn't even play Nexuiz due to it massive graphics issues of missing floors, black spots all over the place, weapon wasn't being drawn and that sort of "lag blur".

Went full Lucid and now I can play every single FPS from the PlayDeb repos.

Integrated Intel GM965 card. :)

---

### Post by Mjchopperboy on 2012-06-29
> **_h_ said:**
> I'd definitely go for an nVidia, as ATI as just a few feet in front of Intel for 3D graphics support from what I can tell by reading the forums.

nVidia > ATI > Intel. Having the short stick sucks. :(
Well I've go a nVidia GeForce 7100, and 3D games suck real bad. They lag at about 1 frame every 2 seconds. No exageration...

---

### Post by Sarys on 2012-06-29
So I can use my Emachines e725 for 2d games with linux? I have intel "card" and cause it's laptop no way of getting better one :(

And the funny thing is that Ubuntu 12.04 doesn't support my card too well (backlights don't work but that can be fixed)

EDIT: and it should have Intel® Graphics Media Accelerator 4500M

---

### Post by Dlambert on 2012-06-29
Not attempting to commit Necromancy, but turn off the Eye-candy in Ubuntu and run 2d unity.

---

### Post by Quackers on 2012-06-29
Thread closed as it's 2 years old.

---

