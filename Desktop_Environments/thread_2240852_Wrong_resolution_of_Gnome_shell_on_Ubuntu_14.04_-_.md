---
title: "Wrong resolution of Gnome shell on Ubuntu 14.04 - Dell Vostro with Nvidia"
date: 2014-08-22
forum: Desktop Environments
---

### Post by nielsonsport on 2014-08-22
Hi Guys.
I'm having a problem with the resolution when use Gnome Shell 3.10 and Ubuntu 14.04.
The resolution of my display is like it at 1366 x 786 px:
[IMG]https://www.diigo.com/item/p/ecdbqdbzccpdsbqrbzbeqbccpd[/IMG]

I've tested xorg-nouveau and nvidia drivers, but didn't worked.

My machine have the following specifications.

```

00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4)
00:1c.1 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 2 (rev e4)
00:1c.2 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1c.4 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 5 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5227 PCI Express Card Reader (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
08:00.0 Network controller: Intel Corporation Wireless 7260 (rev 93)
09:00.0 3D controller: NVIDIA Corporation GK208M [GeForce GT 740M] (rev ff)

```

Thanks,

---

### Post by Jessie_James_A._At on 2014-08-23
we have the same problem buddy, ive read some article regarding this nvidia, it cannot work or run the whole system, but still you can use bumble bee to run your nvidia in discrete which means per application only not a whole system.

---

