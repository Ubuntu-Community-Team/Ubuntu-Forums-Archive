---
title: "M1530 Sound Trouble"
date: 2008-09-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by spongypants23 on 2008-09-03
**The first issue has been solved. Please go to the second page of this topic for my newer problem!**

Having a bit of difficulty with the sound on my computer. (XPS M1530).

The volume is all funky, so to say. I don't hear anything until the meter says about 60%, and then it sounds more like 10%. I don't think it even goes up to 100%, because when the meter says that its still pretty quiet.

Some info:

According to lspci, the sound care i have is:
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

This isn't a recent problem. It's been present for as long as I've had this laptop, I just now decided to try and do something about it, since it's rather annoying.

System Information:
Ubuntu Hardy Heron 8.04 x84_64
Kernel 2.6.24-19-generic


Any help would be much appreciated.

---

### Post by jwalker on 2008-09-03
What happens when you use headphones? I only ask because before I got this model laptop I did I a lot of research. I got this laptop because I decided it was the best power to $$$ ratio. 
Anyway the reviews I read mentioned that the speakers on the 1530 are crap. I am inclined to agree.

---

### Post by TimDaniels on 2008-09-03
> **spongypants23 said:**
> (This is not a "no sound" issue.)

Having a bit of difficulty with the sound on my computer. (XPS M1530).

The volume is all funky, so to say. I don't hear anything until the meter says about 60%, and then it sounds more like 10%. I don't think it even goes up to 100%, because when the meter says that its still pretty quiet.


See the thread "another 'no sound' - M1330".  When everything settled down and I cleaned up the ALSA configuration state file per SuperM1's suggestion, I still had to fiddle with the Preferences panel that comes up when you right-click the speaker icon.  In that Preferences panel, I currently have "HDA Intel (ALSA mixer)" as the device, and "Master" as the track.  In the Open Volume Control panel -> File tab -> "Change device", I have "HDA Intel (ALSA mixer)" selected, and in the panel I have all the sliders set to max.  Then, to set the volume in normal operation, I left-click the speaker icon and use the single slider.  Most of the audible level is still above 50% of the slider's range, but it's wider and more linear than before.  It works, but don't expect an audio console.

*TimDaniels*

---

### Post by putz3000 on 2008-09-03
This laptop's audio works just fine under Vista, I don't think it is crap hardware - personally.  But I too have the same problem under Ubuntu.  However, if you plug head phones in the sound is just fine.  

I am wondering if anybody who bought this model preinstalled with Ubuntu from Dell has this problem or if theirs sounds just fine?

---

### Post by spongypants23 on 2008-09-03
Headphones work fine. Speakers work fine under Vista, so I know they aren't at fault here. But i'd rather not be sitting with headphones every time im on the computer.

@TimDaniels, I've already got HDA Intel set as the thingee.

---

### Post by TimDaniels on 2008-09-03
> **spongypants23 said:**
> Headphones work fine. Speakers work fine under Vista, so I know they aren't at fault here. But i'd rather not be sitting with headphones every time im on the computer.

@TimDaniels, I've already got HDA Intel set as the thingee.

Setting HDA Intel as the "thingee" is the least of the procedure.  Did you clean up the ALSA configuration file per the other thread?

*TimDaniels*

---

### Post by TimDaniels on 2008-09-03
> **putz3000 said:**
> This laptop's audio works just fine under Vista, I don't think it is crap hardware - personally.  But I too have the same problem under Ubuntu.  However, if you plug head phones in the sound is just fine.  

I am wondering if anybody who bought this model preinstalled with Ubuntu from Dell has this problem or if theirs sounds just fine?

The symptoms you describe are exactly the ones my M1330 had, but I installed Hardy from the Ubuntu site, not as part of the re-installation .iso file available on the Dell website.  Since things work fine under Vista, I suspect that the drivers for Ubuntu are "not the best".  And to partially answer your implied question, Dell's rep in these forums says that Dell's sound driver is standard Ubuntu.

*TimDaniels*

---

### Post by spongypants23 on 2008-09-04
> **TimDaniels said:**
> Setting HDA Intel as the "thingee" is the least of the procedure.  Did you clean up the ALSA configuration file per the other thread?

*TimDaniels*

Yeah, I did that as well. Didn't do anything.

---

### Post by Crafty Kisses on 2008-09-05
Post these results: ```
lspci -v 

```

---

### Post by spongypants23 on 2008-09-05
**Results of "lspci -v"**

```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Dell Unknown device 022e
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fa000000-feafffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 022e
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 6f20 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 022e
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 6f00 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 022e
	Flags: bus master, medium devsel, latency 0, IRQ 22
	Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Unknown device 022e
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f9f00000-f9ffffff
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Memory behind bridge: f9e00000-f9efffff
	Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0d, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f9c00000-f9dfffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 022e
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 6f80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 022e
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 6f60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 022e
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 6f40 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 022e
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Memory behind bridge: f9b00000-f9bfffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
	Subsystem: Dell Unknown device 022e
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Unknown device 022e
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 6fa0 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
	Subsystem: Dell Unknown device 022e
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 507
	I/O ports at 6eb0 [size=8]
	I/O ports at 6eb8 [size=4]
	I/O ports at 6ec0 [size=8]
	I/O ports at 6ec8 [size=4]
	I/O ports at 6ee0 [size=32]
	Memory at febfb800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
	Subsystem: Dell Unknown device 022e
	Flags: medium devsel, IRQ 10
	Memory at febfb700 (32-bit, non-prefetchable) [size=256]
	I/O ports at 10c0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device 022e
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at ef00 [size=128]
	[virtual] Expansion ROM at fc000000 [disabled] [size=128K]
	Capabilities: <access denied>

03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device 022e
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at f9bff800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) (prog-if 01)
	Subsystem: Dell Unknown device 022e
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at f9bff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
	Subsystem: Dell Unknown device 022e
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at f9bff500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Dell Unknown device 022e
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at f9bff600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f

09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
	Subsystem: Dell Unknown device 022e
	Flags: bus master, fast devsel, latency 0, IRQ 506
	Memory at f9ffc000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at de00 [size=256]
	Capabilities: <access denied>

0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
	Subsystem: Intel Corporation Unknown device 1121
	Flags: bus master, fast devsel, latency 0, IRQ 505
	Memory at f9efe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>


```

---

### Post by spongypants23 on 2008-09-20
NEVERMIND. I solved my own problem again.

---

### Post by putz3000 on 2008-10-12
You improved your audio performance?  If so how did you do that?

---

### Post by spongypants23 on 2008-10-13
> **putz3000 said:**
> You improved your audio performance?  If so how did you do that?

I didn't really imrove it in terms of quality, I just made it so it was a bit louder. It's audible around 50% volume now.

What I did is I made sure all the sliders under Playback were maxed, except the Master one. Pay special attention to the one labeled Front, since that's the one that likes to be lower.

Screenshot of Volume Control window:
[http://i11.photobucket.com/albums/a168/spongypants23/Skrmbild-VolymkontrollHDAIntelAlsam.png]("http://i11.photobucket.com/albums/a168/spongypants23/Skrmbild-VolymkontrollHDAIntelAlsam.png")

---

