---
title: "Games stretched out off shape on ubuntu"
date: 2013-01-19
forum: Gaming &amp; Leisure
---

### Post by tahdas on 2013-01-19
I downloaded several games from the ubuntu store and all them stretched out of shape when i opened them.
What do i do to change that?

---

### Post by Lightning Dragon on 2013-01-19
Hello,

We will need a little more details on the matter, and if possible, some screenshots of the issue. But first, stretched out of shape? Do you mean the resolution changed/increased?

If you have GPU drivers installed, please see the settings for overscan. If I understand your problem correctly, your screen is stretching to the left/right "beyond" the monitor resolution, right?

---

### Post by tahdas on 2013-01-20
Yes it strechs to right.
Thanks!

---

### Post by Lightning Dragon on 2013-01-20
Hello,

Do you have GPU drivers installed? If so, go into the settings provided and see what the overscan is set to. It might be called something different if you don't have nvidia, but it *should* be in there. 

Or, while the screen is stretching, go to your Displays (top right screen or search through the Dash) and see if it forced your resolution into something different while playing and if it did, see if you can change it **back** to a normal resolution.

---

### Post by tahdas on 2013-01-20
I don't know if i have GPU drivers, how do i check?
Thanks,
tahdas

---

### Post by pardalet on 2013-01-20
> **tahdas said:**
> I don't know if i have GPU drivers, how do i check?
Thanks,
tahdas

Go to 'System Parameters' ---> 'Details'

What does it say next to 'Graphics'?


PS: Also, what brand of GPU do you have? Nvidia, ATI, Intel?

---

### Post by Lightning Dragon on 2013-01-20
Hello,

> **tahdas said:**
> I don't know if i have GPU drivers, how do i check?
Thanks,
tahdas

What are you running? Ubuntu? Or another distro?

Odds are that if you don't know, you don't have any installed. However, open up the terminal and type the following;

> 
$ lspci
 $ lspci -v
 $ lspci -v | lessAnd then post back the output. Also, in the Dash type "nvidia" and see if anything comes up. That will at least rule out nvidia x settings being installed. We also need to know bit type, too. Especially if you aim to install drivers.

It should also be under; System > Preferences > System/Hardware information.

Also, have you tested out what I said with the resolution during gameplay?

---

### Post by tahdas on 2013-01-20
> **pardalet said:**
> Go to 'System Parameters' ---> 'Details'

What does it say next to 'Graphics'?


PS: Also, what brand of GPU do you have? Nvidia, ATI, Intel?

Gallium 0.4 on AMD RV610 
Intel® Core™2 Duo CPU E8200 @ 2.66GHz × 2

---

### Post by tahdas on 2013-01-20
tahdas@tahdas:~$ lspci
00:00.0 Host bridge: Intel Corporation 82Q35 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82Q35 Express PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82Q35 Express MEI Controller (rev 02)
00:03.2 IDE interface: Intel Corporation 82Q35 Express PT IDER Controller (rev 02)
00:03.3 Serial controller: Intel Corporation 82Q35 Express Serial KT Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IO (ICH9DO) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV610 video device [Radeon HD 2400 PRO]
tahdas@tahdas:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82Q35 Express DRAM Controller (rev 02)
	Subsystem: Dell OptiPlex 755
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82Q35 Express PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe900000-feafffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:03.0 Communication controller: Intel Corporation 82Q35 Express MEI Controller (rev 02)
	Subsystem: Dell OptiPlex 755
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at f0200800 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: mei
	Kernel modules: mei

00:03.2 IDE interface: Intel Corporation 82Q35 Express PT IDER Controller (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: Dell OptiPlex 755
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	I/O ports at fe80 [size=8]
	I/O ports at fe90 [size=4]
	I/O ports at fea0 [size=8]
	I/O ports at feb0 [size=4]
	I/O ports at fef0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_generic

00:03.3 Serial controller: Intel Corporation 82Q35 Express Serial KT Controller (rev 02) (prog-if 02 [16550])
	Subsystem: Dell OptiPlex 755
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	I/O ports at ec98 [size=8]
	Memory at febda000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: serial

00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
	Subsystem: Dell OptiPlex 755
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at febe0000 (32-bit, non-prefetchable) [size=128K]
	Memory at febdb000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ecc0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: e1000e
	Kernel modules: e1000e

00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Optiplex 755
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ff20 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Optiplex 755
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at ff00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Optiplex 755
	Flags: bus master, medium devsel, latency 0, IRQ 22
	Memory at febd9c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Optiplex 755
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at febdc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: fe800000-fe8fffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Optiplex 755
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at ff80 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Optiplex 755
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at ff60 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Optiplex 755
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ff40 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Optiplex 755
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at ff980800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801IO (ICH9DO) LPC Interface Controller (rev 02)
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: lpc_ich

00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA Controller [AHCI mode] (rev 02) (prog-if 01 [AHCI 1.0])
	Subsystem: Dell Device 0211
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 42
	I/O ports at fe00 [size=8]
	I/O ports at fe10 [size=4]
	I/O ports at fe20 [size=8]
	I/O ports at fe30 [size=4]
	I/O ports at fec0 [size=32]
	Memory at f0200000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
	Subsystem: Dell Optiplex 755
	Flags: medium devsel, IRQ 9
	Memory at febd9b00 (64-bit, non-prefetchable) [size=256]
	I/O ports at ece0 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV610 video device [Radeon HD 2400 PRO] (prog-if 00 [VGA controller])
	Subsystem: Dell Device 0402
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fe9f0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at dc00 [size=256]
	Expansion ROM at fea00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeon

tahdas@tahdas:~$ 
And i cant cut and paste all of the final command result.

---

### Post by Lightning Dragon on 2013-01-20
Hello,

If you cannot post the *full* output, please go to *System Information* and find what GPU it says you are currently using. It should be under the sub category of "Display".

> **tahdas said:**
> Gallium 0.4 on AMD RV610 
Intel® Core™2 Duo CPU E8200 @ 2.66GHz × 2

Alright, which distro are you using? If you are using Ubuntu 12.04 open the Dash and search up the drivers (what your card is. For example, I use Nvidia so I type "nvidia") and setting options should appear. Open it and see if you can find settings for overscan.

Also, please see if you can change the resolution while you are playing the game, or if it allows you to switch or if it remains on the same resolution and just messes up.

Thanks,

End;

[SIZE=1]If you don't have drivers installed, please consider reading this link. I am unsure of how to install drivers for *your* GPU, but this seems to work for what is listed in your output.

[http://ubuntuforums.org/showthread.php?t=889659](http://ubuntuforums.org/showthread.php?t=889659)[/SIZE]

---

### Post by tahdas on 2013-01-21
Ubuntu 12.10. I can only see a quarter of the screen so i cant really change settings.
thanks
tahdas

---

### Post by Lightning Dragon on 2013-01-21
Hello,

Then the resolution problem is different not like I thought it was. I was under the impression you could scroll left/right up and down "out" of the screen, not that it was simply zoomed in. With this problem, you could have easily accessed the Display manager at the top right of the screen.

Alright, can you see the Dash to the far left? Open it up and try to find Displays through there, or if you have a try, through the driver settings (that will require searching for the name of your driver in the Dash). 

Or, try this command;

```
$ sudo xrandr -s ????x????
```

Where the "?" is the input of your display. For example, for me it would be "$ sudo xrandr -s 1440x900". 

Though it would help to know your current display so if the command messes up you could switch back to it.

---

### Post by tahdas on 2013-01-21
I got it working, sorry i forgot to say so in this thread. It asked if it could send an error report (I dont remember what for) and then it worked.
Thanks 
tahdas

---

