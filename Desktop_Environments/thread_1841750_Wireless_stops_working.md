---
title: "Wireless stops working"
date: 2011-09-10
forum: Desktop Environments
---

### Post by baz.g on 2011-09-10
Hi all,

I seem to have stumbled across a problem with my wireless. I am running 10.04 64bit on a dell laptop and I have the wireless configured to connect automatically with a static ip. Everything works fine, it connects automatically and everything is fine, but the laptop is not regularly used and normally just sits left on with the gltext screensaver running displaying date and time. When we do come to use it recently though, the wireless has disconnected itself and won't reconnect when we try, we have to reboot the laptop (although I am sure sudo /etc/init.d/networking restart would do the same thing).

No major changes recently, although I have added script to keep my wan ip updated to opendns, and a bounce ntp script running from chron.daily.

However, I have added the same scripts to the 32bit 10.04 running on my netbook which is also rarely used and left on all the time.

Any ideas please guys?

---

### Post by fdrake on 2011-09-10
> **baz.g said:**
> Hi all,

I seem to have stumbled across a problem with my wireless. I am running 10.04 64bit on a dell laptop and I have the wireless configured to connect automatically with a static ip. Everything works fine, it connects automatically and everything is fine, but the laptop is not regularly used and normally just sits left on with the gltext screensaver running displaying date and time. When we do come to use it recently though, the wireless has disconnected itself and won't reconnect when we try, we have to reboot the laptop (although I am sure sudo /etc/init.d/networking restart would do the same thing).

No major changes recently, although I have added script to keep my wan ip updated to opendns, and a bounce ntp script running from chron.daily.

However, I have added the same scripts to the 32bit 10.04 running on my netbook which is also rarely used and left on all the time.

Any ideas please guys?

does this happens when your computer is in sleep/suspend mode? Maybe your wirelss driver is not embedded in the kernel. Did you install the driver separately? if so you may want to add your wireless module to this file:
```

sudo cp /etc/default/acpi-suppor ~/acpi-suppor.bk
sudo gedit /etc/default/acpi-support
```
and look for 
> 
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

and add in the module filed your wireless module. reboot and test.


you may also change the following line to stop the network-manager before the pc goes to sleep:
> 
# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""

and on stop services put "/etc/init.d/network-manager".

---

### Post by baz.g on 2011-09-10
hi, thanks for the reply. the laptop does not sleep or suspend, i have disabled it. the wireless driver was not installed separately, it worked from the off.

if you think it will help to add it to the acpi-support file, could you tell me please how i find out the name of the wireless module?

many thanks :)

---

### Post by fdrake on 2011-09-10
> **baz.g said:**
> hi, thanks for the reply. the laptop does not sleep or suspend, i have disabled it. the wireless driver was not installed separately, it worked from the off.

if you think it will help to add it to the acpi-support file, could you tell me please how i find out the name of the wireless module?

many thanks :)
```

lshw -c Network
```
should give you a full description of the device with the module used
```
lsmod
```
list all the module loaded at boot. It should contain the name of the wireless module too. Post here the results of those commands.

---

### Post by baz.g on 2011-09-11
```
lshw -c Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:12:00.0
       logical name: eth1
       version: 01
       serial: 70:f1:a1:49:d3:0a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.51 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:fbd00000-fbd03fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: eth0
       version: 02
       serial: a4:ba:db:b8:6f:23
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:29 ioport:d000(size=256) memory:d0c10000-d0c10fff(prefetchable) memory:d0c00000-d0c0ffff(prefetchable) memory:fb300000-fb31ffff(prefetchable)
```

```
lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
rfcomm                 40393  4 
snd_hda_codec_atihdmi     3023  1 
sco                     9649  2 
snd_hda_codec_idt      61546  1 
snd_hda_intel          25805  3 
snd_hda_codec          85759  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
bridge                 53152  0 
stp                     2171  1 bridge
bnep                   11884  2 
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
l2cap                  34807  16 rfcomm,bnep
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
joydev                 11104  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
lib80211_crypt_tkip     8676  0 
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
fbcon                  39270  71 
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tileblit                2487  1 fbcon
font                    8053  1 fbcon
snd                    71283  18 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_wmi                2177  0 
bitblit                 5811  1 fbcon
uvcvideo               62851  0 
usbhid                 41116  0 
softcursor              1565  1 bitblit
fglrx                2353486  35 
psmouse                65040  0 
dell_laptop             7973  0 
soundcore               8052  1 snd
lp                      9336  0 
videodev               40518  1 uvcvideo
video                  20623  0 
v4l1_compat            15495  2 uvcvideo,videodev
vga16fb                12757  1 
intel_agp              29319  0 
serio_raw               4918  0 
v4l2_compat_ioctl32    11892  1 videodev
btusb                  13097  2 
vgastate                9857  1 vga16fb
output                  2503  1 video
dcdbas                  6886  1 dell_laptop
hid                    83888  1 usbhid
parport                37160  2 ppdev,lp
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
wl                   1964968  0 
lib80211                6151  2 lib80211_crypt_tkip,wl
bluetooth              58685  9 rfcomm,sco,bnep,l2cap,btusb
ahci                   38030  2 
r8169                  39714  0 
mii                     5237  1 r8169

```

many thanks :)

---

### Post by westie457 on 2011-09-11
Hi. Could you post the output of ```
lspci -vnn
```please.

With your wireless being called eth1 it looks like your driver is not configured properly

---

### Post by baz.g on 2011-09-11
```

lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 12)
	Subsystem: Dell Device [1028:0447]
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0045] (rev 12)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fbe00000-fbefffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
	Subsystem: Dell Device [1028:0447]
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at fbf09000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06) (prog-if 20)
	Subsystem: Dell Device [1028:0447]
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at fbf08000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
	Subsystem: Dell Device [1028:0447]
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fbf00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=11, subordinate=11, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d1600000-d17fffff
	Prefetchable memory behind bridge: 00000000d1800000-00000000d19fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=12, subordinate=12, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: fbd00000-fbdfffff
	Prefetchable memory behind bridge: 00000000d1a00000-00000000d1bfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 06)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=13, subordinate=13, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fb300000-fbcfffff
	Prefetchable memory behind bridge: 00000000d0c00000-00000000d15fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 06)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=15, subordinate=15, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fa900000-fb2fffff
	Prefetchable memory behind bridge: 00000000d0100000-00000000d0afffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06) (prog-if 20)
	Subsystem: Dell Device [1028:0447]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fbf07000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=20, subordinate=20, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b0b] (rev 06)
	Subsystem: Dell Device [1028:0447]
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b2f] (rev 06) (prog-if 01)
	Subsystem: Dell Device [1028:0447]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 30
	I/O ports at f070 [size=8]
	I/O ports at f060 [size=4]
	I/O ports at f050 [size=8]
	I/O ports at f040 [size=4]
	I/O ports at f020 [size=32]
	Memory at fbf06000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
	Subsystem: Dell Device [1028:0447]
	Flags: medium devsel, IRQ 3
	Memory at fbf05000 (64-bit, non-prefetchable) [size=256]
	I/O ports at f000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 06)
	Subsystem: Dell Device [1028:0447]
	Flags: bus master, fast devsel, latency 0, IRQ 3
	Memory at fbf04000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series] [1002:68e0]
	Subsystem: Dell Device [1028:0447]
	Flags: bus master, fast devsel, latency 0, IRQ 31
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at fbe20000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at e000 [size=256]
	Expansion ROM at fbe00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx

01:00.1 Audio device [0403]: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series] [1002:aa68]
	Subsystem: Dell Device [1028:0447]
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fbe40000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

12:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
	Subsystem: Dell Device [1028:0010]
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fbd00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl

13:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Dell Device [1028:0447]
	Flags: bus master, fast devsel, latency 0, IRQ 29
	I/O ports at d000 [size=256]
	Memory at d0c10000 (64-bit, prefetchable) [size=4K]
	Memory at d0c00000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at fb300000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

```

---

### Post by westie457 on 2011-09-11
As you are probably aware you are using the correct driver for your system. 

Could you copy and paste this in a terminal ```
sudo apt-get install b43-fwcutter
``` please.

It might make all the difference or none at all.

---

### Post by baz.g on 2011-09-13
Hi westie,

I havent input that last command yet as the problem doesnt seem to have occured again since i first made this post. I really do appreciate your help and if it happens again i will try the command and reply here to update :)

---

