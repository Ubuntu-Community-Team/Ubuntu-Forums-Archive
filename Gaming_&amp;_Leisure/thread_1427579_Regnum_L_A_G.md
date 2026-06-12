---
title: "Regnum L A G"
date: 2010-03-11
forum: Gaming &amp; Leisure
---

### Post by drklunk on 2010-03-11
Im a complete noob to Ubuntu, having switched from Windows 7 Ive just been copy/pasting command lines into the terminal to get what I needed. Google has been a valuable source as well. 

This game though, it lags to the point its almost not playable. Ive got four gigs of ram that share memory with my graphics card. Im on a laptop, brand new, with a dual core processor and all the goodies. I dont understand why Im having issues though. 

Is there a way I can control how much ram my graphics card gets and how much the rest of it gets? Sort of virtually dedicate the card?

Any help would be awesome, feel free to ask for more info and Ill be glad to provide what I can

---

### Post by MaximB on 2010-03-11
Does it happen with all 3D games ?
If yes > you should update your videocard drivers
If No > it's an online game and with such games players sometimes have "lags" , if their internet connection is slow it happens very often.
You must be living far far away from the server you are playing in (they have several).
So the time you give an order and it reaches the server to be displayed on your monitor can take a lot of time.
This also happens on peek-times when a lot of players play at the same time, casing the server to respond slowly.
It happened to me many times when I was playing Regnum Online, and it had nothing to do with my hardware or my high speed connection.

---

### Post by drklunk on 2010-03-11
So far it happens with every 3D game Ive taken a shot at, anothers being Perfect World as well as Guild Wars. Figured it might be something I had or hadnt done with Wine. I updated the drivers the day I installed Ubuntu. Is there a way I can make sure Ive got the latest drivers? 

By the way, I appreciate the reply man.

---

### Post by MaximB on 2010-03-11
If you have Nvidia or ATI/AMD you probebly don't have the latest drivers - but it isn't critical as long as they work.

My "test" was always start Scorch3D in windows mode and see how it runs ;)
If it lags, then something is wrong with the video drivers.
You need to enable the restricted modules and install your video card from add/remove software .

---

### Post by drklunk on 2010-03-11
Ok, gotcha, I think. Im downloading Scorched3D now and going to install. Im also downloading/installing the software add/remove program. Ill be back to let you know how it goes. Probably asking for more help too xD

*edit*
I do not have the restricted modules listed in my Synaptic Package Manager, any clues as to how I can get them to show up in there?

---

### Post by MaximB on 2010-03-11
Just search the drivers for your video card in the add/remove programs (you didn't mention what they are...)

---

### Post by drklunk on 2010-03-12
ATI binary X.Org driver (support for 2D)

That is what I found in the add/remove program. I went and did a hardware drivers update check, I suppose, and it says that I have "ATI/AMD proprietary FGLRX graphics driver" (accelerated 3D and 2D, so it says) installed and in use.  What I have is an ATI Mobility Radeon HD 4200 with dedicated 256mb Im guessing.

I wish I knew as much about Linux as I do Windows ><

*edit*
I played around with the settings a bit more and got it to a playable state by putting it on Shader Model 2.0. There are little lag spikes here and there that I could assume are from the server but I dont know for sure.

---

### Post by MaximB on 2010-03-12
Lesson Number 1 that I myself learned the "hard way" : **DON'T Buy (Video cards) From ATI/AMD .**
Their Linux drivers are very buggy and crappy.
Go with Nvidia instead.

(And it's a bad idea to check if your video card drivers are working on an online game - it could always be the server lags that cases the "issues").

---

### Post by drklunk on 2010-03-12
I suppose I learned the hard way as well. No biggie, this is just my laptop anyway. I do prefer AMD over Intel though and nVidia over ATI. ATI always came across to me as cheaper. 

Anyway, I appreciate the help man. Do you think the restricted modules are still necessary? I tried to find out how to get them to show up in the package manager but with no prevail

---

