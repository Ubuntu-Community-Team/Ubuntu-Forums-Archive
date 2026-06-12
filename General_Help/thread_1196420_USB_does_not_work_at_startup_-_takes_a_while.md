---
title: "USB does not work at startup - takes a while"
date: 2009-06-24
forum: General Help
---

### Post by jackp311 on 2009-06-24
Sorry for the long post, trying to give all the details. 
 
Let me first say that I am a firm believer in search before new threads. I can honestly find nothing on this. 
 
A few days ago, my 9.04 install on a self built computer using a Gigabyte G31-ES2L motherboard froze. Alt + PrtScrn + REISUB was uneffective. I left it for about an hour hoping it would get going. No luck. So, I did a hard shut down. (Power button would not initiate shutdown either)
 
I have done this once before. It usually causes errors when booting the next time (USB addressing: .. USB 1-5: ... error -110.) 
 
So, I did restore from my last backup via acronis. Still same problem. So, I let it boot a few times. (Took about 5 min each time) and it seemed to correct itself. 
 
However, my usb stopped working. 
 
When I went into the bios and disabled the usb 2.0 controller, usb worked again. I did some playing around and just could not get it to work with usb 2.0 enabled. Well, I let it sit for a while after a boot and low and behold it was working. 
 
So, after some reading, I started looking into modules. 
 
```
jack@e5200:~$ lsmod
Module                  Size  Used by
joydev                 18368  0 
usbhid                 42336  0 
binfmt_misc            16776  1 
video                  25360  0 
output                 11008  1 video
input_polldev          11912  0 
nvidiafb               52864  0 
fb_ddc                 10240  1 nvidiafb
i2c_algo_bit           14084  1 nvidiafb
vgastate               18048  1 nvidiafb
i2c_i801               17296  0 
shpchp                 40212  0 
lp                     17156  0 
snd_hda_intel         434100  5 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
arc4                    9856  2 
snd_seq_oss            37760  0 
ecb                    10752  2 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
ath9k                 263224  0 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              217464  1 ath9k
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
cfg80211               38288  1 mac80211
snd                    62628  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
psmouse                61972  0 
led_class              12036  1 ath9k
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
intel_agp              34108  0 
pcspkr                 10496  0 
ppdev                  15620  0 
serio_raw              13316  0 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
nvidia               7233756  36 
agpgart                42696  2 intel_agp,nvidia
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```Well, after seeing all these modules loaded, I wanted to see which of them loaded at startup. _My etc/modules was EMPTY except for "lp_"!!! So, I followed instructions found here [http://sidux.com/PNphpBB2-viewtopic-t-10643-newlang-zho.html](http://sidux.com/PNphpBB2-viewtopic-t-10643-newlang-zho.html) 
 
and used "lspci -v" to get:
 
```

jack@e5200:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
    Subsystem: Giga-byte Technology Device 5000
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: intel-agp
 
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f0000000-f3ffffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
    Subsystem: Giga-byte Technology Device a002
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f4100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at e000 [size=32]
    Kernel driver in use: uhci_hcd
 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at e100 [size=32]
    Kernel driver in use: uhci_hcd
 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at e200 [size=32]
    Kernel driver in use: uhci_hcd
 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at e300 [size=32]
    Kernel driver in use: uhci_hcd
 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20)
    Subsystem: Giga-byte Technology Device 5006
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f4104000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd
 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    Memory behind bridge: f4000000-f40fffff
    Capabilities: <access denied>
 
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
    Subsystem: Giga-byte Technology Device 5001
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt, intel-rng
 
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
    Subsystem: Giga-byte Technology Device b001
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at f000 [size=16]
    Kernel driver in use: ata_piix
 
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Giga-byte Technology Device b002
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at e800 [size=8]
    I/O ports at e900 [size=4]
    I/O ports at ea00 [size=8]
    I/O ports at eb00 [size=4]
    I/O ports at ec00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix
 
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
    Subsystem: Giga-byte Technology Device 5001
    Flags: medium devsel, IRQ 19
    I/O ports at 0500 [size=32]
    Kernel driver in use: i801_smbus
    Kernel modules: i2c-i801
 
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9500 GT (rev a1)
    Subsystem: eVga.com. Corp. Device c954
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f2000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at d000 [size=128]
    [virtual] Expansion ROM at f3000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb
 
03:01.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
    Subsystem: D-Link System Inc Device 3a69
    Flags: bus master, 66MHz, medium devsel, latency 168, IRQ 19
    Memory at f4000000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

```So I added all of those modules named into /etc/modules. But, it still doesn't work at startup. This problem is on the rear and front usb ports. The only USB device I have tried (and am really interested in) is my mouse and keyboard combo (kensington) but because it is not working at boot. Diagnosis is even tougher. 
 
I think that is all the info I have for now. ANy ideas?

---

