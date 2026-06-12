---
title: "Need some help (Video issue?)"
date: 2009-04-20
forum: General Help
---

### Post by Zoquara on 2009-04-20
I've been using Ubuntu 8.04 on my computer quite successfully for a few months now, and my husband finally got sick of WinVista, and asked me to install it on his computer, an Acer Aspire T690. Since I'd already done everything on my computer (some things a few times!) I thought "No problem!"... Was I wrong....

First problem... I couldn't get it to install. It kept freezing up about 10-15% into loading. (Pre-install menus). Not sure why, but I removed the video card he had in there (NVidia GeForce MX4000) and..... It worked. Installed with no hitched. Tried to re-install the vid card, and it wouldn't start up. Ok, fine. He has integrated gfx, and they're PROBABLY better than that card anyways (my line of thought. I'm no expert, so it's possible I'm wrong!)

So, I have it installed, and realize I can just copy most of what he wants straight from my computer (World of Warcraft via Wine) and save myself a LOT of hassle (installing via DVD disc takes time and effort... especially the WotLK expansion). So, I copy everything over, double-check, and attempt to boot up the game. Character selection screen loads no problem... character loads into the game, and then... Game freeze. It also does it with another game he installed. I'm *thinking* it's a video driver issue, but not sure.. What I can find on his video:

Monitor and Graphics
Video Integration:	Integrated
Video Memory Technology:	Dynamic Video Memory Technology 4.0
Display Type:	None.

Am I totally missing something? Is this a fixable problem, or should I knock him over the head and just install XP? Or... will his computer only run Vista for some odd reason?

---

### Post by 3rdalbum on 2009-04-20
On Linux, please give us the output of this command:

```
lspci
```

That will tell us what sort of graphics he actually has. I'm surprised a Geforce MX4000 can actually work on Vista and I'm sure his integrated graphics are better, but we need to know what they actually are.

---

### Post by Zoquara on 2009-04-20
> 00:00.0 Host bridge: Intel Corporation 82946GZ/PL/GL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82946GZ/PL/GL PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82946GZ/GL Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
04:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

That's what I got back (on his computer)

---

### Post by Zoquara on 2009-04-20
Still need help, please.

---

