---
title: "id Software and OpenGL idRender problems"
date: 2012-01-09
forum: Gaming &amp; Leisure
---

### Post by T3RR0RH4WK on 2012-01-09
Hello

I'm running Ubuntu 10.04 LTS 64-bit on a Phenom II X4 955 with 8GB of RAM and a Radeon HD 6850.

I've heard from many people that "Nvidia is the prefered GPU for Linux" but I've had equally bad luck, at times, with both. So this is not a flame war, please keep in mind.

I am, however, having an issue with both Prey and Enemy Territory: Quake Wars.

Upon trying to start Prey, literally nothing happens when I click it. I try to start it in Terminal and I get "SysError: Unable to initialize OpenGL"

Upon trying to start ET:QW, nothing happens as well. Again, I try to run it in Terminal and I get this: idRenderSystem: :Shutdown ()

I have a really powerful GPU with the proprietary AMD drivers (from their site) installed and more than enough power to run these games (for instance, I run them on Windows on this same PC just fine). I did run the glxgears thing and get like 300 frames every time and have played other 3D games yet these two refuse to run. :/

Anyone offering any help would be immensely appreciated. Thank you very much!

---

### Post by mastablasta on 2012-01-10
perhaps you are missing libraries needed by games to run.

---

### Post by Sockerdrickan on 2012-01-10
> **T3RR0RH4WK said:**
> Hello

I'm running Ubuntu 10.04 LTS 64-bit on a Phenom II X4 955 with 8GB of RAM and a Radeon HD 6850.

I've heard from many people that "Nvidia is the prefered GPU for Linux" but I've had equally bad luck, at times, with both. So this is not a flame war, please keep in mind.

I am, however, having an issue with both Prey and Enemy Territory: Quake Wars.

Upon trying to start Prey, literally nothing happens when I click it. I try to start it in Terminal and I get "SysError: Unable to initialize OpenGL"

Upon trying to start ET:QW, nothing happens as well. Again, I try to run it in Terminal and I get this: idRenderSystem: :Shutdown ()

I have a really powerful GPU with the proprietary AMD drivers (from their site) installed and more than enough power to run these games (for instance, I run them on Windows on this same PC just fine). I did run the glxgears thing and get like 300 frames every time and have played other 3D games yet these two refuse to run. :/

Anyone offering any help would be immensely appreciated. Thank you very much!
It sounds like you should reinstall your AMD GPU drivers. Also try the ones that come with Ubuntu if you don't get the manual installation to work. Hope it works!

---

### Post by T3RR0RH4WK on 2012-01-12
> **Sockerdrickan said:**
> It sounds like you should reinstall your AMD GPU drivers. Also try the ones that come with Ubuntu if you don't get the manual installation to work. Hope it works!

Well I downloaded the file itself from AMD's site and it installed no problem, but I guess I could try the open-source FLGRX one or whatever. I'll give that a go and let you know what happens.

---

### Post by T3RR0RH4WK on 2012-01-12
> **mastablasta said:**
> perhaps you are missing libraries needed by games to run.

I wonder how that could have happened. Last I looked, the games both installed SDL and some OpenAL stuff with it, and I already had AMD's proprietary driver installed (and working well with everything else, I might add)

---

### Post by Perfect Storm on 2012-01-12
I know that if you install the Nvidia restricted drivers manual (from their site) and the kernel gets updated you have to reinstall the driver.
This may be the same issue with ATI/AMD restricted drivers?

---

