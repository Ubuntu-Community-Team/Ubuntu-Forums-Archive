---
title: "steam 14.04 problems"
date: 2014-05-29
forum: Gaming &amp; Leisure
---

### Post by dmbNCSU on 2014-05-29
Hey all I am having trouble installing steam on 14.04.  I get the following after starting steam for the first time:
```
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1400690891_client)
/home/david/.steam/steam.sh: line 755:  2918 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
mv: cannot stat ‘/home/david/.steam/registry.vdf’: No such file or directory
Installing bootstrap /home/david/.steam/bootstrap.tar.xz
Reset complete!
Restarting Steam by request...
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/david/.steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(1400690891_client)
/home/david/.steam/steam.sh: line 755:  3041 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
```

I have a fresh install of 14.04 and Nvidia's drivers installed.  Any ideas?

---

### Post by oldrocker99 on 2014-05-29
Try uninstalling Steam and installing the version from [http://store.steampowered.com/about/](http://store.steampowered.com/about/), and report back if there are further problems.

---

### Post by dmbNCSU on 2014-05-29
> **oldrocker99 said:**
> Try uninstalling Steam and installing the version from [http://store.steampowered.com/about/](http://store.steampowered.com/about/), and report back if there are further problems.

That is the version I installed (the .deb provided by the steam website).

I browsed thru the forums and google and this was an issue I believe when 14.04 was initially released.  Not too savvy to figure this one out on my own :(

---

### Post by dmbNCSU on 2014-05-29
Tried uninstalling and reinstalling the deb from the website to no avail.  Anyone else having this problem?

---

### Post by majk2 on 2014-05-30
Yes I am having problems installing Steam.  It  just doesn't! so I would like some more people to weigh in on this one.

I am running a Alienware m17X R2 with Ubuntu 14.04

with specs:
lspci 
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:05.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 3 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:19.0 Ethernet controller: Intel Corporation 82577LC Gigabit Network Connection (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Broadway XT [Mobility Radeon HD 5870]
02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Juniper HDMI Audio [Radeon HD 5700 Series]
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Broadway XT [Mobility Radeon HD 5870]
06:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
08:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
08:00.1 System peripheral: Ricoh Co Ltd R5U2xx (R5U230 / R5U231 / R5U241) [Memory Stick Host Controller] (rev 01)
08:00.3 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 PCIe IEEE 1394 Controller (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)
lsusb
Bus 002 Device 008: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick
Bus 002 Device 007: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
Bus 002 Device 005: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 004: ID 187c:0512 Alienware Corporation 
Bus 002 Device 006: ID 046d:0a0e Logitech, Inc. 
Bus 002 Device 003: ID 05e3:0607 Genesys Logic, Inc. Logitech G110 Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:6412 Microdia 
Bus 001 Device 012: ID e0ff:0002  
Bus 001 Device 011: ID 077d:0410 Griffin Technology PowerMate
Bus 001 Device 010: ID 0738:1109 Mad Catz, Inc. 
Bus 001 Device 009: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by oldrocker99 on 2014-05-30
OK, what is your driver? Is it fglrx, or the open source driver?

---

### Post by mellery on 2014-05-30
I'm seeing this too on 13.10 with an amd video card, its been working find and suddenly stopped

> 
mike@mike-desktop:~$ steam
Running Steam on ubuntu 13.10 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1400690891_client)
[xcb] Extra reply data still left in queue
[xcb] This is most likely caused by a broken X extension library
[xcb] Aborting, sorry about that.
steam: ../../src/xcb_io.c:575: _XReply: Assertion `!xcb_xlib_extra_reply_data_left' failed.
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2014-05-30 19:37:52] Startup - updater built Feb 10 2014 16:03:16
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140530193752_1.dmp
/home/mike/.local/share/Steam/steam.sh: line 755:  4319 Aborted                 (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
mv: cannot stat &#8216;/home/mike/.steam/registry.vdf&#8217;: No such file or directory
Installing bootstrap /home/mike/.local/share/Steam/bootstrap.tar.xz
Reset complete!
Restarting Steam by request...
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-6f6c2747-4d87-4ddc-88f9-1d2202140530
Running Steam on ubuntu 13.10 64-bit
STEAM_RUNTIME has been set by the user to: /home/mike/.local/share/Steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(1400690891_client)
[xcb] Extra reply data still left in queue
[xcb] This is most likely caused by a broken X extension library
[xcb] Aborting, sorry about that.
steam: ../../src/xcb_io.c:575: _XReply: Assertion `!xcb_xlib_extra_reply_data_left' failed.
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2014-05-30 19:37:56] Startup - updater built Feb 10 2014 16:03:16
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140530193756_1.dmp
/home/mike/.local/share/Steam/steam.sh: line 755:  4451 Aborted                 (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-0ea969bd-ca61-4560-878a-be0772140530
mike@mike-desktop:~$ 


---

### Post by dmbNCSU on 2014-06-23
Going back to the problems I originally experienced with 14.04, I had to uninstall the NVIDIA drivers, do a fresh install of steam, then re-install the NVIDIA drivers.  Everything worked fine after that.

---

### Post by thnewguy on 2014-06-23
I removed the steam and steam-launcher packages from my system. Removed the ~/.steam directory from my profile. then I tried re-installing Steam from the Ubuntu repositories (it didn't work). I think removed Steam again and installed the Deb package on Valve's website. I'm still getting the following error
```

Repairing installation, linking /home/jesse/.steam/steam to /home/jesse/.local/share/Steam
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1402354877_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/assert_20140623155251_1.dmp
/home/jesse/.local/share/Steam/steam.sh: line 755:  8563 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
mv: cannot stat ‘/home/jesse/.steam/registry.vdf’: No such file or directory
Installing bootstrap /home/jesse/.local/share/Steam/bootstrap.tar.xz
Reset complete!
Restarting Steam by request...
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/jesse/.local/share/Steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(1402354877_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/assert_20140623155255_1.dmp
/home/jesse/.local/share/Steam/steam.sh: line 755:  8695 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-068ff61a-9774-48ed-a3f1-0a4d62140623
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-cdce72e8-9568-421d-90e6-729f62140623

```

This was working up until a few days ago. So far haven't found any fix.

---

