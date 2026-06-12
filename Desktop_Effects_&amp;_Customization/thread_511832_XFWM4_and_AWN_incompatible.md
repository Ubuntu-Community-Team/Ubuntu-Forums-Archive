---
title: "XFWM4 and AWN incompatible"
date: 2007-07-28
forum: Desktop Effects &amp; Customization
---

### Post by buttons on 2007-07-28
At the moment, AWN steals focus from xfwm4 and refuses to give it back.  I've posted a couple times on the AWN forums, but no luck aside from one person confirming the problem.  Basically, the dock prevents any window from being focused, which makes the window manager itself useless.

It isn't a problem with the internal compositor, as one person suggested, because it steals focus even when the compositor is disabled.

Anyone have ideas?  I really like xfwm4, mostly because its compositor is the lightest and best I've used so far.

---

### Post by andrewsomething on 2007-07-29
Unfortunatly I believe it's a known bug that doesn't currently have a solution... =(

---

### Post by BuntuFreak on 2007-12-24
I was hoping to use XFWM4 with AVN. So thought I would wake up this thread in case there was a solution, since I saw another posting on the web that claimed that xcompmgr and xfwm4 worked with AVN.

I have an old Dell Laptop 750Mhz Latitide with Ubuntu 7.10. My ATI Rage probably has just 8 MB memory. My machine has 512MB. I ran compiz which had "problems compositing" since it was "missing xgl". So I installed xserver-gl and then compiz ran fine. Except that AVN was painfully slow rendering. Then I tried xcompmgr instead of compiz thinking things would be faster. No such luck. Again the slow rendering.

So I'm hoping there's another way. I could care less about the animations, bubbles, bouncing icons. I just want a nice looking "dock bar". Is there a way to get AVN to work in usable fashion? Perhaps my graphics card driver - though I think this is not the problem, and my card itself is.

By the way I tried that "italian project" dock bar application which claimed it was lightweight. They lied!

Maybe someone on the forums is in the same predicament as me and has written their own dock bar application they can share? Or perhaps the AVN team can simply have a AVN light version that just has the "look" without all the fancy animations (hint, hint, hint).

Thanks in advance for any help. I installed Ubuntu 7.10 just a week back. My 2 previous attempts at banishing Windows from my  life with Linux were spectacular failures. This time it is different. I'm almost ready to try Ubuntu on all my computers. It's just AVN and Co. problems that are holding me up.

---

### Post by buttons on 2007-12-24
> **BuntuFreak said:**
> I was hoping to use XFWM4 with AVN. So thought I would wake up this thread in case there was a solution, since I saw another posting on the web that claimed that xcompmgr and xfwm4 worked with AVN.

I have an old Dell Laptop 750Mhz Latitide with Ubuntu 7.10. My ATI Rage probably has just 8 MB memory. My machine has 512MB. I ran compiz which had "problems compositing" since it was "missing xgl". So I installed xserver-gl and then compiz ran fine. Except that AVN was painfully slow rendering. Then I tried xcompmgr instead of compiz thinking things would be faster. No such luck. Again the slow rendering.

So I'm hoping there's another way. I could care less about the animations, bubbles, bouncing icons. I just want a nice looking "dock bar". Is there a way to get AVN to work in usable fashion? Perhaps my graphics card driver - though I think this is not the problem, and my card itself is.

By the way I tried that "italian project" dock bar application which claimed it was lightweight. They lied!

Maybe someone on the forums is in the same predicament as me and has written their own dock bar application they can share? Or perhaps the AVN team can simply have a AVN light version that just has the "look" without all the fancy animations (hint, hint, hint).

Thanks in advance for any help. I installed Ubuntu 7.10 just a week back. My 2 previous attempts at banishing Windows from my  life with Linux were spectacular failures. This time it is different. I'm almost ready to try Ubuntu on all my computers. It's just AVN and Co. problems that are holding me up.

A fix is in the XFWM SVN branch and has been for about a month now.  I'm not sure if the fix made it into the recently-released 4.4.2 version, as I don't use XFCE anymore.

---

### Post by BuntuFreak on 2007-12-24
Thanks for replying and pardon my ignorance.

I'm not using XFCE that I understand comes with Xubuntu - the low memory footprint derivative of Ubuntu. Does this matter? Can I simply get xfwm4 and try to run AVN atop it?

Much obliged.

---

### Post by buttons on 2007-12-24
> **BuntuFreak said:**
> Thanks for replying and pardon my ignorance.

I'm not using XFCE that I understand comes with Xubuntu - the low memory footprint derivative of Ubuntu. Does this matter? Can I simply get xfwm4 and try to run AVN atop it?

Much obliged.

Though it's been a while since I've used a buntu, my understanding is all of the Xubuntu software is available in the standard repos, anyway.

But it doesn't matter, since the current XFWM4 version in Xubuntu doesn't have the fix.

According to [this bug](https://bugs.launchpad.net/awn/+bug/130480), the following ubuntu fix was released:

[quote=Lionel]xfwm4 (4.4.2-1ubuntu2) hardy; urgency=low

  * debian/01_dock-window-fix.patch: fix a bug that prevents windows to be
    focused while running awn. (LP: #130480,#162117)
  * Bump Standards-Version to 3.7.3.[/quote]

So you will need at least 4.4.2-1ubuntu2 (from hardy heron) in order to use AWN with ubuntu (and be using the official software, you could always apply the patch from that link and compile it yourself, but that's a big pain).

If you're feeling adventurous, upgrade your repos to hardy's, only upgrade xfce things, then change your repos back to gutsy.

Or use xcompmgr and turn off XFWM's compositor.

Hope that helps

---

