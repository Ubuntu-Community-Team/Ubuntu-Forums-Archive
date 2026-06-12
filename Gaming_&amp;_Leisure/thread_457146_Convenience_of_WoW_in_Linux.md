---
title: "Convenience of WoW in Linux?"
date: 2007-05-28
forum: Gaming &amp; Leisure
---

### Post by GaMz on 2007-05-28
As I'm sitting here downloading the .iso for Ubuntu, I am wondering how World of Warcraft runs after the recent patch and how hard the initial setup is?

As of right now, WoW is the only game I play on my computer.  Can anyone give any insight whether I should keep Windows on my computer solely to play WoW? Or is it simple enough in Wine (or similar program) to set up to play?


Eh...sorry if this is posted before, I did a quick search and  couldn't really find the answers I was looking for.

---

### Post by gvoima on 2007-05-28
I recommend keeping windows for playing, but WoW is 100% playable on linux too under wine.
Atleast on my computer it works just as it did on windows.

I followed these instructions, they are very good.
[Linux - Wine]("http://www.wowwiki.com/Linux/Wine")

I've used quite alot of linux so the install of WoW was pretty straightforward and easy.

It will be to you to if you just follow the instructions ;-)

---

### Post by Sammi on 2007-05-28
What are your system specs?

cpu, ram, graphics card...

Remenber ATI cards are almost useless in Linux because ATI are such lazy *******. They haven't written any stable Linux drivers yet!

---

### Post by GaMz on 2007-05-28
> **Sammi said:**
> What are your system specs?

cpu, ram, graphics card...

Remenber ATI cards are almost useless in Linux because ATI are such lazy *******. They haven't written any stable Linux drivers yet!

I'm running an HP Laptop with:

Intel(R) Core(TM) 2 Duo T5600(1.83GHz/2MB L2Cache)
15.4" WXGA BrightView Widescreen (1280x800)
256MB NVIDIA(R) GeForce(R) Go 7400
2GB DDR2 System Memory (2 Dimm) 
80GB 5400 RPM 
8X DVD+/-R/RW w/Double Layer Support
Intel(R) PRO/Wireless 3945ABG Network Connection

Thanks for the quick replies so far :D

---

### Post by gvoima on 2007-05-28
Don't worry, that's a sweet WoW combo ;)

---

### Post by GaMz on 2007-05-28
> **gvoima said:**
> Don't worry, that's a sweet WoW combo ;)

Hehe, I hope so ;)

I'm going to try setting it up on the LiveDVD I'm going to make, and see how it runs. (You can do that right?)

Thanks for the posts

---

### Post by hikaricore on 2007-05-28
> 256MB NVIDIA(R) GeForce(R) Go 7400
2GB DDR2 System Memory (2 Dimm) 

Oh you should have nothing to worry about.

You won't be able to run WoW properly on a live cd, you'll need to install Ubuntu for best results.

Unless you have enough RAM to hold build-essential, system updates, nvidia binary drivers, and a full copy of WoW.  Which trust me you don't.  ^_^

Just give Ubuntu a try and make sure you install the proprietary video drivers for your card.
Search around for [Envy]("http://albertomilone.com/nvidia_scripts1.html") if you need help installing said drivers.

Then follow the community WoW howto and you should be set. [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by GaMz on 2007-05-28
> **hikaricore said:**
> Oh you should have nothing to worry about.

You won't be able to run WoW properly on a live cd, you'll need to install Ubuntu for best results.

Unless you have enough RAM to hold build-essential, system updates, nvidia binary drivers, and a full copy of WoW.  Which trust me you don't.  ^_^

Just give Ubuntu a try and make sure you install the proprietary video drivers for your card.
Search around for [Envy]("http://albertomilone.com/nvidia_scripts1.html") if you need help installing said drivers.

Then follow the community WoW howto and you should be set. [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Thanks, I wasn't planning on running it from a LiveCD permanently I was just going to see if I could set it up to, but I'm just going to install the full thing and mess around from there.

Thanks for the advice everyone

---

### Post by Sammi on 2007-05-29
Your systems specs are pretty much ideal for WoW in Linux. Have fun :D

---

### Post by Ferrat on 2007-05-29
> **Sammi said:**
> What are your system specs?

cpu, ram, graphics card...

Remenber ATI cards are almost useless in Linux because ATI are such lazy *******. They haven't written any stable Linux drivers yet!

Please know what you are talking about before you open your mouth, true that the nvidia drivers are way more optimal for gaming on Linux ect. and that the ATi drivers need a workover (which according to AMD is comming soon) 

but saying that ATi drivers are more or less useless is a show of no concept of the matter what so ever, ATi drivers running WoW can produce more than ok results, I've raided ect with my card with pretty high settings on the grafics and allways had a playable FPS.

---

### Post by hikaricore on 2007-05-29
> **Ferrat said:**
> Please know what you are talking about before you open your mouth, true that the nvidia drivers are way more optimal for gaming on Linux ect. and that the ATi drivers need a workover (which according to AMD is comming soon) 

Sammi was making a broad generalization about ati cards.  Maybe it wasn't the best way to word things, but just based on forum experience, ATI cards usually cause a ton of confusion and frustration.  Anyway there's no reason to start a flame war over it.

---

### Post by Rogers on 2007-05-29
ATI cards are problematic at best... I have had 2 ati machines before I bought my 7900GT from nvidia for Linux.   

ATI Cards Can't...........
[LIST=1]
[*]Run anything in anything below 32 bit color depth
[*]Change color depth for applications
[*]Run starcraft via wine without editing the xorg.conf to make X useless for anything but SC.
[/LIST]

---

### Post by ubuntu.daemon on 2007-05-29
> **GaMz said:**
> I'm running an HP Laptop with:

Intel(R) Core(TM) 2 Duo T5600(1.83GHz/2MB L2Cache)
15.4" WXGA BrightView Widescreen (1280x800)
256MB NVIDIA(R) GeForce(R) Go 7400
2GB DDR2 System Memory (2 Dimm) 
80GB 5400 RPM 
8X DVD+/-R/RW w/Double Layer Support
Intel(R) PRO/Wireless 3945ABG Network Connection

Thanks for the quick replies so far :D

lol that be awesome!  
check out this thread for an official howto and what ull need to get started.  pretty self explanatory,
and the guys in the forums are always helpful. GL!

:popcorn:

[http://appdb.winehq.org/appview.php?iVersionId=6482](http://appdb.winehq.org/appview.php?iVersionId=6482)

---

### Post by Sammi on 2007-05-30
When I say that ATI is useless it's because I don't think 99% stability (that only some ATI users are getting, while others are getting nothing at all) is enough. They've got to be 100%.

> **Ferrat said:**
> ...and that the ATi drivers need a workover (which according to AMD is comming soon)
I hope so. I really really hope so. But given ATI's track record of letting Linux users down, I'm not holding my breath.

> **Ferrat said:**
> ... ATi drivers running WoW can produce more than ok results, I've raided ect with my card with pretty high settings on the grafics and allways had a playable FPS.
Yes they caaaaan... but what about all the people having troubles with them? I find it to be unfair to promise people that games will run well with ATI when people are also very likely to experience big problems with them. And noobs will come in here to flame, just as we are seeing right now all the time. I will probably start referring them to you, if it's you that's giving them high hopes.

One of these days I'm going to write a long rant about how much I hate ATI.

Did  I mention that I hate ATI?

---

### Post by ubuntu.daemon on 2007-05-31
lol ati does have a number of issues with wine, hence if you look at all the old versions how many had to be patched to work with wow even.  thats why nvidia + linux = l33t!  BUT the recent ati + amd merger has me sad bc i dont really like intel enuf to move to it, but i dont know why.....;)

---

### Post by ShadowFlar3 on 2007-05-31
Well I was a complete linux noob 4 months ago and I managed to get wow up and running on ubuntu in 2 days with very little outside IRL help. Pretty much just followed tutorials and I made it work.

Whenever there was trouble with ATI I always managed to fix them and mostly they occurred because I didn't simply know enough of things before doing them. So I'd only say (installation-wise) nvidia cards are more "idiotproof" than ATI. 

But yeah you gotta hate ATI for not supporting linux as much as they should, though.

---

