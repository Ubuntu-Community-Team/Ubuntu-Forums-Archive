---
title: "Video card on Dell OptiPlex 170L Mini-Tower"
date: 2009-05-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Falconmauro on 2009-05-08
Well I have double boot on my computer, xp and ubuntu Jaunty.

My computer has:

1 Gig RAM
3 Hard drives
1 Capture Card ( PCI ) which uses an extra PCI
1 Wireless card ( PCI )
1 Ethernet card?  ( im not sure if its an ethernet card, but I never use it, it looks like a dial up slot )

So, my plan is to install a good graphics card like the EVGA GeForce 8400 GS Video Card.

I have 2 questions:

1. I don't think I can uninstall the dell graphics card, cuse it looks like its a part of the mother board, so is it possible for me to have 2 video cards without causing any conflicts? on both xp and ubuntu

2. I really like my capture card, and I dont want to get rid of it, so I was thinking if I could get rid of the Ethernet card, the one I never use, but I don't want to take it off and find out that my computer actually needs it.

I know I'm a noob to all this, but please, if someone can actually help me it would be great

:)

---

### Post by coffeeaddict22 on 2009-05-08
Not 100% sre about the Dell setup, but certainly on another brand I've installed a video card; the trick is to disable the motherboard video in the BIOS and you're away.  

A PCI card almost by definition isn't essential to your system.  If you yank it out and it's got a function you need, you'll find out either a) when the cord attached to the port starts tugging ... or b) when you reboot and discover the lost functionality.  If you've got a non-ethernet connection, then you can only try it.  If you're really lucky it'll be a modem for those times when you want to use dialup... makes a good coaster.

If you're curious, run [CODE]lshw[/CODE before you pull the card, then remove it, reboot and run it again.  you should be able to spot the missing hardware.

---

