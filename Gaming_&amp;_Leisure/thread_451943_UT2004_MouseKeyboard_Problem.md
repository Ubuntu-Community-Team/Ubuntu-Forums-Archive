---
title: "UT2004 Mouse/Keyboard Problem"
date: 2007-05-22
forum: Gaming &amp; Leisure
---

### Post by apostate on 2007-05-22
Ok,

So I am using Ubuntu 7.04 on an intel imac...that probably confuses matters...and now I find that in UT2004 I cannot use the mouse and keyboard at the same time. If I am "looking" with the mouse, the keystrokes have no effect. If I am walking with the keyboard, I cannot look with the mouse! Is this a Mac hardware issue? And ATI issue?  I am stumped.  Every other aspect of the game seems to work right. It sucks a lot. I am using the restricted ATI driver that Ubuntu installs for you.

Any help would be welcome..

---

### Post by apostate on 2007-05-23
Anyone? I am feeling a bit like a pariah here....I haven't had a single post answered since I joined the forum.

:(

---

### Post by Jimbob17 on 2007-05-24
> **apostate said:**
> Anyone? I am feeling a bit like a pariah here....I haven't had a single post answered since I joined the forum.

:(

No, you're not a pariah. I have exactly the same problem with Kubuntu 7.04 running on a AMD Sempron processor. I'm using the PS/2 connections on the motherboard rather than USB. This problem didn't occur on Dapper Drake, when I was testing the PC system. This is using an Nvidia 6800GS card with the 1.0.9755 restricted drivers.

I don't have a solution at the mo though ....

Edit: Ok, I found a solution for my setup. I removed the mouseemu package (look at dmesg to check it's loaded by the kernel) and now UT2k4 works perfectly.

---

### Post by apostate on 2007-05-26
That did it!  Thx.

---

