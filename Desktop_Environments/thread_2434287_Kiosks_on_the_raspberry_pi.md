---
title: "Kiosks on the raspberry pi"
date: 2020-01-03
forum: Desktop Environments
---

### Post by coderchris2 on 2020-01-03
Hi all

(Apologies if this is the wrong forum for this question - it just seemed the one where people might have the most relevent experience regarding my issue)

I've been playing around with tutorials all day that spin off (in one way or another) from [https://tutorials.ubuntu.com/tutorial/electron-kiosk]("https://tutorials.ubuntu.com/tutorial/electron-kiosk#2")

Long story short, I want to create a kiosk application based on electron as described, and I'd like to run that (for trials) on a raspberry pi - (I have all versions of pi to hand for testing, but am currently attempting this on a pi2).

Now, if I install the official "classic" ubuntu 18.04.x or 19.10.x for the raspberry pi 2 I can't get a working version of wayland up and running at all (x11 runs fine with  lubuntu and others).

If I install and use ubuntu core 18 instead, wayland and the mir-kiosk example apps referenced in the tutorial work fine out of the box.

I'd like to get this working with classic ubuntu but am not sure what's missing as such, mainly it seems to be that it can't start/find the drm device in classic (but this seems to be fine out of the box on core).

Given I'm using builds for the raspberry 2 specifically in all cases and that core should be a reduced version of classic I'm surprised something (wayland) works in core but not in classic.

I understand a move back to x11 from wayland generally for classic was initiated a few versions ago (from 17.x? maybe) but as other posts around the web hint, this shouldn't prevent wayland from working in general on new classic versions should it?

Any thoughts on how to compare the two further and work out what's missing in classic that core has?

Or how to get this working in classic generally?

I should add - the x11 instructions for classic do seem to work fine on a standard PC running ubuntu 19.10 - it's more a difference between what's in the raspberry pi specific releases it seems.

---

