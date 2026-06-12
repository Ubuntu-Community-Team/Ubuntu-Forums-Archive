---
title: "Gaming Performance went from great to awful after Laptop ran out of battery"
date: 2015-04-10
forum: Gaming &amp; Leisure
---

### Post by skyhawk2 on 2015-04-10
Greetings,

This computer was used to run several games without issue on Ubuntu for months on end with no issue. Including BioShock Infinite, Dota 2, Left 4 Dead 2, etc. However after the computer ran out of power every 3D application has a completely terrible and absolutely awful 3D performance. The loading, main-menu and everything runs smooth, however when the actual 3D loads everything slows down to a crawl.
 
I have had the same problem before and as weird as it sounds I have no idea how it fixed itself. Even reinstalling Ubuntu, reinstalling drivers, etc.  didn`t seem to solve the issue; but something related did. (The only thing I remember is that after installing L4D 2 the issue fixed itself, however doing it this time around did not fix it)


Probably when the battery was running ubuntu switched the video card to power saving mode or smtg and I just can't change it back via software. I'm not really sure, but MAYBE, for some odd reason, the games are using my integrated video card even while the other Video Card is selected. I'm not sure. HALP.

As weird as it sounds, the video card seems to be seleceted and running as normal, see below
------------- 

nvidia-settings

Runnning in performance mode, tried adaptive and high performanc settings, made no difference. NVIDIA is selected.

----- 

glxinfo

direct rendering: Yes

-----

$ glxheads :0
Name: :0
  Display:     0x1698120
  Window:      0x5000002
  Context:     0x16ada70
  GL_VERSION:  4.4.0 NVIDIA 331.113
  GL_VENDOR:   NVIDIA Corporation
  GL_RENDERER: GeForce 840M/PCIe/SSE2


--------

  *-display               
       description: 3D controller
       product: GM108M [GeForce 840M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:53 memory:d2000000-d2ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:6000(size=128) memory:b2000000-b207ffff

 *-display
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:50 memory:d3000000-d33fffff memory:c0000000-cfffffff ioport:7000(size=64)

Just adding new information.

I uninstalled NVIDIA drivers and used solely the integrated video card, most games actually run better (playable, still bad, but barely playable). So it is problem some problem in loading the driver. Here is dmesg text log

[    3.697900] ACPI Error: [\_SB_.PCI0.GFX0.DD02._BCL] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[    3.697906] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG0.PEGP.DD02._BCL] (Node ffff8802539392a8), AE_NOT_FOUND (20131115/psparse-536)
[    3.698106] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:38/LNXVIDEO:00/input/input9
[    3.711958] init: failsafe main process (726) killed by TERM signal
[    3.730753] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    3.730819] ACPI Error: [\_SB_.CUNM] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[    3.730825] ACPI Error: Method parse/execution failed [\_SB_.PCI0.GFX0.DD1F._BQC] (Node ffff88025392f898), AE_NOT_FOUND (20131115/psparse-536)
[    3.730831] ACPI Warning: Evaluating _BQC failed (20131115/video-689)
[    3.730837] ACPI Error: [\_SB_.CUNM] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[    3.730840] ACPI Error: Method parse/execution failed [\_SB_.PCI0.GFX0.DD1F._BCM] (Node ffff88025392f870), AE_NOT_FOUND (20131115/psparse-536)
[    3.730844] ACPI Error: Evaluating _BCM failed (20131115/video-383)
[    3.730994] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input10
[    3.733952] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.734075] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 1
[    3.734082] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  331.113  Mon Dec  1 21:08:13 PST 2014
[    3.734747] snd_hda_intel 0000:00:1b.0: irq 51 for MSI/MSI-X
[    3.741514] HDA driver get symbol successfully from i915 module
[    3.745878] snd_hda_intel 0000:00:03.0: irq 52 for MSI/MSI-X
[    3.751020] SKU: Nid=0x1d sku_cfg=0x40f59a05
[    3.751023] SKU: port_connectivity=0x1
[    3.751024] SKU: enable_pcbeep=0x1
[    3.751026] SKU: check_sum=0x00000005
[    3.751027] SKU: customization=0x0000009a
[    3.751028] SKU: external_amp=0x0
[    3.751029] SKU: platform_type=0x1
[    3.751030] SKU: swap=0x0
[    3.751031] SKU: override=0x1
[    3.751237] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    3.751239]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.751240]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    3.751241]    mono: mono_out=0x0
[    3.751242]    inputs:
[    3.751244]      Mic=0x18
[    3.751245]      Internal Mic=0x12
[    3.751246] realtek: No valid SSID, checking pincfg 0x40f59a05 for NID 0x1d
[    3.751248] realtek: Enabling init ASM_ID=0x9a05 CODEC_ID=10ec0282
[    3.755945] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input12
[    3.756042] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input11
[    3.758843] random: nonblocking pool is initialized
[    3.762141] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input15
[    3.762279] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input14
[    3.762333] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input13
[    3.810023] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[    4.184995] vboxdrv: Found 4 processor cores.
[    4.186606] vboxdrv: fAsync=0 offMin=0xe5 offMax=0xd9a
[    4.186687] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[    4.186689] vboxdrv: Successfully loaded version 4.3.10_Ubuntu (interface 0x001a0007).
[    4.219030] vboxpci: IOMMU not found (not registered)
[    4.359904] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[    4.360295] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[    4.404740] r8169 0000:08:00.0 eth0: link down
[    4.404786] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.405130] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.424100] bbswitch: version 0.7
[    4.424107] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[    4.424113] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.PEG0.PEGP
[    4.424123] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[    4.424186] bbswitch: detected an Optimus _DSM function
[    4.424196] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is on
[    4.600904] vgaarb: this pci device is not a vga device
[    4.602524] nvidia 0000:01:00.0: irq 53 for MSI/MSI-X

---

### Post by brian62 on 2015-04-20
Do you play with the laptop plugged in or only on battery?

---

### Post by skyhawk2 on 2015-04-20
Thanks for the interest brlan62, I already solved the issue (actually somebody solved it for me). (For reference, I only play with the notebook plugged in.)

I leave the answer here for future generations

From user brebs ([https://devtalk.nvidia.com/default/topic/826459/linux/ubuntu-14-04-huge-10x-performance-loss-after-power-failure/](https://devtalk.nvidia.com/default/topic/826459/linux/ubuntu-14-04-huge-10x-performance-loss-after-power-failure/))
> 
Try *removing* the battery from the laptop, for a minute.

The BIOS can get into a bad state (e.g. preventing bootup), and this can clear it.


---

