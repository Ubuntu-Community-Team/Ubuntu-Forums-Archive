---
title: "screen refreshing issue in xubuntu 14.04"
date: 2015-07-06
forum: Desktop Environments
---

### Post by 1egoman on 2015-07-06
Hello!

After putting xubuntu 14.04 on my asus zenbook ux305, I have run into one really annoying issue. Sometimes, I'll be doing something, like for example moving to a new chrome tab with CTRL+TAB, and the image of the tab won't update in the tab bar until I manually trigger an update by moving my cursor to its position, or by running "xrefresh". This isn't specific to chrome: Something similar repeatedly happens in xfce4-panel, gvim, and a few oher assorted programs I cannot remember right now. Often, if I right-click, I won't get anything either until I move my mouse slightly and then I'll see the first item of the resulting context menu. I'm not all that familiar with gpu/xorg video driver terms, so pardon my lack of knowledge in this area. I have attached an image taken of my screen with my phone (fyi, screenshots update the screen so they don't show the problem). This issue is really annoying and I would appreciate any possible assistance.

Could it be tempurature related? The laptop is passively cooled and is pretty hot right now.
> 
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +47.0°C  (crit = +98.0°C)
temp2:        +27.8°C  (crit = +105.0°C)
temp3:        +29.8°C  (crit = +105.0°C)


GEN2-virtual-0
Adapter: Virtual device
temp1:        +43.0°C  


coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +48.0°C  (high = +95.0°C, crit = +95.0°C)
Core 0:         +45.0°C  (high = +95.0°C, crit = +95.0°C)
Core 1:         +46.0°C  (high = +95.0°C, crit = +95.0°C)


asus-isa-0000
Adapter: ISA adapter
temp1:        +47.0°C  



/etc/X11/xorg.conf doesn't exist. 

> 
$ lspci
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:04.0 Signal processing controller: Intel Corporation Broadwell-U Camarillo Device (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation Wireless 7265 (rev 59)


> 
$ dmesg...
[23530.978258] cfg80211: Calling CRDA for country: US
[23530.980202] cfg80211: Regulatory domain changed to country: US
[23530.980205] cfg80211:  DFS Master region: unset
[23530.980206] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[23530.980209] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm), (N/A)
[23530.980211] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm), (N/A)
[23530.980212] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (0 s)
[23530.980214] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (0 s)
[23530.980215] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (0 s)
[23530.980217] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm), (N/A)
[23530.980218] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)


Any other helpful info needed?

Below: This happened when I pressed ALT+TAB to switch to chrome, (the terminal didn't go away until I "moused over" it), 
[IMG]http://i62.tinypic.com/2jlmq.jpg[/IMG]

Then I opened up a popup window. Notice the corrupted text in the window header and the tab/bookmarks bar parts that have updated and "overwrote" the popup.
[IMG]http://i61.tinypic.com/1hv8lz.jpg[/IMG]
[IMG]http://i58.tinypic.com/2wlvr4g.jpg[/IMG]
[IMG]http://i57.tinypic.com/34e3fqv.jpg[/IMG]

---

