---
title: "Stoping Moblock Moblock"
date: 2006-08-02
forum: Desktop Environments
---

### Post by harryhoudini66 on 2006-08-02
I installed Moblock and it ended up not working for me. I thought I had removed it completely but when I shut down, the menu shows it is being stopped. It shows Stoping Moblock Moblock

How do I remove this? I followed the HOWTO: Listed here BTW

---

### Post by harryhoudini66 on 2006-08-03
Bump

---

### Post by harryhoudini66 on 2006-08-03
Bump

---

### Post by harryhoudini66 on 2006-08-04
Bump

---

### Post by Ramses de Norre on 2006-08-04
What's the output of these commands:```
ls -lA /etc/rc2.d|grep -i k*
ls -lA /etc/rcS.d|grep -i k*
ls -lA /etc/rc6.d|grep -i k*
ls -lA /etc/rc0.d|grep -i k*
```

---

### Post by harryhoudini66 on 2006-08-04
harryhoudini66@linux:~$ ls -lA /etc/rc2.d|grep -i k*
total 0
lrwxrwxrwx 1 root root 20 2006-07-12 18:27 K77ntp-server -> ../init.d/ntp-serverlrwxrwxrwx 1 root root 17 2006-07-08 07:34 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx 1 root root 15 2006-07-08 07:34 S10acpid -> ../init.d/acpid
lrwxrwxrwx 1 root root 25 2006-07-08 07:34 S10powernowd.early -> ../init.d/powernowd.early
lrwxrwxrwx 1 root root 18 2006-07-08 07:34 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx 1 root root 15 2006-07-08 07:34 S11klogd -> ../init.d/klogd
lrwxrwxrwx 1 root root 13 2006-07-08 07:34 S13gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root 13 2006-07-08 07:34 S14ppp -> ../init.d/ppp
lrwxrwxrwx 1 root root 15 2006-07-08 07:34 S18hplip -> ../init.d/hplip
lrwxrwxrwx 1 root root 16 2006-07-08 07:34 S19cupsys -> ../init.d/cupsys
lrwxrwxrwx 1 root root 14 2006-07-08 07:34 S20apmd -> ../init.d/apmd
lrwxrwxrwx 1 root root 14 2006-07-08 07:34 S20dbus -> ../init.d/dbus
lrwxrwxrwx 1 root root 18 2006-07-08 07:34 S20festival -> ../init.d/festival
lrwxrwxrwx 1 root root 21 2006-07-08 21:22 S20firestarter -> ../init.d/firestarter
lrwxrwxrwx 1 root root 22 2006-07-08 07:34 S20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx 1 root root 21 2006-07-08 07:34 S20laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx 1 root root 17 2006-07-08 07:34 S20makedev -> ../init.d/makedev
lrwxrwxrwx 1 root root 21 2006-07-30 15:05 S20moblock-nfq -> ../init.d/moblock-nfq
lrwxrwxrwx 1 root root 23 2006-07-08 07:34 S20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx 1 root root 19 2006-07-08 07:34 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx 1 root root 15 2006-07-08 07:34 S20rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root 21 2006-07-08 07:34 S25bluez-utils -> ../init.d/bluez-utils
lrwxrwxrwx 1 root root 15 2006-07-08 07:34 S25mdadm -> ../init.d/mdadm
lrwxrwxrwx 1 root root 17 2006-07-08 07:34 S89anacron -> ../init.d/anacron
lrwxrwxrwx 1 root root 13 2006-07-08 07:34 S89atd -> ../init.d/atd
lrwxrwxrwx 1 root root 14 2006-07-08 07:34 S89cron -> ../init.d/cron
lrwxrwxrwx 1 root root 17 2006-07-08 07:34 S98usplash -> ../init.d/usplash
lrwxrwxrwx 1 root root 22 2006-07-08 07:34 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx 1 root root 18 2006-07-08 07:34 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx 1 root root 19 2006-07-08 07:34 S99rmnologin -> ../init.d/rmnologin
lrwxrwxrwx 1 root root 24 2006-07-08 07:34 S99stop-readahead -> ../init.d/stop-readahead
harryhoudini66@linux:~$




harryhoudini66@linux:~$ ls -lA /etc/rcS.d|grep -i k*
total 4
-rw-r--r-- 1 root root 734 2006-05-23 03:39 README
lrwxrwxrwx 1 root root  21 2006-07-08 07:34 S01mountvirtfs -> ../init.d/mountvirtfs
lrwxrwxrwx 1 root root  19 2006-07-08 07:34 S01readahead -> ../init.d/readahead
lrwxrwxrwx 1 root root  21 2006-07-08 07:34 S02hostname.sh -> ../init.d/hostname.sh
lrwxrwxrwx 1 root root  19 2006-07-08 07:34 S05keymap.sh -> ../init.d/keymap.sh
lrwxrwxrwx 1 root root  41 2006-07-08 07:34 S07linux-restricted-modules-common -> ../init.d/linux-restricted-modules-common
lrwxrwxrwx 1 root root  18 2006-07-08 07:34 S08loopback -> ../init.d/loopback
lrwxrwxrwx 1 root root  14 2006-07-08 07:34 S10udev -> ../init.d/udev
lrwxrwxrwx 1 root root  23 2006-07-08 07:34 S11mountdevsubfs -> ../init.d/mountdevsubfs
lrwxrwxrwx 1 root root  21 2006-07-08 07:34 S13pcmciautils -> ../init.d/pcmciautils
lrwxrwxrwx 1 root root  27 2006-07-08 07:34 S15module-init-tools -> ../init.d/module-init-tools
lrwxrwxrwx 1 root root  19 2006-07-08 07:34 S17procps.sh -> ../init.d/procps.sh
lrwxrwxrwx 1 root root  22 2006-07-08 07:34 S20checkroot.sh -> ../init.d/checkroot.sh
lrwxrwxrwx 1 root root  14 2006-07-08 07:34 S22mtab -> ../init.d/mtab
lrwxrwxrwx 1 root root  16 2006-07-08 07:34 S25brltty -> ../init.d/brltty
lrwxrwxrwx 1 root root  20 2006-07-08 07:34 S25mdadm-raid -> ../init.d/mdadm-raid
lrwxrwxrwx 1 root root  13 2006-07-08 07:34 S26lvm -> ../init.d/lvm
lrwxrwxrwx 1 root root  14 2006-07-08 07:34 S27evms -> ../init.d/evms
lrwxrwxrwx 1 root root  20 2006-07-08 07:34 S30checkfs.sh -> ../init.d/checkfs.sh
lrwxrwxrwx 1 root root  21 2006-07-08 07:34 S35mountall.sh -> ../init.d/mountall.sh
lrwxrwxrwx 1 root root  27 2006-07-08 07:34 S39readahead-desktop -> ../init.d/readahead-desktop
lrwxrwxrwx 1 root root  20 2006-07-08 07:34 S40networking -> ../init.d/networking
lrwxrwxrwx 1 root root  16 2006-07-08 07:34 S40pcmcia -> ../init.d/pcmcia
lrwxrwxrwx 1 root root  20 2006-07-08 07:34 S45waitnfs.sh -> ../init.d/waitnfs.sh
lrwxrwxrwx 1 root root  20 2006-07-08 07:34 S50hwclock.sh -> ../init.d/hwclock.sh
lrwxrwxrwx 1 root root  19 2006-07-08 07:34 S55dns-clean -> ../init.d/dns-clean
lrwxrwxrwx 1 root root  18 2006-07-08 07:34 S55pppd-dns -> ../init.d/pppd-dns
lrwxrwxrwx 1 root root  16 2006-07-08 07:34 S70screen -> ../init.d/screen
lrwxrwxrwx 1 root root  20 2006-07-08 07:34 S70x11-common -> ../init.d/x11-common
lrwxrwxrwx 1 root root  21 2006-07-08 07:34 S80bootmisc.sh -> ../init.d/bootmisc.sh
lrwxrwxrwx 1 root root  17 2006-07-08 07:34 S85urandom -> ../init.d/urandom
lrwxrwxrwx 1 root root  27 2006-07-08 07:34 S90console-screen.sh -> ../init.d/console-screen.sh
harryhoudini66@linux:~$


harryhoudini66@linux:~$ ls -lA /etc/rc6.d|grep -i k*
total 0
lrwxrwxrwx 1 root root 13 2006-07-08 07:34 K01gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root 17 2006-07-08 07:34 K01usplash -> ../init.d/usplash
lrwxrwxrwx 1 root root 17 2006-07-08 07:34 K11anacron -> ../init.d/anacron
lrwxrwxrwx 1 root root 13 2006-07-08 07:34 K11atd -> ../init.d/atd
lrwxrwxrwx 1 root root 14 2006-07-08 07:34 K11cron -> ../init.d/cron
lrwxrwxrwx 1 root root 16 2006-07-08 07:34 K19cupsys -> ../init.d/cupsys
lrwxrwxrwx 1 root root 22 2006-07-08 07:34 K20acpi-support -> ../init.d/acpi-support
lrwxrwxrwx 1 root root 14 2006-07-08 07:34 K20apmd -> ../init.d/apmd
lrwxrwxrwx 1 root root 20 2006-07-08 07:34 K20bittorrent -> ../init.d/bittorrentlrwxrwxrwx 1 root root 14 2006-07-08 07:34 K20dbus -> ../init.d/dbus
lrwxrwxrwx 1 root root 18 2006-07-08 07:34 K20festival -> ../init.d/festival
lrwxrwxrwx 1 root root 21 2006-07-08 21:22 K20firestarter -> ../init.d/firestarter
lrwxrwxrwx 1 root root 22 2006-07-08 07:34 K20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx 1 root root 21 2006-07-08 07:34 K20laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx 1 root root 17 2006-07-08 07:34 K20makedev -> ../init.d/makedev
lrwxrwxrwx 1 root root 21 2006-07-30 15:05 K20moblock-nfq -> ../init.d/moblock-nfq
lrwxrwxrwx 1 root root 23 2006-07-08 07:34 K20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx 1 root root 19 2006-07-08 07:34 K20powernowd -> ../init.d/powernowd
lrwxrwxrwx 1 root root 15 2006-07-08 07:34 K20rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root 15 2006-07-08 07:34 K21acpid -> ../init.d/acpid
lrwxrwxrwx 1 root root 15 2006-07-08 07:34 K21hplip -> ../init.d/hplip
lrwxrwxrwx 1 root root 20 2006-07-08 07:34 K25hwclock.sh -> ../init.d/hwclock.shlrwxrwxrwx 1 root root 15 2006-07-08 07:34 K25mdadm -> ../init.d/mdadm
lrwxrwxrwx 1 root root 20 2006-07-08 07:34 K50alsa-utils -> ../init.d/alsa-utilslrwxrwxrwx 1 root root 21 2006-07-08 07:34 K74bluez-utils -> ../init.d/bluez-utils
lrwxrwxrwx 1 root root 13 2006-07-08 07:34 K86ppp -> ../init.d/ppp
lrwxrwxrwx 1 root root 16 2006-07-08 07:34 K88pcmcia -> ../init.d/pcmcia
lrwxrwxrwx 1 root root 21 2006-07-08 07:34 K88pcmciautils -> ../init.d/pcmciautils
lrwxrwxrwx 1 root root 15 2006-07-08 07:34 K89klogd -> ../init.d/klogd
lrwxrwxrwx 1 root root 18 2006-07-08 07:34 K90sysklogd -> ../init.d/sysklogd
lrwxrwxrwx 1 root root 41 2006-07-08 07:34 S01linux-restricted-modules-common -> ../init.d/linux-restricted-modules-common
lrwxrwxrwx 1 root root 18 2006-07-08 07:34 S20sendsigs -> ../init.d/sendsigs
lrwxrwxrwx 1 root root 17 2006-07-08 07:34 S30urandom -> ../init.d/urandom
lrwxrwxrwx 1 root root 22 2006-07-08 07:34 S31umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx 1 root root 20 2006-07-08 07:34 S35networking -> ../init.d/networkinglrwxrwxrwx 1 root root 18 2006-07-08 07:34 S40umountfs -> ../init.d/umountfs
lrwxrwxrwx 1 root root 14 2006-07-08 07:34 S49evms -> ../init.d/evms
lrwxrwxrwx 1 root root 13 2006-07-08 07:34 S50lvm -> ../init.d/lvm
lrwxrwxrwx 1 root root 20 2006-07-08 07:34 S50mdadm-raid -> ../init.d/mdadm-raidlrwxrwxrwx 1 root root 20 2006-07-08 07:34 S60umountroot -> ../init.d/umountrootlrwxrwxrwx 1 root root 16 2006-07-08 07:34 S90reboot -> ../init.d/reboot
harryhoudini66@linux:~$



harryhoudini66@linux:~$ ls -lA /etc/rc0.d|grep -i k*
total 0
lrwxrwxrwx 1 root root 13 2006-07-08 07:34 K01gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root 17 2006-07-08 07:34 K01usplash -> ../init.d/usplash
lrwxrwxrwx 1 root root 17 2006-07-08 07:34 K11anacron -> ../init.d/anacron
lrwxrwxrwx 1 root root 13 2006-07-08 07:34 K11atd -> ../init.d/atd
lrwxrwxrwx 1 root root 14 2006-07-08 07:34 K11cron -> ../init.d/cron
lrwxrwxrwx 1 root root 16 2006-07-08 07:34 K19cupsys -> ../init.d/cupsys
lrwxrwxrwx 1 root root 22 2006-07-08 07:34 K20acpi-support -> ../init.d/acpi-support
lrwxrwxrwx 1 root root 14 2006-07-08 07:34 K20apmd -> ../init.d/apmd
lrwxrwxrwx 1 root root 20 2006-07-08 07:34 K20bittorrent -> ../init.d/bittorrentlrwxrwxrwx 1 root root 14 2006-07-08 07:34 K20dbus -> ../init.d/dbus
lrwxrwxrwx 1 root root 18 2006-07-08 07:34 K20festival -> ../init.d/festival
lrwxrwxrwx 1 root root 21 2006-07-08 21:22 K20firestarter -> ../init.d/firestarter
lrwxrwxrwx 1 root root 22 2006-07-08 07:34 K20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx 1 root root 21 2006-07-08 07:34 K20laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx 1 root root 17 2006-07-08 07:34 K20makedev -> ../init.d/makedev
lrwxrwxrwx 1 root root 21 2006-07-30 15:05 K20moblock-nfq -> ../init.d/moblock-nfq
lrwxrwxrwx 1 root root 23 2006-07-08 07:34 K20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx 1 root root 19 2006-07-08 07:34 K20powernowd -> ../init.d/powernowd
lrwxrwxrwx 1 root root 15 2006-07-08 07:34 K20rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root 15 2006-07-08 07:34 K21acpid -> ../init.d/acpid
lrwxrwxrwx 1 root root 15 2006-07-08 07:34 K21hplip -> ../init.d/hplip
lrwxrwxrwx 1 root root 20 2006-07-08 07:34 K25hwclock.sh -> ../init.d/hwclock.shlrwxrwxrwx 1 root root 15 2006-07-08 07:34 K25mdadm -> ../init.d/mdadm
lrwxrwxrwx 1 root root 20 2006-07-08 07:34 K50alsa-utils -> ../init.d/alsa-utilslrwxrwxrwx 1 root root 21 2006-07-08 07:34 K74bluez-utils -> ../init.d/bluez-utils
lrwxrwxrwx 1 root root 13 2006-07-08 07:34 K86ppp -> ../init.d/ppp
lrwxrwxrwx 1 root root 16 2006-07-08 07:34 K88pcmcia -> ../init.d/pcmcia
lrwxrwxrwx 1 root root 21 2006-07-08 07:34 K88pcmciautils -> ../init.d/pcmciautils
lrwxrwxrwx 1 root root 15 2006-07-08 07:34 K89klogd -> ../init.d/klogd
lrwxrwxrwx 1 root root 18 2006-07-08 07:34 K90sysklogd -> ../init.d/sysklogd
lrwxrwxrwx 1 root root 41 2006-07-08 07:34 S01linux-restricted-modules-common -> ../init.d/linux-restricted-modules-common
lrwxrwxrwx 1 root root 18 2006-07-08 07:34 S20sendsigs -> ../init.d/sendsigs
lrwxrwxrwx 1 root root 17 2006-07-08 07:34 S30urandom -> ../init.d/urandom
lrwxrwxrwx 1 root root 22 2006-07-08 07:34 S31umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx 1 root root 20 2006-07-08 07:34 S35networking -> ../init.d/networkinglrwxrwxrwx 1 root root 18 2006-07-08 07:34 S40umountfs -> ../init.d/umountfs
lrwxrwxrwx 1 root root 14 2006-07-08 07:34 S49evms -> ../init.d/evms
lrwxrwxrwx 1 root root 13 2006-07-08 07:34 S50lvm -> ../init.d/lvm
lrwxrwxrwx 1 root root 20 2006-07-08 07:34 S50mdadm-raid -> ../init.d/mdadm-raidlrwxrwxrwx 1 root root 20 2006-07-08 07:34 S60umountroot -> ../init.d/umountrootlrwxrwxrwx 1 root root 14 2006-07-08 07:34 S90halt -> ../init.d/halt
harryhoudini66@linux:~$

---

### Post by harryhoudini66 on 2006-08-04
After reading the results of what you asked me to do, it guided me to what I needed to do. I deleted the reference to moblock in each folder.

Thank you so much for your help.

---

