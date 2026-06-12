---
title: "Kubuntu gusty is giving slow performance"
date: 2008-02-02
forum: Desktop Environments
---

### Post by zeeshan4it on 2008-02-02
Hello!

I have AMD Athlon 64 x2 5600+ dual core processor with 2 GB of RAM and i have both windows vista (32-bit version) and kubuntu gusty installed on it. Windows vista is running like a charm and giving high speed performance on it just click and play environment and no wait for software opening time. On the other hand kubuntu gusty (32-bit version) is not giving vista like performance and even when i open a home folder from desktop using dolphin browser, i have to wait for about 3-4 seconds and then it opens. Same problem with wine based softwares. Dreamweaver runs very fast on vista but on kubunu it opens late and giving slow performance.

Can you please give me tips to optimize response time for opening folders and other softwares on kubuntu?

Zeeshan

---

### Post by ove.almkvist on 2008-02-02
hello

After googeling a bit and read on forums i find out that it looks like many others are having the same problem, including me. For a while i thought it was because of graphic problems. But i have tried out some different graphic cards (ati, nvidia, radeon) and running with and without xserver-xgl packages. and the problem still remains.

So i would be happy if someone could come up with some good idee.

/Ove

---

### Post by TeaSwigger on 2008-02-02
Hello and welcome, to both of you. 

Dolphin took me about ~2-3 sec to open - and that's using Kubuntu (Gutsy, 32bit) on an old Pentium III with only 384mb ram.

There are at least four factors going on, I'll try explaining.

One is "pre-loading." Vista pre-loads a huge mass of stuff, so things like the file manager are always started and should pop up almost instantly. That's one reason Vista won't even run on 384mb ram, because it needs more than that just to sit there. If you compare the resource usage between Kubuntu and Vista, you'll see Kubuntu runs way, way, way leaner. This makes it much friendlier to hardware and gives you more overhead to devote to programs you do run. The trade-off is that since many things in Kubuntu are starting from scratch when you fire 'em up, it could take a bit longer depending of course on how big the program is, so how much needs to be loaded. I hope that description makes sense.

I prefer to use Konqueror as a file manager and web browser in Kubuntu instead of Dolphin. I feel that Konqueror is more flexible, and as a side plus you can chose to have it pre-load (I think it does by default), so it starts quicker. If you would prefer to use it, there's a howto around here somewhere or ask and I'll try to dig it up.

Another factor; is there a reason you're running the 32-bit on a 64-bit system? I don't know that there's anything wrong with that but you surely won't get optimized performance. Running the 32-bit Kubuntu on a 64-bit box would leave Vista with some advantage there.

Thirdly, Kubuntu is a richly featured system as it installs. It is possible to lighten the load and perk it up a bit - using less eye-candy, removing some services like bluetooth if you don't use it, etc - but honestly I'm not sure how much it'd help on your very good spec. system. You'd need other more experienced opinions there.

There are faster performing Linux distros which use KDE just like Kubuntu. One is Gentoo, perhaps the most sophisticated, but also much more involved to learn than Kubuntu, which tries to be point-and-click friendly as is practical. Debian might be an option, and if you ask I'm sure folks know of a number of other options that may tend to be faster.

Finally, WINE. Understand that WINE is pulling off quite a feat to run at all. It's very impressive work by many amazing people. Unfortunately it often can't run as fast as the programs would under Windows. Fortunately, since you have a good spec system, you have options. A prime option is "virtualization." It allows you to run a copy of Windows, say XP or 2000, inside Kubuntu. Can be very convenient and run well. Check out VirtualBox and poke around for more.

Of course I'm going on the presumption from your mention that Kubuntu is running reasonably smoothly and all, it's just not quite up to the speed that it seems it should be. That there are no graphics or other hardware issues etc. Sometimes you have to ensure the ideal graphics driver is being used with whatever card you install. That beef would be with the graphics card companies who don't provide open-source code for the hardware you bought, forcing you to go out of your way to install their proprietary driver (if they even have one) or use Microsoft products. With the Proprietary Device Manager, Ubuntu tries to make that as easy as possible, but sometimes you still have to look into it, make some tweaks etc. Ubuntu can't change the way those companies work, but if you have reason to suspect there may be a lingering problem post and someone may be able to help you dig into that.

---

