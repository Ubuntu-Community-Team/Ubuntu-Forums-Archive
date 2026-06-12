---
title: "Cannot bring back some minimized windows"
date: 2014-06-30
forum: Desktop Environments
---

### Post by LutraMan on 2014-06-30
I have a new installation of Ubuntu 12.04 that came with Unity.

On the left panel I have links for apps. When I start the app, it gets a small triangle to its left indicating that it's activated.
Some of the apps I've started have changed the triangle to an empty triangle, they are still on, **but clicking on the icon now does nothing**. If I haven't minimized them I can still get to them by moving the other windows to see them beneath them, but if I'd already minimized them, I have no idea how to get them back.

Can anyone explain this behaviour?

---

### Post by JohnnyComeL8ly on 2014-07-06
I haven't used Unity for a while, but you can try [Alt + Tab] to switch between open windows.   If you know the name of the app that is acting up, for example: "crazyapp2;" then try this in a Terminal [Ctrl + Alt + T]  ```
pkill crazyapp2
```  Now, if you don't know the name of the app, you can try ```
ps -A
``` in the terminal and get a good guess as to which one(s) on the list you would like to kill.  For example: 
```
me@mymachine: ~$ ps -A
PID TTY          TIME CMD
    1 ?        00:00:03 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:52 ksoftirqd/0
    5 ?        00:00:00 kworker/0:0H
    7 ?        00:00:14 rcu_sched
    8 ?        00:00:00 rcu_bh
    9 ?        00:00:00 migration/0
   10 ?        00:00:01 watchdog/0
   11 ?        00:00:01 watchdog/1
   12 ?        00:00:00 migration/1
   13 ?        00:22:07 ksoftirqd/1
   15 ?        00:00:00 kworker/1:0H
   16 ?        00:00:00 khelper
   17 ?        00:00:00 kdevtmpfs
   18 ?        00:00:00 netns
   19 ?        00:00:00 writeback
   20 ?        00:00:00 kintegrityd
   21 ?        00:00:00 bioset
   22 ?        00:00:00 kworker/u9:0
   23 ?        00:00:00 kblockd
   24 ?        00:00:00 ata_sff
   25 ?        00:00:00 khubd
   26 ?        00:00:00 md
   27 ?        00:00:00 devfreq_wq
   30 ?        00:00:00 khungtaskd
   31 ?        00:00:02 kswapd0
   32 ?        00:00:00 ksmd
   33 ?        00:00:01 khugepaged
   34 ?        00:00:00 fsnotify_mark
   35 ?        00:00:00 ecryptfs-kthrea
   36 ?        00:00:00 crypto
   48 ?        00:00:00 kthrotld
   51 ?        00:00:00 scsi_eh_0
   52 ?        00:00:00 scsi_eh_1
   53 ?        00:00:00 scsi_eh_2
   54 ?        00:00:00 scsi_eh_3
   77 ?        00:00:00 deferwq
   78 ?        00:00:00 charger_manager
  129 ?        00:00:00 scsi_eh_4
  130 ?        00:00:07 usb-storage
  131 ?        00:00:00 kpsmoused
  139 ?        00:00:02 jbd2/sda1-8
  140 ?        00:00:00 ext4-rsv-conver
  261 ?        00:00:00 upstart-udev-br
  267 ?        00:00:00 systemd-udevd
  299 ?        00:00:00 cfg80211
  315 ?        00:00:00 kworker/u9:1
  442 ?        00:00:00 upstart-file-br
  513 ?        00:00:01 rsyslogd
  555 ?        00:00:00 upstart-socket-
  634 ?        00:00:52 dbus-daemon
  672 ?        00:00:00 ModemManager
  692 ?        00:00:00 bluetoothd
  701 ?        00:00:00 systemd-logind
  726 ?        00:00:00 cupsd
  727 ?        00:00:00 krfcommd
  782 ?        00:01:22 NetworkManager
  833 ?        00:00:00 polkitd
  891 tty4     00:00:00 getty
  896 tty5     00:00:00 getty
  900 tty2     00:00:00 getty
  901 tty3     00:00:00 getty
  905 tty6     00:00:00 getty
  937 ?        00:00:00 cron
 1000 ?        00:00:34 irqbalance
 1044 ?        00:00:00 lightdm
 1049 ?        00:00:20 wpa_supplicant
 1078 tty7     00:23:38 Xorg
 1081 ?        00:00:00 accounts-daemon
 1105 ?        00:00:01 whoopsie
 1121 ?        00:04:50 mysqld
 1138 ?        00:00:03 dnsmasq
 1307 ?        00:00:13 apache2
 1354 ?        00:00:00 kauditd
 1551 ?        00:00:00 timidity
 1557 tty1     00:00:00 getty
 1606 ?        00:00:00 lightdm
 1618 ?        00:00:00 init
 1677 ?        00:00:00 dbus-launch
 1679 ?        00:00:00 dbus-daemon
 1691 ?        00:00:07 dbus-daemon
 1694 ?        00:00:00 ssh-agent
 1699 ?        00:00:00 upstart-event-b
 1720 ?        00:01:15 ibus-daemon
 1733 ?        00:00:00 upstart-file-br
 1734 ?        00:00:01 lxsession
 1737 ?        00:00:04 upstart-dbus-br
 1739 ?        00:00:08 upstart-dbus-br
 1742 ?        00:00:00 gvfsd
 1747 ?        00:00:00 gvfsd-fuse
 1756 ?        00:00:00 ibus-dconf
 1757 ?        00:00:31 ibus-ui-gtk3
 1759 ?        00:00:26 ibus-x11
 1763 ?        00:00:00 at-spi-bus-laun
 1767 ?        00:00:00 dbus-daemon
 1770 ?        00:00:00 at-spi2-registr
 1782 ?        00:00:16 ibus-engine-sim
 1797 ?        00:00:22 openbox
 1800 ?        00:00:54 lxpanel
 1801 ?        00:00:36 pcmanfm
 1808 ?        00:00:00 ssh-agent
 1823 ?        00:00:00 menu-cached
 1830 ?        00:00:02 gvfs-udisks2-vo
 1836 ?        00:01:04 udisksd
 1846 ?        00:00:00 gvfs-afc-volume
 1851 ?        00:00:00 gvfs-gphoto2-vo
 1855 ?        00:00:00 gvfs-mtp-volume
 1865 ?        00:05:59 pulseaudio
 1867 ?        00:00:03 rtkit-daemon
 1871 ?        00:00:00 gconfd-2
 1874 ?        00:00:00 gvfsd-trash
 1890 ?        00:00:00 gvfsd-metadata
 2008 ?        00:00:00 xfconfd
 2758 ?        00:00:00 gvfsd-http
 3190 ?        00:00:00 console-kit-dae
 4035 ?        00:01:15 nm-applet
 4053 ?        00:00:00 gnome-keyring-d
 6380 ?        00:00:00 upowerd
 7080 ?        00:00:00 kworker/1:0
 7249 ?        00:00:07 gnome-terminal
 7253 ?        00:00:00 gnome-pty-helpe
 7254 pts/1    00:00:00 bash
 8035 pts/1    00:00:00 nano
10321 ?        00:00:02 kworker/1:2
10344 ?        00:00:00 dhclient
10452 ?        00:00:06 ntpd
10481 ?        00:00:07 kworker/0:0
12165 ?        00:00:00 apache2
12166 ?        00:00:00 apache2
12167 ?        00:00:00 apache2
12168 ?        00:00:00 apache2
12169 ?        00:00:00 apache2
12406 ?        00:00:00 dconf-service
12410 ?        01:44:38 firefox
12449 ?        00:00:00 apache2
12667 ?        00:00:02 kworker/u8:3
12690 pts/3    00:00:00 bash
12718 ?        00:00:02 kworker/u8:0
12721 ?        00:00:00 kworker/0:1
12736 ?        00:00:01 kworker/u8:1
12744 ?        00:00:00 kworker/u8:2
12747 ?        01:14:57 crazyapp2  <fictitious: only for example>
12758 pts/3    00:00:00 ps
```
You can now also use ```
kill 12747
``` instead of ```
pkill crazyapp2
``` because you know the PID of the app.

I hope this helps you; if not, ask me more.

P.S.  I had the same problem in Unity, but now I use LXDE because my olde PC won't keep up (I can't say what your problem is for sure).

---

