---
title: "Cannot install Steam on Ubuntu 18.04"
date: 2019-11-27
forum: Gaming &amp; Leisure
---

### Post by CalvinCopyright on 2019-11-27
I had originally installed Steam on 16.10, then upgraded to 18.04.  I've been using another computer for Steam for a while and this is the first time I've attempted to use Steam on this computer after the upgrade.  When it failed, I tried many attempted solutions I found on the internet but I don't think any of them are sufficiently localized to Ubuntu 18.04.

Here's a partial list of what I've tried:

Running 'steam' in terminal pulls up a separate terminal window with this:

```
Steam needs to install these additional packages: 
    libgl1-mesa-dri:i386, libgl1-mesa-glx:i386
```

Additionally, the output contains this error message:

```
Error: You are missing the following 32-bit libraries, and Steam may not run:libGL.so.1
libdrm.so.2

```

```
sudo apt-get install steam
``` gives the output:

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 steam:i386 : Depends: libgl1-mesa-dri:i386 (>= 17.3) but it is not going to be installed or
                       libtxc-dxtn0:i386
              Depends: libgl1-mesa-dri:i386 but it is not going to be installed
              Depends: libgl1-mesa-glx:i386 but it is not going to be installed
              Recommends: nvidia-driver-libs-i386:i386 but it is not installable
E: Unable to correct problems, you have held broken packages.
```

Attempting to install the packages manually gives cascading dependencies.  Will paste outputs if required.

From one of the older threads, for 14.10:

```
$ apt-cache policy libgl1-mesa-glx libgl1-mesa-glx:i386libgl1-mesa-glx:
  Installed: 19.0.8-0ubuntu0~18.04.3
  Candidate: 19.0.8-0ubuntu0~18.04.3
  Version table:
 *** 19.0.8-0ubuntu0~18.04.3 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     18.0.0~rc5-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
libgl1-mesa-glx:i386:
  Installed: (none)
  Candidate: 19.0.8-0ubuntu0~18.04.3
  Version table:
     19.0.8-0ubuntu0~18.04.3 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages
     18.0.0~rc5-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main i386 Packages
```

i386 is listed under foreign architectures.  I have tried autoremove/update/upgrade/dist-upgrade/clean, but not full-upgrade.

Under "Software and Updates", the 'main', 'restricted', 'universe', and 'multiverse' boxes are checked, source code is not.  Under tab "Other Software", only option "Canonical Partners" is checked.  Under "Additional Drivers", the option I have selected is the X.Org X server.

I have attempted the uninstall/reinstall by deleting .steam/ and .local/share/Steam/ folders.

Is there anything else I can do?

---

### Post by mastablasta on 2019-11-28
did you add the 386 architecture?

```
sudo dpkg --add-architecture i386
```

more:
[https://askubuntu.com/questions/454253/how-to-run-32-bit-app-in-ubuntu-64-bit](https://askubuntu.com/questions/454253/how-to-run-32-bit-app-in-ubuntu-64-bit)
[https://ubuntuforums.org/showthread.php?t=2418075](https://ubuntuforums.org/showthread.php?t=2418075)

---

### Post by CalvinCopyright on 2019-11-28
I did.  This was mentioned in the OP, "i386 is listed under foreign architectures."

EDIT: Also, for the external links, multiarch-support is already up to date, and I've been trying to add :i386 to the library names I'm installing.

---

### Post by bklive on 2019-12-20
After your upgrade have you updated your graphics drivers? Are you using a discrete graphics card?

Would you mind posting the output of ```
$ lspci -kv
```
Additionally, have you done a 3D test since the upgrade? ```
$ glxgears
```

---

### Post by CalvinCopyright on 2019-12-20
I do not know if my graphics drivers have been updated.  I am using a laptop, so I am not sure what the command is to tell the difference between a discrete and integrated graphics card.  Is there something I should be doing to that effect?  Under Software & Updates > Additional Drivers, the checked option is X.org.x display driver.  After previous accidents on other computers involving drivers, I have become very leery of changing anything related to them.

Changing the option to the (proprietary, tested) option and then running Steam gave me the error "Error: You are missing the following 32-bit libraries, and Steam may not run: libGL.so.1" which does NOT include the missing libdrm library from the OP, which is promising.  Will be retrying the standard apt commands again with the different driver because idk what changing drivers might actually do.

EDIT: After running sudo apt clean/autoremove/update/upgrade/install -f in that order, the missing library libdrm.so.2 is BACK???

glxgears seems to work fine.

```
$ sudo lspci -kv
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
    Subsystem: Dell 2nd Generation Core Processor Family DRAM Controller
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>


00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: e4000000-e50fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000e1ffffff
    Capabilities: [88] Subsystem: Dell Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [140] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Dell 2nd Generation Core Processor Family Integrated Graphics Controller
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at e5400000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5000 [size=64]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
    Kernel modules: i915


00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Dell 6 Series/C200 Series Chipset Family MEI Controller
    Flags: bus master, fast devsel, latency 0, IRQ 24
    Memory at e6eb0000 (64-bit, non-prefetchable) [size=16]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: mei_me
    Kernel modules: mei_me


00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (Lewisville) (rev 04)
    Subsystem: Dell 82579LM Gigabit Network Connection (Lewisville)
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Memory at e6e00000 (32-bit, non-prefetchable) [size=128K]
    Memory at e6e80000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 5080 [size=32]
    Capabilities: [c8] Power Management version 2
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] PCI Advanced Features
    Kernel driver in use: e1000e
    Kernel modules: e1000e


00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Dell 6 Series/C200 Series Chipset Family USB Enhanced Host Controller
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at e6e70000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci-pci


00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Dell 6 Series/C200 Series Chipset Family High Definition Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 26
    Memory at e6e60000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Dell 6 Series/C200 Series Chipset Family PCI Express Root Port 1
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: e6d00000-e6dfffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Dell 6 Series/C200 Series Chipset Family PCI Express Root Port 2
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Bus: primary=00, secondary=04, subordinate=09, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: e6200000-e6bfffff
    Prefetchable memory behind bridge: 00000000e2b00000-00000000e34fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Dell 6 Series/C200 Series Chipset Family PCI Express Root Port 3
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: e5800000-e61fffff
    Prefetchable memory behind bridge: 00000000e2100000-00000000e2afffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Dell 6 Series/C200 Series Chipset Family PCI Express Root Port 4
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
    Memory behind bridge: e6c00000-e6cfffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Dell 6 Series/C200 Series Chipset Family PCI Express Root Port 6
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Dell 6 Series/C200 Series Chipset Family USB Enhanced Host Controller
    Flags: bus master, medium devsel, latency 0, IRQ 17
    Memory at e6e50000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci-pci


00:1f.0 ISA bridge: Intel Corporation QM67 Express Chipset LPC Controller (rev 04)
    Subsystem: Dell QM67 Express Chipset Family LPC Controller
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich


00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
    Subsystem: Dell 82801 Mobile SATA Controller [RAID mode]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 25
    I/O ports at 50d0 [size=8]
    I/O ports at 50c0 [size=4]
    I/O ports at 50b0 [size=8]
    I/O ports at 50a0 [size=4]
    I/O ports at 5060 [size=32]
    Memory at e6e40000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ahci
    Kernel modules: ahci


00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
    Subsystem: Dell 6 Series/C200 Series Chipset Family SMBus Controller
    Flags: medium devsel, IRQ 11
    Memory at e6e30000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 5040 [size=32]
    Kernel modules: i2c_i801


01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [NVS 4200M] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Dell GF119M [NVS 4200M]
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at e4000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at e0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 4000 [size=128]
    Expansion ROM at e5000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau


01:00.1 Audio device: NVIDIA Corporation GF119 HDMI Audio Controller (rev ff) (prog-if ff)
    !!! Unknown header type 7f
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
    Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at e6d00000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 24-77-03-ff-ff-33-cb-10
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi


0b:00.0 SD Host controller: O2 Micro, Inc. OZ600FJ0/OZ900FJ0/OZ600FJS SD/MMC Card Reader Controller (rev 05) (prog-if 01)
    Subsystem: Dell OZ600FJ0/OZ900FJ0/OZ600FJS SD/MMC Card Reader Controller
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at e6c20000 (32-bit, non-prefetchable) [size=512]
    Capabilities: [a0] Power Management version 3
    Capabilities: [48] MSI: Enable- Count=1/1 Maskable+ 64bit+
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [200] Advanced Error Reporting
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci_pci


0b:00.1 Mass storage controller: O2 Micro, Inc. Device 8231 (rev 03)
    Subsystem: Dell Device 0493
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at e6c10000 (32-bit, non-prefetchable) [size=4K]
    Memory at e6c00000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [a0] Power Management version 3
    Capabilities: [48] MSI: Enable- Count=1/1 Maskable+ 64bit+
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [200] Advanced Error Reporting
```

---

