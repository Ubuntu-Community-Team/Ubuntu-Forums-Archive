---
title: "Ubuntu 9.04 Freezing"
date: 2009-04-25
forum: General Help
---

### Post by Red207 on 2009-04-25
my computer keeps freezing, locking up and i have to pull the power cord. let it power up then try to go on line it comes up but when i click on any thing if freezes. or lockes up.

---

### Post by tomas.splatch on 2009-04-26
I have a similar problem, I experience similar freezes. Sometimes there is my mouse pointer that stays alive, sometimes not even that, anyway, the only way to make my netbook work is hard off. 
I have a quite new HP multimedia notebook, and I experienced this problem (graphic card blacklisted, unable to start compiz), I found and applied succesfully this solution:

[http://ubuntuforums.org/showthread.php?t=1126944&page=4](http://ubuntuforums.org/showthread.php?t=1126944&page=4)

I wonder if it's due to that? Here is what my /var/log/syslog file is saying abot one of the crashes:

[INDENT]
Apr 26 15:11:44 klarikaatomas-laptop console-kit-daemon[2503]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Apr 26 15:11:44 klarikaatomas-laptop last message repeated 4 times
Apr 26 15:11:44 klarikaatomas-laptop init: tty4 main process (2326) killed by TERM signal
Apr 26 15:11:44 klarikaatomas-laptop init: tty5 main process (2327) killed by TERM signal
Apr 26 15:11:44 klarikaatomas-laptop init: tty1 main process (2967) killed by TERM signal
Apr 26 15:11:44 klarikaatomas-laptop init: tty2 main process (2330) killed by TERM signal
Apr 26 15:11:44 klarikaatomas-laptop init: tty3 main process (2333) killed by TERM signal
Apr 26 15:11:44 klarikaatomas-laptop init: tty6 main process (2334) killed by TERM signal
Apr 26 15:11:44 klarikaatomas-laptop console-kit-daemon[2503]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Apr 26 15:11:44 klarikaatomas-laptop last message repeated 3 times
Apr 26 15:11:44 klarikaatomas-laptop NetworkManager: <info>  (wlan0): device state change: 8 -> 3 
Apr 26 15:11:44 klarikaatomas-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 38). 
Apr 26 15:11:45 klarikaatomas-laptop NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 3523 
Apr 26 15:11:45 klarikaatomas-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess  
Apr 26 15:11:47 klarikaatomas-laptop nm-system-settings:    SCPlugin-Ifupdown: devices removed (udi: /org/freedesktop/Hal/devices/net_00_76_62_6e_65_74)
Apr 26 15:11:49 klarikaatomas-laptop bluetoothd[2667]: Unregistered interface org.bluez.NetworkPeer on path /org/bluez/2667/hci0
Apr 26 15:11:49 klarikaatomas-laptop bluetoothd[2667]: Unregistered interface org.bluez.NetworkHub on path /org/bluez/2667/hci0
Apr 26 15:11:49 klarikaatomas-laptop bluetoothd[2667]: Unregistered interface org.bluez.NetworkRouter on path /org/bluez/2667/hci0
Apr 26 15:11:49 klarikaatomas-laptop bluetoothd[2667]: bridge pan0 removed
Apr 26 15:11:49 klarikaatomas-laptop bluetoothd[2667]: Stopping SDP server
Apr 26 15:11:49 klarikaatomas-laptop bluetoothd[2667]: Exit
Apr 26 15:11:50 klarikaatomas-laptop exiting on signal 15[/INDENT]

---

### Post by cmdrtebok on 2009-05-04
I am having this problem as well. There doesn't seem to be any reason for it. Possibly Flash related but I am not sure. I know its not the Desktop Effects which is the usual cause of my ills. I had the problem when I did the upgrade to 8.10 to 9.04 and I thought a clean install would help it but no luck... Any ideas? Where are the logs?

---

### Post by tomas.splatch on 2009-05-09
it's not compiz (the desktop effects) here either, the same happens with metacity. I suppose it's related to Intel chipset graphic cards problem with new drivers in Xorg 1.6 as pointed here:
[http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html]("http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html")

are you both on netbooks?

another suspicion is using Ext4 filesystem (might be buggy)? do you use it?

logs can be find in var\log\syslog or var\log\messages, but there often is nothing about the crash

---

### Post by tomas.splatch on 2009-05-09
take a look here, in case you are on intel chipset notebook:

[http://ubuntu.igameilive.com/2009/04/ubuntu-904-on-hp-540-part-ii.html]("http://ubuntu.igameilive.com/2009/04/ubuntu-904-on-hp-540-part-ii.html")

---

### Post by mkvnmtr on 2009-05-09
I had the freezing problem when I tried a normal upgrade on my ppc mac. Finally got installed from the live disk. At first on both my machines I froze a time or two. The first thing I do after an install is uninstall all the programs I don't want. There are a lot of them but compiz is one of the things I delete. I have since had no problems with freezing. Got no idea just what was the problem but several times on other installs after deleting stuff I don't use problems were not seen again.

---

### Post by Primefalcon on 2009-05-16
I know this is a week old but whats the common issue?

I am running the new open source driver for ATI
and using
EXT4 (though I have heard of ext3 people having the save issue)

---

### Post by Mirge on 2009-05-16
[http://ubuntuforums.org/showthread.php?t=1135055&page=30](http://ubuntuforums.org/showthread.php?t=1135055&page=30)

30 page thread about freezing in ubuntu... might find more info there.

---

