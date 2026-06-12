---
title: "4 virtual machines on one physical machine"
date: 2011-11-03
forum: Desktop Environments
---

### Post by eyeland on 2011-11-03
hello
1) plan to buy a fully equipped physical computer
2) in addition to buy 3 monitors, 3 keyboards, 3 mice, 3 cameras, 3 columns
3) the need for physical hardware resources are allocated so that one physical receive 4 virtual (1 physical + 3 virtual)
4) Advise please, what recommendations to the physical components, which software to use?
5) computers will be used in office settings, it is minimal: the Internet, communication in audio, video chatting, office documents.
thanks!

---

### Post by 3Miro on 2011-11-03
4-core CPU + 4GB of RAM should give you one core + 1GB of RAM per machine. I would also pick a video card with at least 1GB of Video RAM. Assuming you are going to use Linux as the host OS, I wouldn't use anything other than Nvidia. ATI may work well enough, but Intel will probably choke.

If your budget allows for it. Get a 2GB Video RAM card and 8GB of regular RAM. Couple of extra cores would also be useful.

Virtual Box should be able to handle this in terms of software.

---

### Post by CharlesA on 2011-11-03
> **3Miro said:**
> 4-core CPU + 4GB of RAM should give you one core + 1GB of RAM per machine. I would also pick a video card with at least 1GB of Video RAM. Assuming you are going to use Linux as the host OS, I wouldn't use anything other than Nvidia. ATI may work well enough, but Intel will probably choke.

If your budget allows for it. Get a 2GB Video RAM card and 8GB of regular RAM. Couple of extra cores would also be useful.

Virtual Box should be able to handle this in terms of software.

+1. I didn't think that you could throw a VM on each screen. Not quite sure how it will work with the extra keyboards and mice though - wouldn't they be "fighting" for control of the host OS?

---

### Post by eyeland on 2011-11-03
> **3Miro said:**
> Virtual Box should be able to handle this in terms of software.

bun if I will start 4 VM with VirtualBox on one phisical pc, the conflict will be?

---

### Post by aeiah on 2011-11-03
the virtual machine part isn't going to be your issue: getting 3 keyboard/mouse/monitors working independently of eachother is. there's a way of doing it with linux but its fairly complicated if i remember correctly. roughly speaking:

set up 3 profiles in xorg for the keyboard/mouse/monitors and assign each one to a user account. from the user account, you could then use tsclient to attach to headless virtual machines. are you using the virtual machines for a specific reason? (ie, to run windows?) or do you just presume that it is required to have 3 users using the system at once?

its probably easier and cheaper just to get 3 small machines :p

---

### Post by CharlesA on 2011-11-03
> **aeiah said:**
> 
its probably easier and cheaper just to get 3 small machines :p

Yep. Could even run them as dumb terminals too and boot off the network.

---

### Post by eyeland on 2011-11-03
theoretical issue is: on a physical computer, connect 4 monitors, 4 keyboards, 4 mice, 4 cameras with microphones, 4 pairs of speakers who will work with their own virtual operating system, thank you for comments

---

### Post by CharlesA on 2011-11-03
> **eyeland said:**
> theoretical issue is: on a physical computer, connect 4 monitors, 4 keyboards, 4 mice, 4 cameras with microphones, 4 pairs of speakers who will work with their own virtual operating system, thank you for comments

I doubt that is going to be possible. I guess you could use a huge usb hub to hook up the keyboard, mice, camera and speakers, but then you run into the problem with each input device wanting to work on the host itself.

---

