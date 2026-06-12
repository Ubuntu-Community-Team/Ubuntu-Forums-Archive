---
title: "Dell Laptop E6430 won't detect monitors through docking station"
date: 2013-05-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aerinon on 2013-05-16
So, my work just provided me with a laptop to replace my desktop but I can't seem to get it to detect the monitors attached to the docking station. It looks like I'm dealing with an nvidia optimus setup attached to the DVI/HDMI viewport. (I'm assuming I'm having so much trouble because the dock outputs are hooked to the nvidia card rather than the onboard intel card) The VGA port on the docks works (but there's only one of those, and there's two DVI/HDMI ports) I assume it's because it's attached to the intel card.

Things I've tried:

[LIST]
[*]Install ppa nvidia drivers. But when I run nvidia-settings, it claims that I'm not using the driver.
[*]Turning off optimus entirely in the BIOS. Dell doesn't seem to have an option to use the nvidia stuff exclusively like the Lenovo laptops do, so I think I'm only running off the Intel integrated graphics
[*]Tried bumblebee's [https://github.com/Bumblebee-Project/Bumblebee/wiki/Multi-monitor-setup](https://github.com/Bumblebee-Project/Bumblebee/wiki/Multi-monitor-setup), (I was able to get optirun working properly, but I still can't access the nvidia settings) and I don't think it's quite what I want because their triple monitor setup states that you can't move windows between screens. I may need to go down this road some more.
[*]Tried upgrading to Ubuntu 12.10. This [http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work](http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work) (2nd answer) seems to indicate that there ought to be some support but I'm not sure how successful I've been in reverting to the default drivers. (I'm not opposed to upgrading all the way to 13.04 if I have to. Or even switching linux distros, if I could get the dual monitors via dock to work.)
[/LIST]
Output of lspci:

```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM77 Express Chipset LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0dfc (rev a1)
03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
0c:00.0 SD Host controller: O2 Micro, Inc. Device 8221 (rev 05)

```

Any help or direction would be greatly appreciated.

Thanks,

---

