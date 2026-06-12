---
title: "Can I run compiz for only one monitor? (Intel 945gm)"
date: 2011-04-10
forum: Desktop Environments
---

### Post by vstojkovic on 2011-04-10
I've been looking into this issue this whole afternoon, but I couldn't reach a definitive conclusion, so I decided to ask. Sorry if it's been explained somewhere else, I truly didn't manage to find it.

I'm running Ubuntu 10.04 on a laptop with Intel 945GM graphics controller. My laptop's screen native resolution is 1280x800. When I'm using only that, compiz runs fine.

When I connect a second screen -- a TV with native resolution of 1360x768 -- it doesn't work because the virtual screen resolution exceeds the maximum 3D texture size [2048x2048].

Lowering the resolution of both screens until the total size is less than 2048x2048 works, but it's really ugly and sacrifices a lot of screen real estate.

My question is: is there any way whatsoever to make compiz run only on my laptop screen and disregard the other one? An even better solution would be to run two instances of compiz, one for each screen, but I'll settle for having it on my laptop screen only, if possible.

Please bear in mind that, although I've used linux for a while now, it's always been as a "mortal" user, so I'm quite a newbie when it comes to administration.

Thanks in advance.

---

### Post by 3Miro on 2011-04-10
Compiz either runs or it doesn't. It stands on top of the desktop environment, so there is no way to use it "selectively". There is no way to use two instances of it either.

You can try to set the two monitors to "twin" view (or mirror view) form System -> Prefs -> Display. Then it shouldn't take as much memory.

My experience with Intel video and compiz on external monitor is that it is not very good. Intel cards simply don't have the power to handle the effects on two screens (or even just one large external screen). If you don't have effects, you might as well use Metacity (System -> Prefs -> Appearance -> Visual Effects -> None). Metacity should work on both monitors.

Another solution is to get a smaller external monitor.

---

### Post by Krytarik on 2011-04-10
I believe the only way to be able to utilize both screens (as opposed to mirroring one) *and* have Compiz running, is to set them up as separate xscreens by creating an according xorg.conf. But the downside of this is that you can't move windows between them. If you can live with that, see this guide for a template:
[https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen](https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen)

But:
- create "/etc/X11/xorg.conf" instead
- leave aside the Nvidia specific options
- set "intel" as the 'Driver'

However, it may well be that, like *3miro* pointed out, your video chip isn't capable to do all the work in the end.

Greetings.

---

