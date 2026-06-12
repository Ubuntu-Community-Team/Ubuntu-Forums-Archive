---
title: "games with proton seem to run in the background from steam"
date: 2022-03-15
forum: Gaming &amp; Leisure
---

### Post by Agriesean on 2022-03-15
Hello,


I'm not sure if I'm going to be able to play the game on my computer, but I'm not sure if I'm going to be able to play the game on my computer, but I'm not sure if I'm going to be able to play the game on my computer. I have no window that opens but steam indicates that I am playing this game and I hear the music of this game. (I have tried with 2 different games that are rated Gold and Platinum on protonDb. Does anyone know how to solve this problem?


I am on Ubuntu 20.01.4 LTS


I have tried to run 2 windows games with Proton 5.13 6.3 and 7.01 and I have tried my NVIDIA drivers 470 ( proprietary,tested) and 510 and xx.org drivers . the games and steam are installed on the main partition in ext4 format and I have also tried to force to run in full screen. I also tried to run a Linux compatible game with proton ( Civilization VI ) with the same result.


I followed this steam topic without success

[https://steamcommunity.com/app/221410/d](https://steamcommunity.com/app/221410/d) … 917541481/

I thought the games launched in the background but when I do ctrl + alt + up and down arrow I can't see anything. If this is a resolution problem I don't know how to fix it. 


Thank you in advance for reading this message and for your clarifications

---

### Post by mastablasta on 2022-03-16
i never had this issue. but depends which games you are running and what kind of commands you gave to proton. in ProtonDB it pays to read carefully the notes of others to see if they had a similar issue.

some games start up a launcher and may need a sign up through that. so far i saw Doom Eternal and Sims3 do this. 

parhaps games need the old xserver to run? Default is wayland in Ubutnu i believe and i don't think nvidia fully supports it yet.

---

### Post by Agriesean on 2022-03-17
I tried 3 games : 
my times at portia (platinum)
banner of the maid (gold) ([https://www.protondb.com/app/994730](https://www.protondb.com/app/994730))
civilization VI with proton
I tried to run with nvidia and xxserver-xorg-video drivers but with same reaction

---

### Post by mastablasta on 2022-03-18
and what do the steam logs say? what does system say? is the process running? can you switch to process?

I am on Kubuntu so i won't be able to help much with desktop, but you should be able to see any errors in system log readers as we as in steam logs.

how did you install steam? from software center? using a .deb file from their website?

---

### Post by Agriesean on 2022-03-18
thank's for your questions 

1/ the proton log says there is a problem with the vr. normal I do not have vr. They have a other log to steam ? 

3/ In syslog I have 
```
Failed to load module "gail"
Failed to load module "atk-bridge"
g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Warning: failed to set thread priority: set failed for 8: -1: setpriority() failed
g_object_unref: assertion 'G_IS_OBJECT (object)' failed
src/steamexe/main.cpp (253) : Assertion Failed: reaping pid: 17249 -- gameoverlayui
```

I tried 
```
sudo dpkg-reconfigure xserver-xorg
```

4/ the process running . what do you mean by "can you switch to process" ?
5/ I have forgotten since where I installed steam what you think is best ? from software center ? I would like to try to uninstall and reinstall steam

---

### Post by mastablasta on 2022-03-21
> **Agriesean said:**
> 
5/ I have forgotten since where I installed steam what you think is best ? from software center ? I would like to try to uninstall and reinstall steam

yes reinstall. something is not working as it should if you ask me.

from software center, but .deb is fine as well.

---

### Post by Agriesean on 2022-03-21
i have installed kubuntu and uninstall and reinstall steam from software center in kubuntu but i have same problem's .

---

### Post by mastablasta on 2022-03-22
and what are the system specs?
read:
[https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)

i installed within steam with proton or using playonlinux and many games work as well as could be expected.

does a non proton game launch & work on steam? you can try a free one - for example from Valve Counter Strike: Global Offensive, Team Fortress 2, DOTA2...+there is a bunch of other free linux games on steam that are graphically less intensive but at least you can see if they start and they will download fast (due to their smaller size) such as Unsung Warriors - Prologue, Perfect Vermin, Open TTD (Open Transport Tycoon Deluxe).

check the task manager if the task is running. you can use top in command line or there is also task manager in GUI.

---

### Post by Agriesean on 2022-03-22
no proton game works. 
I installed and played with succes in Civilization VI , stardew walley, and baldur gate's  . 

My level in Linux is : I was PHP web developper. I know Linux in web server it's my first time with graphic interface. 

My version in kubuntu is : 
```
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.4 LTS
Release:        20.04
Codename:       focal

```My video card is 

```

VGA compatible controller: NVIDIA Corporation GP106BM [GeForce GTX 1060 Mobile 6GB] (rev a1)
[/QUOTE]

My PCI card is 
[QUOTE]00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 05)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 05)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model
00:14.0 USB controller: Intel Corporation 100 Series/C230 Series Chipset Family USB 3.0 xHCI Controller (rev 31)
00:16.0 Communication controller: Intel Corporation 100 Series/C230 Series Chipset Family MEI Controller #1 (rev 31)
00:17.0 SATA controller: Intel Corporation Q170/Q150/B150/H170/H110/Z170/CM236 Chipset SATA Controller [AHCI Mode] (rev 31)
00:1b.0 PCI bridge: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #17 (rev f1)
00:1c.0 PCI bridge: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #1 (rev f1)
00:1c.6 PCI bridge: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #7 (rev f1)
00:1c.7 PCI bridge: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #8 (rev f1)
00:1d.0 PCI bridge: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #9 (rev f1)
00:1d.4 PCI bridge: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #13 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Z170 Chipset LPC/eSPI Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation 100 Series/C230 Series Chipset Family Power Management Controller (rev 31)
00:1f.3 Audio device: Intel Corporation 100 Series/C230 Series Chipset Family HD Audio Controller (rev 31)
00:1f.4 SMBus: Intel Corporation 100 Series/C230 Series Chipset Family SMBus (rev 31)
01:00.0 VGA compatible controller: NVIDIA Corporation GP106BM [GeForce GTX 1060 Mobile 6GB] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GP106 High Definition Audio Controller (rev a1)
02:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller SM981/PM981/PM983
6e:00.0 Ethernet controller: Qualcomm Atheros Killer E2400 Gigabit Ethernet Controller (rev 10)
6f:00.0 SD Host controller: Realtek Semiconductor Co., Ltd. RTS5250 PCI Express Card Reader (rev 01)
71:00.0 Network controller: Intel Corporation Wireless-AC 9260 (rev 29)


```

list of hardware is 

```
    description: Ordinateur Bloc-notes
    produit: P7xxDM3(-G) (Not Applicable)
    fabricant: Notebook
    version: Not Applicable
    numéro de série: Not Applicable
    bits: 64 bits
    fonctionnalités: smbios-3.0.0 dmi-3.0.0 smp vsyscall32
    configuration : boot=normal chassis=notebook family=Not Applicable sku=Not Applicable uuid=80FA5B42-6B52-0000-0000-000000000000
  *-core
       description: Carte mère
       produit: P7xxDM3(-G)
       fabricant: Notebook
       identifiant matériel: 0
       version: Not Applicable
       numéro de série: Not Applicable
       emplacement: Not Applicable
     *-firmware
          description: BIOS
          fabricant: American Megatrends Inc.
          identifiant matériel: 0
          version: 1.06.09
          date: 03/20/2017
          taille: 64KiB
          capacité: 5MiB
          fonctionnalités: pci upgrade shadowing cdboot bootselect socketedrom edd int5printscreen int9keyboard int17printer acpi usb biosbootspecification uefi
     *-memory
          description: Mémoire Système
          identifiant matériel: 18
          emplacement: Carte mère
          taille: 64GiB
        *-bank:0
             description: Project-Id-Version: @(#) $Id$Report-Msgid-Bugs-To: PO-Revision-Date: 2021-01-19 19:00+0000Last-Translator: Lyonel Vincent <Unknown>Language-Team: MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-
Export-Date: 2022-02-11 15:39+0000X-Generator: Launchpad (build fb383037dc57f48cc5195c1eb2676319fbdf7e33)Project-Id-Version: @(#) $Id$Report-Msgid-Bugs-To: PO-Revision-Date: 2021-01-19 19:00+0000Last-Translator: Lyonel Vincent <Unknown>Language-Team: MIME-Version: 1.0Con
tent-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2022-02-11 15:39+0000X-Generator: Launchpad (build fb383037dc57f48cc5195c1eb2676319fbdf7e33) [vide]
             identifiant matériel: 0
             emplacement: ChannelA-DIMM0
        *-bank:1
             description: SODIMM DDR4 Synchrone 2667 MHz (0.4 ns)
             produit: KHX2666C16S4/32G
             fabricant: Kingston
             identifiant matériel: 1
             numéro de série: B0AED100
             emplacement: ChannelA-DIMM1
             taille: 32GiB
             bits: 64 bits
             horloge: 2667MHz (0.4ns)
        *-bank:2
             description: Project-Id-Version: @(#) $Id$Report-Msgid-Bugs-To: PO-Revision-Date: 2021-01-19 19:00+0000Last-Translator: Lyonel Vincent <Unknown>Language-Team: MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-
Export-Date: 2022-02-11 15:39+0000X-Generator: Launchpad (build fb383037dc57f48cc5195c1eb2676319fbdf7e33)Project-Id-Version: @(#) $Id$Report-Msgid-Bugs-To: PO-Revision-Date: 2021-01-19 19:00+0000Last-Translator: Lyonel Vincent <Unknown>Language-Team: MIME-Version: 1.0Con
tent-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2022-02-11 15:39+0000X-Generator: Launchpad (build fb383037dc57f48cc5195c1eb2676319fbdf7e33) [vide]
             identifiant matériel: 2
             emplacement: ChannelB-DIMM0
        *-bank:3
             description: SODIMM DDR4 Synchrone 2667 MHz (0.4 ns)
             produit: KHX2666C16S4/32G
             fabricant: Kingston
             identifiant matériel: 3
             numéro de série: A6AED123
             emplacement: ChannelB-DIMM1
             taille: 32GiB
             bits: 64 bits
             horloge: 2667MHz (0.4ns)
     *-cache:0
          description: L1 cache
          identifiant matériel: 1e
          emplacement: L1 Cache
          taille: 256KiB
          capacité: 256KiB
          fonctionnalités: synchronous internal write-back unified
          configuration : level=1
     *-cache:1
          description: L2 cache
          identifiant matériel: 1f
          emplacement: L2 Cache
          taille: 1MiB
          capacité: 1MiB
          fonctionnalités: synchronous internal write-back unified
          configuration : level=2
     *-cache:2
          description: L3 cache
          identifiant matériel: 20
          emplacement: L3 Cache
          taille: 8MiB
          capacité: 8MiB
          fonctionnalités: synchronous internal write-back unified
          configuration : level=3
     *-cpu
          description: CPU
          produit: Intel(R) Core(TM) i7-7700T CPU @ 2.90GHz
          fabricant: Intel Corp.
          identifiant matériel: 21
          information bus: cpu@0
          version: Intel(R) Core(TM) i7-7700T CPU @ 2.90GHz
          numéro de série: To Be Filled By O.E.M.
          emplacement: U3E1
          taille: 3137MHz
          capacité: 4005MHz
          bits: 64 bits
          horloge: 100MHz
          fonctionnalités: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_
tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tp
r_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d cpufreq
          configuration : cores=4 enabledcores=4 threads=8
     *-pci
          description: Host bridge
          produit: Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers
          fabricant: Intel Corporation
          identifiant matériel: 100
          information bus: pci@0000:00:00.0
          version: 05
          bits: 32 bits
          horloge: 33MHz
          configuration : driver=skl_uncore
          ressources : irq:0
        *-pci:0
             description: PCI bridge
             produit: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16)
             fabricant: Intel Corporation
             identifiant matériel: 1
             information bus: pci@0000:00:01.0
             version: 05
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration : driver=pcieport
             ressources : irq:121 portE/S:e000(taille=4096) mémoire:db000000-dc0fffff portE/S:90000000(taille=301989888)
           *-display
                description: VGA compatible controller
                produit: GP106BM [GeForce GTX 1060 Mobile 6GB]
                fabricant: NVIDIA Corporation
                identifiant matériel: 0
                information bus: pci@0000:01:00.0
                version: a1
                bits: 64 bits
                horloge: 33MHz
                fonctionnalités: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration : driver=nouveau latency=0
                ressources : irq:139 mémoire:db000000-dbffffff mémoire:90000000-9fffffff mémoire:a0000000-a1ffffff portE/S:e000(taille=128) mémoire:c0000-dffff
           *-multimedia
                description: Audio device
                produit: GP106 High Definition Audio Controller
                fabricant: NVIDIA Corporation
                identifiant matériel: 0.1
                information bus: pci@0000:01:00.1
                version: a1
                bits: 32 bits
                horloge: 33MHz
                fonctionnalités: pm msi pciexpress bus_master cap_list
                configuration : driver=snd_hda_intel latency=0
                ressources : irq:17 mémoire:dc080000-dc083fff
        *-generic
             description: System peripheral
             produit: Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model
             fabricant: Intel Corporation
             identifiant matériel: 8
             information bus: pci@0000:00:08.0
             nom logique: /dev/fb0
             version: 00
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: msi pm cap_list fb
             configuration : depth=32 latency=0 mode=1920x1080 visual=truecolor xres=1920 yres=1080
             ressources : mémoireE/S:2f0-2ef mémoire:2ffff26000-2ffff26fff
        *-usb
             description: USB controller
             produit: 100 Series/C230 Series Chipset Family USB 3.0 xHCI Controller
             fabricant: Intel Corporation
             identifiant matériel: 14
             information bus: pci@0000:00:14.0
             version: 31
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi xhci bus_master cap_list
             configuration : driver=xhci_hcd latency=0
             ressources : mémoireE/S:2f0-2ef irq:128 mémoire:2ffff10000-2ffff1ffff
           *-usbhost:0
                produit: xHCI Host Controller
                fabricant: Linux 5.13.0-37-generic xhci-hcd
                identifiant matériel: 0
                information bus: usb@1
                nom logique: usb1
                version: 5.13
                fonctionnalités: usb-2.00
                configuration : driver=hub slots=16 speed=480Mbit/s
              *-usb:0 NON-RÉCLAMÉ
                   description: Périphérique USB générique
                   fabricant: Synaptics, Inc.
                   identifiant matériel: 2
                   information bus: usb@1:2
                   version: 1.54
                   numéro de série: 79279800a585
                   fonctionnalités: usb-2.00
                   configuration : maxpower=100mA speed=12Mbit/s
              *-usb:1
                   description: Souris
                   produit: Gaming Mouse G302
                   fabricant: Logitech
                   identifiant matériel: 5
                   information bus: usb@1:5
                   version: 91.00
                   numéro de série: 187434753135
                   fonctionnalités: usb-2.00
                   configuration : driver=usbhid maxpower=300mA speed=12Mbit/s
              *-usb:2
                   description: Vidéo
                   produit: Chicony USB 2.0 Camera
                   fabricant: SunplusIT Inc
                   identifiant matériel: a
                   information bus: usb@1:a
                   version: 36.01
                   fonctionnalités: usb-2.00
                   configuration : driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:3
                   description: Interface sans fil Bluetooth
                   fabricant: Intel Corp.
                   identifiant matériel: b
                   information bus: usb@1:b
                   version: 0.02
                   fonctionnalités: bluetooth usb-2.00
                   configuration : driver=btusb maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                produit: xHCI Host Controller
                fabricant: Linux 5.13.0-37-generic xhci-hcd
                identifiant matériel: 1
                information bus: usb@2
                nom logique: usb2
                version: 5.13
                fonctionnalités: usb-3.00
                configuration : driver=hub slots=10 speed=5000Mbit/s
        *-communication
             description: Communication controller
             produit: 100 Series/C230 Series Chipset Family MEI Controller #1
             fabricant: Intel Corporation
             identifiant matériel: 16
             information bus: pci@0000:00:16.0
             version: 31
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi bus_master cap_list
             configuration : driver=mei_me latency=0
             ressources : mémoireE/S:2f0-2ef irq:140 mémoire:2ffff25000-2ffff25fff
        *-sata
             description: SATA controller
             produit: Q170/Q150/B150/H170/H110/Z170/CM236 Chipset SATA Controller [AHCI Mode]
             fabricant: Intel Corporation
             identifiant matériel: 17
             information bus: pci@0000:00:17.0
             version: 31
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: sata msi pm ahci_1.0 bus_master cap_list
             configuration : driver=ahci latency=0
             ressources : irq:129 mémoire:dc504000-dc505fff mémoire:dc507000-dc5070ff portE/S:f050(taille=8) portE/S:f040(taille=4) portE/S:f020(taille=32) mémoire:dc506000-dc5067ff
        *-pci:1
             description: PCI bridge
             produit: 100 Series/C230 Series Chipset Family PCI Express Root Port #17
             fabricant: Intel Corporation
             identifiant matériel: 1b
             information bus: pci@0000:00:1b.0
             version: f1
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration : driver=pcieport
             ressources : irq:122 mémoire:dc400000-dc4fffff
           *-storage
                description: Non-Volatile memory controller
                produit: NVMe SSD Controller SM981/PM981/PM983
                fabricant: Samsung Electronics Co Ltd
                identifiant matériel: 0
                information bus: pci@0000:02:00.0
                version: 00
                bits: 64 bits
                horloge: 33MHz
                fonctionnalités: storage pm msi pciexpress msix nvm_express bus_master cap_list
                configuration : driver=nvme latency=0
                ressources : irq:16 mémoire:dc400000-dc403fff
              *-nvme0
                   description: NVMe device
                   produit: Samsung SSD 970 EVO Plus 2TB
                   identifiant matériel: 0
                   nom logique: /dev/nvme0
                   version: 2B2QEXM7
                   numéro de série: S4J4NX0R501612R
                   configuration : nqn=nqn.2014.08.org.nvmexpress:144d144dS4J4NX0R501612R     Samsung SSD 970 EVO Plus 2TB state=live
                 *-namespace
                      description: NVMe namespace
                      identifiant matériel: 1
                      nom logique: /dev/nvme0n1
                      taille: 1863GiB (2TB)
                      fonctionnalités: gpt-1.00 partitioned partitioned:gpt
                      configuration : guid=b7bbedd7-e166-4cb9-b027-48cd056cda29 logicalsectorsize=512 sectorsize=512
                    *-volume:0
                         description: Windows FAT volume
                         fabricant: MSWIN4.1
                         identifiant matériel: 1
                         nom logique: /dev/nvme0n1p1
                         nom logique: /boot/efi
                         version: FAT32
                         numéro de série: 52e8-812c
                         taille: 510MiB
                         capacité: 511MiB
                         fonctionnalités: boot fat initialized
                         configuration : FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro name=EFI System Partition state=mounted
                    *-volume:1
                         description: Volume EXT4
                         fabricant: Linux
                         identifiant matériel: 2
                         nom logique: /dev/nvme0n1p2
                         nom logique: /
                         version: 1.0
                         numéro de série: 45f92dcf-27d1-42f9-b1e6-d695a921ec99
                         taille: 931GiB
                         fonctionnalités: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                         configuration : created=2021-03-15 14:26:20 filesystem=ext4 lastmountpoint=/ modified=2022-03-22 18:08:40 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2022-03-22 18:08:40 name=zone-partagee state=mounted
                    *-volume:2
                         description: Windows NTFS volume
                         fabricant: Windows
                         identifiant matériel: 3
                         nom logique: /dev/nvme0n1p3
                         nom logique: /media/partage
                         version: 3.1
                         numéro de série: 38410e18-6b6d-4a47-a6d5-ac61b1dfc330
                         taille: 931GiB
                         capacité: 931GiB
                         fonctionnalités: ntfs initialized
                         configuration : clustersize=4096 created=2021-09-28 00:38:32 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096 name=Windows state=mounted
        *-pci:2
             description: PCI bridge
             produit: 100 Series/C230 Series Chipset Family PCI Express Root Port #1
             fabricant: Intel Corporation
             identifiant matériel: 1c
             information bus: pci@0000:00:1c.0
             version: f1
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration : driver=pcieport
             ressources : irq:123 portE/S:2000(taille=4096) mémoire:ac000000-da0fffff portE/S:2fb0000000(taille=1241513984)
        *-pci:3
             description: PCI bridge
             produit: 100 Series/C230 Series Chipset Family PCI Express Root Port #7
             fabricant: Intel Corporation
             identifiant matériel: 1c.6
             information bus: pci@0000:00:1c.6
             version: f1
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration : driver=pcieport
             ressources : irq:124 portE/S:d000(taille=4096) mémoire:dc300000-dc3fffff
           *-network
                description: Ethernet interface
                produit: Killer E2400 Gigabit Ethernet Controller
                fabricant: Qualcomm Atheros
                identifiant matériel: 0
                information bus: pci@0000:6e:00.0
                nom logique: enp110s0
                version: 10
                numéro de série: 80:fa:5b:42:6b:52
                capacité: 1Gbit/s
                bits: 64 bits
                horloge: 33MHz
                fonctionnalités: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration : autonegotiation=on broadcast=yes driver=alx driverversion=5.13.0-37-generic latency=0 link=no multicast=yes port=twisted pair
                ressources : irq:18 mémoire:dc300000-dc33ffff portE/S:d000(taille=128)
        *-pci:4
             description: PCI bridge
             produit: 100 Series/C230 Series Chipset Family PCI Express Root Port #8
             fabricant: Intel Corporation
             identifiant matériel: 1c.7
             information bus: pci@0000:00:1c.7
             version: f1
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration : driver=pcieport
             ressources : irq:125 mémoire:dc200000-dc2fffff
           *-generic
                description: SD Host controller
                produit: RTS5250 PCI Express Card Reader
                fabricant: Realtek Semiconductor Co., Ltd.
                identifiant matériel: 0
                information bus: pci@0000:6f:00.0
                version: 01
                bits: 32 bits
                horloge: 33MHz
                fonctionnalités: pm msi pciexpress bus_master cap_list
                configuration : driver=sdhci-pci latency=0
                ressources : irq:19 mémoire:dc201000-dc201fff mémoire:dc200000-dc200fff
        *-pci:5
             description: PCI bridge
             produit: 100 Series/C230 Series Chipset Family PCI Express Root Port #9
             fabricant: Intel Corporation
             identifiant matériel: 1d
             information bus: pci@0000:00:1d.0
             version: f1
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration : driver=pcieport
             ressources : irq:126 portE/S:4000(taille=4096) mémoire:40000000-401fffff portE/S:2000000000(taille=2097152)
        *-pci:6
             description: PCI bridge
             produit: 100 Series/C230 Series Chipset Family PCI Express Root Port #13
             fabricant: Intel Corporation
             identifiant matériel: 1d.4
             information bus: pci@0000:00:1d.4
             version: f1
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration : driver=pcieport
             ressources : irq:127 mémoire:dc100000-dc1fffff
           *-network
                description: Interface réseau sans fil
                produit: Wireless-AC 9260
                fabricant: Intel Corporation
                identifiant matériel: 0
                information bus: pci@0000:71:00.0
                nom logique: wlp113s0
                version: 29
                numéro de série: 3c:58:c2:a4:58:26
                bits: 64 bits
                horloge: 33MHz
                fonctionnalités: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration : broadcast=yes driver=iwlwifi driverversion=5.13.0-37-generic firmware=46.4d093a30.0 9260-th-b0-jf-b0- ip=172.22.22.55 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                ressources : irq:16 mémoire:dc100000-dc103fff
        *-isa
             description: ISA bridge
             produit: Z170 Chipset LPC/eSPI Controller
             fabricant: Intel Corporation
             identifiant matériel: 1f
             information bus: pci@0000:00:1f.0
             version: 31
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: isa bus_master
             configuration : latency=0
        *-memory NON-RÉCLAMÉ
             description: Memory controller
             produit: 100 Series/C230 Series Chipset Family Power Management Controller
             fabricant: Intel Corporation
             identifiant matériel: 1f.2
             information bus: pci@0000:00:1f.2
             version: 31
             bits: 32 bits
             horloge: 33MHz (30.3ns)
             configuration : latency=0
             ressources : mémoire:dc500000-dc503fff
        *-multimedia
             description: Audio device
             produit: 100 Series/C230 Series Chipset Family HD Audio Controller
             fabricant: Intel Corporation
             identifiant matériel: 1f.3
             information bus: pci@0000:00:1f.3
             version: 31
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi bus_master cap_list
             configuration : driver=snd_hda_intel latency=32
             ressources : mémoireE/S:2f0-2ef mémoireE/S:2f0-2ef irq:147 mémoire:2ffff20000-2ffff23fff mémoire:2ffff00000-2ffff0ffff
        *-serial
             description: SMBus
             produit: 100 Series/C230 Series Chipset Family SMBus
             fabricant: Intel Corporation
             identifiant matériel: 1f.4
             information bus: pci@0000:00:1f.4
             version: 31
             bits: 64 bits
             horloge: 33MHz
             configuration : driver=i801_smbus latency=0
             ressources : mémoireE/S:2f0-2ef irq:16 mémoire:2ffff24000-2ffff240ff portE/S:f000(taille=32)
     *-pnp00:00
          produit: PnP device PNP0c02
          identifiant matériel: 1
          fonctionnalités: pnp
          configuration : driver=system
     *-pnp00:01
          produit: PnP device PNP0c02
          identifiant matériel: 2
          fonctionnalités: pnp
          configuration : driver=system
     *-pnp00:02
          produit: PnP device PNP0b00
          identifiant matériel: 3
          fonctionnalités: pnp
          configuration : driver=rtc_cmos
     *-pnp00:03
          produit: PnP device INT3f0d
          identifiant matériel: 4
          fonctionnalités: pnp
          configuration : driver=system
     *-pnp00:04
          produit: PnP device PNP0303
          identifiant matériel: 5
          fonctionnalités: pnp
          configuration : driver=i8042 kbd
     *-pnp00:05
          produit: PnP device SYN1220
          identifiant matériel: 6
          fonctionnalités: pnp
          configuration : driver=i8042 aux
     *-pnp00:06
          produit: PnP device PNP0c02
          identifiant matériel: 7
          fonctionnalités: pnp
          configuration : driver=system
     *-pnp00:07
          produit: PnP device PNP0c02
          identifiant matériel: 8
          fonctionnalités: pnp
          configuration : driver=system
     *-pnp00:08
          produit: PnP device PNP0c02
          identifiant matériel: 9
          fonctionnalités: pnp
          configuration : driver=system
     *-pnp00:09
          produit: PnP device PNP0c02
          identifiant matériel: a
          fonctionnalités: pnp
          configuration : driver=system
     *-scsi
          identifiant matériel: b
          nom logique: scsi3
          fonctionnalités: emulated
        *-disk
             description: ATA Disk
             produit: ST2000LM015-2E81
             identifiant matériel: 0.0.0
             information bus: scsi@3:0.0.0
             nom logique: /dev/sda
             version: 0001
             numéro de série: WDZRQHT4
             taille: 1863GiB (2TB)
             fonctionnalités: gpt-1.00 partitioned partitioned:gpt
             configuration : ansiversion=5 guid=0effbce1-8d9f-4687-8ea2-9f31cb55887f logicalsectorsize=512 sectorsize=4096
           *-volume:0
                description: reserved partition
                fabricant: Windows
                identifiant matériel: 1
                information bus: scsi@3:0.0.0,1
                nom logique: /dev/sda1
                numéro de série: 3502c617-b609-4a31-947e-95d45092d253
                capacité: 15MiB
                fonctionnalités: nofs nomount
                configuration : name=Microsoft reserved partition
           *-volume:1
                description: Windows NTFS volume
                fabricant: Windows
                identifiant matériel: 2
                information bus: scsi@3:0.0.0,2
                nom logique: /dev/sda2
                nom logique: /media/ludovic/6E56A85356A81E39
                version: 3.1
                numéro de série: 9ca286e1-8b18-6148-876b-ef596978c9e8
                taille: 1862GiB
                capacité: 1862GiB
                fonctionnalités: ntfs initialized
                configuration : clustersize=4096 created=2021-09-27 23:43:05 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 name=Basic data partition state=mounted
           *-volume:2
                description: Windows NTFS volume
                fabricant: Windows
                identifiant matériel: 3
                information bus: scsi@3:0.0.0,3
                nom logique: /dev/sda3
                version: 3.1
                numéro de série: 8432-3b85
                taille: 519MiB
                capacité: 539MiB
                fonctionnalités: boot precious nomount ntfs initialized
                configuration : clustersize=4096 created=2021-09-30 07:37:02 filesystem=ntfs state=clean


```

Informations to inxi 

```
System:    Host: Ludovic Kernel: 5.13.0-37-generic x86_64 bits: 64 Desktop: KDE Plasma 5.18.8  
           Distro: Ubuntu 20.04.4 LTS (Focal Fossa)  
Machine:   Type: Laptop System: Notebook product: P7xxDM3(-G) v: N/A serial: <superuser/root required>  
           Mobo: Notebook model: P7xxDM3(-G) serial: <superuser/root required> UEFI: American Megatrends v: 1.06.09  
           date: 03/20/2017  
Battery:   ID-1: BAT0 charge: 80.5 Wh condition: 80.5/79.9 Wh (101%)  
CPU:       Topology: Quad Core model: Intel Core i7-7700T bits: 64 type: MT MCP L2 cache: 8192 KiB  
           Speed: 998 MHz min/max: 800/3800 MHz Core speeds (MHz):1: 1899 2: 3040 3: 1935 4: 3410 5: 3306 6: 3142 7: 3340  
           8: 3335  
Graphics:  Device-1: NVIDIA GP106BM [GeForce GTX 1060 Mobile 6GB] driver: nouveau v: kernel  
           Display: x11 server: X.Org 1.20.13 driver: modesetting unloaded: fbdev,vesa  
           resolution: 1920x1080~60Hz, 1920x1080~60Hz  
           OpenGL:renderer: NV136 v: 4.3 Mesa 22.0.0 - kisak-mesa PPA  
Audio:     Device-1: Intel 100 Series/C230 Series Family HD Audio driver: snd_hda_intel  
           Device-2: NVIDIA GP106 High Definition Audio driver: snd_hda_intel  
           Sound Server: ALSA v: k5.13.0-37-generic  
Network:   Device-1: Qualcomm Atheros Killer E2400 Gigabit Ethernet driver: alx  
           IF: enp110s0 state: down mac: 80:fa:5b:42:6b:52  
           Device-2: Intel Wireless-AC 9260 driver: iwlwifi  
           IF: wlp113s0 state: up mac: 3c:58:c2:a4:58:26  
Drives:    Local Storage:total: 3.64 TiB used: 430.63 GiB (11.6%)  
           ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 970 EVO Plus 2TB size: 1.82 TiB  
           ID-2: /dev/sda vendor: Seagate model: ST2000LM015-2E8174 size: 1.82 TiB  
Partition: ID-1: / size: 916.14 GiB used: 86.51 GiB (9.4%) fs: ext4 dev: /dev/nvme0n1p2  
Sensors:   System Temperatures:cpu: 56.0 C mobo: N/A gpu: nouveau temp: 48 C  
           Fan Speeds (RPM): N/A  
Info:      Processes: 356 Uptime: 3h 18m Memory: 62.76 GiB used: 5.16 GiB (8.2%) Shell: bash inxi: 3.0.38 


```

task manager work. For him the game is executed normally ( exemple : my time at portia or banner of the maid) .

---

### Post by mastablasta on 2022-03-25
NVIDIA Corporation GP106BM [GeForce GTX 1060 Mobile 6GB] - mobile? for these usually you need to add the optimus switch or they run on intel. could it be you also have an intel GPU chip + nvidia GPU? do you have two monitors?

it is curious to me as we have two nvidia +ryzen desktop builds and everything works file. we also have AMD APU builds (ryzen and E-450) and have also not faced this issue. is there a way for your to try a GOG windows title in Wine or Play on linux. because if you run in wine you can run the game from command line and then you get all the extra information what is going on, what is missing etc. i am not sure if proton logs everything since you say only complaint was about VR. well CSGo is also giving plenty errors in console, but they don't seem to have any effect on gameplay. in other words they dont' seem to be critical.


and as i understand native titles work fine just proton games won't launch or rather they do launch but remain running in background instead of full screen in the front.

> [COLOR=#000000]task manager work. For him the game is executed normally ( exemple : my time at portia or banner of the maid) .[/COLOR]

is there a way to bring the game to the front?

---

### Post by Agriesean on 2022-03-28
I tried with only one monitor after restarting ubuntu, the problem is the same . 

> and as i understand native titles work fine just proton games won't launch or rather they do launch but remain running in background instead of full screen in the front.
I think like you and that's what I don't understand 
> is there a way to bring the game to the front?
I tried wmctrl and xdotool but they doesn't works and wenn I did command line i doens't had error .

> 
wmctrl -a banner
xdotool search --name banner windowsraise

banner is the game process in steam  

[https://askubuntu.com/questions/21262/shell-command-to-bring-a-program-window-in-front-of-another](https://askubuntu.com/questions/21262/shell-command-to-bring-a-program-window-in-front-of-another)

---

### Post by mastablasta on 2022-03-29
if the intel CPU has it's own GPU chip, do you use optirun or something like that before running the game?

if you have dual GPU chips then it gives additional complexity as i believe the nvidia way is not propperly sopported in linux. the switch is done manually.

how it works on dell and what it is:
[https://www.dell.com/support/kbdoc/en-si/000132622/a-guide-to-nvidia-optimus-on-dell-pcs-with-an-ubuntu-operating-system](https://www.dell.com/support/kbdoc/en-si/000132622/a-guide-to-nvidia-optimus-on-dell-pcs-with-an-ubuntu-operating-system) 

for example here one user  could only make it work by blacklisting nouveau driver:
[https://askubuntu.com/questions/1232211/nvidia-optimus-on-20-04-switching-to-intel-gpu-works-on-ubuntu-mate-but-not-on](https://askubuntu.com/questions/1232211/nvidia-optimus-on-20-04-switching-to-intel-gpu-works-on-ubuntu-mate-but-not-on) 

i try to avoid this combo as many users hasd issue with it. i would only go for it if it was officially supported by laptop manufacturer (for example some prelaoded Ubuntu Dell PC come with out of the box support for this option).

--

however if you do not have two GPU chips, then i am out of ideas what could be going wrong. you have the GPU drivers, the chip is well suported by nvidia, so everything should work without much tinkering. it is one of the reasons why i moved to linux. it just progressed to this stage. and when i upgraded my PC last year, i wanted to go with AMD, but they didn't have any here at descent price or at all in stock. so i had to go with nvidia again (GTX1650). and so far so good.

---

### Post by Agriesean on 2022-04-10
thank's many for your help. They doesn't work. 

I had no choice but to format my computer. put windows on my ssd to be able to play stranquilly and keep ubuntu for the rest in hard disq.


I think I'm the exception that proves the rule but otherwise it's perfectly possible to play quietly on ubuntu.

---

### Post by warner-david0 on 2022-05-01
Switch to experimental, Set launch options

```
-nosplash -skipintro
```


I've set max_map_count ```
sudo sysctl -w vm.max_map_count=1048576
```…to avoid having a black screen (in desktop mode...

I'm putting this here; for you and myself; Heavily copied from this post. [https://www.protondb.com/app/221100](https://www.protondb.com/app/221100) 

Next link: from JackDos... scroll down, he shows how to find two kinds of files to delete and let Steam replenish those files.  One is your character file.  another is removing the proton files, both seem to replenish well through the steam launcher, if 'reset character,' or 'reset files' is your goal.  

[https://www.reddit.com/r/SteamPlay/comments/u0er9f/games_not_launching_with_proton/](https://www.reddit.com/r/SteamPlay/comments/u0er9f/games_not_launching_with_proton/)

---

### Post by DuckHook on 2022-05-02
Welcome to the forums, warner-david0 and thank you for your contribution.

Please use only standard fonts and formatting when posting. I have corrected your post but it was unreadable in my browser as originally formatted.

---

