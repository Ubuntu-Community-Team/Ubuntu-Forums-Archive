---
title: "How to get sound working?"
date: 2008-04-13
forum: Desktop Environments
---

### Post by stair314 on 2008-04-13
Audio seems fairly determined not to work on my computer, and I don't know much about PC hardware or Ubuntu so I'm not having a lot of luck trying to do anything intelligent to fix it.
I've tried installing jackd, changing the device in sound preferences, and turning everything up in alsamixer. And of course I've made sure my volume is turned up and not set to mute, and that my speakers are connected.
I've noticed that alsamixer does not allow any volume control on headphones. Does that mean the OS doesn't realize the computer has a headphone port?
My motherboard is an MSI P79 SLI Platinum, and I don't have any additional sound card or anything like that. I'm running Ubuntu 7.10.

---

### Post by warp99 on 2008-04-13
You can run this in a terminal:
```
lspci -v
```
plus run this:
```
lsmod |grep snd
```
and viola! You have sound card and driver information. Please post the results to this thread.

---

### Post by stair314 on 2008-04-13
Output of sudo lspci -v:
> 

00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 0000
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 0000
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 0000
	Flags: 66MHz, fast devsel

00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 0000
	Flags: 66MHz, fast devsel

00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 0000
	Flags: 66MHz, fast devsel

00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 0000
	Flags: 66MHz, fast devsel

00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 0000
	Flags: 66MHz, fast devsel

00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 0000
	Flags: 66MHz, fast devsel

00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 0000
	Flags: 66MHz, fast devsel

00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 0000
	Flags: 66MHz, fast devsel

00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: bus master, 66MHz, fast devsel, latency 0

00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 0000
	Flags: 66MHz, fast devsel

00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=05, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fa000000-fe9fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0c55
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fea00000-feafffff
	Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0c55
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0c55
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7380
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
	Capabilities: [e0] HyperTransport: MSI Mapping

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7380
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 4f00 [size=128]

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7380
	Flags: 66MHz, fast devsel, IRQ 11
	I/O ports at 5000 [size=64]
	I/O ports at 6000 [size=64]
	Capabilities: [44] Power Management version 2

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7380
	Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7380
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at f9fff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7380
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at f9ffec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port
	Capabilities: [80] Power Management version 2

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7380
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: [44] Power Management version 2

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7380
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at b800 [size=8]
	I/O ports at b480 [size=4]
	I/O ports at b400 [size=8]
	I/O ports at b080 [size=4]
	I/O ports at b000 [size=16]
	Memory at f9ffd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
	Capabilities: [cc] HyperTransport: MSI Mapping

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7380
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at ac00 [size=8]
	I/O ports at a880 [size=4]
	I/O ports at a800 [size=8]
	I/O ports at a480 [size=4]
	I/O ports at a400 [size=16]
	Memory at f9ffc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
	Capabilities: [cc] HyperTransport: MSI Mapping

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=64
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: feb00000-febfffff
	Capabilities: [b8] Subsystem: nVidia Corporation Unknown device cb84
	Capabilities: [8c] HyperTransport: MSI Mapping

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7380
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at f9ff8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7380
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at f9ff7000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at a080 [size=8]
	Capabilities: [44] Power Management version 2

01:00.0 PCI bridge: nVidia Corporation Unknown device 05b1 (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=01, secondary=02, subordinate=05, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fa000000-fe9fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [40] Power Management version 3
	Capabilities: [60] Express Upstream Port IRQ 0
	Capabilities: [a0] Subsystem: Micro-Star International Co., Ltd. Unknown device 7380

02:00.0 PCI bridge: nVidia Corporation Unknown device 05b1 (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=02, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fa000000-fe9fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [40] Power Management version 3
	Capabilities: [60] Express Downstream Port (Slot+) IRQ 0

02:02.0 PCI bridge: nVidia Corporation Unknown device 05b1 (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=02, secondary=04, subordinate=04, sec-latency=0
	Capabilities: [40] Power Management version 3
	Capabilities: [60] Express Downstream Port (Slot+) IRQ 0

02:03.0 PCI bridge: nVidia Corporation Unknown device 05b1 (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=02, secondary=05, subordinate=05, sec-latency=0
	Capabilities: [40] Power Management version 3
	Capabilities: [60] Express Downstream Port (Slot+) IRQ 0

03:00.0 VGA compatible controller: nVidia Corporation Unknown device 0611 (rev a2) (prog-if 00 [VGA])
	Subsystem: XFX Pine Group Inc. Unknown device 2330
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at cc00 [size=128]
	[virtual] Expansion ROM at fe9e0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint IRQ 0

06:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at feafe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [68] Power Management version 2
	Capabilities: [50] Express Legacy Endpoint IRQ 1

06:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03) (prog-if 85 [Master SecO PriO])
	Subsystem: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller
	Flags: bus master, fast devsel, latency 0, IRQ 17
	I/O ports at dc00 [size=8]
	I/O ports at d880 [size=4]
	I/O ports at d800 [size=8]
	I/O ports at d480 [size=4]
	I/O ports at d400 [size=16]
	Capabilities: [68] Power Management version 2

08:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 380d
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at febff800 (32-bit, non-prefetchable) [size=2K]
	I/O ports at ec00 [size=128]
	Capabilities: [50] Power Management version 2


Output of lsmod | grep snd:
> 
snd_hda_intel         337192  1 
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                94344  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27272  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    69288  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
snd_page_alloc         12560  2 snd_hda_intel,snd_pcm


---

### Post by warp99 on 2008-04-13
Well the sound modules are loaded, Your sound driver is snd-hda-intel and your card is listed here:

> 00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
Subsystem: Micro-Star International Co., Ltd. Unknown device 7380
Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
Memory at f9ff8000 (32-bit, non-prefetchable) [size=16K]
Capabilities: [44] Power Management version 2
Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
Capabilities: [6c] HyperTransport: MSI Mapping

This card has the Realtek ACL883 chipset and a host of problems, but the most common are listed here:

> 
Module snd-hda-intel
  --------------------

    Module for Intel HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8),
                ATI SB450, SB600, RS600,
                VIA VT8251/VT8237A,
                SIS966, ULI M5461

    model       - force the model name
    position_fix - Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO si$
    single_cmd  - Use single immediate commands to communicate with
                codecs (for debugging only)
    enable_msi  - Enable Message Signaled Interrupt (MSI) (default = off)

    This module supports one card and autoprobe.
    
    Each codec may have a model table for different configurations.
    If your machine isn't listed there, the default (usually minimal)
    configuration is set up.  You can pass "model=<name>" option to
    specify a certain model in such a case.  There are different
    models depending on the codec chip.

          Model name    Description
          ----------    -----------
        ALC883/888
        
          3stack-dig    3-jack with SPDIF I/O
          6stack-dig    6-jack digital with SPDIF I/O
          3stack-6ch    3-jack 6-channel
          3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
          6stack-dig-demo  6-jack digital for Intel demo board
          acer          Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
          medion        Medion Laptops
          targa-dig     Targa/MSI
          targa-2ch-dig Targs/MSI with 2-channel
          laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
          auto          auto-config reading BIOS (default)


So what you need to do is edit you options file to load one of the models to your sound-card. Most likely it would be '3stack-dig', but maybe not. So do the following:

```
sudo gedit /etc/modprobe.d/options
```

and append this line at the bottom of the file:

```
options snd-hda-intel index=0 model=3stack-dig
```

then save the file and reboot. Sound should be working.  If not it may be that one of the other models listed is yours so replace '3stack-dig' with the correct one.

---

### Post by twist2b on 2008-04-13
Hardy works out of the box,



Gusty: 
There is a much easier way to get sound working. Install linux-backports-modules (which I think is under main, not the backports repo.) It then just works, and you do not have to fiddle around and reinstall stuff from time to time.


Feisty: I dont really remember but try this:
[http://ubuntuforums.org/showpost.php?p=3475485&postcount=235](http://ubuntuforums.org/showpost.php?p=3475485&postcount=235)

---

### Post by stair314 on 2008-04-15
I eventually got sound to work using something from twist's post. I wasn't quite sure which model I had to be able to follow warp's advice and my first guess didn't work.

---

