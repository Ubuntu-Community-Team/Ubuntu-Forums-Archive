---
title: "Sick of the sound system in Ubuntu!"
date: 2009-05-31
forum: General Help
---

### Post by Lockheed on 2009-05-31
I am sick and tired of Ubuntu&#8217;s sound system!

I did all those how-tos describing configuration and tunning of Pulse Audio, ALSA, flash and whatnot. But what for? 
I can watch a movie in VLC, listen to an internet radio or watch YouTube video and everything is fine. Then BAM, the sound is gone, just like that, for no apparent reason. 
Usually I am not even touching the computer. How annoying is that?

This is what I get when I try to test sound in Preferences/Sound
[code]audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not get/set settings from/on resource.[code]
I'm sure there is a command line to restart sound system but so what? It should not crash in the first place.

It supposed to be a good well-around desktop system and replace Windows? I don't mind finetunning, fiddling with configs and stuff but if that doesn't work then what's the point?

I'm gonna go ahead and reboot now so I can finish watchin what I was watchin.

---

### Post by ActiveFrost on 2009-05-31
Check error logs - reason should be visible ;)

---

### Post by Lockheed on 2009-05-31
And where would one look for those logs?

---

### Post by Lockheed on 2009-06-01
There are many logs mentioning pulseaudio in /var/log. 
Which one should I look in for its errors?

---

### Post by Lockheed on 2009-06-01
Ok, it happened again and here are the logs from all modified log files I could find:

```
**user.log**

Jun  1 18:26:20 laptop pulseaudio[7171]: cpulimit.c: Received request to terminate due to CPU overload.
Jun  1 18:26:31 laptop pulseaudio[8091]: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
Jun  1 18:26:31 laptop pulseaudio[8091]: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
Jun  1 18:26:31 laptop pulseaudio[8091]: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
Jun  1 18:26:31 laptop pulseaudio[8094]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jun  1 18:26:31 laptop pulseaudio[8094]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jun  1 18:26:31 laptop pulseaudio[8094]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume. 


**syslog**

Jun  1 18:26:20 laptop pulseaudio[7171]: cpulimit.c: Received request to terminate due to CPU overload.
Jun  1 18:26:31 laptop pulseaudio[8091]: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
Jun  1 18:26:31 laptop pulseaudio[8091]: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
Jun  1 18:26:31 laptop pulseaudio[8091]: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
Jun  1 18:26:31 laptop pulseaudio[8094]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jun  1 18:26:31 laptop pulseaudio[8094]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jun  1 18:26:31 laptop pulseaudio[8094]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume. 


**messages**

Jun  1 18:26:31 laptop pulseaudio[8091]: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
Jun  1 18:26:31 laptop pulseaudio[8091]: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
Jun  1 18:26:31 laptop pulseaudio[8091]: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
Jun  1 18:26:31 laptop pulseaudio[8094]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jun  1 18:26:31 laptop pulseaudio[8094]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jun  1 18:26:31 laptop pulseaudio[8094]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.


**auth.log**

Jun  1 18:26:31 laptop dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.28" (uid=1000 pid=4353 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.63" (uid=1000 pid=8091 comm="/usr/bin/pulseaudio --start --log-target=syslog "))
Jun  1 18:26:31 laptop dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.28" (uid=1000 pid=4353 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.64" (uid=1000 pid=8094 comm="/usr/bin/pulseaudio --start --log-target=syslog ")) 
```

---

### Post by t0p on 2009-06-01
> **Lockheed said:**
> I am sick and tired of Ubuntu&#8217;s sound system!

I did all those how-tos describing configuration and tunning of Pulse Audio, ALSA, flash and whatnot. But what for? 
I can watch a movie in VLC, listen to an internet radio or watch YouTube video and everything is fine. Then BAM, the sound is gone, just like that, for no apparent reason. 
Usually I am not even touching the computer. How annoying is that?

I agree ubuntu sound can be touchy, annoying, evil... Audio on my desktop Hardy installation works fine.  But Intrepid on my Eee PC... Oh my word!  Sound *will not* play if firefox is open.  At all.  It used to, but one day it stopped.  And I don't have a clue how to fix it.  Grrr!!

> **Lockheed said:**
> 
It supposed to be a good well-around desktop system and replace Windows? I don't mind finetunning, fiddling with configs and stuff but if that doesn't work then what's the point?


Oh shush!  You wanna dump ubuntu cos of sound issues??

---

### Post by SunnyRabbiera on 2009-06-01
Sound is one of those things that are win some loose some on Linux, like most other devices most sound cards are made for windows not linux.
Efforts are being made to improve things though, pulseaudio is very promising to deliver a sound server that can play multiple sounds at the same time and not loose quality.
But Pulse is very experimental and new so win some loose some.

---

### Post by Chronon on 2009-06-01
Based on those logs I would add myself to the group "pulse-rt" and see if it improves the situation.

---

### Post by baseface on 2009-06-01
is pulseaudio even in alpha yet? i cant believe ubuntu actually uses it.... its still a hideous mess.

---

### Post by Lockheed on 2009-06-01
So what you are saying is that there is no way to have reasonable sound system on Ubuntu? Seriously?

---

### Post by prem1er on 2009-06-01
Wow, close this thread already. It is going nowhere fast.

---

### Post by philinux on 2009-06-01
> **Lockheed said:**
> So what you are saying is that there is no way to have reasonable sound system on Ubuntu? Seriously?

Why not try this.

System>prefs >sounds set all to either pulse or alsa see if that makes a diff.

---

### Post by t0p on 2009-06-01
> **Lockheed said:**
> So what you are saying is that there is no way to have reasonable sound system on Ubuntu? Seriously?

Not at all!  Many people have perfect audio.  For instance, as I wrote above, my Hardy desktop has no issues with sound.  My system is set to "auto-detect" for everything - I think that's pulseaudio but I might be mistaken.  Other systems use ALSA or OSS, also without problems.

Thing is, *some* sound cards don't seem to work so well in linux.  The manufacturers really ought to sort this out.  But as things are, you may have to experiment with your settings, and maybe you'll have to put up with imperfect audio support until the next release.  Or you can give up and return to Winders, if it really bothers you that much.

---

### Post by Chronon on 2009-06-01
Currently, I have no problems with sound (after some initial configuration mess after upgrading to Jaunty).  Pulseaudio multiplexes sound from various sources, doesn't crash and basically does what it's supposed to.  I can also use the ProjectM-pulseaudio eye-candy application to visualize any audio that's playing from any source.

Did you add yourself to the group and see if it improves things?

---

### Post by DrMelon on 2009-06-01
No problems with sound here. 

Flawless.

I suggest adding yourself to the pulse-rt group, as previously suggested. Or, alternatively, your logs all seem to be talking about CPU Overloads - what exactly is your machine doing at the time?

---

### Post by Lockheed on 2009-06-01
> **DrMelon said:**
> your logs all seem to be talking about CPU Overloads - what exactly is your machine doing at the time?

I added myself and root to the group. We'll see if it changes anything.
I am usually running 1 VirtualBox machine with Win 2003 x64 and either watch a movie in VLC, play live stream in VLC or watch something on youtube.

The other problem is that in this VM machine, I rarely have any sound. It usually starts with sound but after few minutes there is no sound at all even if the sound in Ubuntu is still working.

As for the sound card - this Connexant chip is being used in numerous laptop models so I don't think it is unique or unsupported.

---

### Post by albinootje on 2009-06-01
> **Lockheed said:**
> 
It supposed to be a good well-around desktop system and replace Windows? 

That's a claim that I don't want to make myself, as it all depends on your hardware, and.. your settings.

But the good thing is that there's choice :
- Pulseaudio (can be removed)
- Alsa
- OSS
- the commercial sound software for Linux : [http://www.opensound.com](http://www.opensound.com)

Can you post here what howtos you have followed, and what you have changed ? 
Did you compile alsa from scratch,  did you make changes in /etc/modprobe.d/ 
Is your user in the audio group ?

Can you post the output of the following :
```

lspci
aplay -l
lsb_release -r
dmesg

```

---

### Post by hyperdude111 on 2009-06-01
Sound for me was buggy in the beta and RC but no problems in final release.

---

### Post by Lockheed on 2009-06-01
Adding my user to this group didn't make a difference. It stopped working again. I did not log off/log in after adding the group. Should I?

The HOWTOs I was following were two separate, large-thread ones. They elude me right now following the rule "you won't find it when you need it". They both explained configuration of PulseAudio in detail on Jaunty.

Here are the printouts of the commands you asked for. If it makes any difference, I took them after the sound crashed and before restarting it with this:
```
killall pulseaudio
sudo alsa force-reload
```



lspci
```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
lsb_release -r
```

dmesg
```
[    0.510506] pci 0000:00:0e.0: reg 10 io port: [0x30c0-0x30c7]
[    0.510511] pci 0000:00:0e.0: reg 14 io port: [0x30b4-0x30b7]
[    0.510516] pci 0000:00:0e.0: reg 18 io port: [0x30b8-0x30bf]
[    0.510521] pci 0000:00:0e.0: reg 1c io port: [0x30b0-0x30b3]
[    0.510526] pci 0000:00:0e.0: reg 20 io port: [0x3090-0x309f]
[    0.510531] pci 0000:00:0e.0: reg 24 32bit mmio: [0xb0006000-0xb0006fff]
[    0.510605] pci 0000:00:10.1: reg 10 32bit mmio: [0xb0000000-0xb0003fff]
[    0.510629] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.510633] pci 0000:00:10.1: PME# disabled
[    0.510666] pci 0000:00:14.0: reg 10 32bit mmio: [0xb0008000-0xb0008fff]
[    0.510671] pci 0000:00:14.0: reg 14 io port: [0x30e0-0x30e7]
[    0.510691] pci 0000:00:14.0: supports D1 D2
[    0.510693] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.510696] pci 0000:00:14.0: PME# disabled
[    0.510811] pci 0000:00:02.0: bridge io port: [0x4000-0x4fff]
[    0.510814] pci 0000:00:02.0: bridge 32bit mmio: [0xb4000000-0xb5ffffff]
[    0.510818] pci 0000:00:02.0: bridge 64bit mmio pref: [0xd0000000-0xd01fffff]
[    0.510853] pci 0000:03:00.0: reg 10 64bit mmio: [0xb6000000-0xb600ffff]
[    0.510926] pci 0000:00:03.0: bridge 32bit mmio: [0xb6000000-0xb7ffffff]
[    0.510960] pci 0000:07:05.0: reg 10 32bit mmio: [0xb8000000-0xb80007ff]
[    0.510991] pci 0000:07:05.0: supports D1 D2
[    0.510993] pci 0000:07:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.510997] pci 0000:07:05.0: PME# disabled
[    0.511024] pci 0000:07:05.1: reg 10 32bit mmio: [0xb8000800-0xb80008ff]
[    0.511054] pci 0000:07:05.1: supports D1 D2
[    0.511056] pci 0000:07:05.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.511060] pci 0000:07:05.1: PME# disabled
[    0.511087] pci 0000:07:05.2: reg 10 32bit mmio: [0xb8000c00-0xb8000cff]
[    0.511118] pci 0000:07:05.2: supports D1 D2
[    0.511119] pci 0000:07:05.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.511123] pci 0000:07:05.2: PME# disabled
[    0.511150] pci 0000:07:05.3: reg 10 32bit mmio: [0xb8001000-0xb80010ff]
[    0.511181] pci 0000:07:05.3: supports D1 D2
[    0.511183] pci 0000:07:05.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.511187] pci 0000:07:05.3: PME# disabled
[    0.511213] pci 0000:07:05.4: reg 10 32bit mmio: [0xb8001400-0xb80014ff]
[    0.511244] pci 0000:07:05.4: supports D1 D2
[    0.511246] pci 0000:07:05.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.511250] pci 0000:07:05.4: PME# disabled
[    0.511285] pci 0000:00:10.0: transparent bridge
[    0.511289] pci 0000:00:10.0: bridge 32bit mmio: [0xb8000000-0xb80fffff]
[    0.511299] bus 00 -> node 0
[    0.511307] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.511442] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.511482] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.511528] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.561317] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *0, disabled.
[    0.561592] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[    0.561863] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *11
[    0.562132] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[    0.562401] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[    0.562671] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[    0.562941] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *11
[    0.563212] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *0, disabled.
[    0.563482] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[    0.563750] ACPI: PCI Interrupt Link [LPMU] (IRQs 11) *10
[    0.564028] ACPI: PCI Interrupt Link [LUS0] (IRQs 22) *11
[    0.564298] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[    0.564567] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *10
[    0.564835] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *0, disabled.
[    0.565104] ACPI: PCI Interrupt Link [LACI] (IRQs 21) *0, disabled.
[    0.565374] ACPI: PCI Interrupt Link [LMCI] (IRQs 21) *0, disabled.
[    0.565643] ACPI: PCI Interrupt Link [LPID] (IRQs 21) *0, disabled.
[    0.565923] ACPI: PCI Interrupt Link [LTID] (IRQs 23) *5
[    0.566199] ACPI: PCI Interrupt Link [LSI1] (IRQs 20) *10
[    0.566401] ACPI: WMI: Mapper loaded
[    0.568131] SCSI subsystem initialized
[    0.568139] libata version 3.00 loaded.
[    0.568139] usbcore: registered new interface driver usbfs
[    0.568139] usbcore: registered new interface driver hub
[    0.568139] usbcore: registered new device driver usb
[    0.568139] PCI: Using ACPI for IRQ routing
[    0.580011] Bluetooth: Core ver 2.13
[    0.584014] NET: Registered protocol family 31
[    0.584016] Bluetooth: HCI device and connection manager initialized
[    0.584020] Bluetooth: HCI socket layer initialized
[    0.584022] NET: Registered protocol family 8
[    0.584024] NET: Registered protocol family 20
[    0.584038] NetLabel: Initializing
[    0.584040] NetLabel:  domain hash size = 128
[    0.584042] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.584057] NetLabel:  unlabeled traffic allowed by default
[    0.584257] PCI-DMA: Disabling AGP.
[    0.584354] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.584356] PCI-DMA: using GART IOMMU.
[    0.584361] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.585095] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.585103] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.592101] AppArmor: AppArmor Filesystem Enabled
[    0.600025] Switched to high resolution mode on CPU 0
[    0.600040] Switched to high resolution mode on CPU 1
[    0.605046] pnp: PnP ACPI init
[    0.605066] ACPI: bus type pnp registered
[    0.609216] pnp: PnP ACPI: found 13 devices
[    0.609219] ACPI: ACPI bus type pnp unregistered
[    0.609230] system 00:00: iomem range 0xe0000000-0xefffffff has been reserved
[    0.609238] system 00:01: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.609241] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.609244] system 00:01: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.609247] system 00:01: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.609254] system 00:03: iomem range 0xe0000000-0xefffffff has been reserved
[    0.609260] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.609263] system 00:04: ioport range 0x1080-0x10ff has been reserved
[    0.609266] system 00:04: ioport range 0x1400-0x147f has been reserved
[    0.609269] system 00:04: ioport range 0x1480-0x14ff has been reserved
[    0.609272] system 00:04: ioport range 0x1800-0x187f has been reserved
[    0.609275] system 00:04: ioport range 0x1880-0x18ff has been reserved
[    0.609277] system 00:04: ioport range 0x2000-0x203f has been reserved
[    0.609284] system 00:05: ioport range 0x360-0x361 has been reserved
[    0.609287] system 00:05: ioport range 0x380-0x383 has been reserved
[    0.609289] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.614018] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.614022] pci 0000:00:02.0:   IO window: 0x4000-0x4fff
[    0.614026] pci 0000:00:02.0:   MEM window: 0xb4000000-0xb5ffffff
[    0.614029] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000d01fffff
[    0.614034] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
[    0.614037] pci 0000:00:03.0:   IO window: disabled
[    0.614040] pci 0000:00:03.0:   MEM window: 0xb6000000-0xb7ffffff
[    0.614043] pci 0000:00:03.0:   PREFETCH window: disabled
[    0.614047] pci 0000:00:10.0: PCI bridge, secondary bus 0000:07
[    0.614049] pci 0000:00:10.0:   IO window: disabled
[    0.614053] pci 0000:00:10.0:   MEM window: 0xb8000000-0xb80fffff
[    0.614056] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.614067] pci 0000:00:02.0: setting latency timer to 64
[    0.614072] pci 0000:00:03.0: setting latency timer to 64
[    0.614077] pci 0000:00:10.0: setting latency timer to 64
[    0.614081] bus: 00 index 0 io port: [0x00-0xffff]
[    0.614084] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.614086] bus: 01 index 0 io port: [0x4000-0x4fff]
[    0.614088] bus: 01 index 1 mmio: [0xb4000000-0xb5ffffff]
[    0.614091] bus: 01 index 2 mmio: [0xd0000000-0xd01fffff]
[    0.614093] bus: 01 index 3 mmio: [0x0-0x0]
[    0.614095] bus: 03 index 0 mmio: [0x0-0x0]
[    0.614097] bus: 03 index 1 mmio: [0xb6000000-0xb7ffffff]
[    0.614100] bus: 03 index 2 mmio: [0x0-0x0]
[    0.614101] bus: 03 index 3 mmio: [0x0-0x0]
[    0.614103] bus: 07 index 0 mmio: [0x0-0x0]
[    0.614106] bus: 07 index 1 mmio: [0xb8000000-0xb80fffff]
[    0.614108] bus: 07 index 2 mmio: [0x0-0x0]
[    0.614110] bus: 07 index 3 io port: [0x00-0xffff]
[    0.614113] bus: 07 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.614126] NET: Registered protocol family 2
[    0.653102] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.653928] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.656874] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.657635] TCP: Hash tables configured (established 262144 bind 65536)
[    0.657639] TCP reno registered
[    0.669139] NET: Registered protocol family 1
[    0.669284] checking if image is initramfs... it is
[    1.398738] Freeing initrd memory: 7776k freed
[    1.403978] Simple Boot Flag at 0x36 set to 0x1
[    1.404349] audit: initializing netlink socket (disabled)
[    1.404366] type=2000 audit(1243875043.404:1): initialized
[    1.414503] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.415965] VFS: Disk quotas dquot_6.5.1
[    1.416029] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.416695] fuse init (API version 7.10)
[    1.416783] msgmni has been set to 7520
[    1.417004] alg: No test for stdrng (krng)
[    1.417029] io scheduler noop registered
[    1.417032] io scheduler anticipatory registered
[    1.417034] io scheduler deadline registered
[    1.417082] io scheduler cfq registered (default)
[    1.417098] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.417142] pci 0000:00:02.0: Enabling HT MSI Mapping
[    1.417153] pci 0000:00:03.0: Enabling HT MSI Mapping
[    1.417164] pci 0000:00:05.0: Boot video device
[    1.417187] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.632102] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    1.632113] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.632127] pci 0000:00:10.1: Enabling HT MSI Mapping
[    1.637624] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.637650] pcieport-driver 0000:00:02.0: found MSI capability
[    1.637668] pcieport-driver 0000:00:02.0: irq 2303 for MSI/MSI-X
[    1.637676] pci_express 0000:00:02.0:pcie00: allocate port service
[    1.637693] pci_express 0000:00:02.0:pcie03: allocate port service
[    1.637732] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.637756] pcieport-driver 0000:00:03.0: found MSI capability
[    1.637770] pcieport-driver 0000:00:03.0: irq 2302 for MSI/MSI-X
[    1.637777] pci_express 0000:00:03.0:pcie00: allocate port service
[    1.637791] pci_express 0000:00:03.0:pcie03: allocate port service
[    1.637846] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.637856] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.639366] ACPI: AC Adapter [ACAD] (on-line)
[    1.908817] ACPI: Battery Slot [BAT0] (battery present)
[    1.908917] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.908920] ACPI: Power Button (FF) [PWRF]
[    1.908972] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.908975] ACPI: Power Button (CM) [PWRB]
[    1.909038] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.909041] ACPI: Sleep Button (CM) [SLPB]
[    1.909089] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    1.910148] ACPI: Lid Switch [LID]
[    1.910495] ACPI: processor limited to max C-state 1
[    1.910525] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.910551] processor ACPI_CPU:00: registered as cooling_device0
[    1.910589] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.910607] processor ACPI_CPU:01: registered as cooling_device1
[    2.170109] thermal LNXTHERM:01: registered as thermal_zone0
[    2.172216] ACPI: Thermal Zone [THRM] (35 C)
[    2.209310] Linux agpgart interface v0.103
[    2.209321] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.210337] brd: module loaded
[    2.210683] loop: module loaded
[    2.210758] Fixed MDIO Bus: probed
[    2.210764] PPP generic driver version 2.4.2
[    2.210827] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.210863] Driver 'sd' needs updating - please use bus_type methods
[    2.210873] Driver 'sr' needs updating - please use bus_type methods
[    2.211101] sata_nv 0000:00:0e.0: version 3.5
[    2.211111] sata_nv 0000:00:0e.0: enabling device (0005 -> 0007)
[    2.211561] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 23
[    2.211574] sata_nv 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 23 (level, high) -> IRQ 23
[    2.211577] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    2.211645] sata_nv 0000:00:0e.0: setting latency timer to 64
[    2.211829] scsi0 : sata_nv
[    2.211966] scsi1 : sata_nv
[    2.212153] ata1: SATA max UDMA/133 cmd 0x30c0 ctl 0x30b4 bmdma 0x3090 irq 23
[    2.212157] ata2: SATA max UDMA/133 cmd 0x30b8 ctl 0x30b0 bmdma 0x3098 irq 23
[    3.088064] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.096428] ata1.00: ATA-8: Hitachi HTS543232L9A300, FB4OC40C, max UDMA/133
[    3.096432] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.112425] ata1.00: configured for UDMA/133
[    3.846561] ata2: SATA link down (SStatus 0 SControl 300)
[    3.846667] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54323 FB4O PQ: 0 ANSI: 5
[    3.846767] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    3.846785] sd 0:0:0:0: [sda] Write Protect is off
[    3.846787] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.846814] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.846901] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    3.846916] sd 0:0:0:0: [sda] Write Protect is off
[    3.846918] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.846943] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.846947]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 >
[    3.944863] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.944920] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.945041] pata_amd 0000:00:0d.0: version 0.3.10
[    3.945087] pata_amd 0000:00:0d.0: setting latency timer to 64
[    3.945184] scsi2 : pata_amd
[    3.945261] scsi3 : pata_amd
[    3.946051] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[    3.946054] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[    4.108335] ata3.00: ATAPI: HL-DT-ST DVDRAM GSA-T10N, PC05, max MWDMA2
[    4.108361] ata3: nv_mode_filter: 0x39f&0x39f->0x39f, BIOS=0x0 (0xc700) ACPI=0x39f (120:600:0x12)
[    4.124287] ata3.00: configured for MWDMA2
[    4.126661] ata4: port disabled. ignoring.
[    4.129977] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T10N  PC05 PQ: 0 ANSI: 5
[    4.141639] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.141642] Uniform CD-ROM driver Revision: 3.20
[    4.141764] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    4.141812] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    4.142333] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.142783] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    4.142797] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, high) -> IRQ 22
[    4.142817] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    4.142821] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    4.142892] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    4.142929] ehci_hcd 0000:00:0b.1: debug port 1
[    4.142934] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    4.142962] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xb0005000
[    4.152041] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    4.152118] usb usb1: configuration #1 chosen from 1 choice
[    4.152146] hub 1-0:1.0: USB hub found
[    4.152155] hub 1-0:1.0: 8 ports detected
[    4.152270] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.152686] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[    4.152690] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, high) -> IRQ 22
[    4.152704] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    4.152707] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    4.152751] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    4.152767] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xb0004000
[    4.210083] usb usb2: configuration #1 chosen from 1 choice
[    4.210108] hub 2-0:1.0: USB hub found
[    4.210121] hub 2-0:1.0: 8 ports detected
[    4.210226] uhci_hcd: USB Universal Host Controller Interface driver
[    4.210313] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    4.228239] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.228247] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.237057] mice: PS/2 mouse device common for all mice
[    4.297093] rtc_cmos 00:09: RTC can wake from S4
[    4.297131] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    4.297170] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    4.297237] device-mapper: uevent: version 1.0.3
[    4.297366] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.297575] device-mapper: multipath: version 1.0.5 loaded
[    4.297579] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.297847] cpuidle: using governor ladder
[    4.297912] cpuidle: using governor menu
[    4.298395] TCP cubic registered
[    4.298473] NET: Registered protocol family 10
[    4.298907] lo: Disabled Privacy Extensions
[    4.299229] NET: Registered protocol family 17
[    4.299249] Bluetooth: L2CAP ver 2.11
[    4.299251] Bluetooth: L2CAP socket layer initialized
[    4.299254] Bluetooth: SCO (Voice Link) ver 0.6
[    4.299255] Bluetooth: SCO socket layer initialized
[    4.299318] Bluetooth: RFCOMM socket layer initialized
[    4.299325] Bluetooth: RFCOMM TTY layer initialized
[    4.299327] Bluetooth: RFCOMM ver 1.10
[    4.299391] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-52 processors (2 cpu cores) (version 2.20.00)
[    4.299443] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x12
[    4.299446] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e
[    4.299601] registered taskstats version 1
[    4.299788]   Magic number: 13:557:842
[    4.299894] rtc_cmos 00:09: setting system clock to 2009-06-01 16:50:46 UTC (1243875046)
[    4.299898] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.299900] EDD information not available.
[    4.299950] Freeing unused kernel memory: 532k freed
[    4.300248] Write protecting the kernel read-only data: 6684k
[    4.329128] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    4.752033] usb 2-6: new low speed USB device using ohci_hcd and address 2
[    4.836291] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    4.836779] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    4.836794] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, high) -> IRQ 20
[    4.836800] forcedeth 0000:00:14.0: setting latency timer to 64
[    4.836856] nv_probe: set workaround bit for reversed mac addr
[    4.862429] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[    4.862446] ohci1394 0000:07:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, high) -> IRQ 5
[    4.914223] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[b8000000-b80007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.975220] usb 2-6: configuration #1 chosen from 1 choice
[    5.103794] usbcore: registered new interface driver hiddev
[    5.115601] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:0b.0/usb2/2-6/2-6:1.0/input/input6
[    5.145069] generic-usb 0003:046D:C50E.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:0b.0-6/input0
[    5.145094] usbcore: registered new interface driver usbhid
[    5.145098] usbhid: v2.6:USB HID core driver
[    5.357109] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:16:36:62:5f:fa
[    5.357114] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
[    5.535246] PM: Starting manual resume from disk
[    5.535250] PM: Resume from partition 8:6
[    5.535252] PM: Checking hibernation image.
[    5.535485] PM: Resume from disk failed.
[    5.565998] EXT4-fs: barriers enabled
[    5.582123] kjournald2 starting.  Commit interval 5 seconds
[    5.582135] EXT4-fs: delayed allocation enabled
[    5.582137] EXT4-fs: file extents enabled
[    5.582272] EXT4-fs: mballoc enabled
[    5.582278] EXT4-fs: mounted filesystem with ordered data mode.
[    6.196153] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[009fc000c7efa200]
[   11.193619] udev: starting version 141
[   11.498964] acpi device:24: registered as cooling_device2
[   11.499282] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:22/input/input7
[   11.529211] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   11.550519] ath_hal: module license 'Proprietary' taints kernel.
[   11.552110] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   11.565362] wlan: 0.9.4
[   11.574878] ath_pci: 0.9.4
[   11.575404] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   11.575418] ath_pci 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, high) -> IRQ 19
[   11.575428] ath_pci 0000:03:00.0: setting latency timer to 64
[   11.842055] sdhci: Secure Digital Host Controller Interface driver
[   11.842059] sdhci: Copyright(c) Pierre Ossman
[   12.013608] sdhci-pci 0000:07:05.1: SDHCI controller found [1180:0822] (rev 19)
[   12.014080] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[   12.014094] sdhci-pci 0000:07:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, high) -> IRQ 7
[   12.017218] mmc0: SDHCI controller on PCI [0000:07:05.1] using PIO
[   12.024905] ricoh-mmc: Ricoh MMC Controller disabling driver
[   12.024909] ricoh-mmc: Copyright(c) Philip Langdale
[   12.024947] ricoh-mmc: Ricoh MMC controller found at 0000:07:05.2 [1180:0843] (rev 1)
[   12.024962] ricoh-mmc: Controller is now disabled.
[   12.241795] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   12.241823] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   12.361690] ath_rate_sample: 1.2 (0.9.4)
[   13.224901] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   13.224911] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   13.224916] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   13.224926] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   13.224930] wifi0: mac 10.3 phy 6.1 radio 10.2
[   13.224935] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   13.224937] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   13.224939] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   13.224941] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   13.224943] wifi0: Use hw queue 8 for CAB traffic
[   13.224945] wifi0: Use hw queue 9 for beacons
[   13.266091] wifi0: Atheros 5212: mem=0xb6000000, irq=19
[   13.338627] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   13.413498] nvidia 0000:00:05.0: power state changed by ACPI to D0
[   13.413974] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 18
[   13.413988] nvidia 0000:00:05.0: PCI INT A -> Link[LK3E] -> GSI 18 (level, high) -> IRQ 18
[   13.413996] nvidia 0000:00:05.0: setting latency timer to 64
[   13.414463] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
[   13.511970] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   13.511987] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 21 (level, high) -> IRQ 21
[   13.512069] HDA Intel 0000:00:10.1: setting latency timer to 64
[   13.700628] input: btnx keyboard as /devices/virtual/input/input8
[   13.724241] input: btnx mouse as /devices/virtual/input/input9
[   14.177806] input: btnx keyboard as /devices/virtual/input/input10
[   14.200631] input: btnx keyboard as /devices/virtual/input/input11
[   14.201240] input: btnx mouse as /devices/virtual/input/input12
[   14.228154] input: btnx mouse as /devices/virtual/input/input13
[   14.330216] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   14.394009] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input14
[   14.844520] input: btnx keyboard as /devices/virtual/input/input15
[   14.868243] input: btnx mouse as /devices/virtual/input/input16
[   14.869749] input: btnx keyboard as /devices/virtual/input/input17
[   14.925257] input: btnx mouse as /devices/virtual/input/input18
[   15.029583] input: btnx keyboard as /devices/virtual/input/input19
[   15.065210] input: btnx mouse as /devices/virtual/input/input20
[   15.612596] input: btnx keyboard as /devices/virtual/input/input21
[   15.633627] input: btnx keyboard as /devices/virtual/input/input22
[   15.636220] input: btnx mouse as /devices/virtual/input/input23
[   15.661267] input: btnx mouse as /devices/virtual/input/input24
[   15.995888] lp: driver loaded but no devices found
[   16.809534] EXT4 FS on sda6, internal journal on sda6:8
[   17.886945] atkbd.c: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
[   17.886949] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
[   18.619602] type=1505 audit(1243871460.816:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2644
[   18.679368] type=1505 audit(1243871460.876:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2648
[   18.679539] type=1505 audit(1243871460.876:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2648
[   18.679597] type=1505 audit(1243871460.876:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2648
[   18.679649] type=1505 audit(1243871460.876:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2648
[   18.843863] type=1505 audit(1243871461.040:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2653
[   18.844113] type=1505 audit(1243871461.044:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2653
[   18.882221] type=1505 audit(1243871461.080:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2657
[   23.299418] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   23.299422] vboxdrv: Successfully done.
[   23.299424] vboxdrv: Found 2 processor cores.
[   23.299497] VBoxDrv: dbg - g_abExecMemory=ffffffffa0ad4f00
[   23.299519] vboxdrv: fAsync=1 offMin=0xa1f63 offMax=0xa1f63
[   23.299579] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   23.299581] vboxdrv: Successfully loaded version 2.2.4 (interface 0x000a0009).
[   23.510598] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa0c74bc0
[   24.504032] Clocksource tsc unstable (delta = -252328368 ns)
[   25.774670] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.774677] Bluetooth: BNEP filters: protocol multicast
[   25.839891] Bridge firewalling registered
[   26.962221] input: btnx keyboard as /devices/virtual/input/input25
[   26.985317] input: btnx mouse as /devices/virtual/input/input26
[   27.575630] ppdev: user-space parallel port driver
[   31.801129] eth0: no link during initialization.
[   31.803560] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   42.477043] ath0: no IPv6 routers present
[   85.348747] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[   99.314059] powernow-k8: error - out of sync, fix 0x0 0x0, vid 0x1e 0x23
[  175.858843] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[  221.477054] operapluginwrap[4740]: segfault at 58 ip 00007f7bcd1f36f3 sp 00007fffe3188c30 error 4 in libflashplayer.so[7f7bcd166000+8c7000]
[  642.038847] pulseaudio[4151]: segfault at 7faba2aa4fd0 ip 00007faba2aa4fd0 sp 00007fffb3753fa8 error 14 in module-null-sink.so[7faba32cb000+3000]
[ 6121.253458] HDA Intel 0000:00:10.1: PCI INT B disabled
[ 6122.135514] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 21 (level, high) -> IRQ 21
[ 6122.135646] HDA Intel 0000:00:10.1: setting latency timer to 64
[ 6144.987325] powernow-k8: ph2 null fid transition 0x8
[ 7402.396255] Too big adjustment 32
[ 7432.976818] Too big adjustment 32
[ 7525.858846] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[10873.820611] Too big adjustment 32
[13182.902617] powernow-k8: ph2 null fid transition 0x8
```

This one was longer but this is all what fits into the console.



> System>prefs >sounds set all to either pulse or alsa see if that makes a diff.
I set everything to ALSA, Pulse and default. Made no difference.

---

### Post by abjt on 2009-06-01
> **Lockheed said:**
> Adding my user to this group didn't make a difference. It stopped working again. I did not log off/log in after adding the group. Should I?

The HOWTOs I was following were two separate, large-thread ones. They elude me right now following the rule "you won't find it when you need it". They both explained configuration of PulseAudio in detail on Jaunty.

Here are the printouts of the commands you asked for. If it makes any difference, I took them after the sound crashed and before restarting it with this:
```
killall pulseaudio
sudo alsa force-reload
```




not sure if these were the posts you were referring to

[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

regards

---

### Post by albinootje on 2009-06-01
> **Lockheed said:**
>  Here are the printouts of the commands you asked for. 

> 
[  175.858843] hda-intel: IRQ timing workaround is activated for card #0.   Suggest a bigger bdl_pos_adj.
[  221.477054] operapluginwrap[4740]: segfault at 58 ip 00007f7bcd1f36f3 sp 00007fffe3188c30 error 4 in libflashplayer.so[7f7bcd166000+8c7000]
[  642.038847] pulseaudio[4151]: segfault at 7faba2aa4fd0 ip
00007faba2aa4fd0 sp 00007fffb3753fa8 error 14 in module-null-sink.so[7faba32cb000+3000]

These errors (segfaults, and IRQ remark) looks like something you can search for with a search-engine.

And this is the howto for Intel HDA :
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
Did you use that ?

---

### Post by Lockheed on 2009-06-01
> **abjt said:**
> not sure if these were the posts you were referring to

abjt, thanks! These are not the threads BUT in one of them there was a link to one of the HOWTOs I followed:
[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)
Before that, I followed another one with some orange headers within.


> **albinootje said:**
> These errors (segfaults, and IRQ remark) looks like something you can search for with a search-engine.

And this is the howto for Intel HDA :
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
Did you use that ?

No but I am doing it right now. What is HDA Intel doing in AMD based laptop anyway?

---

### Post by albinootje on 2009-06-01
> **Lockheed said:**
> 
What is HDA Intel doing in AMD based laptop anyway?

Don't know. Can you try the recommendations here :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267913](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267913)
[http://linux.derkeiler.com/Mailing-Lists/Kernel/2009-05/msg05767.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2009-05/msg05767.html)

And post :
```

cat /proc/interrupts

```

---

### Post by kruegger on 2009-06-01
> **Lockheed said:**
> So what you are saying is that there is no way to have reasonable sound system on Ubuntu? Seriously?

Downgrade to or install Hardy Heron LTS and you'll be fine.;)
Unless you are a top-programmer and you like OREOS :-))

---

### Post by Lockheed on 2009-06-01
> **albinootje said:**
> And post :
```

cat /proc/interrupts

```

```
           CPU0       CPU1       
  0:        131        394   IO-APIC-edge      timer
  1:          1        572   IO-APIC-edge      i8042
  5:          0          3   IO-APIC-fasteoi   ohci1394
  7:          1          0   IO-APIC-fasteoi   mmc0
  8:          0          1   IO-APIC-edge      rtc0
  9:         22       1181   IO-APIC-fasteoi   acpi
 12:          0        126   IO-APIC-edge      i8042
 14:        145       9283   IO-APIC-edge      pata_amd
 15:          0          0   IO-APIC-edge      pata_amd
 18:       6424       4507   IO-APIC-fasteoi   nvidia
 19:       2130     225269   IO-APIC-fasteoi   wifi0
 20:       1089      87786   IO-APIC-fasteoi   eth0
 21:        510      41558   IO-APIC-fasteoi   HDA Intel
 22:        284      31451   IO-APIC-fasteoi   ehci_hcd:usb1, ohci_hcd:usb2
 23:        692      86741   IO-APIC-fasteoi   sata_nv
NMI:          0          0   Non-maskable interrupts
LOC:     384851     372568   Local timer interrupts
RES:     117248      88470   Rescheduling interrupts
CAL:       5710       5207   Function call interrupts
TLB:       2031       1118   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          1
MIS:          0
```


Also, this is dmesg after upgrading to the newest ALSA
```
[    0.510750] pci 0000:00:0a.1: reg 24 io port: [0x3000-0x303f]
[    0.510764] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.510769] pci 0000:00:0a.1: PME# disabled
[    0.510802] pci 0000:00:0a.3: reg 10 32bit mmio: [0xb0040000-0xb007ffff]
[    0.510893] pci 0000:00:0b.0: reg 10 32bit mmio: [0xb0004000-0xb0004fff]
[    0.510921] pci 0000:00:0b.0: supports D1 D2
[    0.510923] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.510928] pci 0000:00:0b.0: PME# disabled
[    0.510958] pci 0000:00:0b.1: reg 10 32bit mmio: [0xb0005000-0xb00050ff]
[    0.510983] pci 0000:00:0b.1: supports D1 D2
[    0.510985] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.510989] pci 0000:00:0b.1: PME# disabled
[    0.511027] pci 0000:00:0d.0: reg 20 io port: [0x3080-0x308f]
[    0.511068] pci 0000:00:0e.0: reg 10 io port: [0x30c0-0x30c7]
[    0.511073] pci 0000:00:0e.0: reg 14 io port: [0x30b4-0x30b7]
[    0.511077] pci 0000:00:0e.0: reg 18 io port: [0x30b8-0x30bf]
[    0.511082] pci 0000:00:0e.0: reg 1c io port: [0x30b0-0x30b3]
[    0.511087] pci 0000:00:0e.0: reg 20 io port: [0x3090-0x309f]
[    0.511092] pci 0000:00:0e.0: reg 24 32bit mmio: [0xb0006000-0xb0006fff]
[    0.511166] pci 0000:00:10.1: reg 10 32bit mmio: [0xb0000000-0xb0003fff]
[    0.511190] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.511194] pci 0000:00:10.1: PME# disabled
[    0.511227] pci 0000:00:14.0: reg 10 32bit mmio: [0xb0008000-0xb0008fff]
[    0.511232] pci 0000:00:14.0: reg 14 io port: [0x30e0-0x30e7]
[    0.511251] pci 0000:00:14.0: supports D1 D2
[    0.511253] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.511257] pci 0000:00:14.0: PME# disabled
[    0.511370] pci 0000:00:02.0: bridge io port: [0x4000-0x4fff]
[    0.511373] pci 0000:00:02.0: bridge 32bit mmio: [0xb4000000-0xb5ffffff]
[    0.511377] pci 0000:00:02.0: bridge 64bit mmio pref: [0xd0000000-0xd01fffff]
[    0.511412] pci 0000:03:00.0: reg 10 64bit mmio: [0xb6000000-0xb600ffff]
[    0.511484] pci 0000:00:03.0: bridge 32bit mmio: [0xb6000000-0xb7ffffff]
[    0.511518] pci 0000:07:05.0: reg 10 32bit mmio: [0xb8000000-0xb80007ff]
[    0.511548] pci 0000:07:05.0: supports D1 D2
[    0.511550] pci 0000:07:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.511554] pci 0000:07:05.0: PME# disabled
[    0.511581] pci 0000:07:05.1: reg 10 32bit mmio: [0xb8000800-0xb80008ff]
[    0.511611] pci 0000:07:05.1: supports D1 D2
[    0.511613] pci 0000:07:05.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.511617] pci 0000:07:05.1: PME# disabled
[    0.511644] pci 0000:07:05.2: reg 10 32bit mmio: [0xb8000c00-0xb8000cff]
[    0.511673] pci 0000:07:05.2: supports D1 D2
[    0.511675] pci 0000:07:05.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.511679] pci 0000:07:05.2: PME# disabled
[    0.511706] pci 0000:07:05.3: reg 10 32bit mmio: [0xb8001000-0xb80010ff]
[    0.511737] pci 0000:07:05.3: supports D1 D2
[    0.511739] pci 0000:07:05.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.511743] pci 0000:07:05.3: PME# disabled
[    0.511770] pci 0000:07:05.4: reg 10 32bit mmio: [0xb8001400-0xb80014ff]
[    0.511800] pci 0000:07:05.4: supports D1 D2
[    0.511801] pci 0000:07:05.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.511805] pci 0000:07:05.4: PME# disabled
[    0.511840] pci 0000:00:10.0: transparent bridge
[    0.511844] pci 0000:00:10.0: bridge 32bit mmio: [0xb8000000-0xb80fffff]
[    0.511854] bus 00 -> node 0
[    0.511862] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.511998] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.512042] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.512087] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.561770] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *0, disabled.
[    0.562044] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[    0.562314] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *11
[    0.562583] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[    0.562852] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[    0.563120] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[    0.563390] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *11
[    0.563660] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *0, disabled.
[    0.563929] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[    0.564202] ACPI: PCI Interrupt Link [LPMU] (IRQs 11) *10
[    0.564475] ACPI: PCI Interrupt Link [LUS0] (IRQs 22) *11
[    0.564745] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[    0.565014] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *10
[    0.565282] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *0, disabled.
[    0.565551] ACPI: PCI Interrupt Link [LACI] (IRQs 21) *0, disabled.
[    0.565820] ACPI: PCI Interrupt Link [LMCI] (IRQs 21) *0, disabled.
[    0.566089] ACPI: PCI Interrupt Link [LPID] (IRQs 21) *0, disabled.
[    0.566368] ACPI: PCI Interrupt Link [LTID] (IRQs 23) *5
[    0.566644] ACPI: PCI Interrupt Link [LSI1] (IRQs 20) *10
[    0.566847] ACPI: WMI: Mapper loaded
[    0.568130] SCSI subsystem initialized
[    0.568138] libata version 3.00 loaded.
[    0.568138] usbcore: registered new interface driver usbfs
[    0.568138] usbcore: registered new interface driver hub
[    0.568138] usbcore: registered new device driver usb
[    0.568138] PCI: Using ACPI for IRQ routing
[    0.580011] Bluetooth: Core ver 2.13
[    0.584014] NET: Registered protocol family 31
[    0.584016] Bluetooth: HCI device and connection manager initialized
[    0.584020] Bluetooth: HCI socket layer initialized
[    0.584022] NET: Registered protocol family 8
[    0.584024] NET: Registered protocol family 20
[    0.584038] NetLabel: Initializing
[    0.584040] NetLabel:  domain hash size = 128
[    0.584041] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.584058] NetLabel:  unlabeled traffic allowed by default
[    0.584256] PCI-DMA: Disabling AGP.
[    0.584354] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.584356] PCI-DMA: using GART IOMMU.
[    0.584361] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.585097] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.585104] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.592101] AppArmor: AppArmor Filesystem Enabled
[    0.600026] Switched to high resolution mode on CPU 0
[    0.600039] Switched to high resolution mode on CPU 1
[    0.605046] pnp: PnP ACPI init
[    0.605066] ACPI: bus type pnp registered
[    0.609661] pnp: PnP ACPI: found 13 devices
[    0.609663] ACPI: ACPI bus type pnp unregistered
[    0.609675] system 00:00: iomem range 0xe0000000-0xefffffff has been reserved
[    0.609682] system 00:01: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.609685] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.609688] system 00:01: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.609691] system 00:01: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.609698] system 00:03: iomem range 0xe0000000-0xefffffff has been reserved
[    0.609705] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.609707] system 00:04: ioport range 0x1080-0x10ff has been reserved
[    0.609710] system 00:04: ioport range 0x1400-0x147f has been reserved
[    0.609713] system 00:04: ioport range 0x1480-0x14ff has been reserved
[    0.609716] system 00:04: ioport range 0x1800-0x187f has been reserved
[    0.609719] system 00:04: ioport range 0x1880-0x18ff has been reserved
[    0.609722] system 00:04: ioport range 0x2000-0x203f has been reserved
[    0.609728] system 00:05: ioport range 0x360-0x361 has been reserved
[    0.609731] system 00:05: ioport range 0x380-0x383 has been reserved
[    0.609734] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.614462] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.614465] pci 0000:00:02.0:   IO window: 0x4000-0x4fff
[    0.614469] pci 0000:00:02.0:   MEM window: 0xb4000000-0xb5ffffff
[    0.614473] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000d01fffff
[    0.614478] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
[    0.614480] pci 0000:00:03.0:   IO window: disabled
[    0.614483] pci 0000:00:03.0:   MEM window: 0xb6000000-0xb7ffffff
[    0.614486] pci 0000:00:03.0:   PREFETCH window: disabled
[    0.614491] pci 0000:00:10.0: PCI bridge, secondary bus 0000:07
[    0.614493] pci 0000:00:10.0:   IO window: disabled
[    0.614496] pci 0000:00:10.0:   MEM window: 0xb8000000-0xb80fffff
[    0.614500] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.614510] pci 0000:00:02.0: setting latency timer to 64
[    0.614516] pci 0000:00:03.0: setting latency timer to 64
[    0.614521] pci 0000:00:10.0: setting latency timer to 64
[    0.614525] bus: 00 index 0 io port: [0x00-0xffff]
[    0.614527] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.614529] bus: 01 index 0 io port: [0x4000-0x4fff]
[    0.614532] bus: 01 index 1 mmio: [0xb4000000-0xb5ffffff]
[    0.614534] bus: 01 index 2 mmio: [0xd0000000-0xd01fffff]
[    0.614537] bus: 01 index 3 mmio: [0x0-0x0]
[    0.614539] bus: 03 index 0 mmio: [0x0-0x0]
[    0.614541] bus: 03 index 1 mmio: [0xb6000000-0xb7ffffff]
[    0.614543] bus: 03 index 2 mmio: [0x0-0x0]
[    0.614545] bus: 03 index 3 mmio: [0x0-0x0]
[    0.614547] bus: 07 index 0 mmio: [0x0-0x0]
[    0.614549] bus: 07 index 1 mmio: [0xb8000000-0xb80fffff]
[    0.614552] bus: 07 index 2 mmio: [0x0-0x0]
[    0.614554] bus: 07 index 3 io port: [0x00-0xffff]
[    0.614556] bus: 07 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.614570] NET: Registered protocol family 2
[    0.653102] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.653927] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.656879] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.657638] TCP: Hash tables configured (established 262144 bind 65536)
[    0.657642] TCP reno registered
[    0.669139] NET: Registered protocol family 1
[    0.669281] checking if image is initramfs... it is
[    1.398104] Freeing initrd memory: 7776k freed
[    1.403425] Simple Boot Flag at 0x36 set to 0x1
[    1.403789] audit: initializing netlink socket (disabled)
[    1.403806] type=2000 audit(1243898818.400:1): initialized
[    1.413939] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.415405] VFS: Disk quotas dquot_6.5.1
[    1.415465] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.416133] fuse init (API version 7.10)
[    1.416221] msgmni has been set to 7520
[    1.416443] alg: No test for stdrng (krng)
[    1.416459] io scheduler noop registered
[    1.416462] io scheduler anticipatory registered
[    1.416464] io scheduler deadline registered
[    1.416512] io scheduler cfq registered (default)
[    1.416527] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.416571] pci 0000:00:02.0: Enabling HT MSI Mapping
[    1.416582] pci 0000:00:03.0: Enabling HT MSI Mapping
[    1.416592] pci 0000:00:05.0: Boot video device
[    1.416615] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.632101] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    1.632112] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.632126] pci 0000:00:10.1: Enabling HT MSI Mapping
[    1.637689] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.637715] pcieport-driver 0000:00:02.0: found MSI capability
[    1.637733] pcieport-driver 0000:00:02.0: irq 2303 for MSI/MSI-X
[    1.637741] pci_express 0000:00:02.0:pcie00: allocate port service
[    1.637758] pci_express 0000:00:02.0:pcie03: allocate port service
[    1.637797] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.637821] pcieport-driver 0000:00:03.0: found MSI capability
[    1.637835] pcieport-driver 0000:00:03.0: irq 2302 for MSI/MSI-X
[    1.637842] pci_express 0000:00:03.0:pcie00: allocate port service
[    1.637856] pci_express 0000:00:03.0:pcie03: allocate port service
[    1.637910] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.637921] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.639407] ACPI: AC Adapter [ACAD] (on-line)
[    1.908753] ACPI: Battery Slot [BAT0] (battery present)
[    1.908852] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.908855] ACPI: Power Button (FF) [PWRF]
[    1.908908] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.908911] ACPI: Power Button (CM) [PWRB]
[    1.908962] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.908965] ACPI: Sleep Button (CM) [SLPB]
[    1.909023] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    1.909798] ACPI: Lid Switch [LID]
[    1.910145] ACPI: processor limited to max C-state 1
[    1.910176] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.910202] processor ACPI_CPU:00: registered as cooling_device0
[    1.910240] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.910258] processor ACPI_CPU:01: registered as cooling_device1
[    2.170195] thermal LNXTHERM:01: registered as thermal_zone0
[    2.172539] ACPI: Thermal Zone [THRM] (60 C)
[    2.209309] Linux agpgart interface v0.103
[    2.209320] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.210335] brd: module loaded
[    2.210681] loop: module loaded
[    2.210755] Fixed MDIO Bus: probed
[    2.210762] PPP generic driver version 2.4.2
[    2.210824] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.210861] Driver 'sd' needs updating - please use bus_type methods
[    2.210870] Driver 'sr' needs updating - please use bus_type methods
[    2.211099] sata_nv 0000:00:0e.0: version 3.5
[    2.211109] sata_nv 0000:00:0e.0: enabling device (0005 -> 0007)
[    2.211558] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 23
[    2.211571] sata_nv 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 23 (level, high) -> IRQ 23
[    2.211574] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    2.211643] sata_nv 0000:00:0e.0: setting latency timer to 64
[    2.211827] scsi0 : sata_nv
[    2.211965] scsi1 : sata_nv
[    2.212153] ata1: SATA max UDMA/133 cmd 0x30c0 ctl 0x30b4 bmdma 0x3090 irq 23
[    2.212156] ata2: SATA max UDMA/133 cmd 0x30b8 ctl 0x30b0 bmdma 0x3098 irq 23
[    3.088064] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.096426] ata1.00: ATA-8: Hitachi HTS543232L9A300, FB4OC40C, max UDMA/133
[    3.096429] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.112424] ata1.00: configured for UDMA/133
[    3.846558] ata2: SATA link down (SStatus 0 SControl 300)
[    3.846664] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54323 FB4O PQ: 0 ANSI: 5
[    3.846765] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    3.846783] sd 0:0:0:0: [sda] Write Protect is off
[    3.846786] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.846812] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.846898] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    3.846913] sd 0:0:0:0: [sda] Write Protect is off
[    3.846916] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.846941] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.846945]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 >
[    3.945979] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.946036] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.946143] pata_amd 0000:00:0d.0: version 0.3.10
[    3.946189] pata_amd 0000:00:0d.0: setting latency timer to 64
[    3.946289] scsi2 : pata_amd
[    3.946367] scsi3 : pata_amd
[    3.947157] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[    3.947160] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[    4.108333] ata3.00: ATAPI: HL-DT-ST DVDRAM GSA-T10N, PC05, max MWDMA2
[    4.108359] ata3: nv_mode_filter: 0x39f&0x39f->0x39f, BIOS=0x0 (0xc700) ACPI=0x39f (120:600:0x12)
[    4.124284] ata3.00: configured for MWDMA2
[    4.126656] ata4: port disabled. ignoring.
[    4.129970] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T10N  PC05 PQ: 0 ANSI: 5
[    4.141626] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.141630] Uniform CD-ROM driver Revision: 3.20
[    4.141751] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    4.141801] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    4.142323] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.142772] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    4.142785] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, high) -> IRQ 22
[    4.142805] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    4.142809] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    4.142880] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    4.142916] ehci_hcd 0000:00:0b.1: debug port 1
[    4.142921] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    4.142949] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xb0005000
[    4.152040] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    4.152116] usb usb1: configuration #1 chosen from 1 choice
[    4.152145] hub 1-0:1.0: USB hub found
[    4.152153] hub 1-0:1.0: 8 ports detected
[    4.152269] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.152684] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[    4.152688] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, high) -> IRQ 22
[    4.152702] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    4.152705] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    4.152749] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    4.152765] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xb0004000
[    4.210084] usb usb2: configuration #1 chosen from 1 choice
[    4.210110] hub 2-0:1.0: USB hub found
[    4.210121] hub 2-0:1.0: 8 ports detected
[    4.210226] uhci_hcd: USB Universal Host Controller Interface driver
[    4.210313] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    4.227701] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.227710] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.237057] mice: PS/2 mouse device common for all mice
[    4.297094] rtc_cmos 00:09: RTC can wake from S4
[    4.297134] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    4.297171] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    4.297239] device-mapper: uevent: version 1.0.3
[    4.297367] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.297573] device-mapper: multipath: version 1.0.5 loaded
[    4.297576] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.297847] cpuidle: using governor ladder
[    4.297912] cpuidle: using governor menu
[    4.298398] TCP cubic registered
[    4.298475] NET: Registered protocol family 10
[    4.298909] lo: Disabled Privacy Extensions
[    4.299232] NET: Registered protocol family 17
[    4.299253] Bluetooth: L2CAP ver 2.11
[    4.299255] Bluetooth: L2CAP socket layer initialized
[    4.299258] Bluetooth: SCO (Voice Link) ver 0.6
[    4.299259] Bluetooth: SCO socket layer initialized
[    4.299322] Bluetooth: RFCOMM socket layer initialized
[    4.299329] Bluetooth: RFCOMM TTY layer initialized
[    4.299331] Bluetooth: RFCOMM ver 1.10
[    4.299393] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-52 processors (2 cpu cores) (version 2.20.00)
[    4.299446] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x12
[    4.299449] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e
[    4.299605] registered taskstats version 1
[    4.299793]   Magic number: 13:887:452
[    4.299900] rtc_cmos 00:09: setting system clock to 2009-06-01 23:27:01 UTC (1243898821)
[    4.299903] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.299905] EDD information not available.
[    4.299956] Freeing unused kernel memory: 532k freed
[    4.300247] Write protecting the kernel read-only data: 6684k
[    4.309861] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    4.704021] usb 2-6: new low speed USB device using ohci_hcd and address 2
[    4.843597] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    4.844086] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    4.844102] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, high) -> IRQ 20
[    4.844108] forcedeth 0000:00:14.0: setting latency timer to 64
[    4.844214] nv_probe: set workaround bit for reversed mac addr
[    4.873321] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[    4.873337] ohci1394 0000:07:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, high) -> IRQ 5
[    4.925125] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[b8000000-b80007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.976683] usb 2-6: configuration #1 chosen from 1 choice
[    5.137809] usbcore: registered new interface driver hiddev
[    5.149585] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:0b.0/usb2/2-6/2-6:1.0/input/input6
[    5.173075] generic-usb 0003:046D:C50E.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:0b.0-6/input0
[    5.173097] usbcore: registered new interface driver usbhid
[    5.173101] usbhid: v2.6:USB HID core driver
[    5.362102] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:16:36:62:5f:fa
[    5.362107] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
[    5.520987] PM: Starting manual resume from disk
[    5.520991] PM: Resume from partition 8:6
[    5.520993] PM: Checking hibernation image.
[    5.521211] PM: Resume from disk failed.
[    5.544880] EXT4-fs: barriers enabled
[    5.561015] kjournald2 starting.  Commit interval 5 seconds
[    5.561029] EXT4-fs: delayed allocation enabled
[    5.561031] EXT4-fs: file extents enabled
[    5.561166] EXT4-fs: mballoc enabled
[    5.561171] EXT4-fs: mounted filesystem with ordered data mode.
[    6.201156] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[009fc000c7efa200]
[   11.083614] udev: starting version 141
[   11.388176] acpi device:24: registered as cooling_device2
[   11.388508] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:22/input/input7
[   11.417146] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   11.437186] ath_hal: module license 'Proprietary' taints kernel.
[   11.438777] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   11.458495] wlan: 0.9.4
[   13.110138] ath_pci: 0.9.4
[   13.110655] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   13.110669] ath_pci 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, high) -> IRQ 19
[   13.110679] ath_pci 0000:03:00.0: setting latency timer to 64
[   13.348100] nvidia 0000:00:05.0: power state changed by ACPI to D0
[   13.348541] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 18
[   13.348555] nvidia 0000:00:05.0: PCI INT A -> Link[LK3E] -> GSI 18 (level, high) -> IRQ 18
[   13.348563] nvidia 0000:00:05.0: setting latency timer to 64
[   13.348881] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
[   13.376088] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   13.376138] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   13.398922] sdhci: Secure Digital Host Controller Interface driver
[   13.398926] sdhci: Copyright(c) Pierre Ossman
[   13.400871] sdhci-pci 0000:07:05.1: SDHCI controller found [1180:0822] (rev 19)
[   13.401352] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[   13.401366] sdhci-pci 0000:07:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, high) -> IRQ 7
[   13.404502] mmc0: SDHCI controller on PCI [0000:07:05.1] using PIO
[   13.405728] ricoh-mmc: Ricoh MMC Controller disabling driver
[   13.405731] ricoh-mmc: Copyright(c) Philip Langdale
[   13.405769] ricoh-mmc: Ricoh MMC controller found at 0000:07:05.2 [1180:0843] (rev 1)
[   13.405785] ricoh-mmc: Controller is now disabled.
[   13.677763] ath_rate_sample: 1.2 (0.9.4)
[   13.681478] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   13.681488] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   13.681493] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   13.681503] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   13.681507] wifi0: mac 10.3 phy 6.1 radio 10.2
[   13.681512] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   13.681514] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   13.681517] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   13.681518] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   13.681520] wifi0: Use hw queue 8 for CAB traffic
[   13.681522] wifi0: Use hw queue 9 for beacons
[   13.693712] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   13.697627] wifi0: Atheros 5212: mem=0xb6000000, irq=19
[   13.927130] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   13.927145] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 21 (level, high) -> IRQ 21
[   13.927247] HDA Intel 0000:00:10.1: setting latency timer to 64
[   13.960591] input: btnx keyboard as /devices/virtual/input/input8
[   13.984237] input: btnx mouse as /devices/virtual/input/input9
[   14.444602] input: btnx keyboard as /devices/virtual/input/input10
[   14.476551] input: btnx keyboard as /devices/virtual/input/input11
[   14.476776] input: btnx mouse as /devices/virtual/input/input12
[   14.536175] input: btnx mouse as /devices/virtual/input/input13
[   14.686248] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   14.754817] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input14
[   15.108619] input: btnx keyboard as /devices/virtual/input/input15
[   15.132236] input: btnx mouse as /devices/virtual/input/input16
[   15.133798] input: btnx keyboard as /devices/virtual/input/input17
[   15.189388] input: btnx mouse as /devices/virtual/input/input18
[   15.264575] input: btnx keyboard as /devices/virtual/input/input19
[   15.312315] input: btnx mouse as /devices/virtual/input/input20
[   15.804622] input: btnx keyboard as /devices/virtual/input/input21
[   15.828442] input: btnx keyboard as /devices/virtual/input/input22
[   15.828681] input: btnx mouse as /devices/virtual/input/input23
[   15.888223] input: btnx mouse as /devices/virtual/input/input24
[   16.260880] lp: driver loaded but no devices found
[   17.060756] EXT4 FS on sda6, internal journal on sda6:8
[   18.965731] type=1505 audit(1243895236.165:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2666
[   19.024932] type=1505 audit(1243895236.221:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2670
[   19.025126] type=1505 audit(1243895236.225:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2670
[   19.025188] type=1505 audit(1243895236.225:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2670
[   19.025241] type=1505 audit(1243895236.225:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2670
[   19.189456] type=1505 audit(1243895236.389:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2675
[   19.189678] type=1505 audit(1243895236.389:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2675
[   19.227715] type=1505 audit(1243895236.425:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2679
[   23.544596] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   23.544600] vboxdrv: Successfully done.
[   23.544603] vboxdrv: Found 2 processor cores.
[   23.544667] VBoxDrv: dbg - g_abExecMemory=ffffffffa0a87f00
[   23.544688] vboxdrv: fAsync=1 offMin=0x2e595 offMax=0x2e595
[   23.544753] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   23.544755] vboxdrv: Successfully loaded version 2.2.4 (interface 0x000a0009).
[   23.754264] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa0c27bc0
[   24.000036] Clocksource tsc unstable (delta = -111846215 ns)
[   25.997609] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.997617] Bluetooth: BNEP filters: protocol multicast
[   26.079256] Bridge firewalling registered
[   27.029186] input: btnx keyboard as /devices/virtual/input/input25
[   27.052229] input: btnx mouse as /devices/virtual/input/input26
[   27.864071] ppdev: user-space parallel port driver
[   31.800826] eth0: no link during initialization.
[   31.803213] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   42.278269] ath0: no IPv6 routers present
[   87.415015] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[   91.406072] powernow-k8: error - out of sync, fix 0x0 0x0, vid 0x1e 0x23
[   91.406082] powernow-k8: ignoring illegal change in lo freq table-0 to 0x0
[   91.406090] powernow-k8: transition frequency failed
[   98.431822] powernow-k8: error - out of sync, fix 0x0 0x0, vid 0x23 0x1e
[  115.862599] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[ 1289.526740] VirtualBox[4608]: segfault at 7fa18a819000 ip 00007fa1a32dd11b sp 00007fffabf11c18 error 4 in libc-2.9.so[7fa1a3259000+168000]

```



> **kruegger said:**
> Downgrade to or install Hardy Heron LTS and you'll be fine.;)
Unles you are a top-programmer.
I put a month of configuration in this system. I don't feel like throwing it away.

---

### Post by Lockheed on 2009-06-04
Well, it seems like installing the newest verion of ALSA fixed it.

On the other hand, (probably) it totally destroyed flash. More details [_HERE_]("http://ubuntuforums.org/showthread.php?t=1178516").

---

### Post by passonno on 2009-06-19
> **t0p said:**
> I agree ubuntu sound can be touchy, annoying, evil... 


Oh shush!  You wanna dump ubuntu cos of sound issues??

I actually have done that on more than one occasion, when the need to finish a particular musical project was greater than any theoretical ideas about software freedom and choice, I simply reinstalled Windows XP and was able to pretty much instantly get back to work.

And I hated doing that, but Windows audio is a known quantity, and has changed very little in many years, whereas you have I think three or four different sound server solutions in Linux, none of which would I ever put any trust into time or project wise.  

As far as I am concerned, sometimes you can have too many choices.

I would even pay for a Linux distro that was professionally polished and designed with pro audio in mind.

---

### Post by brookie on 2009-06-22
Good luck getting it all figured out. 

I had to use OSS drivers for my Creative Audigy Z Notebook card to work. At first I thought it was hell opening, sound preferences, volume control, and volume preferences, testing many combinations. 

I finally narrowed it down that my system just doesn't work with ALSA (music skips, and scratches). The only weird thing left is that sound in Flash videos like on youtube, only play out of the pc speakers of my laptop and will not play out of the creative sound card. Hope you can get it dialed in for your specific system. 

...and it also took some trial and error to get skype sound configured correctly. The drop down lists for audio choices are confusing and not verry descriptive and should better match what is already set in the sound preferences. 

Cheers, 
Brook

---

