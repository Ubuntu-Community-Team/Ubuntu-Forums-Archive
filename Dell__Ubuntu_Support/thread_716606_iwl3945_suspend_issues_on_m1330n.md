---
title: "iwl3945 suspend issues on m1330n"
date: 2008-03-06
forum: Dell  Ubuntu Support
---

### Post by pormogo on 2008-03-06
So I've been messing around with the wireless config on my laptop for the last few days. Before i delve anymore into this let me say that everything else has worked itself out pretty well. I was able to get compiz and video working with the blacklisted GM965 video solution. However I have noticed that the ipw3945 module enabled by default was absolutely terrible. it would frequently loose all connectivity at which point I would have to restart nm and unload/reload the module into the kernel. Sometimes this didn't even work and a reboot would be required.

So I checked on dells website and found the following fix [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues) awesome. So I followed the pretty basic directions blacklisting the ipw module and adding the iwl module into the modules file. I rebooted and everything works great

[i]root@dell-desktop:~#  lsmod |grep iwl
iwl3945                88168  0 
iwlwifi_mac80211      175112  1 iwl3945
cfg80211                7304  1 iwlwifi_mac80211
[/i]

However anytime I suspend or hibernate my wireless is completely broken. nm doesn't see any networks. I can unload and reload the module, restarting nm and nmd doesn't fix anything either. I have to reboot any time I need to suspend my laptop, not cool. This is a pretty big show stopper for me. Is there any way to correct this? I read a forum post in the fedora core forms that said the only way to do this was to unload the module when suspending and reload the module when coming back from a suspend. This can obviously most easily be done with shell scripts in /etc/acpi/suspend.d and resume.d. But I haven't read anything on the ubuntu forums with users having the same issue. Is there something I'm missing here?

---

### Post by pormogo on 2008-03-06
I've tried manually unloading the iwl module before suspending and then reloading the module when coming back from the suspend however that doesn't seem to fix anything so I have no real reason to believe that creating shell scripts to load and unload the modules when suspending would really have any effect. Any help would be most appreciated.

---

### Post by pormogo on 2008-03-07
Upon further examination this doesn't even seem to require a suspend I left my laptop sitting on the table connected to wifi with the lid closed (screen off) and when I came home a few hours later my laptop was trying to connect to my home network without success. When I ran dmesg the latest update was 

*[71672.320000] ADDRCONF(NETDEV_UP): wlan0_rename: link is not ready*

I tired restarting nm and nmd and even reloading the module but nothing would bring it back. After reloading the module the following comes up in dmesg and gnome appears to have dropped basically all wireless functionality.

[i][71735.208000] ACPI: PCI interrupt for device 0000:0c:00.0 disabled
[71751.736000] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.1.0
[71751.736000] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[71751.736000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[71751.736000] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[71751.736000] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[71751.888000] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[71751.888000] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[71800.572000] tg3: eth0: Link is up at 100 Mbps, full duplex.
[71800.576000] tg3: eth0: Flow control is on for TX and on for RX.
[71800.580000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[71817.820000] eth0: no IPv6 routers present
[73570.196000]  CIFS VFS: server not responding
[73570.196000]  CIFS VFS: No response for cmd 50 mid 22
[/i]

I'm pretty frusterated at this point. Wireless networking is a sloppy mess on this laptop. This is a HUGE break, it's very rare that I am ever in a location where I can get a hard line for my laptop. I'm rebooting this thing at least 4 times a day just so I can connect to wireless networks. To make matters worse none of the modules appear to work for me :(

At this point I'm pretty furious. I've been looking for a solution to this day and night. This laptop without wireless access is basically useless to me. I feel like a complete fool for paying MORE for the same ;aptop JUST so I could have a laptop where the hardware was certified to work with ubuntu not to mention voting for OSS with my consumer dollar. WHAT THE HELL!!!! I could have found a lenovo or any other manner of laptop that actually functions with ubuntu. How can cannocial enter into a dell partnership and claim "full support" for the wireless card when it breaks almost every 20-35 minutes. Sometimes I can't use wireless for more then 5 minutes after booting my computer.

---

### Post by fragos on 2008-03-07
I have a 1420n but don't use suspend and hybernate -- I always shutdown (better for battery life and security).  I set my 1420n to turn off the screen when the lid is closed.  If it sits for a long time and power saving cuts in I don't loose my wireless connection when it come alive.  I've seen a few complaints about hybernate and suspend.  Adopting my approach should give you a workable system.  I will on ocassion loose a connection when an access points gets very busy but I can always click on the NM icon and select that AP again.  If you don't see the AP you may still be able to connect by clicking the NM icon and selecting "Connect to another network."  Enter the SSID and it will attempt to connect again.  I never have problems when there is a high signal strength and few users.  The access point I see occasional drops from is a linksys.  My home TrendNet always works.

---

### Post by pormogo on 2008-03-07
I don't necassarily see the logic in that. If your computer is shut off anyone can boot it and put it into single user mode and then have access to the entire system. If the system is hibernated at least anyone compromising my system would have to shut down my computer and reboot it before taking control of the root user (hardly a herculean task is they're holding my laptop =P). There is no computer security when someone else is in front of the machine. Hibernate has no impact on battery. Which kernel module are using the iwl or ipw module? I have found that suspending 100% breaks the iwl module and the ipw module seems to only survive about 65% of the time. To make matters worse sometimes the ipw module seems to drop the connection and just lock up a very short while after I start working causing me to loose all established connections and essentially have to start over.

Wrestling with my computers wireless has not been among my favorite things in the past few weeks.

---

