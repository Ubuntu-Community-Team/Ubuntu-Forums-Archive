---
title: "Problems With Fullscreen WINE Games In Unity/Compiz"
date: 2013-01-18
forum: Gaming &amp; Leisure
---

### Post by Stephen Wayne Hamilton on 2013-01-18
I'm having issues with getting Windows games to go fullscreen. The top bar is gray and always says "WINE Windows Program Loader" and the Ubuntu sidebar shows as well. I've did a bit of reading and it appears to be related to Unity's Compiz. So I downloaded CompizConfig Settings Manager (ccsm) from the Ubuntu Software Center and ticked the box beside "Legacy Fullscreen Support" in the "Workarounds" section, since that's what another site recommended. But to no avail. I've also tried emulating a virtual desktop in winecfg (WINE Config), no luck there either. Non-WINE applications like VLC have no issue going fullscreen. All I want is for all my Steam games to go into fullscreen correctly like they do on Windows. I've already tested alot of games and got them into fullscreen and running correctly, but to do so I had to install KDE and XFCE. I really dont want to feel forced to use another windowing manager just to get games to play right.

Also, can someone recommend a script or app that disables Compiz's desktop effects while games are running? I have heard that it can have a huge hit on performance.

Thanks!

---

### Post by Stephen Wayne Hamilton on 2013-01-18
noone knows?

---

### Post by oldrocker99 on 2013-01-18
The program you need is called fusion-icon. You can quickly install it by entering

sudo apt-get install fusion-icon

or you can install it with the pokey Software Center, or the still-great package manager Synaptic. It will give you an icon that allows you to turn Compiz on or off at will.

Or;), you could install lubuntu-desktop:biggrin:, log out, and log back in to Lubuntu, which is lightweight and fast. It is Ubuntu, with the LXDE interface. If it'll quickly run a single-core laptop such as I'm typing on, it'll run games for you very well indeed. It runs (some) games for me on this laptop. Also, kde-full or kubuntu-desktop, when logged into, has a settings app for desktop effects. On the third tab of that app, there's a checkbox for "disable effects for full-screen windows." Check that and games will run at full speed. You might also log into Unity 2D.

I am most decidedly not a user of the Unity interface](*,), but fusion-icon is the file you need (or my other, uh, suggestions:biggrin:. 

And DON'T hesitate to ask questions in these forums. Everybody here was once 100% clueless. I'm now (I estimate) 86% clueless...

---

### Post by Stephen Wayne Hamilton on 2013-01-23
@ oldrocker99: I installed CFI as you suggested but couldnt get it to run by clicking its' icon. So I entered the command 'compiz-fusion icon &' in a terminal just before I was about to run a game, and it messed up my display entirely (see [http://ubuntuforums.org/showthread.php?p=12469601#post12469601](http://ubuntuforums.org/showthread.php?p=12469601#post12469601)). I know I will get this fixed, there is no doubt about that.

So, to anyone that's willing to help, what are my options for getting WINE games to go into fullscreen properly and increase gaming performance? If someone can post links that would be very helpful. I'm more than willing to do the research and legwork to get things working the way I want them to, just need a bit of guidance.

Thanks in advance!

---

