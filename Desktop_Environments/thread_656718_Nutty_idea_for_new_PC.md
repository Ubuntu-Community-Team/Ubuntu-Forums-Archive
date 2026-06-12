---
title: "Nutty idea for new PC"
date: 2008-01-02
forum: Desktop Environments
---

### Post by jefuchs on 2008-01-02
I'm planning to build my own PC very soon.  It will be a pretty decent machine, with lots of multi-media capability.

Here's what I'm thinking.  I want to run multiple operating systems, and I got the idea to install a minimal version of Linux as the primary OS, and install VirtualBox to run other OSes within the primary system.

This would require a minimal Linux distro as the primary OS.  After booting up, it would act as a dashboard for launching whichever OS I needed for any given task.

So my question is, what distro do I need in order to run virtual machines efficiently, while eliminating bloat at bootup?

I primarily plan to run Ubuntu and Windows, but will play around with Mythbuntu and Linux MCE.  I may have multiple copies of some OS's, if it suits my needs.

Too nutty?

---

### Post by sceo on 2008-01-04
I think it sounds like a pretty cool idea, myself - and would love to hear how it goes.  I really like Damn Small Linux (DSL) for minimalist stuff.  I'm not sure if VirtualBox will run on it (but it's just Linux -- so why wouldn't it?), but if it does maybe that's the way to go?  You should start a wiki or a blog somewhere for your little project if you do get it underway.

---

### Post by kellemes on 2008-01-04
I hope you understand a guest os in a virtual machine will **not** give you the multimedia capability of the machine. You will be using a **virtual** graphic-card.

---

### Post by kidders on 2008-01-04
Hi there,

Any Linux will do, really. Your best options are small or very customisable distros (eg DSL, Gentoo, etc.). Within reason, your choice really shouldn't impact the actual functionality of your virtualised OSs, provided all your hardware is fully supported.

Personally, it's not a road I would go down though ... aside from the *massive* performance hit the applications running on your virtual machines will suffer, all your operating systems will see your hardware through the host OS's eyes, with a made-up virtual hardware implementation sandwiched in between. In my opinion (for what it's worth hehe), a standard, native multi-boot arrangement would be infinitely superior.

**Edit:** kidders echoes kellemes' sentiments :-/

---

### Post by kellemes on 2008-01-04
> **kidders said:**
> 
**Edit:** kidders echoes kellemes' sentiments :-/


Indeed.. being non-native-english-speaking I could never find the words you spoke. :popcorn:

---

### Post by kidders on 2008-01-04
> **kellemes said:**
> Indeed.. being non-native-english-speaking I could never find the words you spoke.Lol... actually, when I read what you wrote, my first thought was "Damn... that's *waaaay* clearer than what I posted!"

Anyhow, as we've both said, it seems a pity to waste a hardcore multimedia PC by running operating systems non-natively on it. Having said that, constantly having to reboot, just to switch from one OS to another would be a nightmare. There are ways of limiting the amount of rebooting that jefuchs would need to do though, and speeding them up a bit too ... hopefully he'll post back soon.

---

### Post by jefuchs on 2008-01-08
> **kidders said:**
> There are ways of limiting the amount of rebooting that jefuchs would need to do though, and speeding them up a bit too ... hopefully he'll post back soon.

Thanks for the responses. I suppose I should choose a decent Linux OS and use a VM only when I need Windows.

---

