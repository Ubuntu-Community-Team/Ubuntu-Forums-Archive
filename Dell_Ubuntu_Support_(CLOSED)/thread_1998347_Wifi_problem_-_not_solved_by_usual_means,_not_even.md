---
title: "Wifi problem - not solved by usual means, not even compat."
date: 2012-06-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Rodoljop on 2012-06-06
Hello there,

I'm sorry about once again having thead about wireless on a Dell computer on the internet, but all the tutorials and ways found in the internet did not work with  this wifi card (I'm goint to post the lspci and lshw..), from the simple jockey software that didn't find any closed-source driver to installing all drivers from the compat package (which is very good, and was what enabled the wired hardware to work). I'll be very grateful if even anyone using linux with similiar hardware experienced the same problems.

So... the mains problem was all the network hardware, but as I said compat fixed the wired driver problem. what remains is bluetooth functionality and the complete functionality of the wifi card. the specs:

lspci:

```
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 08)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 08)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 08)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.4 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 5 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0de9 (rev a1)
02:00.0 Network controller: Broadcom Corporation Device 4365 (rev 01)
03:00.0 Ethernet controller: Atheros Communications Inc. AR8162 Fast Ethernet (rev 08)

```lshw -c net:

```
  *-network UNCLAIMED     
       descrição: Network controller
       produto: Broadcom Corporation
       fabricante: Broadcom Corporation
       physical id: 0
       informações do barramento: pci@0000:02:00.0
       versão: 01
       largura: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuração: latency=0
       recursos: memória:e1900000-e1907fff
  *-network UNCLAIMED
       descrição: Ethernet controller
       produto: AR8162 Fast Ethernet
       fabricante: Atheros Communications Inc.
       physical id: 0
       informações do barramento: pci@0000:03:00.0
       versão: 08
       largura: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix cap_list
       configuração: latency=0
       recursos: memória:e1800000-e183ffff ioport:2000(tamanho=128)
  *-network
       descrição: Interface sem fio
       physical id: 2
       informações do barramento: usb@2:1.4
       nome lógico: wlan0
       serial: 1c:7e:e5:5d:31:8e
       capabilities: ethernet physical wireless
       configuração: broadcast=yes driver=rt2800usb driverversion=3.2.0-24-generic firmware=0.29 ip=192.168.1.112 link=yes multicast=yes wireless=IEEE 802.11bgn

```the third network is an usb adpater i bought just because the wifi didn't work and the wireless was really needed.

rfkill list:

```

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
5: phy3: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```I think this is enough to see all the network-hardware specs; just reassuring that I searched about this stuff for about seven days and still didn't find an answer.

Sorry about long thread, this is my first post in the forum. Also, please redirect me if this is posted in the wrong place, thanks.


- - - - - - - - UPDATE - - - - - - - -

Hello again, i'm almost sure that i've found the exact model of this laptop: INSPIRON-M5420; if not the exact model, the hardware is almost equal... 
Also, i've searched the dell compatibility part in ubuntu site and found that the complete compatibility only comes with a pre-installed image of the Ubuntu.
    Any Ideas where I can find such

---

### Post by thotz on 2012-07-14
Hello,

look here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/921911](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/921911)

Thomas

---

