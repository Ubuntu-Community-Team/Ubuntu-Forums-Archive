---
title: "Gaming performance for GTX 550Ti"
date: 2013-11-29
forum: Gaming &amp; Leisure
---

### Post by Yuliyan_Hristov on 2013-11-29
Hello there! I really like Ubuntu and there is only one thing which is separating me of removing Windows...and this is game installing and performance. For example - WoT. Installed it via PoL, with the newest video driver for my GTX 550Ti video card and still doesnt run good which drives me crazy. First - i cant change the resolution to the native one of my monitor...when i try to do that the game crashes and the game closes itself. The other thing is the FPS...the game doesnt run smooth as on Windows...is there any way i can make it run normal? Im sorry if this threat isnt on the right place and my english is bad.

Best regards - Yuli.

---

### Post by mikewhatever on 2013-11-30
Not much we can do here. While Linux graphics drivers do improve, there is still a long way to go.

---

### Post by dannyboy79 on 2013-11-30
playing windows games in linux using wine is just never going to get you the result you desire. if you want to game in linux i suggest running native linux games in linux, not thru emulation. for example i only have a HD7770 black edition but i get very decent performance out of Metro Last Light running at 1680x1050 (native res). Linux is definitely still behind in the gaming department BUT that's all because AMD and Nvidia really had no interest to make their drivers better when the percentage of linux gamers is like 1% compared to 99% windows gamers. THey are getting better now and actually releasing some documentation about their hardware not to mention Nvidia  is in bed with Valve in regards to Steam Machines and SteamOS so the support should just keep getting better AND then we just need developers to start making their games in linux

---

### Post by Yuliyan_Hristov on 2013-11-30
Im not sure if the problem is coming from the drivers. Maybe it is somewhere else, but i dont know where look for it. There are people saying games are running normally (as on Windows) when using wine. I tried some other methods of installing WoT for example and none of then were successfull. I found another mothod, which is user made, described in the WoT Forum. They say it runs good, no FPS drop, no problems with the resolutions or something. I hope it will be successfull. If it is - Bye Bye Windows!

---

### Post by DanglingPointer on 2013-12-03
> **Yuliyan_Hristov said:**
> Hello there! I really like Ubuntu and there is only one thing which is separating me of removing Windows...and this is game installing and performance. For example - WoT. Installed it via PoL, with the newest video driver for my GTX 550Ti video card and still doesnt run good which drives me crazy. First - i cant change the resolution to the native one of my monitor...when i try to do that the game crashes and the game closes itself. The other thing is the FPS...the game doesnt run smooth as on Windows...is there any way i can make it run normal? Im sorry if this threat isnt on the right place and my english is bad.

Best regards - Yuli.

Hi Yuliyan, there will always be a penalty for using WINE.  The game is not native to Linux so DirectX will need to get mapped to OpenGL GPU calls to the Nvidia driver.

Perhaps if you post your problem in the WINE subforum of this forum, the people there could perhaps help you tweak it.  This forum you're in is predominantly for linux native games.

---

### Post by cRaZyBisCuiT on 2013-12-03
Actually that's not entirely true [**[COLOR=#000000]DanglingPointer[/COLOR]**]("http://ubuntuforums.org/member.php?u=838528"). In the case of the TO, yes (including closed drivers). MESA 10 inludes Gallium 3D drivers for amd, intel and nvidia. With mesa 10 there are native DirectX 9 calls possible. So if you got a game and this kind of driver, there's no speed cap gpu wise anymore. The CPU part ist still a problem but if you use a version of wine which includes better multicore support ([http://www.winehq.org/pipermail/wine-devel/2013-September/101106.html](http://www.winehq.org/pipermail/wine-devel/2013-September/101106.html)) the frame rate you achieve could be doubled. For example my average fps in Starcraft II jump up from 15 average to 30 average + the minimum fps from 8 fps to 15 fps (560ti). It's not good at all (huge battles are not playable) but at least the performance got doubled (!), it's the right direction developers go. :)

---

### Post by DanglingPointer on 2013-12-03
Interesting!  I never knew that the mesa driver had DirectX calls built in!  That's impressive
However I'm playing the likes of Wargame (both), Serious Sam, Metro LL, etc. so unfortunately until Mesa can properly compete with the closed source driver, I won't be using it.

---

### Post by Yuliyan_Hristov on 2013-12-05
So how do i install Mesa 10 driver and do i have to do anything else before installing it?

---

