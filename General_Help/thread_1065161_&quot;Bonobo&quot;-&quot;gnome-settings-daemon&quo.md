---
title: "&quot;Bonobo&quot;-&quot;gnome-settings-daemon&quot;-conflict"
date: 2009-02-09
forum: General Help
---

### Post by wompy on 2009-02-09
I've got a problem when i'm starting the "theme-installation" under applications->other->theme-installation
Hope this is the right translation.

Error:
```
Der Einstellungsverwalter »gnome-settings-daemon« konnte nicht gestartet werden.
Ohne den GNOME-Einstellungsverwalter werden möglicherweise einige Einstellungen nicht wirksam. Dies könnte auf ein Problem mit Bonobo oder einen bereits aktiven, nicht-GNOME- (z.B. KDE-)Einstellungsverwalter hindeuten, der mit GNOME-Einstellungsverwalter in Konflikt geraten ist.
```

It means, that its not able to start gnome-settings-daemon because there's already an active non-gnome settings-manager.

The big problem is the following: i installed a "oxygen"-theme with system->settings->appearance an the "look" changed. But after a few minutes,die theme changed back to the old theme without any obvious reason. After starting again system->settings->appearance the look changed back to "oxygen" but a few moments later i was not able to "click" any links in firefox or some menu-buttons.

I tried to find some bugs relating to this,but i'm not very familar to these things. I hope there's a solution because this spontaneous "change" is getting annoying.

Thanks for your help! Hope my english is not that bad ;-)

wompy

```
ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:05 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   46 ?        00:00:00 kintegrityd/0
   48 ?        00:00:01 kblockd/0
   50 ?        00:00:00 kacpid
   51 ?        00:00:00 kacpi_notify
  133 ?        00:00:00 cqueue
  137 ?        00:00:00 kseriod
  180 ?        00:00:11 kswapd0
  222 ?        00:00:00 aio/0
  689 ?        00:00:00 avahi-publish
 1250 ?        00:00:00 khpsbpkt
 1259 ?        00:00:00 ksuspend_usbd
 1263 ?        00:00:00 khubd
 1286 ?        00:00:06 ata/0
 1289 ?        00:00:00 ata_aux
 1299 ?        00:00:00 knodemgrd_0
 2006 ?        00:00:00 scsi_eh_0
 2008 ?        00:00:13 scsi_eh_1
 2142 ?        00:00:00 scsi_eh_2
 2144 ?        00:00:08 usb-storage
 2202 ?        00:00:03 kjournald
 2399 ?        00:00:00 udevd
 2519 ?        00:00:55 ntos_wq
 2520 ?        00:00:00 ndis_wq
 2521 ?        00:00:00 wrapndis_wq
 2645 ?        00:00:00 pccardd
 2658 ?        00:00:00 pccardd
 2746 ?        00:00:00 kpsmoused
 2781 ?        00:00:00 kgameportd
 4043 ?        00:00:04 artsd
 4384 tty4     00:00:00 getty
 4385 tty5     00:00:00 getty
 4392 tty2     00:00:00 getty
 4393 tty3     00:00:00 getty
 4394 tty6     00:00:00 getty
 4580 ?        00:00:00 acpid
 4627 ?        00:00:09 kondemand/0
 4691 ?        00:00:00 syslogd
 4741 ?        00:00:00 dd
 4743 ?        00:00:00 klogd
 4766 ?        00:00:08 dbus-daemon
 4788 ?        00:00:00 avahi-daemon
 4789 ?        00:00:00 avahi-daemon
 4832 ?        00:00:00 cupsd
 5214 ?        00:00:00 uml_switch
 5317 ?        00:00:00 winbindd
 5329 ?        00:00:00 winbindd
 5340 ?        00:00:12 hald
 5343 ?        00:00:00 console-kit-dae
 5406 ?        00:00:00 hald-runner
 5426 ?        00:00:00 hald-addon-inpu
 5436 ?        00:00:00 hald-addon-cpuf
 5437 ?        00:00:00 hald-addon-acpi
 5451 ?        00:00:17 hald-addon-stor
 5499 ?        00:00:00 bluetoothd
 5504 ?        00:00:00 btaddconn
 5506 ?        00:00:00 btdelconn
 5520 ?        00:00:00 krfcommd
 5554 ?        00:00:08 NetworkManager
 5558 ?        00:00:02 wpa_supplicant
 5561 ?        00:00:00 nm-system-setti
 5592 ?        00:00:00 gdm
 5595 ?        00:00:00 gdm
 5599 tty7     01:05:58 Xorg
 5615 ?        00:00:00 system-tools-ba
 5650 ?        00:00:00 atd
 5678 ?        00:00:00 cron
 5748 ?        00:00:00 dhclient
 5767 tty1     00:00:00 getty
 5865 ?        00:00:00 gnome-keyring-d
 5876 ?        00:00:00 x-session-manag
 5932 ?        00:00:00 dbus-launch
 5933 ?        00:00:41 dbus-daemon
 5936 ?        00:19:46 pulseaudio
 5939 ?        00:00:00 gconf-helper
 5941 ?        00:00:13 gconfd-2
 5947 ?        00:00:00 seahorse-agent
 5951 ?        00:00:00 gnome-keyring-d
 5955 ?        00:00:00 gvfsd
 5957 ?        00:00:00 compiz
 5989 ?        00:00:00 gvfs-fuse-daemo
 6030 ?        00:27:23 compiz.real
 6038 ?        00:02:32 gnome-screensav
 6039 ?        00:00:00 sh
 6040 ?        00:00:00 compiz-decorato
 6042 ?        00:00:14 gtk-window-deco
 6043 ?        00:00:18 gnome-panel
 6045 ?        00:00:23 nautilus
 6047 ?        00:00:00 bonobo-activati
 6055 ?        00:00:00 gvfs-hal-volume
 6057 ?        00:00:00 gvfs-gphoto2-vo
 6060 ?        00:00:00 gvfsd-burn
 6065 ?        00:00:00 gvfsd-trash
 6083 ?        00:00:05 fast-user-switc
 6086 ?        00:00:01 mixer_applet2
 6103 ?        00:00:00 evolution-alarm
 6104 ?        00:00:00 trackerd
 6105 ?        00:00:00 tracker-applet
 6106 ?        00:00:06 python
 6107 ?        00:00:02 update-notifier
 6108 ?        00:00:00 bluetooth-apple
 6113 ?        00:00:00 python
 6114 ?        00:00:00 gnome-do
 6122 ?        00:16:02 python
 6126 ?        00:03:18 python
 6127 ?        00:02:05 gnome-do
 6129 ?        00:00:04 gnome-power-man
 6134 ?        00:00:00 evolution-excha
 6143 ?        00:00:00 evolution-data-
 6405 ?        00:00:08 notification-da
 6534 ?        00:03:55 pidgin
 7060 ?        00:55:17 firefox
10581 ?        00:00:02 python
10724 ?        00:00:00 gnome-pty-helpe
10729 pts/0    00:00:00 bash
12804 ?        00:00:00 su-to-root
12819 ?        00:00:00 gksu
12848 ?        00:00:01 kvpnc
13055 ?        00:00:00 kdeinit
13066 ?        00:00:00 dcopserver
13071 ?        00:00:00 klauncher
13086 ?        00:00:04 kded
13210 ?        00:00:02 knotify
13233 ?        00:00:15 artsd
17510 ?        00:00:00 pdflush
17898 pts/0    00:00:00 ps
21300 ?        00:02:17 amarokapp
21424 ?        00:00:00 kdeinit
21427 ?        00:00:14 dcopserver
21435 ?        00:00:01 klauncher
21449 ?        00:00:02 kded
21500 ?        00:00:00 kio_file
21510 ?        00:00:00 ruby
21511 ?        00:00:00 python
21550 ?        00:00:00 knotify
21592 ?        00:00:24 Tasque
23120 ?        00:01:25 evolution
24010 ?        00:00:00 pdflush
24506 ?        00:00:07 gnome-settings-
26981 ?        00:00:00 kdeinit4
26982 ?        00:00:00 klauncher
27003 ?        00:00:01 kded4
27142 ?        00:00:00 kwalletd
27915 ?        00:00:00 kio_file
28208 ?        00:00:00 gvfsd-http

```

---

