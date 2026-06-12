---
title: "Ubuntu Feisty on Optiplex 745n"
date: 2007-07-19
forum: Dell  Ubuntu Support
---

### Post by unclben on 2007-07-19
I want to encourage what Dell is doing with Ubuntu and my desktop computer (P4 2.6C, born Fall 2003) recently died. What a nice coincidence! I couldn't find any Dellbuntus that I really liked, so I did the next-best thing - I bought a Dell n-series (i.e. no Windows) computer. I've got my shiny new Optiplex 745n up and running, so I figured I'd document my hardware-compatibility experience with Ubuntu 7.04 (Feisty).

**Hardware of interest...**
Monitor: Viewsonic VP201b LCD, 1600x1200 native res
CPU: Intel Core 2 Duo E4400
Chipset; Intel 965G
Video: Intel 965G (GMA3000X), VGA onboard + DVI dongle (I'm using DVI only)
Sound: Intel HDA onboard + SB Audigy 2 PCI
LAN: Broadcom 5754 onboard gigabit

**LiveCD experience...**
The only problem was related to video. As soon as GDM loaded, it was obvious that something was wrong. Everything was fuzzy, as if I was drunk or had taken off my glasses. It stayed that way after logging in. Five minutes of searching (ubuntuforums, google) later, it was obvious that I just needed to switch from the 'i810' video driver to the 'intel' driver. A few clicks in Synaptic and an X restart later (ctrl-alt-bksp), everything was sharp and crisp.

Note that my resolution was always detected correctly. I don't know what the actual problem is that caused the fuzziness, but the intel driver definitely fixed it.

**Install experience...**
The installation process went flawlessly. Ubuntu again chose the i810 driver, so I had to download and install the intel driver after booting into my new Fiesty install.

This time, however, I had a new problem - no sound! Audio had worked fine with the LiveCD, so I was pretty confused. Eventually I realized that there was probably some kind of conflict between the onboard audio (not in use) and the Audigy 2 (connected to my speakers). I rebooted, disabled the onboard audio in BIOS, and loaded Feisty again. Sure enough, sound worked perfectly.

**Summary**
Overall, I'm happy with my new 745n. I got a nice computer for a decent price, with the added bonus of showing support for non-Windows Dells. I'm not sure who to blame for the sound thing, but the video issue is probably Ubuntu's fault. Is there a reason to prefer the i810 driver over the intel driver? I really don't know the difference, other than I think the latter is suppopsed to be the 'new hotness'.

Other misc notes... the 745n is a solid machine. The cable routing is good, interior access is cake, hard drives have damped mounts, the whole thing is tool-less, and anyone outside the SPCR crowd would call it quiet. Most importantly to me, it offers Intel graphics (open-source drivers ftw!) with a DVI output. To top it all off, delivery was crazy-fast. I ordered the computer on a Sunday and it arrived at my house while I was at work on Wednesday. Three days!

(I hadn't seen a thread like this here or at the Dell Linux forums, so I thought I'd post something for posterity...)

---

