---
title: "Compiz Fusion + ATI HD2600 + 3D/video = flicker"
date: 2009-03-06
forum: General Help
---

### Post by humphreybc on 2009-03-06
Hi all, firstly, let me say that yes I do know this problem exists and yes I have looked in to it on my own and done forum searches etc, but most of the solutions I find seem to be applicable to higher-end ATI cards, and those that I come across that could be worked with my setup are much to hard for a ubuntu beginner like myself to implement. I also realise this is probably in the wrong forum, but I just signed up, so please forgive me and feel free to move it :)

**The problem**

Short version for those who can't be bothered reading:
Compiz Fusion + ATI HD2600 + 3D/video = mad flicker

Long version for those who want more information:

Most of you will know exactly what I am talking about just by reading the title, but here it is - I am running Ubuntu 8.10 x64 from the "install inside windows" option as a dual-boot with Vista on a Toshiba Satellite A200/S01 (specs: T7500 2.2Ghz Dual Core, ATI Radeon HD2600, 320GB HDD and 15.4" screen). Ubuntu runs really really nicely on my computer, and, after a few slightly painful days of setting everything up and numerous google searches, I have it configured well enough so that I set it as my default OS :)

Now one of the few problems I have left to solve is the fact that while running Compiz WM, 3D games and videos, and screensavers, flicker when played, fullscreen or not. I've found that by changing VLC player to use X11 output resolves the video playback issue, but not the other ones concerning games and the screensaver.

I updated my ATI drivers from the ati website, and that reduced flickering slightly but did not entirely remove it. So, my question is, will this be fixed in an update by either ubuntu, Compiz or ATI in the near future, or is there a way to fix it myself?

(By the way I tried using the Compiz icon to turn it off whenever I want to watch videos/use Celestia but this seemed to be a temporary fix to a serious issue and I would much prefer to fix it properly!)

Many thanks,
Benjamin

---

### Post by Josesordo on 2009-06-06
I have the same problems....to see videos good, I needed to off compiz..but now, I can see the videos good with X11 output in VLC player.
But the others issues with screensavers or 3D games...dont have solution yet. T_T
if you did find the solution...pls send me a email :p

---

### Post by Legace on 2009-06-06
It's a problem with the FGRLX driver and Compiz, and as of now has no good solution.

---

### Post by Josesordo on 2009-06-06
grr...well, maybe someday will be fix this..
And I have problem with flash in firefox...running slow T_T ..with compiz or not...

---

### Post by 3rdalbum on 2009-06-06
> **Legace said:**
> It's a problem with the FGRLX driver and Compiz, and as of now has no good solution.

More precisely, it's a problem with the FGLRX driver, as I haven't observed the problem with any other video cards.

I'm guessing your HD2600 is not supported in 3D operation by the default open-source driver?

---

### Post by Josesordo on 2009-06-07
well, the creator of this topic..told me that he fixed the problems, downloading the newest catalyst driver (9.4) from ATI...so, he said that now he can play videos good, screensaver running good and another stuff..
Lets see if that work for me...if not, I will post here..again...hehe;)

---

### Post by QIII on 2009-06-07
Catalyst has worked wonders.

Two problems I encountered:

1.  It buggered System -> Preferences -> Display so that the system freezes when I try to use that.

2.  I had to be sure to set the resolution in xorg.conf.

You have to use ATI Catalyst Control Center to adjust monitor settings.

---

