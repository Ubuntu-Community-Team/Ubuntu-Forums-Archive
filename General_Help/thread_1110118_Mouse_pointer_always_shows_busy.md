---
title: "Mouse pointer always shows busy"
date: 2009-03-29
forum: General Help
---

### Post by amadeus266 on 2009-03-29
This started yesterday while I was trying to find an audio player that will play music files from across the network. I installed audacious, didn't work. I installed gxine, segmentation fault. Now my mouse pointer always shows busy except when the pointer is within a window that I am using or the menus. I thought that this would be related to the two programs I installed but even after completely removing them the problem is still there. Even after a reboot.

---

### Post by khelben1979 on 2009-03-29
```
sudo ps -A
```

and post the output here so I and others can see what processes you have which might give you a pain in this matter.

Also if the Gnome enviroment seems to be messed up because of this, then you might consider installing KDE and start using this instead:

```
sudo apt-get install kde
```

---

### Post by amadeus266 on 2009-03-29
As requested
```
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   41 ?        00:00:00 kblockd/0
   44 ?        00:00:00 kacpid
   45 ?        00:00:00 kacpi_notify
  130 ?        00:00:00 kseriod
  170 ?        00:00:00 kswapd0
  211 ?        00:00:00 aio/0
 1504 ?        00:00:00 ata/0
 1510 ?        00:00:00 ata_aux
 1513 ?        00:00:00 ksuspend_usbd
 1519 ?        00:00:00 khubd
 1525 ?        00:00:00 scsi_eh_0
 1531 ?        00:00:01 scsi_eh_1
 2556 ?        00:00:16 mount.ntfs
 2578 ?        00:00:01 loop0
 2590 ?        00:00:00 kjournald
 2864 ?        00:00:00 udevd
 3172 ?        00:00:00 lirc_dev
 3286 ?        00:00:00 kpsmoused
 3396 ?        00:00:00 kgameportd
 4339 ?        00:00:00 dhclient3
 4916 tty4     00:00:00 getty
 4919 tty5     00:00:00 getty
 4925 tty2     00:00:00 getty
 4927 tty3     00:00:00 getty
 4928 tty6     00:00:00 getty
 5092 ?        00:00:00 acpid
 5142 ?        00:00:00 kondemand/0
 5197 ?        00:00:00 syslogd
 5254 ?        00:00:00 dd
 5256 ?        00:00:00 klogd
 5278 ?        00:00:00 dbus-daemon
 5294 ?        00:00:00 NetworkManager
 5308 ?        00:00:00 NetworkManagerD
 5321 ?        00:00:00 system-tools-ba
 5341 ?        00:00:00 avahi-daemon
 5342 ?        00:00:00 avahi-daemon
 5369 ?        00:00:00 atieventsd
 5394 ?        00:00:00 cupsd
 5497 ?        00:00:00 inetd
 5527 ?        00:00:00 nmbd
 5529 ?        00:00:00 smbd
 5576 ?        00:00:00 dhcdbd
 5595 ?        00:00:00 smbd
 5596 ?        00:00:00 hald
 5599 ?        00:00:00 console-kit-dae
 5661 ?        00:00:00 hald-runner
 5684 ?        00:00:00 hald-addon-inpu
 5686 ?        00:00:00 hald-addon-cpuf
 5687 ?        00:00:00 hald-addon-acpi
 5701 ?        00:00:02 hald-addon-stor
 5741 ?        00:00:00 gdm
 5744 ?        00:00:00 gdm
 5748 tty7     00:04:56 Xorg
 5800 ?        00:00:00 atd
 5814 ?        00:00:00 cron
 5895 tty7     00:00:00 Xorg
 5896 ?        00:00:00 miniserv.pl
 5913 tty1     00:00:00 getty
 5933 ?        00:00:01 gconfd-2
 5935 ?        00:00:00 gnome-keyring-d
 5936 ?        00:00:00 x-session-manag
 5989 ?        00:00:00 seahorse-agent
 5993 ?        00:00:00 dbus-daemon
 5994 ?        00:00:02 gnome-settings-
 5998 ?        00:00:11 pulseaudio
 6001 ?        00:00:00 gconf-helper
 6019 ?        00:00:02 nautilus
 6020 ?        00:00:10 gnome-panel
 6022 ?        00:00:00 bonobo-activati
 6023 ?        00:00:00 update-notifier
 6030 ?        00:00:00 bluetooth-apple
 6035 ?        00:00:00 evolution-alarm
 6036 ?        00:00:00 tracker-applet
 6038 ?        00:00:00 trackerd
 6044 ?        00:00:06 nm-applet
 6046 ?        00:00:00 gvfsd
 6047 ?        00:00:00 python
 6049 ?        00:00:00 gnome-volume-ma
 6050 ?        00:00:00 fusion-icon
 6051 ?        00:00:00 gnome-power-man
 6062 ?        00:00:00 gvfs-fuse-daemo
 6073 ?        00:00:00 evolution-excha
 6099 ?        00:00:00 gvfsd-burn
 6105 ?        00:00:00 evolution-data-
 6108 ?        00:00:00 trashapplet
 6110 ?        00:00:07 multiload-apple
 6117 ?        00:00:00 gvfsd-trash
 6173 ?        00:00:00 mixer_applet2
 6217 ?        00:00:48 compiz.real
 6221 ?        00:00:00 sh
 6222 ?        00:00:03 gtk-window-deco
 6359 ?        00:01:29 firefox
 6470 ?        00:00:00 pdflush
 6501 ?        00:00:00 pdflush
 6795 ?        00:00:00 gweather-applet
10898 ?        00:00:00 gnome-terminal
10901 ?        00:00:00 gnome-pty-helpe
10902 pts/0    00:00:00 bash
10931 pts/0    00:00:00 ps

```

Gnome seems to be running just fine.

---

### Post by khelben1979 on 2009-03-30
At the present I myself don't know what you should do. Maybe a reinstallation of the Gnome desktop will solve the problem? (I don't know)

Let's hope someone else here can solve your problem.

---

### Post by Yashiro on 2009-03-30
First open Synaptic and remove the stuff you added.
Use the COMPLETELY REMOVE option.

This issue usually occurs if an app is trying to launch but failing or is launching from a corrupt .desktop file.
You could try searching for hidden files called .desktop and deleting any you do not use or need.

---

### Post by amadeus266 on 2009-03-30
> **Yashiro said:**
> First open Synaptic and remove the stuff you added.
Use the COMPLETELY REMOVE option.

This issue usually occurs if an app is trying to launch but failing or is launching from a corrupt .desktop file.
You could try searching for hidden files called .desktop and deleting any you do not use or need.
I did this just before I posted this thread. Everything seems to be working just fine, but the mouse pointer is always busy when resting on the desktop. I just find it annoying.

---

