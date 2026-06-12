---
title: "OpenGL terribad linux noob needs help"
date: 2009-11-14
forum: Gaming &amp; Leisure
---

### Post by Kisame on 2009-11-14
I just installed ubuntu because now i stopped playing any games other than HoN, i downloaded and installed it but it seems my openGL isnt good enough (i think)
The VAD has been replaced by a hack pending a complete rewrite
K2 - Fatal Error: OpenGL 2.0 not available.

Thats what it says, now how do I update my opengl? I can't figure it out..

---

### Post by Kisame on 2009-11-14
Oh and if you want I should have a few beta keys

---

### Post by idodos on 2009-11-14
I trust that you have installed the latest drivers for your graphic card?
And which graphic card are you using?

---

### Post by Kisame on 2009-11-14
dude honestly i dont know, i thought drivers were automatic in linux and my gfx is shitty onboard crap on a gigabyte GA-MA74GM-S2H model, i literally just now installed ubuntu then went on the hon site and downloaded it, didnt work and i came here

also invite site is down for the moment but ill hit u up when its back

---

### Post by joeelmex on 2009-11-14
Hon requires open GL 2.0 and if you have a intel card, i don't think their drivers support opengl 2.0.

---

### Post by Kisame on 2009-11-14
my cpu is AMD so i dont expect anything else is intel but **** id be pissed if it was

---

### Post by Kisame on 2009-11-14
# Integrated ATI Radeon 2100-based graphics

---

### Post by idodos on 2009-11-14
Then you probably don't have any drivers installed for your graphic card.
Your motherboard comes with an ATI integrated graphic card, that could mean bad news. Linux lack good ATI drivers. Although ubuntu 9.10 comes with better ones I do not know how well it will go.
But, first thing's first. Install the driver:
Go to System=>Administrations=>Hardware Drivers

From there you can install your graphic card driver. Tell me how it goes!
Good luck!

---

### Post by Kisame on 2009-11-14
the windows are totally empty? nothing there at all

---

### Post by Kisame on 2009-11-14
also, using ubuntu 9.10

---

### Post by idodos on 2009-11-14
If you see this, Do not use that command.

use the following instead: 
sudo apt-get install envyng-core

then in terminal type:
envyng -t

And type the number for the ATI driver.

---

### Post by Kisame on 2009-11-14
i followed the tutorial and ended up looking at 4 uncompatible drivers all of which were unrecomended but i installed the ATI one anyway restarting now

---

### Post by idodos on 2009-11-14
Ok, about me telling you not to use it. It's because the envyng-qt package requires KDE libraries so you might want to remove it along with the KDE libraries after you restart. Hope it all works well!

Edit: eh.. Further digging show there's no driver for that card. So I do hope your computer boots up to Ubuntu. And you should go back to windows really.

---

### Post by Vadi on 2009-11-14
It would be real awesome if clueless people didn't give advice, because you know, it can break computers if you follow that clueless advice.

Ubuntu has a 'Hardware Drivers' tool in System - Administration that's been working just fine for the past few releases, and as such, there is no need for Envy.

---

### Post by Kisame on 2009-11-14
Yeah that messed my pc up a lot and im gonna format it with ubuntu again
no harm done really, im looking for a gfx card i have lying around but appears to be lost, another ati card a HD4870 i think it was but i dont know if that would help anyway

---

### Post by Duskao on 2009-11-14
Kisame. You are going to want to use the open source Radeon/RadeonHD drivers for you on board video card. 

[http://ubuntuforums.org/showthread.php?t=1313828&highlight=enable+radeon+driver%3F](http://ubuntuforums.org/showthread.php?t=1313828&highlight=enable+radeon+driver%3F)

Following the instructions in there is your best bet. You should be able to actually get some decent 3D with it. 

If you use the Radeon 4870, you should be able to use the proprietary drivers with Ubuntu, or in other words System->Administration->Hardware Drivers. Or you could also go to the AMD/Ati website and download the latest drivers and install them that way. 

Best of luck.

---

### Post by Kisame on 2009-11-14
Okay, so i installed the PPA thing, which was not easy, then after about an hour figured out how to actually use it to install drivers, and even after doing so the error from hon does not change, always opengl 2.0 not available.

what am i doing wrong?
could it be the driver wasnt the problem to begin with?

---

### Post by idodos on 2009-11-14
Er.. sorry. I really screwed up. Um.. according to the AMD website, there is a driver supporting HD4870 on linux.

I guess I really am lacking but according to AMD they support the followring:
"ATI Mobility RadeonTM HD 4870"
"ATI RadeonTM HD 4870 X2 Series"

I assume you have the "ATI RadeonTM HD 4870 X2 Series" card. But, you should check just in case. And did you actually find the card? You don't seem to mention it. Your Integrated ATI Radeon 2100-based graphics card will not work, it's not supported.

---

### Post by Sindwiller on 2009-11-15
Holy dog****! Horribly incomplete problem description, terrifyingly stupid advices, trolling *and* fanboying in one single thread. How did I get to a Windows "support" forum?

As idodos already adressed, AMD/ATI have very poor Linux support, as opposed to Intel, who provide GPL drivers for their integrated chipsets, or NVIDIA, whose proprietary drivers are on a decent level. Obviously, there has been some efforts to write GPL drivers for both NVIDIA (nouveau) and ATI (radeon, radeonhd), which have already yielded fruits, though they're not ready for everyday use just yet.

In other words, if you have an ATI card, you're doomed. If you have an ATI card that's not supported by the proprietary ATI driver called "fglrx", then you're pretty much done. The GPL radeonhd *might* support your chipset. However, it does not support 3d acceleration yet.

For more on how to get yourself fglrx on the proper way, you might consider [this page]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI").

---

### Post by Vadi on 2009-11-15
And by decent, it's implied best performance from hardware on Linux ;)

---

