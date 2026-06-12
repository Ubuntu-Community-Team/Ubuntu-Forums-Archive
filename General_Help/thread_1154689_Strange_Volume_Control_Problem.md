---
title: "Strange Volume Control Problem"
date: 2009-05-10
forum: General Help
---

### Post by -kg- on 2009-05-10
I am currently using my desktop, which is running 64 bit Hardy, and noticed a strange thing.

When you single-click the volume control on the right of the top menu bar, the volume control slider pop-down appears which allows you to adjust the volume.  Unfortunately, this slider does nothing for me.  I can take it from full volume to off and it doesn't adjust the volume.

However, I can double-click the icon, which brings up the full mixer and volume controls, and every applicable control on it will change the volume normally.  I have pulled them up together and neither one affects the other.  If I change the single-click slider, none of the ones on the mixer move, and if I vary the ones on the mixer (the other slider disappears, and I have to pull it back up) the single-click one has not moved.

I have noticed this a few times before this, but I just adjusted the volume on my player (normally, I use Rhythmbox on the desktop, as I listen to a particular radio station) to compensate.  But it seems strange to me that the volume control brought up by a single-click on the speaker icon isn't the same as the volume control brought up by a double-click on the same icon.

```
glenn@glenn-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:08.0 RAID bus controller: Promise Technology, Inc. PDC20378 (FastTrak 378/SATA 378) (rev 02)
00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
00:0c.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
00:0c.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
00:0e.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:0e.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
```

This is one of the early Soundblaster Live MP3+ cards.  Any more information you might need, just ask.

Think it might be that the single-click control is somehow linked to the on-board audio and the mixer volume controls are linked to the Soundblaster?

At some point in the future, I *really* need to upgrade some of my PCI cards.  Like I said, the SB card is really kind of old, and so is my video card (I mean; an nVidea 5200?! :rolleyes:).

---

