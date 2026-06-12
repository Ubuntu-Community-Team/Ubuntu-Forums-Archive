---
title: "intrepid freezes randomly"
date: 2009-03-05
forum: General Help
---

### Post by slouse on 2009-03-05
Dear all, 
I saw a few similar threads, but they did not help me sort out the random freezes I am experiencing since upgrading to ubuntu 8.10. The symptoms are that the system just stops reacting to mouse clicks or keyboard while the mouse cursor can still be moved. This happens often when I just try to start a new program, open the menu and then nothing reacts any more. Sometimes it happens when I try to view a picture. Really random and both in KDE and Gnome.
Yesterday I tried a few things like connecting usb devices while the system was frozen, and I saw the hdd activity lamp flash up, but nothing changed on the screen. After rebooting today, I found some clues in the system log which might be helpful. First of all, the system did register the USB devices I plugged in after freezing, secondly the log suggests a hardware problem, but I never had problems before the upgrade or when I dual boot into windows. Hope someone can help.

Cheers,
slouse

system log excerpt:

2009-03-04 21:54:03	stemma-laptop	NetworkManager	<info>  (wlan0): supplicant connection state change: 7 -> 6 
2009-03-04 21:54:03	stemma-laptop	NetworkManager	<info>  (wlan0): supplicant connection state change: 6 -> 7 
2009-03-04 21:59:43	stemma-laptop	kernel	[ 7547.706012] Uhhuh. NMI received for unknown reason a0 on CPU 0.
2009-03-04 21:59:43	stemma-laptop	kernel	[ 7547.706027] You have some hardware problem, likely on the PCI bus.
2009-03-04 21:59:43	stemma-laptop	kernel	[ 7547.706033] Dazed and confused, but trying to continue
2009-03-04 22:00:01	stemma-laptop	/USR/SBIN/CRON[12018]	(root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
2009-03-04 22:03:14	stemma-laptop	kernel	[ 7757.816181] usb 3-2: new low speed USB device using uhci_hcd and address 2

---

