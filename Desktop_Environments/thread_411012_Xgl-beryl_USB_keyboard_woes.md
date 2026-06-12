---
title: "Xgl-beryl USB keyboard woes"
date: 2007-04-16
forum: Desktop Environments
---

### Post by amohanty on 2007-04-16
I am running Xgl+Beryl SVN on a TP-60. I run into this weird problem with my MS-4000 USB keyboard. Every so often the key-repeat goes nuts, even if I have barely tapped the key. It does not happen if I use the laptop keyboard. 

Unfortunately the TP does not have a PS2 port, and the docking station does not seem to like the USB to PS2 converter so I am stuck with the USB keyboard. 

I have searched quite a bit and cannot seem to explain this. I think it may be an XGL problem, however things are fine under Metacity and I am guessing that Metacity is hiding Xgl's problems.

How do I go about debugging this, xev is not that useful since the events are generated correctly, just that there are too many of them.

Any clues would be greatly appreciated.

Thanks.
AM

---

### Post by mystran on 2007-04-27
> **amohanty said:**
> 
Unfortunately the TP does not have a PS2 port, and the docking station does not seem to like the USB to PS2 converter so I am stuck with the USB keyboard. 


PS/2 would not necessarily help. I've got a regular desktop, with Logitech iTouch connected as PS/2 with an adapter (since I sometimes boot operating systems that won't support USB). I'm getting the same problem as you do. Never seen it under anything other than Xgl so I'd say it's indeed an Xgl bug.

In fact, it seems it happens more often when I quickly tap a key, so I'd guess it's some timing-sensitive race somewhere in Xgl that causes it to drop the key release. I've also never seen it happen while I'm just typing text. Most often something relatively heavy happens at the same time. Like scrolling in Firefox often gets stuck. Thought it was Firefox bug, until I got it in Vim when I hit a key immediately after switching desktop (naturally with the mandatory cube rotation).

I haven't personally tried running Xgl without Beryl though, since switching to Metacity (under Xgl) causes some things to pretty much freeze on me: a minute average for each character typed into Firefox location bar for them to actually appear, and such.

---

