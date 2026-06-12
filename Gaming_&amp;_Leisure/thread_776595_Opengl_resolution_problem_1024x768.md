---
title: "Opengl resolution problem 1024x768"
date: 2008-04-30
forum: Gaming &amp; Leisure
---

### Post by marcoskorner on 2008-04-30
HI everyone, not sure it belongs in this forum but..
Im new to ubuntu and im having problems with the way Opengl is working with  resolution 1024x768, If i set that resolution on my desktop it works just fine, but if i try to play any game (openGL like ioquake, Enemy territory or Frets on fire) it stretches too far and I cant see the sides of the screen, it also looks like scanlines.
Im using a GeForceFX 5200 with NVIDIA original drivers, and Ubuntu 8.04 on a 17 inches screen not wide screen of course. Every other resolution works fine in Opengl 640x480, 800x600, 1280x1024.

The other problem I seem to have is that I can only set 24 bit color and not 32 in Xserver

So what can i do to be able to play games on 1024x768, since 1280x1024 causes some serious fps drop and 800x600 looks bad.

Thanks

---

### Post by slink3r on 2008-05-01
I use OpenGL, and I was having 1600x1200 problems perhaps similar to yours.

I have compiled my wine upon a vmware installation that was created within wine (kinda irrelevant)

Wine uses 1 MB footprint to install its "proxies" into which data travels through multiple thread handling processes.the IPC (being looped permanently in a poll()) could be optimized with an application perhaps to speed up the transition of your resolution switching.

I don't know about these applications, but I just recently installed Ubuntu and was hoping to find some advice in this area, and perhaps I can help you with your issue simultaneously?

---

### Post by slink3r on 2008-05-03
It's a DLL thing I mean.

The point being that if they used that process they could optimize their DLLs. I figure that way graphics companies will be more inclined to use my operating system.

And feel free to post what you'd like :)

---

### Post by marcoskorner on 2008-05-10
OK,Ijust dont get it but i think you really have not understand me, I play these games in their Linux distribution not in WINE, so theproblem is in ubuntu, maybe drivers, maybe Xorg.

---

