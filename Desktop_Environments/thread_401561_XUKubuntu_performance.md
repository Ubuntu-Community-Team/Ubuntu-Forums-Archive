---
title: "X/U/Kubuntu performance?"
date: 2007-04-04
forum: Desktop Environments
---

### Post by tubunu on 2007-04-04
I've tired Ubuntu, Kubuntu and Xubuntu. I love them all. I'm interested in the differences in performance of each of the *buntu flavours. 

1. If I install the lightweight Xubuntu and then add KDE on top, will it still run faster than say, installing Kubuntu first and adding Xubuntu-desktop on top?

2. If I install Ubuntu with its latest packages (as yet unavailable in Kubuntu) like OpenOffice 2.2.0, once I add kubuntu-desktop will I have OpenOffice 2.2.0 or 2.2.0.rc3 in KDE?

3. I already know what happens if I install Ubuntu or Xubuntu desktops on my Kubuntu.. tried that already ;)

---

### Post by Bad_Byte on 2007-04-04
1. No, they will run at the same speed, the base installation is the same for both systems (if my memory is correct) so the only performance gain is from the light weight windowmanager vs the heavy weight kde/gnome windowmanager(s).

---

### Post by case1976 on 2007-04-05
Xubuntu should run fastest of all the rest (gnome and kde)... And if not, then try to install pure Xfce 4.4, which everyone can easily install with the graphical installer taken from [www.xfce.org](www.xfce.org).

I am running xfce 4.4 on dapper and it works fine, probably it's even faster than xubuntu, imho.

---

### Post by FuturePilot on 2007-04-05
XFCE is a minimalistic desktop environment.  That's mainly where the speed gain is going to come from. The system under the hood is that same no matter what *buntu you are using. XFCE is definitely lighter on resources than both Gnome or KDE.

---

### Post by bmartin on 2007-04-05
In terms of resource usage, from what I've seen on posts such as [http://ktown.kde.org/~seli/memory/desktop_benchmark.html](http://ktown.kde.org/~seli/memory/desktop_benchmark.html), Gnome > KDE > Xfce. I once installed Xfce within Ubuntu, but I didn't notice any performance gain at all. It might be my computer's hardware; it's really fast.

Recently, I switched from Gnome to Fluxbox; the performance leap was amazing, in terms of memory usage, responsiveness, and speed! It was a lot easier than I thought it would be. With a little tweaking of the startup and keys files in the ~/.fluxbox directory, I was able to get everything the way I wanted (e.g. keyboard shortcuts to load my favorite programs and a very fast startup).

If Xfce is minimalistic, I don't know what Fluxbox qualifies as. It takes some getting used to, but it's incredibly fast at starting up and incredibly responsive. If you don't care how your desktop looks and are very concerned with speed and resource usage, it's worth a try. The hardest part was getting all my keyboard shortcuts to do what I wanted them to.

I had a problem with mapping my Super (Windows) key in Gnome; it registered the key itself as a shortcut (i.e. I couldn't use Super+D to show the desktop because as soon as I hit Super, it set that as the shortcut). In Fluxbox, I was able to configure every little detail to my liking. If you're not a fan of text-based interfaces and terminals, I'd recommend against it.

---

### Post by case1976 on 2007-04-05
> **bmartin said:**
> 
If Xfce is minimalistic, I don't know what Fluxbox qualifies as. 

That's true, fluxbox runs faster than Xfce, i assume that is because it doesn't depend on gtk+, unlike Xfce or Gnome.
I've been also playing around with another configuration: blackbox + fbpanel, which also is very fast and lightweight, and reasonably imitates a full desktop environment. However, Xfce is my favorite anyway.

---

### Post by FuturePilot on 2007-04-05
Well I consider Fluxbox extremely minimalistic. XFCE is like a compromise between Fluxbox and Gnome. It's somewhere in the middle.

---

### Post by garybrlow on 2007-04-05
Xubuntu is faster even with Beryl on but you can only feel the difference if you use old computers with low resources. Gnome and KDE is really slow on them.

I tried all 3 desktop/window managers at default settings on a Celeron 2.0Ghz with 256MB RAM and an NVIDIA 5200 card with 128MB VIDEO RAM. KDE is the slowest, GNOME in the middle, and XFCE the fastest. There's also Enlightenment, Fluxbox, IceWM and many others but I chose XFCE because it fits my needs. But the most compete desktop/window manager is KDE its configuration wizards for almost everything. I started out on KDE on route migration from Windows. You can actually set KDE to run on slower machines it will remove most if not all of its eye candy bling but still slow compared to XFCE.

Enlightenment is a miracle on a Pentium even a even a 386/486 it does amazing things but its very different from the rest. Its layout and set-up is very different from the ones that we are used to. Its no Beryl/Compiz but it does have bling, lots of it.

I am not even sure if you can run Beryl/Compiz on Enlightenment, Fluxbox or IceM perhaps someone could give more input. :)

Cheers!!!

GaryBrlow :biggrin:

---

### Post by bmartin on 2007-04-05
Agreed; the thing that amazes me is that it runs Gnome/KDE apps. I haven't found one that doesn't work yet. At allegedly supports KDE fully; Gnome app support is supposed to be mostly implemented.

Xfce is a great solution for someone who wants a Gnome-like interface without the huge memory footprint you get with Gnome or KDE.

---

### Post by bmartin on 2007-04-05
No, you can't run Beryl on Fluxbox because [both are window managers](http://wiki.gentoo-xeffects.org/FAQ#Can_I_use_compiz_or_beryl_with_fluxbox.2Fopenbox.3F). When Beryl starts, it replaces the currently running window manager. I believe it's the same case for Enlightenment and IceWM, but I'm not familiar with them.

---

### Post by diskotek on 2007-04-07
i think beryl is composite manager (i really don't know what does it mesn, haha). when you install beryl on xubuntu you are still seeing XFCE desktop with beryl effects..i think i should be same with other desktop managers like gnome/kde. 

by the way , Xfce+beryl is quite fast. i'm running it on 1,6 centrino, with 268 mb ram (that is shared with graphic vard as well). 

i suggest to give a try to samlinux 2007, it comes with beryl+xfce.just to taste it. but they make box full with programmes that i would never use :(

---

