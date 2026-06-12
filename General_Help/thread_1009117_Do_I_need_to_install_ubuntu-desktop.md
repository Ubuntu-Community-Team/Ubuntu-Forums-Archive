---
title: "Do I need to install *ubuntu-desktop?"
date: 2008-12-12
forum: General Help
---

### Post by robzy on 2008-12-12
Hey guys :) I am currently trying to build a desktop/server hybrid Ubuntu box. It has file/mail/web server responsibilities, but I also use NX co connect into it in order to use it as a desktop every now and then (for things like Ktorrent/Azureus/Firefox).

I don't want GNOME/KDE as it's pretty modest hardware (P4 1.6Ghz, 512mb RAM) and thus am leaning more towards xfce4.

I used the Ubuntu minimal CD (the 10mb one) to install a pretty bare-bones Ubuntu on it, and now I'm a bit stuck at the point of getting a GUI up and running.

First instinct was to run a "apt-get install xubuntu-desktop", but that was going to download 386MB and then use 1.5GB of hard disk space, which I am not totally happy with as I like a clean Linux box and there was a lot of stuff included I don't want/need.

So I'm now tempted just to do an "apt-get install xfce4" without having ubuntu-desktop or kubuntu-desktop or xubuntu-desktop, but from the small bits and pieces I have read from google (mostly relating to 6.xx I think) this is unadvisable.

So this poses a question, what's the best way of getting of getting xfce4 up and running with the least additional software being installed? Is simply install xfce4 (without *-desktop) acceptable?

Thanks,
Rob.

---

### Post by howefield on 2008-12-12
You'll need xorg as well
```

sudo apt-get install xfce4 xorg
```

---

### Post by karlr42 on 2008-12-12
You get very little with xubuntu-desktop: 
[http://packages.ubuntu.com/intrepid/xubuntu-desktop](http://packages.ubuntu.com/intrepid/xubuntu-desktop)
Showing exactly what packages you get. I'd say go for it, it's the easiest option, and 1.5GB harddrive-space for a great desktop environment isn't a lot.

---

### Post by robzy on 2008-12-12
> **howefield said:**
> You'll need xorg as well
```

sudo apt-get install xfce4 xorg
```
Thanks for the headsup :) Having a quick look, though, xfce4 already depends on xorg anyways. Just to confirm though, does this mean that you are saying that I *do not* need to get a *-desktop package?

> **karlr42 said:**
> You get very little with xubuntu-desktop: 
[http://packages.ubuntu.com/intrepid/xubuntu-desktop](http://packages.ubuntu.com/intrepid/xubuntu-desktop)
Showing exactly what packages you get. I'd say go for it, it's the easiest option, and 1.5GB harddrive-space for a great desktop environment isn't a lot.
Ah, but this is Linux... not Windows :P If I wanted my OS to be cluttered with useless binaries I would be using XP, heh. Besides, half the fun of Linux is getting it just how you want it.

Hrm, for some reason apt-get seems to want to be dragging down a bunch of stuff that isn't listed as a dependancy there, Abiword for instance. Is there any way to track down which packages are wanting to drag down all this extra stuff and block them?

This is a copy of my apt-get output:
[http://pastebin.com/f7c176d9d](http://pastebin.com/f7c176d9d)

[edit]: A ha! --no-install-recommends fixes the problem. Now it only wants 526mb of HDD space and much less clutter :D That brings my total install close to the 1.7gb a vanilla Xubuntu install (from the livecd) takes up, which doesnt quite make sense, but meh - I'm happy.

Rob.

---

### Post by mkvnmtr on 2008-12-12
I can't help you from experience but I am planing to wipe my Ubuntu and reinstall from the minimum install disk also. Like you I don't want a lot of stuff I don't use. I googled "Ubuntu+minimum install" and found some good tutorials on quick ways to get a minimal desktop. You might want to read several. People have different ideas of what they like.

---

### Post by howefield on 2008-12-12
> **robzy said:**
> Thanks for the headsup :) Having a quick look, though, xfce4 already depends on xorg anyways. Just to confirm though, does this mean that you are saying that I *do not* need to get a *-desktop package?

That's right, you do not need the -desktop, just that you'll end up with very little by way of packages, but that seems to be what you want, you'll be able to install exactly what you want/need.

---

### Post by albinootje on 2008-12-12
Are you using FreeNX or the NX closed source and free-of-charge server edition from Nomachine ?
I'm using FreeNX on a server, and it works fine with Gnome and xfce4.

You probably need to install the xauth package too.

---

### Post by robzy on 2008-12-12
> **howefield said:**
> That's right, you do not need the -desktop, just that you'll end up with very little by way of packages, but that seems to be what you want, you'll be able to install exactly what you want/need.
If you don't mind me just running the past you.... the things I was reading were saying that without *-desktop I would have trouble upgrading when the next version of Ubuntu was released (9.04, right?). I take it that this is not the case?

> **albinootje said:**
> Are you using FreeNX or the NX closed source and free-of-charge server edition from Nomachine ?
I'm using FreeNX on a server, and it works fine with Gnome and xfce4.

You probably need to install the xauth package too.
I think I will be using the NX closed-source free-as-in-beer edition from Nomachine. Last I tried FreeNX (albeit on Gentoo ~2 yeras ago) I had many troubles.

And thanks muchly for the prompt replies guys :) I really ought to try and pop in here more often, could probably offer a fair bit of help to others myself :)

Rob.

---

