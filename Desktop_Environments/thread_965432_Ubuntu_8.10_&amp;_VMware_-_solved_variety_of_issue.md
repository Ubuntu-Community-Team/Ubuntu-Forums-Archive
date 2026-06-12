---
title: "Ubuntu 8.10 &amp; VMware - solved variety of issues"
date: 2008-10-31
forum: Desktop Environments
---

### Post by bmullan on 2008-10-31
I've been using Ubuntu for a couple of years now.   My home PC is an AMD 4200+ x64 machine w/4 G memory, 6 USB 2 SATA, DVD, CD, Bluetooth etc desktop.

Like many people I've had to cope with keeping Windows XP happy (re not hosing it up) but I kept wanting to move more toward Ubuntu/Linux over time.

One thing that has continuosly perplexed me was the issues I would have with my Linksys Wireless/driver, my built-in TV Tuner, wireless mouse/keyboard etc.

Yes, I've discovered via many hours of effort, learning, & searching to overcome most problems (ndiswrapper et al) but it always came down to compromises.    

For instance 

I had my Linksys wireless running OK ... but ONLY in 32Bit mode not 64bit.   

To avoid installing Grub I installed a 2nd hard drive and used my BIOS to choose which drive to boot from.  (I had my reasons <g>).

Anyway... I know this isn't perfect and some will argue but for me I've found a happy medium that seems to work quite well and cost me NO pain to use.

I bought VMware's Workstation s/w (v6.5) and installed it on my Windows XP machine (see above).

I created a new Virtual Machine w/2gig of my 4 Gig memory and 15Gig of virtual disk (it will grow automagically as needed).

I then told VMware to load & install the 

         ubuntu-8.10-desktop-amd.iso

image I had downloaded.

15 minutes later I was up and operational with Ubuntu 8.10 in 64 bit mode.

Performance is really good!   

Yes, Ubuntu could be be better installed natively without the virtual machine BUT what I got offsets that:

#1 everything works - my Linksys wireless, my bluetooth, my USB, my TV Tuner etc etc.

#2 Just a few weeks ago I'd played with installing Apple's OS-X the same way.

#3 I now have XP (which ugly as it sounds it the "host" for the virtual machine software VMWare).. 

OS-X and Ubuntu Ibis all running together on 1 machine and I didn't have to spend hours on any of it figuring out work-arounds for anything.

The virtualization meant my wireless keyboard/mouse, etc all works in any of the 3 environments and I didn't have to repartition anything, install any new boot-loaders (grub etc) at all.

I just thought I'd share this experience as there may be other's who'd like to try the same... it does work and works pretty well.

I was surprised !

---

### Post by bmullan on 2008-10-31
By the way I guess I should have mentioned this but my previous conversation could go the other direction as VMWare is available for the MAC (called Fusion) or for Linux.   So if you use a MAC and wanted for some reason to run XP ??? or Linux --- or if you run Linux and needed to do vice-versa ... you could do it without changing your host system.

---

