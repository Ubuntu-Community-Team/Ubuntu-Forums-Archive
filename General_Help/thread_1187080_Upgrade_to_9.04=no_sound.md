---
title: "Upgrade to 9.04=no sound"
date: 2009-06-14
forum: General Help
---

### Post by tklaus on 2009-06-14
I saw that other people have had problems with no sound after upgrading to 9.04 and was wondering if there is a fix. I don't have any sound at all after I upgraded.

---

### Post by twright on 2009-06-14
> **tklaus said:**
> I saw that other people have had problems with no sound after upgrading to 9.04 and was wondering if there is a fix. I don't have any sound at all after I upgraded.
Hi,
can you try the command alsamixer -c 0 in terminal to check the volume levels are all correctly set up. If that does not work I suggest submitting a bug with more details (e.g. soundcard and the output of lspci -nnv

---

### Post by tklaus on 2009-06-14
It looks like the master volume is all the way up. Could I be missing a driver for my soundcard?

---

### Post by wanderingtux on 2009-06-14
Could you give a few more details about your system? And how are you listening to sound? Headphones or external speakers?

Also check if the following thread helps

[http://ubuntuforums.org/showthread.php?p=7454288](http://ubuntuforums.org/showthread.php?p=7454288)

---

### Post by tklaus on 2009-06-14
It is an HP pavilion laptop that I actually just installed Ubuntu on a couple of days ago (for my sister) and went ahead and upgraded to 9.04. I am only trying to use the speakers on the laptop itself, and headphones don't work on it either. If you need any other details let me know, and I will look at that thread.

---

### Post by suffery on 2009-06-14
i have heard problems of people who are using hp laptops for both ubuntu and windows
they have driver issues but i dont know what its about..
whats your driver stat for your sound card?

and im not smart about this at all but i might know your problem

---

### Post by TrakerJon on 2009-06-14
Well, in the time it took to upgrade you might have been better off to do a fresh install. Upgrades tend to be messy or a challenge depending on how you look at it. I recommend a clean install unless you like learning how to fix Linux issues.

This should speed up a fresh install for you...

**[http://ubuntuforums.org/showthread.php?t=1181327](http://ubuntuforums.org/showthread.php?t=1181327)**

---

### Post by tklaus on 2009-06-14
Where do you find your drivers on Ubuntu? I might just do a fresh install, if that might fix the problem.

---

### Post by twright on 2009-06-15
> **tklaus said:**
> Where do you find your drivers on Ubuntu? I might just do a fresh install, if that might fix the problem.
I don't think that the method of installation is the problem but you could try if it is convenient. Otherwise please post the output of the command lspci -nnv and lsmod which will list your sound devices and the loaded drivers.

---

### Post by tklaus on 2009-06-15
Ok well after a installation back to 8.10 I still have no sound, so I don't think that is the problem. 

Here are the outputs:

00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
	Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: intel-agp

00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: d0000000-d2ffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: [88] Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Capabilities: [80] Power Management version 3
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [a0] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [140] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 80e0 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 80c0 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at df004c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCIe advanced features <?>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at df000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: de000000-deffffff
	Prefetchable memory behind bridge: 00000000d3000000-00000000d3ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: dd000000-ddffffff
	Prefetchable memory behind bridge: 00000000d4000000-00000000d4ffffff
	Capabilities: [40] Express Root Port (Slot-), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: dc000000-dcffffff
	Prefetchable memory behind bridge: 00000000d5000000-00000000d5ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: db000000-dbffffff
	Prefetchable memory behind bridge: 00000000d6000000-00000000d6ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: da000000-daffffff
	Prefetchable memory behind bridge: 00000000d7000000-00000000d7ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=09, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: d9000000-d9ffffff
	Prefetchable memory behind bridge: 00000000d8000000-00000000d8ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 80a0 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 8080 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 8060 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 8040 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at df004800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCIe advanced features <?>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
	Capabilities: [50] Subsystem: Hewlett-Packard Company Device [103c:30f7]

00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>

00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03) (prog-if 01)
	Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 216
	I/O ports at 8108 [size=8]
	I/O ports at 8114 [size=4]
	I/O ports at 8100 [size=8]
	I/O ports at 8110 [size=4]
	I/O ports at 8020 [size=32]
	Memory at df004000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/4 Enable+
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA <?>
	Capabilities: [b0] PCIe advanced features <?>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Flags: medium devsel, IRQ 11
	Memory at df005000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 8000 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:06ec] (rev a1)
	Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 7000 [size=128]
	Expansion ROM at <ignored> [disabled]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information <?>
	Kernel modules: nvidiafb

04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:137c]
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at dc000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [58] Vendor Specific Information <?>
	Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [13c] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 21-00-dd-ff-ff-00-a8-67
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: wl
	Kernel modules: wl

05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Flags: bus master, fast devsel, latency 0, IRQ 215
	I/O ports at 3000 [size=256]
	Memory at d6010000 (64-bit, prefetchable) [size=4K]
	Memory at d6000000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at d6020000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Mask- TabSize=2
	Capabilities: [d0] Vital Product Data <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
	Kernel driver in use: r8169
	Kernel modules: r8169

06:00.0 System peripheral [0880]: JMicron Technologies, Inc. SD/MMC Host Controller [197b:2382]
	Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at da000300 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

06:00.2 SD Host controller [0805]: JMicron Technologies, Inc. Standard SD Host Controller [197b:2381] (prog-if 01)
	Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Flags: fast devsel, IRQ 16
	Memory at da000200 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel modules: sdhci-pci

06:00.3 System peripheral [0880]: JMicron Technologies, Inc. MS Host Controller [197b:2383]
	Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at da000100 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

06:00.4 System peripheral [0880]: JMicron Technologies, Inc. xD Host Controller [197b:2384]
	Subsystem: Hewlett-Packard Company Device [103c:30f7]
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at da000000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-


Module                  Size  Used by
ipv6                  263972  14 
michael_mic            10496  4 
arc4                    9984  4 
ecb                    10880  4 
crypto_blkcipher       25476  1 ecb
af_packet              25728  4 
binfmt_misc            16904  1 
rfcomm                 44432  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  16 rfcomm,bnep
ppdev                  15620  0 
acpi_cpufreq           15500  1 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  1 
cpufreq_stats          13188  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
sbs                    19464  0 
pci_slot               12552  0 
sbshc                  13440  1 sbs
container              11520  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
snd_hda_intel         381488  5 
psmouse                45200  0 
snd_pcm_oss            46848  0 
evdev                  17696  14 
snd_mixer_oss          22784  1 snd_pcm_oss
serio_raw              13444  0 
snd_pcm                83204  3 snd_hda_intel,snd_pcm_oss
uvcvideo               62728  0 
compat_ioctl32          9344  1 uvcvideo
pcspkr                 10624  0 
snd_seq_dummy          10884  0 
videodev               41344  1 uvcvideo
snd_seq_oss            38528  0 
sdhci_pci              15360  0 
v4l1_compat            22404  2 uvcvideo,videodev
sdhci                  23940  1 sdhci_pci
ieee80211_crypt_tkip    17024  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
wl                   1076372  0 
mmc_core               58268  1 sdhci
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ieee80211_crypt        13572  2 ieee80211_crypt_tkip,wl
snd_timer              29960  3 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
btusb                  19736  3 
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
bluetooth              61924  11 rfcomm,bnep,sco,l2cap,btusb
video                  25104  0 
output                 11008  1 video
ac                     12292  0 
wmi                    14504  0 
battery                18436  0 
button                 14224  0 
intel_agp              33724  0 
shpchp                 37908  0 
agpgart                42184  1 intel_agp
pci_hotplug            35236  1 shpchp
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
ahci                   37132  2 
libata                177312  1 ahci
scsi_mod              155212  4 sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
r8169                  35972  0 
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  5 uvcvideo,btusb,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 
alyssa@alyssa-laptop:~$

---

### Post by twright on 2009-06-16
Hi,
some other people seem to be having problems with your sound card. You might want to look through this thread for some potential solutions: [http://ubuntuforums.org/archive/index.php/t-940689.html](http://ubuntuforums.org/archive/index.php/t-940689.html)

---

### Post by tklaus on 2009-06-18
Ok so the title of this thread is incorrect. The error was due to my sound card. I added one line of code from the bottom of this bug report. [https://bugs.launchpad.net/ubuntu/+bug/269586](https://bugs.launchpad.net/ubuntu/+bug/269586)

Thanks sooooo much twright and everyone else who helped!

---

