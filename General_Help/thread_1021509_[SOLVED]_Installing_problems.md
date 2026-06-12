---
title: "[SOLVED] Installing problems"
date: 2008-12-25
forum: General Help
---

### Post by winedryhten on 2008-12-25
Hey, I'm having problems installing any programs using the standard Add/Remove thing. It always gives me the error:

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

I'm an absolute beginner so I've tried the standard fixes I could find through google but I'm not sure I understood the instructions fully. Could someone please explain it to me simply?

Sorry if I'm posting in the wrong section.

Thanks

---

### Post by taurus on 2008-12-25
Looks like there is another program running in the background, probably updating is looking update.  Therefore, wait a few minutes and then try to see if you can install your programs again.  Otherwise, open a terminal and look at the output to see which process is running or locking it.

Applications -> Accessories -> Terminal
```
ps -A
```

---

### Post by logos34 on 2008-12-25
use** sudo** apt-get...

(edit: nm, you're using the gui)

---

### Post by winedryhten on 2008-12-25
Which of these is the problem? This has been happening for more than just a few minutes though and the updater doesn't seem to be doing anything. 



  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:03 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   46 ?        00:00:00 kintegrityd/0
   48 ?        00:00:00 kblockd/0
   50 ?        00:00:00 kacpid
   51 ?        00:00:00 kacpi_notify
  132 ?        00:00:00 cqueue
  136 ?        00:00:00 kseriod
  170 ?        00:00:00 pdflush
  171 ?        00:00:00 pdflush
  172 ?        00:00:00 kswapd0
  214 ?        00:00:00 aio/0
 1149 ?        00:00:00 ksuspend_usbd
 1152 ?        00:00:00 khubd
 1172 ?        00:00:04 ata/0
 1175 ?        00:00:00 ata_aux
 1651 ?        00:00:00 scsi_eh_0
 1652 ?        00:00:07 scsi_eh_1
 2032 ?        00:00:02 kjournald
 2206 ?        00:00:00 udevd
 2485 ?        00:00:00 kpsmoused
 2627 ?        00:00:00 pccardd
 2726 ?        00:00:00 ktpacpid
 2825 ?        00:00:00 pccardd
 4222 tty4     00:00:00 getty
 4223 tty5     00:00:00 getty
 4230 tty2     00:00:00 getty
 4231 tty3     00:00:00 getty
 4232 tty6     00:00:00 getty
 4408 ?        00:00:00 acpid
 4450 ?        00:00:00 kondemand/0
 4522 ?        00:00:00 syslogd
 4574 ?        00:00:00 dd
 4576 ?        00:00:00 klogd
 4613 ?        00:00:03 dbus-daemon
 4635 ?        00:00:00 avahi-daemon
 4636 ?        00:00:00 avahi-daemon
 4679 ?        00:00:00 cupsd
 4751 ?        00:00:02 hald
 4754 ?        00:00:00 console-kit-dae
 4817 ?        00:00:00 hald-runner
 4837 ?        00:00:00 hald-addon-inpu
 4847 ?        00:00:00 hald-addon-cpuf
 4848 ?        00:00:00 hald-addon-acpi
 4855 ?        00:00:09 hald-addon-stor
 4905 ?        00:00:00 bluetoothd
 4910 ?        00:00:00 btaddconn
 4912 ?        00:00:00 btdelconn
 4937 ?        00:00:00 krfcommd
 4960 ?        00:00:02 NetworkManager
 4964 ?        00:00:00 wpa_supplicant
 4967 ?        00:00:00 nm-system-setti
 5034 ?        00:00:00 system-tools-ba
 5071 ?        00:00:00 atd
 5099 ?        00:00:00 cron
 5171 tty1     00:00:00 getty
 6477 ?        00:00:00 gdm
 8120 ?        00:00:00 espeak-synthesi
 8123 ?        00:00:00 espeak-synthesi
 8814 ?        00:00:00 gdm
10323 ?        00:00:00 winbindd
10326 ?        00:00:00 winbindd
11125 ?        00:00:00 dhclient
11320 ?        00:00:00 SystemToolsBack
12424 ?        00:00:01 apt-get
12442 ?        00:00:00 sh
12443 ?        00:00:00 dpkg-preconfigu
12449 ?        00:00:00 dpkg-preconfigu <defunct>
12478 ?        00:00:00 hddtemp.config.
12480 ?        00:44:04 whiptail
12780 tty7     00:03:21 Xorg
12817 ?        00:00:00 x-session-manag
12936 ?        00:00:00 ssh-agent
12939 ?        00:00:00 dbus-daemon
12940 ?        00:00:00 dbus-launch
12943 ?        00:00:42 pulseaudio
12946 ?        00:00:00 gconf-helper
12948 ?        00:00:00 gconfd-2
12954 ?        00:00:00 seahorse-agent
12957 ?        00:00:00 gvfsd
12963 ?        00:00:00 gvfs-fuse-daemo
12970 ?        00:00:00 gnome-keyring-d
12971 ?        00:00:01 gnome-settings-
12973 ?        00:00:00 gnome-keyring-d
12975 ?        00:00:00 compiz
13015 ?        00:00:03 gnome-screensav
13049 ?        00:00:12 compiz.real
13050 ?        00:00:00 sh
13051 ?        00:00:00 compiz-decorato
13053 ?        00:00:02 gtk-window-deco
13054 ?        00:00:06 gnome-panel
13056 ?        00:00:03 nautilus
13058 ?        00:00:00 bonobo-activati
13068 ?        00:00:00 gvfs-hal-volume
13070 ?        00:00:00 gvfs-gphoto2-vo
13073 ?        00:00:00 gvfsd-trash
13076 ?        00:00:00 trashapplet
13079 ?        00:00:00 fast-user-switc
13081 ?        00:00:00 gvfsd-burn
13091 ?        00:00:00 mixer_applet2
13102 ?        00:00:00 bluetooth-apple
13103 ?        00:00:00 trackerd
13105 ?        00:00:00 update-notifier
13106 ?        00:00:00 nm-applet
13107 ?        00:00:00 tracker-applet
13116 ?        00:00:00 evolution-alarm
13119 ?        00:00:00 python
13120 ?        00:00:00 gnome-power-man
13134 ?        00:00:00 evolution-excha
13152 ?        00:00:00 evolution-data-
13328 ?        00:00:00 notification-da
13523 ?        00:00:03 pidgin
13545 ?        00:00:01 gnome-terminal
13547 ?        00:00:00 gnome-pty-helpe
13548 pts/1    00:00:00 bash
13575 ?        00:00:20 gnome-system-mo
13606 ?        00:00:00 pidgin
13610 pts/1    00:00:00 ps

---

### Post by ajcham on 2008-12-25
This appears to be the culprit:
```
12424 ? 00:00:01 apt-get
```

---

### Post by taurus on 2008-12-25
> 12424 ? 00:00:01 apt-get
That could be the suspect.

See if you can kill it and then run the update again.

```
sudo kill -9 12424
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by winedryhten on 2008-12-25
Awesome, it's fixed. Thanks guys, I just didn't understand what it meant by locked.

---

### Post by ajcham on 2008-12-25
> **winedryhten said:**
> Awesome, it's fixed. Thanks guys, I just didn't understand what it meant by locked.

No problem - I've had this error *plenty* of times, usually by trying to use apt-get while synaptic is still open.

Also, if you mark the thread as [solved] it makes it more useful for others experiencing the same thing.

---

### Post by MaxIBoy on 2008-12-25
Essentially, a lot of installing programs for Debian-based Linuxes (such as Ubuntu Linux) use a program called "dpkg" as a back-end. In fact, if you download a .deb package manually, the command to install it is "dpkg -i." 

Only one copy of dpkg can run at a time, so if apt-get (which is a program to download installer files and all dependencies, then run dpkg -i on them in the correct order) is running at the time, you won't be able to bring up, for example, synaptic.

---

