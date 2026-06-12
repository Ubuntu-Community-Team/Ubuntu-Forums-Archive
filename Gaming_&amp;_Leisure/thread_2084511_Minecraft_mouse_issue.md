---
title: "Minecraft mouse issue"
date: 2012-11-15
forum: Gaming &amp; Leisure
---

### Post by Rz666 on 2012-11-15
Hello fellow Ubuntu users,

Today I tried to install Minecraft on my Ubuntu x64 system and now i've got a problem with my controls in game.

I can launch and enter a game but when i move my mouse the view starts turning in every direction. I'm about 100% sure that this occurs due to the mouse actually leaving the screen so the pointer actually stays on the side/top/bottom. This is confirmed by the fact that I have a limited view angle when I play in fullscreen mode (because the pointer cannot go further to the side/top/bottom).

Knowing what causes this problem is helpful but when I tried searching for common problems I didn't find anything useful.

Additional notes:

[LIST]
[*]I've installed java from oracle NOT the open JDK or something like that;
[*]Because after logging in a black screen occured I updated LWJGL manually ([http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL](http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL)).
[*]Using Ubuntu 12.10 64-bit
[*]Running Ubuntu in VMware (newest VMware tools installed)
[/LIST]
Suggestions?


Thanks in advance,




Rz666

---

### Post by efflandt on 2012-11-18
I have had no problems running minecraft in 64-bit 10.10, 11.10, or 12.04 using openjdk-6 or openjdk-7, although, I have always been using lwjgl 2.6 to resolve the occasionally sticky movement key issue with the lwjgl 2.4.2 included with minecraft, so I have not tried the most recent lwjgl (2.8.4 I think).

But I wanted to try Ubuntu 12.10 before I commented, and from that experience, the problem might be Ubuntu 12.10 which seems to have a number of issues, possibly due to massive graphics changes that have not been sorted out yet.

When I tried 64-bit 12.10 in a virtual box the mouse was very jumpy and erratic and graphics noticeably slow vs. Debian Linux in virtual box which was very smooth with much faster graphics.

But just to give it a fair shake, I installed 64-bit 12.10 on a USB hard drive and to be kind I'll just say it was a disappointment, not ready for prime time or inexperienced users.  The default nouveau graphics for nvidia cards is sluggish and turns to colored snow when scrolling windows.  And installing nvidia drivers from Software Center, like they expect you to, totally messed up everything so all I get in X is the background with nothing else.  I don't know what they did to the graphics, but it is horribly broken compared with 12.04.

PS: I finally figured out how to get nvidia graphics working by using apt-get to install linux-sources and linux-headers-generic and then --reinstall of nvidia-current.  So now 12.10 works fine for minecraft.  But if you have other graphics (or drivers) that could vary.  I didn't have even tried to play it with the sluggish snowy nouveau graphic driver that is the default for nvidia chips.

---

### Post by Rz666 on 2012-11-19
@efflandt,

Thanks for your response, the "colored snow" you described does not occur on my system. Also using a nVidia graphics card. Although i'm running Ubuntu in VMware so the VMware drivers might bypass this.

> But I wanted to try Ubuntu 12.10 before I commented, and from that  experience, the problem might be Ubuntu 12.10 which seems to have a  number of issues, possibly due to massive graphics changes that have not  been sorted out yet.> PS: I finally figured out how to get nvidia graphics working by using  apt-get to install linux-sources and linux-headers-generic and then  --reinstall of nvidia-current.  So now 12.10 works fine for minecraft.   But if you have other graphics (or drivers) that could vary.  I didn't  have even tried to play it with the sluggish snowy nouveau graphic  driver that is the default for nvidia chips.     Do you mean the best option is to wait for a huge fix for the massive graphics changes or that installing the right graphic card drivers may solve this.

Also, I suppose you've used openJDK for the 12.10 testing am I correct?

---

### Post by gennoveus on 2012-12-24
I have the same problem with the mouse getting 'stuck' in the screen area when in fullscreen mode. Please help I don't know where to start.

P.S. I also has the problem on my old computer, but I somehow resolved the problem but have no recollection. I think I was tweaking a lot of settings for other games, etc. and when I tried playing minecratt again after a long time it had fixed itself.

Help!

---

### Post by holastickboy on 2012-12-24
Did you manually update the lwjgl?

---

### Post by gennoveus on 2012-12-24
> **holastickboy said:**
> Did you manually update the lwjgl?

Thanks for the reply!

Yes, I updated to version 2.8.5 manually
I confirmed this by running minecraft from the console and checking the output:

LWJGL Version: 2.8.5

Or so it tells me. Any ideas?

EDIT:

It suddenly started working today... ?
All's well that ends well I suppose.

---

