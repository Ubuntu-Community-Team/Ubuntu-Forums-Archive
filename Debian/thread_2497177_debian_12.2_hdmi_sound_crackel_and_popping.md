---
title: "debian 12.2 hdmi sound crackel and popping"
date: 2024-04-25
forum: Debian
---

### Post by jimbean on 2024-04-25
i use ubuntu 19.04 live usb drive no sound problems with hdmi 
i use debian 12.2 all kinds of crackling and popping
pc specs 
i7 45?? haswell processor
8 gigs ddr3 ram


  :~$ lspci
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 1 (rev e4)
00:1c.2 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 4 (rev e4)
00:1c.5 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 6 (rev e4)
00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
04:00.0 Network controller: Broadcom Limited BCM43225 802.11b/g/n (rev 01)
  

~$ sudo  lshw -c video
  *-display                 
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:50 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64) memory:c0000-dffff

i installed pulseaudio and it made no difference
ps: i think i was having the same issues with ubuntu 22.04 thats why i tried debian 12 with bluetooth, and everything runs fine with bluetooth on debian 12 
Is there help for an outdated machine
this oild PC is pushing the 10 year old date for newer versions of linux
is there a newer version of linux that can run older PC's
and i can't post on my account that i have with debian forum

thankyou for reading

---

### Post by guiverc on 2024-04-25
> **jimbean said:**
> i use ubuntu 19.04 live usb drive no sound problems with hdmi 
i use debian 12.2 all kinds of crackling and popping


Ubuntu 19.04 is EOL, and I can't think of anything unique in it that would make a difference, except it used the *old *5.0 kernel maybe.  Do you know what kernel modules as being used for sound?

With Ubuntu 22.04 LTS you mention you weren't specific; as the GA kernel of 22.04 was 5.15, HWE used 5.19, 6.2 & 6.5 - but you didn't specify which kernel stack or what media/install & importantly when (*if you updated it*) such that stack details can be guessed at... those kernels are newer though than a 2019-April release.

I wonder if the difference relates to kernel stack used, and given little changes need to made to explore that; as you can download ISOs & just test them *live* using the TRY mode, it maybe what I'd explore... eg. 18.04 media exists that used the 4.15, 4.18 (from 18.10), 5.0 (from 19.04), 5.3 (from 19.10) & finally 5.4 (from 20.04), likewise 20.04 media exists using 5.4, 5.8, 5.11, 5.13 & 5.15 kernels etc.

The Debian you mention uses the 6.1 kernel, given I see `linux-image-amd64 | 6.1.67-1           | stable-updates     | amd64` from a CLI query here.  Debian *oldoldstable* would be the closest to 5.0 used by 19.04 (`4.19+105+deb10u16  | oldoldstable`, then `5.10.209-2         | oldstable`)

FYI: I don't consider your box really *old*, as the box I've used most in *Quality Assurance* testing most in the last few weeks for Ubuntu 24.04 LTS was a 2005 HP Compaq; that being a box I do consider old. On older hardware though, I do tend to find the older kernels help (*this is very hardware specific though!!*);. Given Ubuntu LTS releases offer kernel stack choice; that often means using the GA kernel stack; did you try 22.04 with an older GA or newer HWE stack? (*it provided an older kernel option than your Debian choice, but newer option too*).

Sorry I can't help with your issue, but I'd likely contrast it working on different kernels in *live* or TRY mode, Ubuntu LTS does make this somewhat easy with media created with each kernel provided on *point release *ISOs. If it works on kernels before a version; you at least have one option available to you; until you get a better solution

---

### Post by jimbean on 2024-04-26
thanks for support

but your way over my head Ubuntu PC knowledge

i am more a gleaner junkie so please try to take it easy on me and my grammar is really really bad
so if i download 24.04 lts it will give me an option for different kernel

never saw that before
quote (Given Ubuntu LTS releases offer kernel stack choice; that often means using the GA kernel stack; did you try 22.04 with an older GA or newer HWE stack? (it provided an older kernel option than your Debian choice, but newer option too).

i've been searching not posting because of my limited software knowledge
and it seem there are a lot of posts and no answers to older hdmi pc ports on linux OS's

thank you thank you for any knowledge
if this helps it a Cresent bay processor every time i install a linux distribution it calls my SFF PC a laptop

---

