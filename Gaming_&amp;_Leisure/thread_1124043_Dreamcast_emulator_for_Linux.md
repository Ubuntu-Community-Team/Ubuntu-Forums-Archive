---
title: "Dreamcast emulator for Linux"
date: 2009-04-12
forum: Gaming &amp; Leisure
---

### Post by arashiko28 on 2009-04-12
Hello! I have a Lenovo Ideapad Y530, and I want to run a dreamcast emulator, I tried to run the nullDC for windows from wine and play on linux, yet had no success, especially for having to create my own script - I have no idea how to do that... at least not one that works- also tried with lxdream but there are a few errors about the video. Do I have any hope about this?

---

### Post by arashiko28 on 2009-04-13
BUMP!

Anyone? Is it so hard to emulate a console game on Ubuntu?

---

### Post by wingnux on 2009-04-13
nullDC and chankast work just fine for me under wine.

---

### Post by Mokoma on 2009-04-13
lxdream is coming along nicely

[http://www.lxdream.org/news/](http://www.lxdream.org/news/)

but to be honest just go and buy a secondhand dc. nothing beats playing shenmue on the real thing :D

---

### Post by arashiko28 on 2009-04-13
The real problem comes as I've mentioned before, it needs some scripts to be done and and I know nothing about that. I already tried to install lxdream, and don't get to the point. I have about 4 scripts done but none of them seems to work. :(

---

### Post by Mokoma on 2009-04-13
> **arashiko28 said:**
> The real problem comes as I've mentioned before, it needs some scripts to be done and and I know nothing about that. I already tried to install lxdream, and don't get to the point. I have about 4 scripts done but none of them seems to work. :(

dude you dont need scripts to install lxdream its a deb!

---

### Post by Mokoma on 2009-04-13
ok just read your post properly. what issues where you facing, i can run rez flawlessly on a pretty medicore system :P

---

### Post by arashiko28 on 2009-04-13
> **Mokoma said:**
> ok just read your post properly. what issues where you facing, i can run rez flawlessly on a pretty medicore system :P

Unable to create render buffers (requires either EXT_framebuffer_object or GLX 1.3+)

Video driver "gtk" failed to initialize

These are the messages I get from lxdream.

From play on linux, it requires a script supposedly made by the user.

demul shows a screen like the snapshot before but the screen it's not complete and doesn't show the last box to configure and save, tried to enlarge it, but no good.

What I'm really looking for is something that works out of the box or with a manual for dummies.

---

### Post by Johnny19734 on 2009-04-13
DUDE, 

Install wine from add/remove.

Then download nullDC(just google it), its the best DC emu out there anyway.

Intall the exe under wine and boom your done.

Dont forget you have to have the DC bios for this emu as well, and don't ask me ask google :)

---

### Post by wingnux on 2009-04-13
> **arashiko28 said:**
> Unable to create render buffers (requires either EXT_framebuffer_object or GLX 1.3+)


Video driver "gtk" failed to initialize.

Can you post your system specs? It seems that you don't have your graphics card's driver installed.

---

### Post by Mokoma on 2009-04-13
> **Johnny19734 said:**
> DUDE, 

Install wine from add/remove.

Then download nullDC(just google it), its the best DC emu out there anyway.

Intall the exe under wine and boom your done.

Dont forget you have to have the DC bios for this emu as well, and don't ask me ask google :)

nulldc sucks under wine! go with a native application like lxdream, stop running back to windows :P

---

### Post by Mokoma on 2009-04-13
> **arashiko28 said:**
> Unable to create render buffers (requires either EXT_framebuffer_object or GLX 1.3+)

Video driver "gtk" failed to initialize

These are the messages I get from lxdream.

From play on linux, it requires a script supposedly made by the user.

demul shows a screen like the snapshot before but the screen it's not complete and doesn't show the last box to configure and save, tried to enlarge it, but no good.

What I'm really looking for is something that works out of the box or with a manual for dummies.

what graphics card/chip are you using? 

if its an intel your probably just better off with windows

---

### Post by Johnny19734 on 2009-04-13
> **Mokoma said:**
> nulldc sucks under wine! go with a native application like lxdream, stop running back to windows :P

NullDC has superior coding, sorry it just does. You could even run Chankast which is better. I wouldn't want to run an emu that doesn't play games. #-o

---

### Post by arashiko28 on 2009-04-13
> **Johnny19734 said:**
> DUDE, 

Install wine from add/remove.

Then download nullDC(just google it), its the best DC emu out there anyway.

Intall the exe under wine and boom your done.

Dont forget you have to have the DC bios for this emu as well, and don't ask me ask google :)

I already did that as my first option and simply doesn't run, just thinks for a few seconds and then... nothing...

---

### Post by arashiko28 on 2009-04-13
> **Mokoma said:**
> what graphics card/chip are you using? 

if its an intel your probably just better off with windows

That's not an option, window$ is gone beyond recovery, new PC's don't come with CD's anymore and I deleted all from my drive.

---

### Post by Johnny19734 on 2009-04-13
One needs to copy the following Windows dll's:

* d3dx9_35.dll (in game directory) 
* msvcp80.dll (under windows/system) 
* msvcr80d.dll (under windows/system) 
* msvcr80.dll (under windows/system)

---

### Post by arashiko28 on 2009-04-13
> **wingnux said:**
> Can you post your system specs? It seems that you don't have your graphics card's driver installed.

I hope this can help
> display:0
description: 	VGA compatible controller
product: 	Mobile 4 Series Chipset Integrated Graphics Controller
vendor: 	Intel Corporation
physical id: 	
2
bus info: 	
pci@0000:00:02.0
version: 	07
width: 	64 bits
clock: 	33MHz
capabilities: 	msi pm bus_master cap_list
configuration:	
latency	=	0
id:	
display:1
description: 	Display controller
product: 	Mobile 4 Series Chipset Integrated Graphics Controller
vendor: 	Intel Corporation
physical id: 	
2.1
bus info: 	
pci@0000:00:02.1
version: 	07
width: 	64 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list
configuration:	
latency	=	0

---

### Post by Mokoma on 2009-04-13
> **arashiko28 said:**
> I hope this can help

yeah you have intel. your not going to get nice results with nulldc under wine or with lxdream sorry. if your machine has an agp or even a free pci slot you can get a better card. hell even a 5200 would rape an intergrated intel chip :/

---

### Post by arashiko28 on 2009-04-13
Well... so far... The first thing I said is that this is a laptop, I just want a few games to relax when I'm on my 24 hr shifts on the hospital. But no way I'm going back to winblow$, don't take it personal, but I just want an OS that works when I want to, that's why I changed to Linux and I like it that way.

Thanks to all of you for your help, and if anyone knows how to get play on linux going, let me know. I'm not loosing hope, just looking forward.:lolflag:

---

### Post by Mokoma on 2009-04-13
> **arashiko28 said:**
> Well... so far... The first thing I said is that this is a laptop, I just want a few games to relax when I'm on my 24 hr shifts on the hospital. But no way I'm going back to winblow$, don't take it personal, but I just want an OS that works when I want to, that's why I changed to Linux and I like it that way.

Thanks to all of you for your help, and if anyone knows how to get play on linux going, let me know. I'm not loosing hope, just looking forward.:lolflag:

lol sorry missed that xD

intels drivers are notorious on windows and linux. they really dont work nicely at all.

24hours shits? whats are you a security guard or something?

---

### Post by wingnux on 2009-04-13
A doctor, maybe?

---

### Post by Mokoma on 2009-04-13
> **wingnux said:**
> A doctor, maybe?

a doctor really wouldnt have time to play on a laptop now would they.....

---

### Post by arashiko28 on 2009-04-16
> **Mokoma said:**
> a doctor really wouldnt have time to play on a laptop now would they.....

Jejeje, yeap, I'm a doctor. Well actually if my shift is on the ER, no, no time not even to eat, patients keep coming and work never ends. But when it's at the patients dorms you get about 5 to 6 hours to rest :D, so why not to relax and enjoy? Right now all I do is sleep those hours because you never know when you're going to miss it back.

---

### Post by arashiko28 on 2009-04-16
Well someone told me I could request a CD with win$$$ since I paid for it already, well sorry to say it's a WRONG choice, to get support, by email, online or by phone you have to pay the special price of US$59.99 would you risk to pay it and get a one liner answer of a big fat NO and saying that you have to purchase it again? I don't think so.

---

### Post by CharmyBee on 2009-04-16
There's no use replying twice to a banned person.

---

### Post by arashiko28 on 2009-04-16
> **CharmyBee said:**
> There's no use replying twice to a banned person.

who's banned?

---

