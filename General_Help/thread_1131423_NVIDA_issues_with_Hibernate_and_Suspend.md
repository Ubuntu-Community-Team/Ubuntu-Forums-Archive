---
title: "NVIDA issues with Hibernate and Suspend"
date: 2009-04-20
forum: General Help
---

### Post by m.cowan on 2009-04-20
Hi Everyone. 

Although there are a few threads on this issue - none of them seem to provide a solution to me. 

**The suspend issue:**After executing suspend I cannot resume the session. The screen remains blank (except for one line of text which displays monetarily) something about 'outside of bus sequence'
[B]
The hibernate issue: [/B]After executing hibernate the screen dims, however after a moment the password box pops up and I'm back in my session (fails to hibernate).

From what I've been told over IRC #ubuntu is that it's related to the nvida drivers. I've got the latest nvida restricted driver version 96.

Can I resolve this?
Any help will be appreciated,
Thanks :popcorn:

---

### Post by Captain Regular on 2009-04-25
I'm having the exact same problem. Intel Core2 Duo on a P35 chipset motherboard, and an nVidia 8800GT video card. It was working back in 8.04, but I decided to do the distro upgrade to 8.10 and that broke suspend. It ENTERS suspend just fine, but upon restart, all I get is a black screen with a blinking white underline-style cursor in the top left, and the system is completely unresponsive to anything except the power and reset buttons.

---

### Post by Therion on 2009-04-25
> **Captain Regular said:**
> I'm having the exact same problem. Intel Core2 Duo on a P35 chipset motherboard, and an nVidia 8800GT video card. It was working back in 8.04...
Things are a LITTLE better on my Intel P45 chipset (via an Asus P5Q mobo (I'm also running an Intel C2D and an 8800GTS video card)): Suspend works great, but when I resume I have no Internet (my WIRED eth0 can't obtain a MAC address) and the whole system is so slow and jerky it's unusable.  I've quite Suspending altogether.  Suspend was a treat with 8.04 for me as well.

---

