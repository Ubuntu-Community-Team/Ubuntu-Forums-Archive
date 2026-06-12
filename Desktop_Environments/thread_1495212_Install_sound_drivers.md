---
title: "Install sound drivers"
date: 2010-05-27
forum: Desktop Environments
---

### Post by L4nce0 on 2010-05-27
I was trying to reinstall vista on my laptop and 7 in my desktop a few days ago, and I kid you not, both failed on installation. Being already annoyed as I just reinstalled at the start of this college semester, I popped in my roommates disc and here I am! Though I'm having a bit of trouble =) I have no sound! Please help!


l4nce0@NexusLinux:~$ lspci -v
00:00.0 Host bridge: nVidia Corporation Device 0800 (rev b1)
    Subsystem: nVidia Corporation Device c73e
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation Device 0808 (rev a1)
    Subsystem: nVidia Corporation Device c73e
    Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation Device 0809 (rev a1)
    Subsystem: nVidia Corporation Device c73e
    Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation Device 080a (rev a1)
    Subsystem: nVidia Corporation Device c73e
    Flags: bus master, 66MHz, fast devsel, latency 0

00:00.4 RAM memory: nVidia Corporation Device 080b (rev a1)
    Subsystem: nVidia Corporation Device c73e
    Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation Device 080c (rev b1)
    Subsystem: nVidia Corporation Device c73e
    Flags: bus master, 66MHz, fast devsel, latency 0

00:00.6 RAM memory: nVidia Corporation Device 080d (rev a1)
    Subsystem: nVidia Corporation Device c73e
    Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation Device 080e (rev a1)
    Subsystem: nVidia Corporation Device c73e
    Flags: 66MHz, fast devsel

00:01.0 RAM memory: nVidia Corporation Device 080f (rev a1)
    Subsystem: nVidia Corporation Device c73e
    Flags: 66MHz, fast devsel

00:01.1 RAM memory: nVidia Corporation Device 0810 (rev a1)
    Subsystem: nVidia Corporation Device c73e
    Flags: 66MHz, fast devsel

00:01.2 RAM memory: nVidia Corporation Device 0811 (rev a1)
    Subsystem: nVidia Corporation Device c73e
    Flags: 66MHz, fast devsel

00:01.3 RAM memory: nVidia Corporation Device 0812 (rev a1)
    Subsystem: nVidia Corporation Device c73e
    Flags: 66MHz, fast devsel

00:01.4 RAM memory: nVidia Corporation Device 0813 (rev a1)
    Subsystem: nVidia Corporation Device c73e
    Flags: 66MHz, fast devsel

00:01.5 RAM memory: nVidia Corporation Device 0814 (rev a1)
    Subsystem: nVidia Corporation Device c73e
    Flags: 66MHz, fast devsel

00:01.6 RAM memory: nVidia Corporation Device 081a (rev a1)
    Subsystem: nVidia Corporation Device c73e
    Flags: bus master, 66MHz, fast devsel, latency 0

00:01.7 RAM memory: nVidia Corporation Device 080e (rev a1)
    Subsystem: nVidia Corporation Device c73e
    Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation Device 0815 (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=04, sec-latency=0
    I/O behind bridge: 00008000-00009fff
    Memory behind bridge: dfc00000-dfefffff
    Prefetchable memory behind bridge: 00000000b0000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:04.0 PCI bridge: nVidia Corporation Device 0817 (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
    Subsystem: nVidia Corporation Device c73e
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
    Subsystem: nVidia Corporation Device c73e
    Flags: bus master, 66MHz, fast devsel, latency 0
    I/O ports at fc00 [size=128]

00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
    Subsystem: nVidia Corporation Device c73e
    Flags: 66MHz, fast devsel, IRQ 255
    I/O ports at f800 [size=64]
    I/O ports at f400 [size=64]
    I/O ports at f000 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1) (prog-if 10)
    Subsystem: nVidia Corporation Device c73e
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at dffff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2) (prog-if 20)
    Subsystem: nVidia Corporation Device c73e
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at dfffe000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1) (prog-if 8a [Master SecP PriP])
    Subsystem: nVidia Corporation Device c73e
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at ec00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_amd

00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
    Subsystem: nVidia Corporation Device c73e
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    I/O ports at 09f0 [size=8]
    I/O ports at 0bf0 [size=4]
    I/O ports at 0970 [size=8]
    I/O ports at 0b70 [size=4]
    I/O ports at d800 [size=16]
    Memory at dfffd000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv

00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
    Subsystem: nVidia Corporation Device c73e
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    I/O ports at 09e0 [size=8]
    I/O ports at 0be0 [size=4]
    I/O ports at 0960 [size=8]
    I/O ports at 0b60 [size=4]
    I/O ports at c400 [size=16]
    Memory at dfffc000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv

00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
    Subsystem: nVidia Corporation Device c73e
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    I/O ports at c000 [size=8]
    I/O ports at bc00 [size=4]
    I/O ports at b800 [size=8]
    I/O ports at b400 [size=4]
    I/O ports at b000 [size=16]
    Memory at dfffb000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv

00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2) (prog-if 01)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
    I/O behind bridge: 00007000-00007fff
    Memory behind bridge: d4000000-dbffffff
    Capabilities: <access denied>

00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
    Subsystem: nVidia Corporation Device c73e
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at dfff0000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
    Subsystem: nVidia Corporation Device c73e
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 30
    Memory at dfffa000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at ac00 [size=8]
    Memory at dfff9000 (32-bit, non-prefetchable) [size=256]
    Memory at dfff8000 (32-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
    Subsystem: nVidia Corporation Device c73e
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 31
    Memory at dfff7000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at a800 [size=8]
    Memory at dfff6000 (32-bit, non-prefetchable) [size=256]
    Memory at dfff5000 (32-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:15.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    I/O behind bridge: 00005000-00006fff
    Memory behind bridge: dfb00000-dfbfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

01:00.0 PCI bridge: PLX Technology, Inc. PEX 8647 48-Lane, 3-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ab)
    Flags: bus master, fast devsel, latency 0
    Memory at dfee0000 (32-bit, non-prefetchable) [size=128K]
    Bus: primary=01, secondary=02, subordinate=04, sec-latency=0
    I/O behind bridge: 00008000-00009fff
    Memory behind bridge: dfc00000-dfdfffff
    Prefetchable memory behind bridge: 00000000b0000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

02:04.0 PCI bridge: PLX Technology, Inc. PEX 8647 48-Lane, 3-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ab)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=02, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: dfd00000-dfdfffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

02:08.0 PCI bridge: PLX Technology, Inc. PEX 8647 48-Lane, 3-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ab)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=02, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00008000-00008fff
    Memory behind bridge: dfc00000-dfcfffff
    Prefetchable memory behind bridge: 00000000b0000000-00000000bfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

03:00.0 VGA compatible controller: ATI Technologies Inc R700 [Radeon HD 4850]
    Subsystem: PC Partner Limited Device e870
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at dfde0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at 9c00 [size=256]
    [virtual] Expansion ROM at dfd00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: radeon

03:00.1 Audio device: ATI Technologies Inc HD48x0 audio
    Subsystem: PC Partner Limited Device aa30
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at dfdfc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

04:00.0 Display controller: ATI Technologies Inc R700 [Radeon HD 4850]
    Subsystem: PC Partner Limited Device e870
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    Memory at dfce0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at 8c00 [size=256]
    [virtual] Expansion ROM at dfc00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: radeon

04:00.1 Audio device: ATI Technologies Inc HD48x0 audio
    Subsystem: PC Partner Limited Device aa30
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at dfcfc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

06:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
    Subsystem: nVidia Corporation Device c73e
    Flags: bus master, medium devsel, latency 32, IRQ 19
    Memory at dbfff000 (32-bit, non-prefetchable) [size=2K]
    Memory at dbff8000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

06:09.0 Multimedia audio controller: Creative Labs SB X-Fi
    Subsystem: Creative Labs Device 002c
    Flags: bus master, medium devsel, latency 32, IRQ 17
    I/O ports at 7c00 [size=32]
    Memory at dbc00000 (64-bit, non-prefetchable) [size=2M]
    Memory at d4000000 (64-bit, non-prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: SB-XFi
    Kernel modules: snd-ctxfi

07:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 03) (prog-if 01)
    Subsystem: nVidia Corporation Device 0156
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at dfbfe000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

07:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 03) (prog-if 85 [Master SecO PriO])
    Subsystem: nVidia Corporation Device 0156
    Flags: bus master, fast devsel, latency 0, IRQ 16
    I/O ports at 6c00 [size=8]
    I/O ports at 6800 [size=4]
    I/O ports at 6400 [size=8]
    I/O ports at 6000 [size=4]
    I/O ports at 5c00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_jmicron

l4nce0@NexusLinux:~$ lsmod |grep snd
snd_hda_codec_atihdmi     3356  2 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_ctxfi              81876  2 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_pcm_oss
snd_timer              22276  2 snd_seq,snd_pcm
snd                    59204  21 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_ctxfi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
l4nce0@NexusLinux:~$

---

### Post by L4nce0 on 2010-05-28
bump

---

