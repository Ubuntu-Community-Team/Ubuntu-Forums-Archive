---
title: "Re: Teclast X2 Pro: On board keyboard on at boot then immediately blanked out."
date: 2017-11-29
forum: Desktop Environments
---

### Post by makem2 on 2017-11-29
This machine is a two in one. The screen can be removed to use it as a tablet.

This is a fresh install of xubuntu with a gnome desktop and I had  noticed that the screen would seem to flicker, like a refresh before I started to sign in. I didn't think anything about it as it didn't seem to have any adverse effect.

I have set the on-board keyboard to come on at boot to enable me to sign in.

I enabled it to at startup in LightDM GTK+Greeter settings and also in Session and startup.

When I reboot, the keyboard comes up and if it stayed that way I could then sign in. However, immediately the keyboard keys are blanked out, leaving a blank black box.

I suspect the screen is being refreshed for some reason but cannot fathom why, or why if refreshed, why it should affect the on-board keyboard in this way.

Any suggestions would be appreciated.

EDIT: This also occurs when logging back in. I am beginning to suspect a video driver.

```

makem@teclast:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Broadwell-U Host Bridge -OPI [8086:1604] (rev 09)
	Subsystem: Intel Corporation Broadwell-U Host Bridge -OPI [8086:1604]
	Kernel driver in use: bdw_uncore
00:02.0 VGA compatible controller [0300]: Intel Corporation Broadwell-U Integrated Graphics [8086:161e] (rev 09)
	DeviceName:  Onboard IGD
	Subsystem: Intel Corporation Broadwell-U Integrated Graphics [8086:161e]
	Kernel driver in use: i915
	Kernel modules: i915
00:03.0 Audio device [0403]: Intel Corporation Broadwell-U Audio Controller [8086:160c] (rev 09)
	Subsystem: Intel Corporation Broadwell-U Audio Controller [8086:160c]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
00:04.0 Signal processing controller [1180]: Intel Corporation Broadwell-U Camarillo Device [8086:1603] (rev 09)
	Subsystem: Intel Corporation Broadwell-U Processor Thermal Subsystem [8086:1603]
	Kernel driver in use: proc_thermal
	Kernel modules: processor_thermal_device
00:14.0 USB controller [0c03]: Intel Corporation Wildcat Point-LP USB xHCI Controller [8086:9cb1] (rev 03)
	Subsystem: Intel Corporation Wildcat Point-LP USB xHCI Controller [8086:9cb1]
	Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation Wildcat Point-LP MEI Controller #1 [8086:9cba] (rev 03)
	Subsystem: Intel Corporation Wildcat Point-LP MEI Controller [8086:9cba]
	Kernel driver in use: mei_me
	Kernel modules: mei_me
00:1b.0 Audio device [0403]: Intel Corporation Wildcat Point-LP High Definition Audio Controller [8086:9ca0] (rev 03)
	Subsystem: Realtek Semiconductor Co., Ltd. Wildcat Point-LP High Definition Audio Controller [10ec:1082]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
00:1f.0 ISA bridge [0601]: Intel Corporation Wildcat Point-LP LPC Controller [8086:9cc7] (rev 03)
	Subsystem: Intel Corporation Wildcat Point-LP LPC Controller [8086:9cc7]
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] [8086:9c83] (rev 03)
	Subsystem: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] [8086:9c83]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation Wildcat Point-LP SMBus Controller [8086:9ca2] (rev 03)
	Subsystem: Intel Corporation Wildcat Point-LP SMBus Controller [8086:9ca2]
	Kernel modules: i2c_i801
00:1f.6 Signal processing controller [1180]: Intel Corporation Wildcat Point-LP Thermal Management Controller [8086:9ca4] (rev 03)
	Subsystem: Intel Corporation Wildcat Point-LP Thermal Management Controller [8086:9ca4]
	Kernel driver

```

I add this question as a reply because the EDIT was getting quite long:

Any thoughts on whether this route would be productive; it appears so but may also break the system:

[https://01.org/linuxgraphics/downloads/intel-graphics-update-tool-linux-os-v2.0.2](https://01.org/linuxgraphics/downloads/intel-graphics-update-tool-linux-os-v2.0.2)

In ubuntu the tool must be run using this method:

[https://01.org/linuxgraphics/documentation/running-update-tool-using-gdebi](https://01.org/linuxgraphics/documentation/running-update-tool-using-gdebi)

---

