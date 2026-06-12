---
title: "Unexplained System Hanging in Feisty, logs don't help."
date: 2008-04-12
forum: Desktop Environments
---

### Post by MaddMatt on 2008-04-12
Hey all! 

I've been running Feisty for some time, tried installing  7.10 but it didn't like my hardware or something so I'm waiting for LTS (yay). 

Anyway, my system has recently been hanging inexplicably for the past two weeks. The computer seems to be running to some extent, because it accepts connections through FTP still, but without actually allowing logins. The keyboard won't work, (USB, caps lock / num lock do nothing), but in instances the mouse (also USB) will continue to work. No windows are operational, and the only way to get function back is a hard-reboot (ouch). Sometimes this happens during the day, but it often happens in the middle of the night, and has been happening nearly 1x / day for the last week and a half. 

Recently, in order to get onto a local WPA-LEAP network in the area, I installed a new Trend Net TEW-443PI desktop wireless adapter, and have begun using WPA-Supplicant and the Madwifi driver. 

Also recently, I began using ReplayGain through AmaroK to equalize my volume, and AmaroK runs several background tasks, such as Last.fm statistics, etc. 

Furthermore, my network settings are handled through kwlan because network-manager can't seem to deal with WPA in the version I have. 

Now, the network is initialized at boot, so I can't seem to isolate that. Most of the time when it freezes at night, AmaroK is running, because it pumps music to my clock-radio as a morning alarm (obvious difficulty here... :| ) BUT it does not need to be running for the system to hang, it may just add to the problems. I was hoping to be able to get information from the logs, but they aren't too helpful - usually gaps in the system -MARK- messages. Here's an example:

Logs:
> 
Apr 11 01:31:59 Sparta -- MARK --
Apr 11 01:51:59 Sparta -- MARK --
Apr 11 02:12:00 Sparta -- MARK --
Apr 11 02:32:00 Sparta -- MARK --
Apr 11 02:52:00 Sparta -- MARK --
Apr 11 09:10:20 Sparta syslogd 1.4.1#20ubuntu4: restart.
Apr 11 09:10:20 Sparta kernel: Inspecting /boot/System.map-2.6.20-16-generic
Apr 11 09:10:20 Sparta kernel: Loaded 24980 symbols from /boot/System.map-2.6.20-16-generic.
Apr 11 09:10:20 Sparta kernel: Symbols match kernel version 2.6.20.

or one of the more useful ones:

> 
Apr  8 01:24:01 Sparta -- MARK --
Apr  8 01:37:50 Sparta kernel: [104109.458668]  [softlockup_tick+156/240] softlockup_tick+0x9c/0xf0
Apr  8 01:37:50 Sparta kernel: [104109.458688]  [update_process_times+51/128] update_process_times+0x33/0x80
Apr  8 01:37:50 Sparta kernel: [104109.458698]  [smp_apic_timer_interrupt+112/128] smp_apic_timer_interrupt+0x70/0x80
Apr  8 01:37:50 Sparta kernel: [104109.458707]  [apic_timer_interrupt+40/48] apic_timer_interrupt+0x28/0x30
Apr  8 01:37:50 Sparta kernel: [104109.458721]  [_spin_lock_irqsave+47/80] _spin_lock_irqsave+0x2f/0x50
Apr  8 01:37:50 Sparta kernel: [104109.458730]  [<f8c768f4>] ieee80211_free_node+0x24/0x80 [wlan]
Apr  8 01:37:50 Sparta kernel: [104109.458759]  [<f8c716d7>] ieee80211_input_all+0x57/0x90 [wlan]
Apr  8 01:37:50 Sparta kernel: [104109.458787]  [<f89f2fe1>] ath_rx_tasklet+0x751/0x7e0 [ath_pci]
Apr  8 01:37:50 Sparta kernel: [104109.458800]  [rtnl_setlink+0/1104] rtnl_setlink+0x0/0x450
Apr  8 01:37:50 Sparta kernel: [104109.458817]  [tasklet_action+99/224] tasklet_action+0x63/0xe0
Apr  8 01:37:50 Sparta kernel: [104109.458827]  [__do_softirq+130/256] __do_softirq+0x82/0x100
Apr  8 01:37:50 Sparta kernel: [104109.458837]  [do_softirq+85/96] do_softirq+0x55/0x60
Apr  8 01:37:50 Sparta kernel: [104109.458844]  [do_IRQ+69/128] do_IRQ+0x45/0x80
Apr  8 01:37:50 Sparta kernel: [104109.458849]  [netlink_sendskb+33/64] netlink_sendskb+0x21/0x40
Apr  8 01:37:50 Sparta kernel: [104109.458860]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Apr  8 01:37:50 Sparta kernel: [104109.458872]  [<f8a155b4>] zz016e309b+0x1a4/0x1c0 [ath_hal]
Apr  8 01:37:50 Sparta kernel: [104109.458889]  [<f8a159e0>] zz016e189b+0x398/0x3ac [ath_hal]
Apr  8 01:37:50 Sparta kernel: [104109.458907]  [<f89e7bc3>] ath_txq_update+0xd3/0xe0 [ath_pci]
Apr  8 01:37:50 Sparta kernel: [104109.458925]  [<f8a01a46>] zz0067d221+0x1a/0x34 [ath_hal]
Apr  8 01:37:50 Sparta kernel: [104109.458941]  [<f89e7bef>] ath_wme_update+0x1f/0x90 [ath_pci]
Apr  8 01:37:50 Sparta kernel: [104109.458952]  [<f8c7dac3>] ieee80211_wme_updateparams_locked+0x123/0x210 [wlan]
Apr  8 01:37:50 Sparta kernel: [104109.458977]  [<f8c7e141>] ieee80211_wme_initparams_locked+0x41/0x170 [wlan]
Apr  8 01:37:50 Sparta kernel: [104109.459005]  [<f8c7f521>] ieee80211_wme_initparams+0x21/0x40 [wlan]
Apr  8 01:37:50 Sparta kernel: [104109.459031]  [<f8c77a00>] ieee80211_sta_join1+0xa0/0x200 [wlan]
Apr  8 01:37:50 Sparta kernel: [104109.459055]  [<f8c821d0>] mlmelookup+0x0/0x60 [wlan]
Apr  8 01:37:50 Sparta kernel: [104109.459084]  [<f8c82e2f>] ieee80211_ioctl_setmlme+0xbf/0x250 [wlan]
Apr  8 01:37:50 Sparta kernel: [104109.459114]  [wireless_process_ioctl+701/992] wireless_process_ioctl+0x2bd/0x3e0
Apr  8 01:37:50 Sparta kernel: [104109.459122]  [<f8c82d70>] ieee80211_ioctl_setmlme+0x0/0x250 [wlan]
Apr  8 01:37:50 Sparta kernel: [104109.459148]  [sock_ioctl+0/528] sock_ioctl+0x0/0x210
Apr  8 01:37:50 Sparta kernel: [104109.459156]  [dev_ioctl+531/896] dev_ioctl+0x213/0x380
Apr  8 01:37:50 Sparta kernel: [104109.459163]  [__switch_to+198/496] __switch_to+0xc6/0x1f0
Apr  8 01:37:50 Sparta kernel: [104109.459178]  [sock_ioctl+0/528] sock_ioctl+0x0/0x210
Apr  8 01:37:50 Sparta kernel: [104109.459183]  [do_ioctl+43/144] do_ioctl+0x2b/0x90
Apr  8 01:37:50 Sparta kernel: [104109.459191]  [vfs_ioctl+92/672] vfs_ioctl+0x5c/0x2a0
Apr  8 01:37:50 Sparta kernel: [104109.459199]  [sys_ioctl+114/144] sys_ioctl+0x72/0x90
Apr  8 01:37:50 Sparta kernel: [104109.459206]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9
Apr  8 01:37:50 Sparta kernel: [104109.459220]  =======================
Apr  8 08:00:25 Sparta syslogd 1.4.1#20ubuntu4: restart.
Apr  8 08:00:25 Sparta kernel: Inspecting /boot/System.map-2.6.20-16-generic


I'm tempted to just wait for 8.04 to see if this gets resolved, but it's kind of a big issue, and I'm worried about permanent damage to my / partition. Your thoughts? 

Thanks!
-Matt

---

### Post by sardion on 2008-04-13
It kinda looks like a hardware issue (hate to say it).

You should run some tests.  The most likely issue is memory:

Install memtest86+ (if its not already there) and reboot and choose it from the GRUB menu.

There are some other hardware testers out there as well.

---

### Post by MaddMatt on 2008-04-14
thanks, I did run memtest and no dice. It just did it again a few minutes ago and popped up this 'bug' entry in the syslog:

> 
Apr 13 21:50:52 Sparta -- MARK --
Apr 13 22:09:40 Sparta kernel: [ 8413.883195] BUG: soft lockup detected on CPU#1!
Apr 13 22:09:40 Sparta kernel: [ 8413.883223]  [softlockup_tick+156/240] softlockup_tick+0x9c/0xf0
Apr 13 22:09:40 Sparta kernel: [ 8413.883241]  [update_process_times+51/128] update_process_times+0x33/0x80
Apr 13 22:09:40 Sparta kernel: [ 8413.883250]  [smp_apic_timer_interrupt+112/128] smp_apic_timer_interrupt+0x70/0x80
Apr 13 22:09:40 Sparta kernel: [ 8413.883258]  [apic_timer_interrupt+40/48] apic_timer_interrupt+0x28/0x30
Apr 13 22:09:40 Sparta kernel: [ 8413.883271]  [_spin_lock_irqsave+47/80] _spin_lock_irqsave+0x2f/0x50
Apr 13 22:09:40 Sparta kernel: [ 8413.883280]  [<f89e28f4>] ieee80211_free_node+0x24/0x80 [wlan]
Apr 13 22:09:40 Sparta kernel: [ 8413.883308]  [<f89dd6d7>] ieee80211_input_all+0x57/0x90 [wlan]
Apr 13 22:09:40 Sparta kernel: [ 8413.883333]  [<f8b21fe1>] ath_rx_tasklet+0x751/0x7e0 [ath_pci]
Apr 13 22:09:40 Sparta kernel: [ 8413.883353]  [tasklet_action+99/224] tasklet_action+0x63/0xe0
Apr 13 22:09:40 Sparta kernel: [ 8413.883362]  [__do_softirq+130/256] __do_softirq+0x82/0x100
Apr 13 22:09:40 Sparta kernel: [ 8413.883372]  [do_softirq+85/96] do_softirq+0x55/0x60
Apr 13 22:09:40 Sparta kernel: [ 8413.883379]  [do_IRQ+69/128] do_IRQ+0x45/0x80
Apr 13 22:09:40 Sparta kernel: [ 8413.883387]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Apr 13 22:09:40 Sparta kernel: [ 8413.883399]  [<f8a2bff0>] zz033ebfbf+0xc0/0x148 [ath_hal]
Apr 13 22:09:40 Sparta kernel: [ 8413.883414]  [<f8a3f3b8>] zz0b709eff+0x38/0x48 [ath_hal]
Apr 13 22:09:40 Sparta kernel: [ 8413.883430]  [<f8b16b77>] ath_txq_update+0x87/0xe0 [ath_pci]
Apr 13 22:09:40 Sparta kernel: [ 8413.883449]  [<f8a2ba46>] zz0067d221+0x1a/0x34 [ath_hal]
Apr 13 22:09:40 Sparta kernel: [ 8413.883463]  [<f8b16bef>] ath_wme_update+0x1f/0x90 [ath_pci]
Apr 13 22:09:40 Sparta kernel: [ 8413.883474]  [<f89e9ac3>] ieee80211_wme_updateparams_locked+0x123/0x210 [wlan]
Apr 13 22:09:40 Sparta kernel: [ 8413.883499]  [<f89ea141>] ieee80211_wme_initparams_locked+0x41/0x170 [wlan]
Apr 13 22:09:40 Sparta kernel: [ 8413.883524]  [<f89eb521>] ieee80211_wme_initparams+0x21/0x40 [wlan]
Apr 13 22:09:40 Sparta kernel: [ 8413.883546]  [<f89e3a00>] ieee80211_sta_join1+0xa0/0x200 [wlan]
Apr 13 22:09:40 Sparta kernel: [ 8413.883567]  [<f89ee1d0>] mlmelookup+0x0/0x60 [wlan]
Apr 13 22:09:40 Sparta kernel: [ 8413.883589]  [<f89ee1d0>] mlmelookup+0x0/0x60 [wlan]
Apr 13 22:09:40 Sparta kernel: [ 8413.883614]  [<f89eee2f>] ieee80211_ioctl_setmlme+0xbf/0x250 [wlan]
Apr 13 22:09:40 Sparta kernel: [ 8413.883641]  [wireless_process_ioctl+701/992] wireless_process_ioctl+0x2bd/0x3e0
Apr 13 22:09:40 Sparta kernel: [ 8413.883650]  [<f89eed70>] ieee80211_ioctl_setmlme+0x0/0x250 [wlan]
Apr 13 22:09:40 Sparta kernel: [ 8413.883673]  [sock_ioctl+0/528] sock_ioctl+0x0/0x210
Apr 13 22:09:40 Sparta kernel: [ 8413.883681]  [dev_ioctl+531/896] dev_ioctl+0x213/0x380
Apr 13 22:09:40 Sparta kernel: [ 8413.883697]  [sock_ioctl+0/528] sock_ioctl+0x0/0x210
Apr 13 22:09:40 Sparta kernel: [ 8413.883704]  [do_ioctl+43/144] do_ioctl+0x2b/0x90
Apr 13 22:09:40 Sparta kernel: [ 8413.883712]  [vfs_ioctl+92/672] vfs_ioctl+0x5c/0x2a0
Apr 13 22:09:40 Sparta kernel: [ 8413.883719]  [sys_ioctl+114/144] sys_ioctl+0x72/0x90
Apr 13 22:09:40 Sparta kernel: [ 8413.883725]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9
Apr 13 22:09:40 Sparta kernel: [ 8413.883741]  =======================
Apr 13 22:35:43 Sparta syslogd 1.4.1#20ubuntu4: restart.
Apr 13 22:35:43 Sparta kernel: Inspecting /boot/System.map-2.6.20-16-generic

I'm rather convinced that it's some sort of bug with the madwifi drivers, as it's been hanging w/o kwlan too. This last one was as I was logging in! Haven't seen any issues mentioned in the forums with the driver since dapper though...

---

