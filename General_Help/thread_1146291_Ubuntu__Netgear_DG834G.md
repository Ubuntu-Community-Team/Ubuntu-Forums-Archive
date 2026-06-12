---
title: "Ubuntu  Netgear DG834G"
date: 2009-05-02
forum: General Help
---

### Post by king4eva on 2009-05-02
Hello im a newbie !!!!!I just installed ubuntu 9.04 but for some reason i cant connect to the internet!!!! It finds my wireless network, but when i enter the password it doesnt connect. I have a Netgear DG834G wireless router.

---

### Post by codeseer on 2009-05-02
What wireless card?

I assume that you have already went to System->Administration->Networking and set all the up.

Could you give us an output of iwconfig in CODE blocks? This can be gotten by going to Applications->Accessories->Terminal and in the black window typing 'iwconfig' without the quotes. Then copy/paste the output by selecting it and right clicking and choosing copy.

---

### Post by king4eva on 2009-05-02
atheros ar5007eg

---

### Post by codeseer on 2009-05-02
Could you give us the output of 'lshw', 'lsmod' and 'iwconfig', in separate CODE blocks (# symbol in the post interface) please?

Could you also give us a screenshot of your System->Administration->Hardware Drivers window?

---

### Post by king4eva on 2009-05-02
[SIZE=4]_**lsmod**_[/SIZE][SIZE=4]
[/SIZE]
Module                  Size  Used by

i915                   65540  2 

drm                    96296  3 i915

binfmt_misc            16776  1 

ppdev                  15620  0 

bridge                 56340  0 

stp                    10500  1 bridge

bnep                   20224  2 

input_polldev          11912  0 

joydev                 18368  0 

lp                     17156  0 

parport                42220  2 ppdev,lp

arc4                    9856  2 

snd_hda_intel         435636  3 

ecb                    10752  2 

snd_pcm_oss            46336  0 

snd_mixer_oss          22656  1 snd_pcm_oss

snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss

snd_seq_dummy          10756  0 

ath5k                 107008  0 

snd_seq_oss            37760  0 

snd_seq_midi           14336  0 

snd_rawmidi            29696  1 snd_seq_midi

snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi

snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

snd_timer              29704  2 snd_pcm,snd_seq

snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

mac80211              217208  1 ath5k

psmouse                61972  0 

acer_wmi               24260  0 

iTCO_wdt               19108  0 

intel_agp              34108  1 

pcspkr                 10496  0 

serio_raw              13316  0 

snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

led_class              12036  2 ath5k,acer_wmi

cfg80211               38032  2 ath5k,mac80211

iTCO_vendor_support    11652  1 iTCO_wdt

agpgart                42696  3 drm,intel_agp

soundcore              15200  1 snd

video                  25360  0 

snd_page_alloc         16904  2 snd_hda_intel,snd_pcm

output                 11008  1 video

tg3                   131204  0 

fbcon                  46112  0 

tileblit               10752  1 fbcon

font                   16384  1 fbcon

bitblit                13824  1 fbcon

softcursor              9984  1 bitblit


[SIZE=5]_**iwconfig**_[/SIZE]

lo        no wireless extensions.



eth0      no wireless extensions.



wmaster0  no wireless extensions.



wlan0     IEEE 802.11bg  ESSID:""  

          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   

          Tx-Power=20 dBm   

          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   

          Power Management:off

          Link Quality:0  Signal level:0  Noise level:0

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



pan0      no wireless extensions.


[SIZE=5][U][B]lshw
[/B][/U][/SIZE]
WARNING: you should run this program as super-user.

ubuntu                    

    description: Computer

    width: 32 bits

  *-core

       description: Motherboard

       physical id: 0

     *-memory

          description: System memory

          physical id: 0

          size: 1498MiB

     *-cpu

          product: Intel(R) Celeron(R) CPU          550  @ 2.00GHz

          vendor: Intel Corp.

          physical id: 1

          bus info: cpu@0

          version: 6.6.1

          serial: 0001-0661-0000-0000-0000-0000

          size: 150MHz

          width: 64 bits

          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe x86-64 constant_tsc up arch_perfmon pebs bts pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm

     *-pci

          description: Host bridge

          product: Mobile PM965/GM965/GL960 Memory Controller Hub

          vendor: Intel Corporation

          physical id: 100

          bus info: pci@0000:00:00.0

          version: 03

          width: 32 bits

          clock: 33MHz

          configuration: driver=agpgart-intel module=intel_agp

        *-display:0 UNCLAIMED

             description: VGA compatible controller

             product: Mobile GM965/GL960 Integrated Graphics Controller

             vendor: Intel Corporation

             physical id: 2

             bus info: pci@0000:00:02.0

             version: 03

             width: 64 bits

             clock: 33MHz

             capabilities: bus_master cap_list

             configuration: latency=0

        *-display:1 UNCLAIMED

             description: Display controller

             product: Mobile GM965/GL960 Integrated Graphics Controller

             vendor: Intel Corporation

             physical id: 2.1

             bus info: pci@0000:00:02.1

             version: 03

             width: 64 bits

             clock: 33MHz

             capabilities: bus_master cap_list

             configuration: latency=0

        *-usb:0

             description: USB Controller

             product: 82801H (ICH8 Family) USB UHCI Controller #4

             vendor: Intel Corporation

             physical id: 1a

             bus info: pci@0000:00:1a.0

             version: 03

             width: 32 bits

             clock: 33MHz

             capabilities: bus_master

             configuration: driver=uhci_hcd latency=0 module=uhci_hcd

        *-usb:1

             description: USB Controller

             product: 82801H (ICH8 Family) USB UHCI Controller #5

             vendor: Intel Corporation

             physical id: 1a.1

             bus info: pci@0000:00:1a.1

             version: 03

             width: 32 bits

             clock: 33MHz

             capabilities: bus_master

             configuration: driver=uhci_hcd latency=0 module=uhci_hcd

        *-usb:2

             description: USB Controller

             product: 82801H (ICH8 Family) USB2 EHCI Controller #2

             vendor: Intel Corporation

             physical id: 1a.7

             bus info: pci@0000:00:1a.7

             version: 03

             width: 32 bits

             clock: 33MHz

             capabilities: bus_master cap_list

             configuration: driver=ehci_hcd latency=0 module=ehci_hcd

        *-multimedia

             description: Audio device

             product: 82801H (ICH8 Family) HD Audio Controller

             vendor: Intel Corporation

             physical id: 1b

             bus info: pci@0000:00:1b.0

             version: 03

             width: 64 bits

             clock: 33MHz

             capabilities: bus_master cap_list

             configuration: driver=HDA Intel latency=0 module=snd_hda_intel

        *-pci:0

             description: PCI bridge

             product: 82801H (ICH8 Family) PCI Express Port 1

             vendor: Intel Corporation

             physical id: 1c

             bus info: pci@0000:00:1c.0

             version: 03

             width: 32 bits

             clock: 33MHz

             capabilities: pci bus_master cap_list

             configuration: driver=pcieport-driver

        *-pci:1

             description: PCI bridge

             product: 82801H (ICH8 Family) PCI Express Port 2

             vendor: Intel Corporation

             physical id: 1c.1

             bus info: pci@0000:00:1c.1

             version: 03

             width: 32 bits

             clock: 33MHz

             capabilities: pci bus_master cap_list

             configuration: driver=pcieport-driver

        *-pci:2

             description: PCI bridge

             product: 82801H (ICH8 Family) PCI Express Port 3

             vendor: Intel Corporation

             physical id: 1c.2

             bus info: pci@0000:00:1c.2

             version: 03

             width: 32 bits

             clock: 33MHz

             capabilities: pci bus_master cap_list

             configuration: driver=pcieport-driver

           *-network

                description: Ethernet interface

                product: NetLink BCM5906M Fast Ethernet PCI Express

                vendor: Broadcom Corporation

                physical id: 0

                bus info: pci@0000:05:00.0

                logical name: eth0

                version: 02

                serial: 00:1b:38:dd:eb:5c

                width: 64 bits

                clock: 33MHz

                capabilities: bus_master cap_list ethernet physical

                configuration: broadcast=yes driver=tg3 driverversion=3.94 latency=0 module=tg3 multicast=yes

        *-pci:3

             description: PCI bridge

             product: 82801H (ICH8 Family) PCI Express Port 4

             vendor: Intel Corporation

             physical id: 1c.3

             bus info: pci@0000:00:1c.3

             version: 03

             width: 32 bits

             clock: 33MHz

             capabilities: pci bus_master cap_list

             configuration: driver=pcieport-driver

           *-network

                description: Wireless interface

                product: AR242x 802.11abg Wireless PCI Express Adapter

                vendor: Atheros Communications Inc.

                physical id: 0

                bus info: pci@0000:06:00.0

                logical name: wmaster0

                version: 01

                serial: 00:1f:3a:96:f1:09

                width: 64 bits

                clock: 33MHz

                capabilities: bus_master cap_list logical ethernet physical wireless

                configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg

        *-usb:3

             description: USB Controller

             product: 82801H (ICH8 Family) USB UHCI Controller #1

             vendor: Intel Corporation

             physical id: 1d

             bus info: pci@0000:00:1d.0

             version: 03

             width: 32 bits

             clock: 33MHz

             capabilities: bus_master

             configuration: driver=uhci_hcd latency=0 module=uhci_hcd

        *-usb:4

             description: USB Controller

             product: 82801H (ICH8 Family) USB UHCI Controller #2

             vendor: Intel Corporation

             physical id: 1d.1

             bus info: pci@0000:00:1d.1

             version: 03

             width: 32 bits

             clock: 33MHz

             capabilities: bus_master

             configuration: driver=uhci_hcd latency=0 module=uhci_hcd

        *-usb:5

             description: USB Controller

             product: 82801H (ICH8 Family) USB UHCI Controller #3

             vendor: Intel Corporation

             physical id: 1d.2

             bus info: pci@0000:00:1d.2

             version: 03

             width: 32 bits

             clock: 33MHz

             capabilities: bus_master

             configuration: driver=uhci_hcd latency=0 module=uhci_hcd

        *-usb:6

             description: USB Controller

             product: 82801H (ICH8 Family) USB2 EHCI Controller #1

             vendor: Intel Corporation

             physical id: 1d.7

             bus info: pci@0000:00:1d.7

             version: 03

             width: 32 bits

             clock: 33MHz

             capabilities: bus_master cap_list

             configuration: driver=ehci_hcd latency=0 module=ehci_hcd

        *-pci:4

             description: PCI bridge

             product: 82801 Mobile PCI Bridge

             vendor: Intel Corporation

             physical id: 1e

             bus info: pci@0000:00:1e.0

             version: f3

             width: 32 bits

             clock: 33MHz

             capabilities: pci bus_master cap_list

        *-isa

             description: ISA bridge

             product: 82801HEM (ICH8M) LPC Interface Controller

             vendor: Intel Corporation

             physical id: 1f

             bus info: pci@0000:00:1f.0

             version: 03

             width: 32 bits

             clock: 33MHz

             capabilities: isa bus_master cap_list

             configuration: latency=0

        *-ide

             description: IDE interface

             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller

             vendor: Intel Corporation

             physical id: 1f.1

             bus info: pci@0000:00:1f.1

             version: 03

             width: 32 bits

             clock: 33MHz

             capabilities: ide bus_master

             configuration: driver=ata_piix latency=0

        *-storage

             description: SATA controller

             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller

             vendor: Intel Corporation

             physical id: 1f.2

             bus info: pci@0000:00:1f.2

             version: 03

             width: 32 bits

             clock: 66MHz

             capabilities: storage bus_master cap_list

             configuration: driver=ahci latency=0 module=ahci

        *-serial UNCLAIMED

             description: SMBus

             product: 82801H (ICH8 Family) SMBus Controller

             vendor: Intel Corporation

             physical id: 1f.3

             bus info: pci@0000:00:1f.3

             version: 03

             width: 32 bits

             clock: 33MHz

             configuration: latency=0

  *-network DISABLED

       description: Ethernet interface

       physical id: 1

       logical name: pan0

       serial: 2e:be:1c:09:2d:df

       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


[SIZE=4][COLOR=DarkOrange][U][B]
When i go to Hardware Drivers a madwifi driver comes up but when i activate no wireless networks are detected[/B][/U][/COLOR][/SIZE]

---

### Post by codeseer on 2009-05-02
Did you configure System->Administration->Setup? Because 'iwconfig' says you're not associated with a router yet:

```

Mode:Managed Frequency:2.462 GHz Access Point: Not-Associated 

```

You have used this card with this router before, correct?

---

