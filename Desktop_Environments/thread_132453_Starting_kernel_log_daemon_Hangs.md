---
title: "Starting kernel log daemon Hangs"
date: 2006-02-18
forum: Desktop Environments
---

### Post by sparty2809 on 2006-02-18
Starting kernel log daemon hangs at boot.  It says [ok] but it won't go passed it.  Any ideas why?  It was booting fine until today.

---

### Post by zanoni on 2006-10-04
Hello,

I have the same problem. You find a solution ?

---

### Post by nothingxs on 2006-10-12
I just got this same problem. I think it may have something to do with ndiswrapper because my network configuration seems to take forever now on startup.

If, like in my situation, you're using ndiswrapper to run a wireless PCMCIA card (for example, my Netgear WG511v2), and the computer seems to take longer during the Network Interfaces step, then just make sure you don't boot with the card plugged in. Wait until you're at your desktop before plugging it in. This is the only work-around I've noticed (for this particular issue).

---

