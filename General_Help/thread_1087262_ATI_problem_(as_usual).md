---
title: "ATI problem (as usual)"
date: 2009-03-04
forum: General Help
---

### Post by dougfresh on 2009-03-04
Hey guys,

almost got my system up and running, the last thing was installing the drivers for my ATI x1650 (old I know dont laugh) and I checked the hardware drivers and downloaded them. Now I can't change my screens, Ubuntu can't recognize? is what its saying through the resolution window. Is there an app I forgot somewhere or something? As much as I like having mirrored screens, its a little annoying lol. Moreover, when I boot it up its like the Login is centered between my two screens lol. Suggestions?

Doug

---

### Post by WatchingThePain on 2009-03-04
Hi,
I am another 'victim' of ATI!.
Do you know if the ATI catalyst software is installed?.
My Ubuntu wouldn't change resolution because the catalyst control centre was overiding it, when I set resolution in catalyst first then Ubuntu accepted it.
Other than that the resolutions are in the /etc/X11/xorg.conf file, maybe you need to add some resolutions to that.
There should already be threads that give more detail because this kind of thing happens quite a bit .

---

### Post by neppakyo on 2009-03-04
Is replacing it with a geforce card an option? lol..

I had a radeon 2400 HD piece of shi... You don't know how many hours I spent trying to get it to work properly..

If you don't want fglrx Opengl, give the radeonhd driver a shot

---

### Post by dougfresh on 2009-03-04
> **WatchingThePain said:**
> Hi,
I am another 'victim' of ATI!.
Do you know if the ATI catalyst software is installed?.
My Ubuntu wouldn't change resolution because the catalyst control centre was overiding it, when I set resolution in catalyst first then Ubuntu accepted it.
Other than that the resolutions are in the /etc/X11/xorg.conf file, maybe you need to add some resolutions to that.
There should already be threads that give more detail because this kind of thing happens quite a bit .

That's exactly my problem, should I install ATI CCC and run it through Wine? or what?

And I've been reading alot about it and apparently its not that easy. All I want to do is make sure my graphics card is running and not a piece of crap. Next is WoW that's all I need. Everything else on this works perfectly.

---

### Post by WatchingThePain on 2009-03-05
Well I looked under applications and catalyst had already installed itself somehow. Wine does't work with quite a few things.
In my xorg.conf it uses the fglrx driver. You can probably use the VESA driver too but the resolution will be low.
Does your system show restricted drivers so that you can just select the driver?
Also theres commands like xfree86 -config or something like that which run you through all the configuration options.
If all else fails I wonder if you can use Envyng. It worked for me on Ubuntu.
You are on Jaunty?..so it's an old card for a very new distro.

---

### Post by Torgas Prim on 2009-04-26
I just installed 9.04 myself and when I tried to install the restricted drivers as I did effortlessly in 8.04, I get a Report Bug error and no more X.
I have formatted my drive and got it back but am affraid to attempt it again.
Anyone know what this is or what the workaround is?
Or do I just wait till they update 9.04 again.... :confused:

---

