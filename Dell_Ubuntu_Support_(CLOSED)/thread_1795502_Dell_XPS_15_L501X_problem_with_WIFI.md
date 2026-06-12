---
title: "Dell XPS 15 L501X problem with WIFI"
date: 2011-07-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jyothidamu on 2011-07-02
[FONT=Arial Black][SIZE=2]Hi there 



 i have recently installed Ubuntu on my dell laptop everything is going on perfect i have tried to trouble shoot it could please check the below commands output and let me know please if i have to make any changes 

```
indira@ubuntu:~$ lsb_release -a 
 No LSB modules are available. 
 Distributor ID:    Ubuntu 
 Description:    Ubuntu 11.04 
 Release:    11.04 
 Codename:    natty 


indira@ubuntu:~$ sudo lshw -c network 
 [sudo] password for indira:  
   *-network                
        description: Wireless interface 
        product: Centrino Wireless-N 1000 
        vendor: Intel Corporation 
        physical id: 0 
        bus info: pci@0000:04:00.0 
        logical name: wlan0 
        version: 00 
        serial: 00:26:c7:99:de:9a 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
        configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=128.50.3.1 build 13488 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn 
        resources: irq:48 memory:f0400000-f0401fff 
   *-network 
        description: Ethernet interface 
        product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
        vendor: Realtek Semiconductor Co., Ltd. 
        physical id: 0 
        bus info: pci@0000:09:00.0 
        logical name: eth0 
        version: 06 
        serial: f0:4d:a2:54:bb:6a 
        size: 100Mbit/s 
        capacity: 1Gbit/s 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.81 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s 
        resources: irq:41 ioport:5000(size=256) memory:f0a04000-f0a04fff memory:f0a00000-f0a03fff

indira@ubuntu:~$ sudo rfkill list]
 0: dell-wifi: Wireless LAN 
     Soft blocked: no 
     Hard blocked: no 
 1: phy0: Wireless LAN 
     Soft blocked: no 
     Hard blocked: no 


indira@ubuntu:~$ lsmod 
 Module                  Size  Used by 
 cryptd                 20510  0  
 aes_x86_64             17208  0  
 aes_generic            38279  1 aes_x86_64 
 joydev                 17606  0  
 binfmt_misc            17565  1  
 parport_pc             36959  0  
 ppdev                  17113  0  
 snd_hda_codec_hdmi     28103  1  
 snd_hda_codec_realtek   336693  1  
 arc4                   12529  2  
 snd_hda_intel          33211  2  
 snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel 
 snd_hwdep              13604  1 snd_hda_codec 
 snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
 snd_seq_midi           13324  0  
 snd_rawmidi            30486  1 snd_seq_midi 
 iwlagn                333500  0  
 snd_seq_midi_event     14899  1 snd_seq_midi 
 snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event 
 nouveau               682322  0  
 snd_timer              29602  2 snd_pcm,snd_seq 
 snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq 
 i915                  514985  8  
 uvcvideo               72195  0  
 videodev               82052  1 uvcvideo 
 iwlcore               167503  1 iwlagn 
 dell_wmi               12681  0  
 mac80211              294370  2 iwlagn,iwlcore 
 psmouse                73535  0  
 dell_laptop            13827  0  
 sparse_keymap          13898  1 dell_wmi 
 snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 ttm                    76664  1 nouveau 
 cfg80211              178528  3 iwlagn,iwlcore,mac80211 
 dcdbas                 14438  1 dell_laptop 
 v4l2_compat_ioctl32    17078  1 videodev 
 drm_kms_helper         42136  2 nouveau,i915 
 xhci_hcd               77643  0  
 soundcore              12680  1 snd 
 serio_raw              13166  0  
 intel_ips              18097  0  
 drm                   227495  6 nouveau,ttm,i915,drm_kms_helper 
 snd_page_alloc         18529  2 snd_hda_intel,snd_pcm 
 i2c_algo_bit           13400  2 nouveau,i915 
 video                  19438  2 nouveau,i915 
 lp                     17825  0  
 parport                46458  3 parport_pc,ppdev,lp 
 ahci                   25951  1  
 r8169                  48022  0  
 libahci                26642  1 ahci 
 indira@ubuntu:~$ lsusb 
 Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
 Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub 
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 001 Device 003: ID 0408:2fb1 Quanta Computer, Inc.  
 Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 




indira@ubuntu:~$ lspci
 00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (
 00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
 00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
 00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06) 
 00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) 
 00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06) 
 00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) 
 00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06) 
 00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06) 
 00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06) 
 00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06) 
 00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) 
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6) 
 00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06) 
 00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06) 
 00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06) 
 00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06) 
 02:00.0 VGA compatible controller: nVidia Corporation Device 0df1 (rev a1) 
 04:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000 
 05:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03) 
 09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06) 
 ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05) 
 ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05) 
 ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05) 
 ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05) 
 ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05) 
 ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05) 
 indira@ubuntu:~$
```

---

### Post by lisati on 2011-07-03
Closed. Duplicate of [http://ubuntuforums.org/showthread.php?p=11006206#post11006206](http://ubuntuforums.org/showthread.php?p=11006206#post11006206)

And please use the default font..... :D

---

