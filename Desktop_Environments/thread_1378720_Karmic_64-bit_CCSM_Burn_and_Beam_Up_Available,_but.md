---
title: "Karmic 64-bit CCSM Burn and Beam Up Available, but not working"
date: 2010-01-11
forum: Desktop Environments
---

### Post by sacredfaith on 2010-01-11
Okay, this is my first real post in the Ubuntu forums. Excuse me for a second while I breathe in the fresh air of the open source movement, gaze upon the ever rising summit of computer customization that lay before me, and now...I take my first step towards...well, knowing more than I did yesterday. Here we go:

Posting in the right forum? Check.
Specific title? Check.
Grammar/Spelling to the best of my ability? Check and double check.
Spent more than 10 minutes searching these forums as well as Google? Check
(I've been working on this for the past few hours...actually). 

OS Specs:
Karmic 9.10 - 64 bit 

Relevant Hardware Specs:
Radeon HD 3870 
2 GB RAM

Summary: The "burn" and "beam up" effect do not work when activated through CompizConfig

System > Administration > Hardware Drivers ? Installed.
Simple CompizConfig Settings Manager Installed? Yes.

Installed packages listed in attached screenshot.

I've tried airplane, dream, explode, leaf spread, etc...and they all "do something". However, when I try 'burn' or 'beam up' the window simply disappears (it doesn't even try!) 

About an hour ago, I got it to give me a 'black silhouette'-ish effect. Like, it paused for the alloted amount of time, but nothing happened (except flickering horizontal black lines about the width of a single pixel - i.e. something went wrong). The windows hadn't changed after the install, and other things seemed a little...off. So I uninstalled everything with 'compiz' in it, and reinstalled it (with a better order in mind). 

While this is a fairly weathered topic, most of the advice catered to the 32 bit versions of Jaunty.

Please do not hesitate to ask for any further information! 

Kind Regards,

-sf

---

### Post by sacredfaith on 2010-01-11
SOLVED:

Under 
CCSM > Effects > Animation Add Ons

I had the "Animation Time Step for Intense Effects" set at 200 ms (roughly the entire length of the animation). Hence...the nothingness.

Kind Regards,

-sf

---

### Post by sacredfaith on 2010-01-11
...how do I set the thread to "solved"? 

I searched the forums...but searching for "solved" is...well circuitous. 

Kind Regards,

-sf

Found it!! It's under "Thread Tools"...silly me!

---

