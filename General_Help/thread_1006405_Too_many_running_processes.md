---
title: "Too many running processes?"
date: 2008-12-09
forum: General Help
---

### Post by chhama on 2008-12-09
Hi, I'm running Ubuntu Hardy and below is the output of my ps-e command. 

  > PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   47 ?        00:00:00 kblockd/0
   48 ?        00:00:00 kblockd/1
   51 ?        00:00:00 kacpid
   52 ?        00:00:00 kacpi_notify
  170 ?        00:00:00 kseriod
  212 ?        00:00:00 pdflush
  213 ?        00:00:00 pdflush
  214 ?        00:00:00 kswapd0
  255 ?        00:00:00 aio/0
  256 ?        00:00:00 aio/1
 1594 ?        00:00:00 ksuspend_usbd
 1595 ?        00:00:00 khubd
 1635 ?        00:00:00 ata/0
 1642 ?        00:00:00 ata/1
 1646 ?        00:00:00 ata_aux
 1649 ?        00:00:00 khpsbpkt
 2377 ?        00:00:00 scsi_eh_0
 2379 ?        00:00:00 scsi_eh_1
 2409 ?        00:00:00 scsi_eh_2
 2411 ?        00:00:00 scsi_eh_3
 2484 ?        00:00:00 knodemgrd_0
 2676 ?        00:00:00 kjournald
 2882 ?        00:00:00 udevd
 2978 ?        00:00:00 kmpathd/0
 2984 ?        00:00:00 kmpathd/1
 3322 ?        00:00:00 btaddconn
 3331 ?        00:00:00 btdelconn
 3375 ?        00:00:00 kmmcd
 3700 ?        00:00:00 kpsmoused
 3721 ?        00:00:00 b43
 5997 ?        00:00:00 portmap
 6126 tty4     00:00:00 getty
 6127 tty5     00:00:00 getty
 6129 tty2     00:00:00 getty
 6132 tty3     00:00:00 getty
 6133 tty6     00:00:00 getty
 6317 ?        00:00:00 acpid
 6361 ?        00:00:00 kondemand/0
 6362 ?        00:00:00 kondemand/1
 6428 ?        00:00:00 syslogd
 6485 ?        00:00:00 dd
 6488 ?        00:00:00 klogd
 6510 ?        00:00:00 dbus-daemon
 6527 ?        00:00:00 NetworkManager
 6541 ?        00:00:00 NetworkManagerD
 6554 ?        00:00:00 system-tools-ba
 6589 ?        00:00:00 sshd
 6646 ?        00:00:00 avahi-daemon
 6647 ?        00:00:00 avahi-daemon
 6680 ?        00:00:00 ypbind
 6842 ?        00:00:00 mysqld_safe
 6884 ?        00:00:00 mysqld
 6886 ?        00:00:00 logger
 6984 ?        00:00:00 cupsd
 7000 ?        00:00:00 dictd
 7258 ?        00:00:00 exim4
 7317 ?        00:00:00 tnslsnr
 7322 ?        00:00:00 oracle
 7324 ?        00:00:00 oracle
 7326 ?        00:00:00 oracle
 7328 ?        00:00:00 oracle
 7330 ?        00:00:00 oracle
 7332 ?        00:00:00 oracle
 7334 ?        00:00:00 oracle
 7336 ?        00:00:00 oracle
 7338 ?        00:00:00 oracle
 7340 ?        00:00:00 oracle
 7342 ?        00:00:00 oracle
 7344 ?        00:00:00 oracle
 7346 ?        00:00:00 oracle
 7348 ?        00:00:00 oracle
 7350 ?        00:00:00 oracle
 7352 ?        00:00:00 oracle
 7358 ?        00:00:00 oracle
 7388 ?        00:00:00 nmbd
 7392 ?        00:00:00 smbd
 7435 ?        00:00:00 smbd
 7486 ?        00:00:00 winbindd
 7491 ?        00:00:00 winbindd
 7538 ?        00:00:00 xinetd
 7570 ?        00:00:00 dhcdbd
 7589 ?        00:00:01 hald
 7592 ?        00:00:00 console-kit-dae
 7654 ?        00:00:00 hald-runner
 7670 ?        00:00:00 hald-addon-inpu
 7681 ?        00:00:00 hald-addon-cpuf
 7682 ?        00:00:00 hald-addon-acpi
 7705 ?        00:00:00 hald-addon-stor
 7718 ?        00:00:00 oracle
 7730 ?        00:00:00 hcid
 7736 ?        00:00:00 oracle
 7745 ?        00:00:00 ipolldevd
 7749 ?        00:00:00 bluetoothd-serv
 7750 ?        00:00:00 bluetoothd-serv
 7756 ?        00:00:00 krfcommd
 7790 ?        00:00:00 gdm
 7791 ?        00:00:00 gdm
 7800 tty7     00:00:27 Xorg
 7826 ?        00:00:00 apache2
 7860 ?        00:00:00 atd
 7874 ?        00:00:00 cron
 7929 ?        00:00:00 apache2
 7931 ?        00:00:00 apache2
 7932 ?        00:00:00 apache2
 7933 ?        00:00:00 apache2
 7934 ?        00:00:00 apache2
 8029 tty1     00:00:00 getty
 8047 ?        00:00:01 gconfd-2
 8049 ?        00:00:00 gnome-keyring-d
 8052 ?        00:00:00 x-session-manag
 8104 ?        00:00:00 seahorse-agent
 8108 ?        00:00:00 dbus-daemon
 8109 ?        00:00:01 gnome-settings-
 8113 ?        00:00:00 pulseaudio
 8120 ?        00:00:00 gconf-helper
 8143 ?        00:00:00 compiz
 8144 ?        00:00:00 gnome-screensav
 8150 ?        00:00:01 gnome-panel
 8151 ?        00:00:01 nautilus
 8164 ?        00:00:00 bonobo-activati
 8181 ?        00:00:00 gvfsd
 8191 ?        00:00:00 gvfs-fuse-daemo
 8219 ?        00:00:08 compiz.real
 8220 ?        00:00:00 bluetooth-apple
 8223 ?        00:00:01 python
 8225 ?        00:00:00 update-notifier
 8230 ?        00:00:00 evolution-alarm
 8231 ?        00:00:00 tracker-applet
 8235 ?        00:00:00 obex-data-serve
 8236 ?        00:00:00 trackerd
 8239 ?        00:00:04 avant-window-na
 8241 ?        00:00:00 notification-da
 8242 ?        00:00:01 python
 8243 ?        00:00:00 python
 8246 ?        00:00:03 python
 8247 ?        00:00:00 python
 8250 ?        00:00:00 nm-applet
 8251 ?        00:00:00 gnome-volume-ma
 8253 ?        00:00:00 gnome-power-man
 8258 ?        00:00:00 gvfsd-burn
 8261 ?        00:00:00 evolution-excha
 8269 ?        00:00:00 gvfsd-trash
 8289 ?        00:00:00 battstat-applet
 8292 ?        00:00:00 trashapplet
 8296 ?        00:00:00 gnome-brightnes
 8299 ?        00:00:00 mixer_applet2
 8329 ?        00:00:00 evolution-data-
 8409 ?        00:00:00 python
 8448 ?        00:00:00 sh
 8449 ?        00:00:00 compiz-decorato
 8451 ?        00:00:00 gtk-window-deco
 8558 ?        00:01:13 firefox
 8613 ?        00:00:00 gtk-gnash
 8629 ?        00:00:00 gtk-gnash
 8630 ?        00:00:00 gtk-gnash
 8673 ?        00:00:00 gnome-terminal
 8675 ?        00:00:00 gnome-pty-helpe
 8676 pts/0    00:00:00 bash
 8696 pts/0    00:00:00 ps

Is this normal? There seems to be a lot of duplicate processes as well. Please help.

---

### Post by binbash on 2008-12-09
I dont know the oracle part, but others are normal

---

### Post by chhama on 2008-12-09
OK. It's quite a lot compared to my ps-e output in gNewSense. So I'm a bit confused. Thanks.

---

