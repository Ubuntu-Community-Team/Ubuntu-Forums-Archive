---
title: "Supertuxkart 0.8.1. running really slow"
date: 2013-12-28
forum: Gaming &amp; Leisure
---

### Post by mastablasta on 2013-12-28
So i instaleed Kubuntu 12.04.3, 32 bit on :
AMD 3200 2.4 Ghz signle core
Radeon 9200 128 MB (i think it's por but not sure) 
1 GB RAM

- the radeon driver page says: 
> **Fully Supported**

 All these Radeon(HD) cards and derivatives have good 3D acceleration support. This is not an exhaustive list:RV280                       Radeon 9200PRO/9200/9200SE/9250, M9+

Indeed running glxgears i get about 150 FPS-180FPS. all effects seem to work etc.

so far: 
-I've set it to disable special desktop effects for fullscreen apps.
-set all GPU settings in game down to minimum (resolution is also set to 800x600)

result:
i still get only a few FPS in game. the sound seems to be OK in game. 
the CPU is going like crazy but is not at 100% or at leats i can't see it at 100%). 
the RAM is not fully used. swap has only 20 MB out of over 2GB taken.

what is wrong? this game should work with a much weaker card i believe. at least with so many settings disabled and reduced to minimum...
i know this card is nothing special. and i know radeon opensource drivers are hit or miss. but they seem to work for the most of the time in system. 
and the card though old and nothing special could run Morrowind decently in windows XP.so it's not that crappy either. is there any tweaking i could do? could xorg edger PPA actually help? Adobe Flash also performs badly in fullscreen on low dpi. i've seen it do better on old Athlon 1,2 Ghz combined with s3 with 32MB taken form 256 MB RAM...

---

### Post by Arthur_D on 2013-12-28
Hi, you are probably experiencing issues due to the very low amount of VRAM available. I'd say 256 MB would probably be the bare minimum for running it at a decent speed, though there might be a workaround: there's a unofficial data package where all textures have been resized to fit within a much tighter space: [http://bayfiles.net/file/10C0X/75rACm/data.zip](http://bayfiles.net/file/10C0X/75rACm/data.zip)
At the moment the server seems down unfortunately, but you could also use the 'convert' terminal application to resize them yourself. If you do, don't resize the contents of folders data/gui and data/fonts folders as that may lead to some issues in the menus.

If you are playing on a desktop computer and have 50 dollars to spare I'd highly recommend getting a better graphics card (around where I live that will get you a Radeon HD 6450 with 1 GB VRAM). I know that probably isn't what you want to hear but as the years have gone by we want to improve how the game looks and that sadly places higher demands on hardware.

Hopefully you'll be able to keep enjoying the game. :)

---

### Post by mastablasta on 2013-12-29
aw.... that's troubling... what older version would work with this card then? i might try to resize them when i figure out how. or perhaps find something else to entertain on that old mashicne. there are a couple of old DOS games that should work ok.

i understand that the game has to move on. 

I won't be buying GPU card for this old thing. this motherboard has AGP interface and computer was upgraded a lot (only the small disk inside is orignal and box and it's abotu 15 years old) . computer will work until it works after it dies it will get canibalised. there is no point in investing anything into this old mashcine. i barely got it to work. i think one of the drives went bad in it. i just thought my kid could occasionaly play supertuxkart on it.

---

### Post by Arthur_D on 2013-12-29
I'm honestly not sure, but the 0.6.x versions should work fine I reckon. 0.7.x might work as well but textures were getting larger at that point.
Yeah with an AGP interface it would not be worth it; with a PCI slot it might have been.

DOS games should work indeed, but there's also some nice 2D FOSS games out there like Hedgewars, Battle for Wesnoth and more. Unfortunately for 3D games there are very few alternatives that will run well on that hardware - some early 2000 era games, Armagetron (a Tron clone) and maybe a few others. And as mentioned you could try SuperTuxKart 0.6.2 for example.

Edit: also I can try to get hold of the resized data package for you and put it on a better hosting site for you to download.

---

### Post by mastablasta on 2014-01-04
that ok no need. i will find some old dos and windows racing games and use wine.

it's not often i am there to mess arroudn with that old computer.

---

