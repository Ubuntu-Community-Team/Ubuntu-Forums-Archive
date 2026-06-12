---
title: "Need help with playing Dota Underlords"
date: 2019-07-16
forum: Gaming &amp; Leisure
---

### Post by odyssevs2 on 2019-07-16
My Windows 10 just crashed and I was unable to reinstall it. So I installed ubuntu 18.04 instead. I have never used Ubuntu before yesterday and I am not able to get windows 10 for free again.

When I was using windows 10 I had no issues running the game Dota Underlords game from steam. But now I have issues.

I get the message:

"Unable To Start Game

Failed to initialize Vulkan.
Please make sure your driver and GPU support Vulkan."

As far as I know:
 I have all the drivers for my AMD Radeon HD 6870 installed. 
I also have the vulkan installed. However, I also now see that perhaps Vulkan doesnt support my GPU.

What should I do? How am I able to play Dota Underlords? Is it only possible with Windows?
Can I run it with something else than Vulkan?

---

### Post by mastablasta on 2019-07-17
old card. you owuld be using opensoruce radeon driver.: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

not sure if latest opensource - the amdgpu works on this chip.

> [COLOR=#000000]Can I run it with something else than Vulkan?[/COLOR]

check the system requirements for the game. looks like it needs vulcan, though some report there is a switch to ruin it without. if card supports vulcan, you can add the support to OS:
[https://linuxconfig.org/install-and-test-vulkan-on-linux](https://linuxconfig.org/install-and-test-vulkan-on-linux)

---

### Post by odyssevs2 on 2019-07-19
I dont think it works. The card wasnt old when I bought it. :D Time passes by so fast. I seem to be able to play other steam games though. Maybe ill buy a new card sometime in the future.

---

### Post by mastablasta on 2019-07-22
i am sure they will also make some backwards compatibility on the game. Underlords is still "beta", right? or the driver might get an upgrade with later kernels or some switch to easily turn on Vulkan support.

yeah plenty of games that work fine. there are also many windows games on GOG that work well with Wine or Steam Proton. of course they are not the latest fad.

---

