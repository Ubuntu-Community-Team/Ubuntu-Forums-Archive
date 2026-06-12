---
title: "Xubuntu lost window decorations"
date: 2013-11-24
forum: Desktop Environments
---

### Post by cmcanulty on 2013-11-24
same issue here installed xubuntu 13.10 yesterday. Today min max close all gone and this fix didn't work. I am trying xubuntu to keep it simple not have problems

---

### Post by Toz on 2013-11-24
> **cmcanulty said:**
> same issue here installed xubuntu 13.10 yesterday. Today min max close all gone and this fix didn't work. I am trying xubuntu to keep it simple not have problems

Is xfwm4 running?
```
ps -ef | grep xfwm4 | grep -v grep
```

If not, try starting it:
```
xfwm4
```

Do you get any error messages?

---

### Post by cmcanulty on 2013-11-24
```
cmcanulty@gateway:~$ ps -ef | grep -v grep
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  2 18:37 ?        00:00:02 /sbin/init
root         2     0  0 18:37 ?        00:00:00 [kthreadd]
root         3     2  0 18:37 ?        00:00:00 [ksoftirqd/0]
root         4     2  0 18:37 ?        00:00:00 [kworker/0:0]
root         5     2  0 18:37 ?        00:00:00 [kworker/0:0H]
root         6     2  0 18:37 ?        00:00:00 [kworker/u2:0]
root         7     2  0 18:37 ?        00:00:00 [migration/0]
root         8     2  0 18:37 ?        00:00:00 [rcu_bh]
root         9     2  0 18:37 ?        00:00:00 [rcuob/0]
root        10     2  0 18:37 ?        00:00:00 [rcu_sched]
root        11     2  0 18:37 ?        00:00:00 [rcuos/0]
root        12     2  0 18:37 ?        00:00:00 [watchdog/0]
root        13     2  0 18:37 ?        00:00:00 [khelper]
root        14     2  0 18:37 ?        00:00:00 [kdevtmpfs]
root        15     2  0 18:37 ?        00:00:00 [netns]
root        16     2  0 18:37 ?        00:00:00 [writeback]
root        17     2  0 18:37 ?        00:00:00 [kintegrityd]
root        18     2  0 18:37 ?        00:00:00 [bioset]
root        19     2  0 18:37 ?        00:00:00 [kworker/u3:0]
root        20     2  0 18:37 ?        00:00:00 [kblockd]
root        21     2  0 18:37 ?        00:00:00 [ata_sff]
root        22     2  0 18:37 ?        00:00:00 [khubd]
root        23     2  0 18:37 ?        00:00:00 [md]
root        24     2  0 18:37 ?        00:00:00 [devfreq_wq]
root        25     2  0 18:37 ?        00:00:00 [kworker/0:1]
root        26     2  0 18:37 ?        00:00:00 [khungtaskd]
root        27     2  0 18:37 ?        00:00:00 [kswapd0]
root        28     2  0 18:37 ?        00:00:00 [ksmd]
root        29     2  0 18:37 ?        00:00:00 [khugepaged]
root        30     2  0 18:37 ?        00:00:00 [fsnotify_mark]
root        31     2  0 18:37 ?        00:00:00 [ecryptfs-kthrea]
root        32     2  0 18:37 ?        00:00:00 [crypto]
root        44     2  0 18:37 ?        00:00:00 [kthrotld]
root        45     2  0 18:37 ?        00:00:00 [kworker/u2:1]
root        46     2  0 18:37 ?        00:00:00 [kworker/0:2]
root        47     2  0 18:37 ?        00:00:00 [kworker/u2:2]
root        66     2  0 18:37 ?        00:00:00 [deferwq]
root        67     2  0 18:37 ?        00:00:00 [charger_manager]
root       112     2  0 18:37 ?        00:00:00 [firewire]
root       113     2  0 18:37 ?        00:00:00 [kworker/0:3]
root       114     2  0 18:37 ?        00:00:00 [scsi_eh_0]
root       115     2  0 18:37 ?        00:00:00 [scsi_eh_1]
root       116     2  0 18:37 ?        00:00:00 [kworker/u2:3]
root       117     2  0 18:37 ?        00:00:00 [kworker/u2:4]
root       128     2  0 18:37 ?        00:00:00 [jbd2/sda1-8]
root       129     2  0 18:37 ?        00:00:00 [ext4-rsv-conver]
root       130     2  0 18:37 ?        00:00:00 [ext4-unrsv-conv]
root       253     1  0 18:37 ?        00:00:00 upstart-udev-bridge --daemon
root       258     1  0 18:37 ?        00:00:00 /lib/systemd/systemd-udevd --daemon
root       314     2  0 18:37 ?        00:00:00 [tifm]
root       321     2  0 18:37 ?        00:00:00 [edac-poller]
root       325     2  0 18:37 ?        00:00:00 [kpsmoused]
root       326     2  0 18:37 ?        00:00:00 [cfg80211]
root       337     2  0 18:37 ?        00:00:00 [ttm_swap]
root       338     2  0 18:37 ?        00:00:00 [kworker/0:4]
root       339     2  0 18:37 ?        00:00:00 [pccardd]
root       352     2  0 18:37 ?        00:00:00 [kworker/0:5]
root       403     1  0 18:37 ?        00:00:00 upstart-socket-bridge --daemon
root       447     2  0 18:37 ?        00:00:00 [kworker/u3:1]
root       533     2  0 18:37 ?        00:00:00 [jbd2/sda2-8]
root       534     2  0 18:37 ?        00:00:00 [ext4-rsv-conver]
root       535     2  0 18:37 ?        00:00:00 [ext4-unrsv-conv]
102        585     1  0 18:37 ?        00:00:00 dbus-daemon --system --fork
root       653     1  0 18:37 ?        00:00:00 /usr/sbin/modem-manager
syslog     663     1  0 18:37 ?        00:00:00 rsyslogd -c5
root       668     1  0 18:37 ?        00:00:00 /lib/systemd/systemd-logind
root       683     1  0 18:37 ?        00:00:00 /usr/sbin/bluetoothd
root       708     2  0 18:37 ?        00:00:00 [krfcommd]
root       721     1  0 18:37 ?        00:00:00 upstart-file-bridge --daemon
avahi      733     1  0 18:37 ?        00:00:00 avahi-daemon: running [gateway.local]
avahi      736   733  0 18:37 ?        00:00:00 avahi-daemon: chroot helper
root       761     1  0 18:37 ?        00:00:00 /usr/sbin/cupsd -F
root       788     1  0 18:37 ?        00:00:00 NetworkManager
root       827     1  0 18:37 ?        00:00:00 /usr/lib/policykit-1/polkitd --no-debug
root       833     1  0 18:37 tty4     00:00:00 /sbin/getty -8 38400 tty4
root       840     1  0 18:37 tty5     00:00:00 /sbin/getty -8 38400 tty5
root       852     1  0 18:37 tty2     00:00:00 /sbin/getty -8 38400 tty2
root       854     1  0 18:37 tty3     00:00:00 /sbin/getty -8 38400 tty3
root       861     1  0 18:37 tty6     00:00:00 /sbin/getty -8 38400 tty6
root       914     1  0 18:37 ?        00:00:00 /usr/sbin/cups-browsed
root       929     1  0 18:37 ?        00:00:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root       931     2  0 18:37 ?        00:00:00 [irq/22-b43]
root       933     1  0 18:37 ?        00:00:00 cron
root       944     1  0 18:37 ?        00:00:00 /sbin/wpa_supplicant -B -P /run/sendsigs.omit.d/wpasupplicant.pid -u -s -O /var/run/wpa_supplicant
root       958     1  0 18:37 ?        00:00:00 lightdm
root       976     1  0 18:37 ?        00:00:00 /usr/lib/accountsservice/accounts-daemon
root       981     1  0 18:37 tty1     00:00:00 /sbin/getty -8 38400 tty1
whoopsie   991     1  0 18:37 ?        00:00:00 whoopsie
root      1008   958  1 18:37 tty7     00:00:01 /usr/bin/X -core :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
root      1014   958  0 18:37 ?        00:00:00 lightdm --session-child 12 15
root      1017     2  0 18:37 ?        00:00:00 [kauditd]
1000      1031  1014  0 18:37 ?        00:00:00 init --user
1000      1081  1031  0 18:37 ?        00:00:00 /bin/sh -e /proc/self/fd/9
1000      1082  1081  0 18:37 ?        00:00:00 sleep 60
1000      1084  1031  0 18:37 ?        00:00:00 ssh-agent
1000      1086  1031  0 18:37 ?        00:00:00 dbus-daemon --fork --session --address=unix:abstract=/tmp/dbus-VGgzprxDlr
1000      1092  1031  0 18:37 ?        00:00:00 upstart-event-bridge
1000      1105  1031  0 18:37 ?        00:00:00 /bin/sh /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xserverrc
1000      1113  1105  0 18:37 ?        00:00:00 xfce4-session
root      1114   788  0 18:37 ?        00:00:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /run/sendsigs.omit.d/network-manager.dhclient-eth0.pid -lf /var/lib/NetworkManager/dhclient-c06a90d1-f75e-486b-9fab-9fc56649f615-eth0.lease -cf /var/lib/NetworkManager/dhclient-eth0.conf eth0
1000      1116  1031  0 18:37 ?        00:00:00 upstart-file-bridge --daemon --user
1000      1118  1031  0 18:37 ?        00:00:00 upstart-dbus-bridge --daemon --system --user --bus-name system
1000      1120  1031  0 18:37 ?        00:00:00 upstart-dbus-bridge --daemon --session --user --bus-name session
1000      1124  1031  0 18:37 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xfce4/xfconf/xfconfd
1000      1129  1031  0 18:37 ?        00:00:00 gnome-keyring-daemon --start
1000      1134  1113  0 18:37 ?        00:00:00 xfwm4 --replace --display :0.0 --sm-client-id 23cbc66a7-fb36-48ee-8a5a-9d471819c520
1000      1136  1113  0 18:37 ?        00:00:00 Thunar --sm-client-id 2d5128cd3-de79-433e-b58b-091e3ed92930 --daemon
1000      1137  1113  0 18:37 ?        00:00:00 xfce4-panel --display :0.0 --sm-client-id 208a09c85-961b-4dbf-87d3-db2c5b05c7ed
1000      1139  1113  0 18:37 ?        00:00:00 xfdesktop --display :0.0 --sm-client-id 23a87c0b6-d037-41ee-a577-f3f7993a7310
1000      1140  1031  0 18:37 ?        00:00:00 xfsettingsd --display :0.0 --sm-client-id 221d9ee53-bfac-4982-b73c-54bedc0f8d2b
1000      1143  1031  0 18:37 ?        00:00:00 /usr/lib/gvfs/gvfsd
1000      1148  1031  0 18:37 ?        00:00:00 /usr/lib/gvfs//gvfsd-fuse -f /run/user/1000/gvfs
nobody    1159   788  0 18:37 ?        00:00:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/NetworkManager/dnsmasq.pid --listen-address=127.0.1.1 --conf-file=/var/run/NetworkManager/dnsmasq.conf --cache-size=0 --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
1000      1168  1031  0 18:37 ?        00:00:00 xfce4-power-manager --restart --sm-client-id 2bd79a2ab-0f5e-44d0-9e86-cc00c989dc2a
1000      1196  1031  0 18:37 ?        00:00:00 zeitgeist-datahub
1000      1207  1031  0 18:37 ?        00:00:00 nm-applet
1000      1214  1137  0 18:37 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libsystray.so 4 10485799 systray Notification Area Area where notification icons appear 
1000      1215  1031  0 18:37 ?        00:00:00 update-notifier
1000      1217  1137  0 18:37 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xfce4/panel-plugins/xfce4-indicator-plugin  5 10485800 indicator Indicator Plugin An indicator of something that needs your attention on the desktop 
1000      1225  1031  0 18:37 ?        00:00:00 xscreensaver -no-splash
1000      1228  1137  0 18:37 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libactions.so 9 10485801 actions Action Buttons Log out, lock or other system actions 
1000      1231  1031  0 18:37 ?        00:00:00 /usr/bin/python /usr/share/system-config-printer/applet.py
1000      1233  1031  0 18:37 ?        00:00:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
1000      1235  1031  0 18:37 ?        00:00:00 xfce4-power-manager
1000      1236  1031  0 18:37 ?        00:00:00 xfce4-volumed
1000      1239  1031  0 18:37 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xfce4/notifyd/xfce4-notifyd
1000      1241  1137  0 18:37 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libthunar-tpa.so 34 10485805 thunar-tpa Trash Applet Display the trash can 
1000      1244  1031  0 18:37 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.10 /org/gtk/gvfs/exec_spaw/0
1000      1254  1031  0 18:37 ?        00:00:00 /usr/bin/pulseaudio --start --log-target=syslog
rtkit     1256     1  0 18:37 ?        00:00:00 /usr/lib/rtkit/rtkit-daemon
root      1261     1  0 18:37 ?        00:00:00 /usr/lib/upower/upowerd
1000      1269  1031  0 18:37 ?        00:00:00 /usr/lib/x86_64-linux-gnu/tumbler-1/tumblerd
1000      1275  1031  0 18:37 ?        00:00:00 /usr/bin/zeitgeist-daemon
1000      1362  1031  0 18:37 ?        00:00:00 /usr/lib/x86_64-linux-gnu/zeitgeist-fts
root      1380     1  0 18:37 ?        00:00:00 /usr/sbin/winbindd -F
1000      1400  1031  0 18:37 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-application-service
1000      1402  1031  0 18:37 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-sound/indicator-sound-service
1000      1412  1031  0 18:37 ?        00:00:00 /usr/lib/dconf/dconf-service
root      1475  1380  0 18:37 ?        00:00:00 /usr/sbin/winbindd -F
1000      1560  1031  0 18:37 ?        00:00:00 /usr/lib/at-spi2-core/at-spi-bus-launcher
1000      1564  1560  0 18:37 ?        00:00:00 /bin/dbus-daemon --config-file=/etc/at-spi2/accessibility.conf --nofork --print-address 3
1000      1567  1031  0 18:37 ?        00:00:00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
1000      1573  1362  0 18:37 ?        00:00:00 /bin/cat
1000      1583  1031  0 18:37 ?        00:00:00 /usr/lib/x86_64-linux-gnu/gconf/gconfd-2
1000      1585  1031  0 18:37 ?        00:00:00 /usr/lib/gvfs/gvfs-udisks2-volume-monitor
root      1588     1  0 18:37 ?        00:00:00 /usr/lib/udisks2/udisksd --no-debug
1000      1597  1031  0 18:37 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
1000      1601  1031  0 18:37 ?        00:00:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
1000      1607  1031  0 18:37 ?        00:00:00 /usr/lib/gvfs/gvfs-mtp-volume-monitor
1000      1633  1031  0 18:37 ?        00:00:00 /usr/bin/xfce4-terminal
1000      1637  1633  0 18:38 ?        00:00:00 gnome-pty-helper
1000      1638  1633  0 18:38 pts/3    00:00:00 bash
root      1688   788  0 18:38 ?        00:00:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /run/sendsigs.omit.d/network-manager.dhclient-wlan0.pid -lf /var/lib/NetworkManager/dhclient-94a25c77-dc42-4c84-9de7-1afc05c3b1a9-wlan0.lease -cf /var/lib/NetworkManager/dhclient-wlan0.conf wlan0
1000      1756  1638  0 18:38 pts/3    00:00:00 ps -ef
cmcanulty@gateway:~$ xf
xf: command not found
cmcanulty@gateway:~$ xfwm4
xfwm4-Message: Another Window Manager (Xfwm4) is already running on screen :0.0
xfwm4-Message: To replace the current window manager, try "--replace"

(xfwm4:1786): xfwm4-WARNING **: Could not find a screen to manage, exiting
cmcanulty@gateway:~$ xfwm4 --replace
Waiting for current window manager (Xfwm4) on screen :0.0 to exit: Done
```

---

### Post by Toz on 2013-11-24
Which Window Manager theme are you using (Settings Manager -> Window Manager -> Style)?

If you change this theme, does it make a difference?

---

### Post by vasa1 on 2013-11-24
> **Toz said:**
> Is xfwm4 running?
```
ps -ef | grep xfwm4 | grep -v grep
```
...
```
pgrep -l xfwm4
``` is another way. For example (because I use Openbox instead of xfwm4),
```
[07:41 AM] ~ $ pgrep -l openbox
1219 openbox
[07:41 AM] ~ $ pgrep -l xfc
1205 xfce4-session
1216 xfconfd
1221 xfce4-panel
1246 xfce4-power-man
[07:41 AM] ~ $ 

```

---

### Post by vasa1 on 2013-11-24
I think that ```
ps -ef | grep xfwm4 | grep -v grep
``` did not work as intended because "|" doesn't run in the order present in the code but *simultaneously*, if I understand correctly and *may* result in confusion on occasion. There's more reading on "|" being simultaneous [here]("http://unix.stackexchange.com/q/37508/15760").

Incidentally, cmcanulty's code "proves" something else: that having multiple desktops and then running the lighter desktop doesn't give the full benefit (in terms of "lightness") as running a computer with just the lighter desktop present. See process **1275** in cmcanulty's ps output. I understand that such a process isn't present in vanilla Xubuntu.

---

### Post by Toz on 2013-11-24
> **vasa1 said:**
> ```
pgrep -l xfwm4
``` is another way. For example (because I use Openbox instead of xfwm4),
```
[07:41 AM] ~ $ pgrep -l openbox
1219 openbox
[07:41 AM] ~ $ pgrep -l xfc
1205 xfce4-session
1216 xfconfd
1221 xfce4-panel
1246 xfce4-power-man
[07:41 AM] ~ $ 

```

Thanks. This old dog learns something new again. :)

---

### Post by Toz on 2013-11-24
> **vasa1 said:**
> Incidentally, the OP's code "proves" something else: that having multiple desktops and then running the lighter desktop doesn't give the full benefit (in terms of "lightness") as running a computer with just the lighter desktop present. See process **1275** in OP's ps output. I understand that such a process isn't present in vanilla Xubuntu.
At one point in time, in one of the betas, I noticed that zietgeist got installed. 
> Zeitgeist is a service which logs the user's activities and events (files
 opened, websites visited, conversations held with other people, etc.) and
 makes the relevant information available to other applications.
 .
 It serves as a comprehensive activity log and also makes it possible to
 determine relationships between items based on usage patterns.
 .
 This metapackage depends on the Zeitgeist engine and a set of packages
 (such as data providers) commonly used together with it.
...it freaked me out and I removed it and catfish (dependency). However, in the final release, its not part of the [manifest]("http://cdimage.ubuntu.com/xubuntu/releases/13.10/release/xubuntu-13.10-desktop-amd64.manifest") so I'm guessing that it was removed. Although it brings up an interesting question about which version of 13.10 was installed (beta vs final), I don't think the package itself would cause the issue the OP is facing. The other processes all look normal for a Xubuntu install.

---

### Post by vasa1 on 2013-11-24
> **Toz said:**
> ..., I don't think the package itself would cause the issue the OP is facing. The other processes all look normal for a Xubuntu install.
It is a side-issue and most probably unrelated to cmcanulty's losing the window decorations but I mentioned it because troubleshooting *may* be different for a standalone Xubuntu versus xubuntu-desktop running on a computer with other desktops present; some processes supposedly unique to other desktops may *leak* over with unexpected results. Pure speculation but seeing that process put it in my mind!

---

### Post by cmcanulty on 2013-11-25
I only had xubuntu. After this problem I tried adding xfce4 to see if that would give me an option without this problem but it did nothing. In fact I don't even get an option to log in to xfce4 like I should. I am using clearlooks-phenix-master. Though I tried others and it makes no difference.I didn't use a beta for xubuntu

```
cmcanulty@gateway:~$ pgrep -l xfwm4
1134 xfwm4
cmcanulty@gateway:~$ 
```

---

### Post by Toz on 2013-11-25
> **cmcanulty said:**
> . I am using clearlooks-phenix-master. Though I tried others and it makes no difference.
Did you try other Window Manager themes (Settings Manager -> Window Manager) or Appearance themes (Settings Manager -> Appearance)? It is the Window Manager theme you would want to change.

Can you change both the Appearance and the Window Manager themes to Greybird and see if that fixes the problem?

> 
```
cmcanulty@gateway:~$ pgrep -l xfwm4
1134 xfwm4
cmcanulty@gateway:~$ 
```
It is running.....

Any chance you could post a screenshot? What type of video card do you have and which driver are you using?

---

### Post by cmcanulty on 2013-11-26
this is not 
an uncommon problem many search results but nothing has worked for me I changed both to greybird, no difference. Here is the output this happened to me once on classic and required  a whole reinstall. sure would like to avoid that! thanks
```
cmcanulty@gateway:~$ pgrep -l xfwm4
1131 xfwm4
cmcanulty@gateway:~$
```

---

### Post by Toz on 2013-11-26
Things to report back on:

1. Video card and drivers:
```
lspci -k | grep -iA2 VGA
```

2. Attach your apt history logs to see what you've installed. These are all of the history files located in /var/log/apt. Shouldn't be too large if you've just installed.

3. Attach or post back the contents of your ~/.xsession-errors log file after you've changed both the appearance and window manager themes (in case there are error messages).

EDIT: Can you also attach a screenshot of the missing decorations?

---

### Post by vasa1 on 2013-11-26
Maybe a good idea to start a new thread seeing as this particular issue may now be different from the original which was solved.

---

### Post by Toz on 2013-11-26
> **vasa1 said:**
> Maybe a good idea to start a new thread seeing as this particular issue may now be different from the original which was solved.

Good idea. New thread created.

---

### Post by cmcanulty on 2013-11-26
```
cmcanulty@gateway:~$ lspci -k | grep -iA2 VGA
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS480M [Mobility Radeon Xpress 200]
	Subsystem: Gateway, Inc. Device 0300
	Kernel driver in use: radeon
cmcanulty@gateway:~$ 
```
i have 3 of these old laptops and the video and graphics do fine in linux.

```
dvd+rw-tools		install
grub-gfxpayload-lists		install
bind9-host		install
desktop-base		install
growisofs		install
zenity		install
libmimic0		install
libpam-runtime		install
dc		install
libkde3support4		install
xfonts-mathml		install
fakeroot		install
initscripts		install
libidl-common		install
libresid-builder0c2a		install
ntrack-module-libnl-0		install
libmpeg2-4		install
gir1.2-atk-1.0		install
libept1.4.12		install
libdvdread4		install
pciutils		install
libhunspell-1.3-0		install
ibus-table		install
libmplex2-2.0-0		install
gnumeric		install
python3-problem-report		install
libxfce4util-bin		install
python3		install
libtotem-plparser17		install
kdegames-data		install
mime-support		install
libumfpack5.4.0		install
brasero-cdrkit		install
libio-socket-ssl-perl		install
libkrosscore4		install
libqapt2		install
aptdaemon-data		install
brltty-x11		install
libavutil-extra-51		install
oxygen-icon-theme		install
libktexteditor4		install
libpangomm-1.4-1		install
geoip-database		install
libebook-contacts-1.2-0		install
libavformat53		install
libcdio-paranoia1		install
python-httplib2		install
ed		install
gstreamer0.10-plugins-base-apps		install
libdb5.1		install
libdb5.1:i386		install
kdelibs5-data		install
libsgutils2-2		install
xfce4-power-manager-data		install
gettext-base		install
liblwres90		install
libclutter-gtk-1.0-0		install
libstartup-notification0		install
python-compizconfig		install
libcdr-0.0-0		install
libhttp-message-perl		install
liblqr-1-0		install
kmod		install
libnl-genl-3-200		install
python-dbus		install
hddtemp		install
libstdc++-4.8-dev		install
libedit2		install
libcrystalhd3		install
libdc1394-22		install
libisl10		install
e2fslibs		install
libfluidsynth1		install
libgusb2		install
liblua5.1-0		install
python3-oauthlib		install
liba52-0.7.4		install
cracklib-runtime		install
gmusicbrowser		install
libreoffice-pdfimport		install
network-manager-pptp-gnome		install
apg		install
plymouth-theme-xubuntu-logo		install
whiptail		install
xfce4-verve-plugin		install
libnepomukcleaner4		install
nano		install
fonts-tlwg-kinnari		install
libkdeui5		install
obexd-client		install
libreoffice-base-core		install
oneconf		install
libreoffice		install
libkdeclarative5		install
pulseaudio		install
gir1.2-gexiv2-0.4		install
liblwp-mediatypes-perl		install
libtimedate-perl		install
apt		install
hplip		install
libunique-1.0-0		install
language-selector-common		install
libevent-2.0-5		install
libjack-jackd2-0		install
libjack-jackd2-0:i386		install
libpython3.3-minimal		install
libautodie-perl		install
kerneloops-daemon		install
libfontembed1		install
libxapian22		install
libdigest-hmac-perl		install
evolution-data-server-common		install
libnotify-bin		install
libhttp-cookies-perl		install
libplist1		install
rhythmbox-plugins		install
libdbus-glib-1-2		install
libhtml-form-perl		install
pgn-extract		install
dmz-cursor-theme		install
libcrypt-passwdmd5-perl		install
xserver-xorg-video-vmware		install
xscreensaver-data		install
libgeoclue0		install
libtinfo5		install
libtinfo5:i386		install
app-install-data-partner		install
libabiword-3.0		install
fonts-dejavu		install
libbonobo2-common		install
gconf2		install
apparmor-easyprof		install
libasan0		install
libchamplain-gtk-0.12-0		install
xserver-xorg-video-siliconmotion		install
apt-xapian-index		install
initramfs-tools-bin		install
libmad0		install
liboobs-1-5		install
libsasl2-modules-db		install
libsasl2-modules-db:i386		install
libnet-smtp-ssl-perl		install
libqt4-xml		install
libsystemd-login0		install
xdg-user-dirs		install
printer-driver-min12xxw		install
linux-headers-generic		install
debianutils		install
python-support		install
python-pam		install
laptop-detect		install
libgmime-2.6-0		install
libgnutls-openssl27		install
libxcb-dri2-0		install
libxcb-dri2-0:i386		install
mousetweaks		install
python-crypto		install
libmpeg2encpp-2.0-0		install
libquadmath0		install
libthreadweaver4		install
liblcms2-2		install
libnetfilter-conntrack3		install
abiword		install
libijs-0.35		install
ppp		install
libmpc3		install
xubuntu-desktop		install
gcc-4.8-base		install
gcc-4.8-base:i386		install
libmxml1		install
libsemanage-common		install
phonon-backend-gstreamer		install
bsdmainutils		install
libgdiplus		install
update-manager-core		install
libgssdp-1.0-3		install
libwmf0.2-7		install
librasqal3		install
libqt4-network		install
libustr-1.0-1		install
libvorbisfile3		install
install-info		install
xfwm4-dbg		install
libegl1-mesa		install
gvfs-bin		install
libmythes-1.2-0		install
unixodbc		install
libpangoxft-1.0-0		install
libpython2.7-stdlib		install
libmtdev1		install
glib-networking-common		install
libxfixes3		install
libxfixes3:i386		install
multiarch-support		install
libswitch-perl		install
resolvconf		install
xbrlapi		install
libatk1.0-0		install
libxft2		install
perl		install
cups-server-common		install
libqt4-sql-mysql		install
accountsservice		install
libcogl-pango12		install
liblwp-protocol-https-perl		install
libopenvg1-mesa		install
x11-xserver-utils		install
leafpad		install
libjpeg-turbo8		install
libjpeg-turbo8:i386		install
make		install
libidl0		install
libxml-twig-perl		install
xfce4-wavelan-plugin		install
libasound2-data		install
update-inetd		install
libxau6		install
libxau6:i386		install
syslinux-themes-debian-wheezy		install
xubuntu-restricted-extras		install
xfce4-mount-plugin		install
libcogl12		install
libibus-1.0-5		install
fonts-tlwg-purisa		install
xfce4-battery-plugin		install
libpaper1		install
xboard		install
libgail-3-0		install
libgirepository-1.0-1		install
default-jre		install
ttf-punjabi-fonts		install
kde-runtime		install
gstreamer0.10-plugins-good		install
libexo-1-0		install
python-minimal		install
unetbootin-translations		install
libassuan0		install
iw		install
x11-xkb-utils		install
fuse		install
libpango-perl		install
ure		install
libnm-gtk0		install
libpciaccess0		install
libpciaccess0:i386		install
libchromaprint0		install
zeitgeist-core		install
libisccfg90		install
python-dirspec		install
evince		install
libfile-fcntllock-perl		install
libgtkmm-2.4-1c2a		install
libnet-ssleay-perl		install
gnome-session-bin		install
orage		install
man-db		install
libreadline5		install
qtchooser		install
gir1.2-wnck-3.0		install
libreadline6		install
systemd-services		install
sysinfo		install
rfkill		install
libgettextpo-dev		install
unrar		install
python-twisted-bin		install
librsvg2-2		install
libx86-1		install
libnet-domain-tld-perl		install
libreoffice-writer		install
libssl1.0.0		install
libssl1.0.0:i386		install
libkparts4		install
aspell		install
ftp		install
perl-base		install
nepomuk-core-data		install
libgail18		install
libpangox-1.0-0		install
libqt4-sql		install
libdirectfb-1.2-9		install
apt-transport-https		install
procps		install
os-prober		install
python-pkg-resources		install
avahi-daemon		install
syslinux-themes-debian		install
python-nautilus		install
libexiv2-12		install
libqca2		install
gconf-service-backend		install
libsbc1		install
isc-dhcp-common		install
libxaw7		install
busybox-static		install
libpam0g		install
libgraphite2-3		install
libopenobex1		install
libntrack0		install
upower		install
libbind9-90		install
libindicator3-7		install
fonts-tlwg-umpush		install
kde-runtime-data		install
libphonon4		install
libxext6		install
libxext6:i386		install
xfonts-utils		install
im-config		install
libblas3		install
gconf2-common		install
gtk2-engines-murrine		install
mono-gac		install
xscreensaver-gl		install
e2fsprogs		install
libsane-common		install
libspeexdsp1		install
libspeexdsp1:i386		install
tcpdump		install
libkemoticons4		install
libnewt0.52		install
dbus		install
libaspell15		install
libice6		install
libice6:i386		install
vlc-plugin-notify		install
m4		install
libdmapsharing-3.0-2		install
libcheese7		install
libio-string-perl		install
xfce4-power-manager		install
libltdl7		install
libltdl7:i386		install
libsoup2.4-1		install
xorg		install
fonts-dejavu-extra		install
gnumeric-common		install
x11-utils		install
xfce4-netload-plugin		install
xinit		install
libpeas-common		install
libnepomukquery4a		install
libsdl-image1.2		install
gnome-icon-theme-full		install
libauthen-sasl-perl		install
libgssapi-krb5-2		install
libgssapi-krb5-2:i386		install
libegl1-mesa-drivers		install
libpulse-mainloop-glib0		install
libsensors4		install
x11-session-utils		install
libsane-hpaio		install
libx11-xcb1		install
libx11-xcb1:i386		install
simple-scan		install
firefox-locale-en		install
pidgin-data		install
brasero-common		install
gstreamer1.0-libav		install
libzip2		install
xfce4-genmon-plugin		install
default-jre-headless		install
liboil0.3		install
dpkg		install
python3.3		install
gir1.2-gst-plugins-base-1.0		install
cpp-4.8		install
qdbus		install
libcairomm-1.0-1		install
libkmediaplayer4		install
gnome-system-monitor		install
xserver-xorg-video-sisusb		install
xfonts-75dpi		install
winbind		install
python-serial		install
google-chrome-stable		install
libnfnetlink0		install
libkrb5-26-heimdal		install
libkrb5-26-heimdal:i386		install
libneon27-gnutls		install
libgettextpo0		install
libgstreamer-plugins-base1.0-0		install
libicu48		install
xfce4-systemload-plugin		install
libpopt0		install
libgexiv2-2		install
libgomp1		install
libindicator7		install
libxi6		install
libxi6:i386		install
whoopsie		install
libroken18-heimdal		install
libroken18-heimdal:i386		install
libqtcore4		install
libass4		install
libavcodec-extra-53		install
libvlccore5		install
fonts-tlwg-mono		install
xfce4-volumed		install
app-install-data		install
xfce4-mailwatch-plugin		install
at-spi2-core		install
libdecoration0		install
libnautilus-extension1a		install
debconf		install
libgstreamer-perl		install
myspell-en-au		install
libsox-fmt-alsa		install
libhttp-daemon-perl		install
hyphen-en-us		install
libgtk2.0-cil		install
libqt4-qt3support		install
libreoffice-impress		install
mobile-broadband-provider-info		install
libido-0.1-0		install
t1utils		install
libdvbpsi8		install
gstreamer1.0-plugins-base		install
libopencore-amrwb0		install
gimp-help-common		install
libcdaudio1		install
libiw30		install
libmail-sendmail-perl		install
uno-libs3		install
xserver-xorg-video-savage		install
dkms		install
libxfce4ui-1-0		install
libpng12-0		install
libpng12-0:i386		install
libncurses5		install
libncurses5:i386		install
python-notify		install
libgif4		install
libgif4:i386		install
katepart		install
libcanberra0		install
libpango-1.0-0		install
libqt4-svg		install
indicator-sound-gtk2		install
dmsetup		install
libdrm-intel1		install
libdrm-intel1:i386		install
libgnomekbd-common		install
libvo-aacenc0		install
libcrack2		install
thunar-archive-plugin		install
xserver-xorg-input-all		install
libgeis1		install
libharfbuzz-icu0		install
libasprintf-dev		install
libreoffice-base		install
libqt4-dbus		install
libarchive13		install
libmspub-0.0-0		install
libxcursor1		install
libxcursor1:i386		install
dreamchess		install
libqt4-xmlpatterns		install
vlc-nox		install
adduser		install
espeak-data		install
libacl1		install
printer-driver-pnm2ppa		install
coreutils		install
consolekit		install
onboard-data		install
xkb-data		install
xserver-xorg-input-wacom		install
xul-ext-ubufox		install
libnet-dbus-perl		install
tcl8.5-lib		install
xfce4-session		install
libnet-ip-perl		install
yelp-xsl		install
xscreensaver		install
libkdnssd4		install
soprano-daemon		install
libmono-i18n-west4.0-cil		install
pulseaudio-module-x11		install
gstreamer0.10-alsa		install
p11-kit		install
libfribidi0		install
libupnp6		install
phonon		install
foomatic-db-compressed-ppds		install
libkrb5-3		install
libkrb5-3:i386		install
gir1.2-packagekitglib-1.0		install
libusb-0.1-4		install
gir1.2-ibus-1.0		install
libjavascriptcoregtk-3.0-0		install
gir1.2-pango-1.0		install
libical1		install
libpcap0.8		install
libqt4-opengl		install
libalgorithm-diff-xs-perl		install
libsoprano4		install
libdbusmenu-qt2		install
libpcsclite1		install
lightdm-gtk-greeter		install
wireless-regdb		install
libqapt2-runtime		install
libwebp4		install
vim-common		install
iputils-tracepath		install
libattr1		install
sed		install
libtsan0		install
python3-gi-cairo		install
thunderbird-locale-en-us		install
console-setup		install
libnih-dbus1		install
gir1.2-gtk-3.0		install
libwebkitgtk-1.0-0		install
gimp		install
libllvm3.3		install
libllvm3.3:i386		install
screensaver-default-images		install
apport-symptoms		install
libvte9		install
libwind0-heimdal		install
libwind0-heimdal:i386		install
libquvi7		install
libvirtodbc0		install
libgdk-pixbuf2.0-common		install
dpkg-dev		install
libgl1-mesa-dri		install
libgl1-mesa-dri:i386		install
apt-utils		install
cpio		install
gstreamer0.10-gnomevfs		install
libkatepartinterfaces4		install
libfontconfig1		install
libfontconfig1:i386		install
wodim		install
libperlio-gzip-perl		install
iproute2		install
libkeybinder0		install
libsm6		install
libsm6:i386		install
libsox-fmt-base		install
xserver-xorg-video-neomagic		install
xfce4-places-plugin		install
libtumbler-1-0		install
bleachbit		install
hostname		install
genisoimage		install
gir1.2-peas-1.0		install
fonts-tibetan-machine		install
gstreamer1.0-x		install
libpam-cap		install
libexttextcat-2.0-0		install
python-xapian		install
libwpg-0.2-2		install
libcolorhug1		install
libcups2		install
libcups2:i386		install
libreoffice-draw		install
udisks2		install
gnugo		install
libcdparanoia0		install
libexo-common		install
p7zip-full		install
python-cups		install
toshset		install
sensible-utils		install
cups-daemon		install
gir1.2-javascriptcoregtk-3.0		install
libtiff5		install
libtiff5:i386		install
libcomerr2		install
libcomerr2:i386		install
xfwm4-themes		install
anacron		install
sudo		install
thunderbird		install
gnome-desktop-data		install
alacarte		install
libsdl-mixer1.2		install
xfce4-clipman-plugin		install
abiword-plugin-grammar		install
python-pexpect		install
libart-2.0-2		install
fonts-tlwg-loma		install
libglade2-0		install
libfftw3-double3		install
libreoffice-help-en-gb		install
mtools		install
wine1.4-amd64		install
libgnome-desktop-3-7		install
libselinux1		install
libselinux1:i386		install
xfce4-datetime-plugin		install
fonts-sil-abyssinica		install
libcogl-common		install
netbase		install
libmailtools-perl		install
groff-base		install
libglibmm-2.4-1c2a		install
gnome-calculator		install
libcap-ng0		install
libclass-accessor-perl		install
libhpmud0		install
python3-update-manager		install
rarian-compat		install
ubuntu-minimal		install
libx11-data		install
lockfile-progs		install
ubuntu-keyring		install
libhtml-format-perl		install
libtag1c2a		install
printer-driver-pxljr		install
liblist-moreutils-perl		install
libxkbcommon0		install
ubuntu-drivers-common		install
fonts-opensymbol		install
kdelibs5-plugins		install
gnome-icon-theme-symbolic		install
libjson-c2		install
libjson-c2:i386		install
plymouth-theme-ubuntu-text		install
libhcrypto4-heimdal		install
libhcrypto4-heimdal:i386		install
python3-software-properties		install
compiz-core		install
dash		install
liborcus-0.6-0		install
firefox		install
xserver-xorg-input-synaptics		install
xfonts-100dpi		install
printer-driver-foo2zjs		install
openprinting-ppds		install
libvte-2.90-9		install
xubuntu-artwork		install
myspell-en-gb		install
gnome-system-tools		install
libqtwebkit4		install
libdrm-radeon1		install
libdrm-radeon1:i386		install
libopenjpeg2		install
libebml3		install
libqt4-script		install
mount		install
python-renderpm		install
grep		install
libheimntlm0-heimdal		install
libheimntlm0-heimdal:i386		install
libnetpbm10		install
libts-0.0-0		install
libwnck-3-0		install
libxcb-xv0		install
libreoffice-core		install
libilmbase6		install
python-piston-mini-client		install
libgnome-menu-3-0		install
diffstat		install
libopenal1		install
libopenal1:i386		install
parted		install
alsa-base		install
libfreetype6		install
libfreetype6:i386		install
libsystemd-daemon0		install
libalgorithm-merge-perl		install
libcupsmime1		install
libgudev-1.0-0		install
libsonic0		install
libkjsapi4		install
libxcb1		install
libxcb1:i386		install
mawk		install
libmeanwhile1		install
python-apt		install
ndiswrapper-common		install
libcddb2		install
cups-client		install
gnuchess-book		install
libvisual-0.4-plugins		install
p7zip		install
libgimp2.0		install
libcapi20-3		install
libcapi20-3:i386		install
libpipeline1		install
libgs9-common		install
libotr5		install
libreoffice-gnome		install
libxp6		install
command-not-found		install
ibus-pinyin		install
tzdata-java		install
xserver-xorg-input-evdev		install
libbz2-1.0		install
ttf-wqy-microhei		install
xfce4-cpufreq-plugin		install
ubuntu-release-upgrader-gtk		install
xfconf		install
libncursesw5		install
libpolkit-agent-1-0		install
libnss-mdns		install
lp-solve		install
libwayland-server0		install
gir1.2-vte-2.90		install
libieee1284-3		install
libieee1284-3:i386		install
libjson-glib-1.0-common		install
libzbar0		install
ncurses-bin		install
gvfs-common		install
libc-dev-bin		install
libgcc1		install
libgcc1:i386		install
grub-common		install
libcupsimage2		install
file		install
xfce-keyboard-shortcuts		install
ttf-mscorefonts-installer		install
libxres1		install
dh-python		install
libgnome-keyring0		install
libmono-security4.0-cil		install
libkactivities6		install
libots0		install
libxfce4ui-utils		install
xfburn		install
libnspr4		install
thunar-media-tags-plugin		install
libvisio-0.0-0		install
libapparmor1		install
libpangocairo-1.0-0		install
mountall		install
liblockfile1		install
libiso9660-8		install
libgnomekbd8		install
libdbusmenu-gtk4		install
libio-html-perl		install
libmagic1		install
libpam-systemd		install
libsigc++-2.0-0c2a		install
gstreamer0.10-plugins-bad		install
hardening-includes		install
fontconfig		install
menu		install
fonts-liberation		install
libxtst6		install
xfce4-xkb-plugin		install
libgnome-keyring-common		install
libmhash2		install
python3-oneconf		install
python3-pkg-resources		install
libwildmidi-config		install
python3-commandnotfound		install
gtk2-engines-pixbuf		install
xfce4-quicklauncher-plugin		install
ndisgtk		install
libc-bin		install
libc6		install
libc6:i386		install
gir1.2-gdkpixbuf-2.0		install
libexif12		install
libexif12:i386		install
libuuid-perl		install
libgsm1		install
dconf-service		install
gtk-theme-config		install
libnuma1		install
libglib2.0-0		install
libglib2.0-0:i386		install
python-gobject		install
gparted		install
libprotobuf7		install
python2.7		install
xserver-xorg-core		install
libwildmidi1		install
intltool-debian		install
libss2		install
dosfstools		install
xz-utils		install
python-imaging		install
virtuoso-opensource-6.1-common		install
wine		install
libprocps0		install
libgnome2-common		install
libxkbfile1		install
libglapi-mesa		install
libglapi-mesa:i386		install
debhelper		install
libsepol1		install
virtuoso-opensource-6.1-bin		install
busybox-initramfs		install
psmisc		install
evince-common		install
flashplugin-installer		install
libyajl2		install
python-libxml2		install
libsexy2		install
usbutils		install
libxfconf-0-2		install
python-dbus-dev		install
libidn11		install
rhythmbox-mozilla		install
libapt-inst1.5		install
plymouth-theme-xubuntu-text		install
libpci3		install
gstreamer0.10-tools		install
libuuid1		install
libuuid1:i386		install
python-oauthlib		install
gucharmap		install
libgme0		install
libnss3-1d		install
libboost-date-time1.53.0		install
libgtk2.0-bin		install
libboost-system1.53.0		install
libtevent0		install
gnome-accessibility-themes		install
libxcb-keysyms1		install
xserver-xorg-input-mouse		install
cgoban		install
libtelepathy-glib0		install
cups		install
libmount1		install
libpoppler-glib8		install
libdv4		install
libsnmp-base		install
libcompizconfig0		install
libgoa-1.0-common		install
libportaudio2		install
libusbmuxd2		install
libxt6		install
libxt6:i386		install
libcdio13		install
libperl5.14		install
libgtk2.0-common		install
winetricks		install
libvpx1		install
libvpx1:i386		install
virtuoso-minimal		install
libpoppler43		install
gnome-control-center		install
fonts-sil-gentium		install
libpython3.3		install
dreamchess-data		install
libenchant1c2a		install
libgcr-3-1		install
xdg-utils		install
libtxc-dxtn-s2tc0		install
libtxc-dxtn-s2tc0:i386		install
libgtk-3-bin		install
fonts-lyx		install
libelfg0		install
libvorbis0a		install
libvorbis0a:i386		install
abiword-plugin-mathview		install
dnsutils		install
libcanberra-gtk3-module		install
cups-pk-helper		install
cabextract		install
libgutenprint2		install
rhythmbox-data		install
libatk1.0-data		install
libssh-4		install
libtext-charwidth-perl		install
libwnck-3-common		install
xbitmaps		install
xfce4-indicator-plugin		install
libxcb-render0		install
gvfs-daemons		install
ssl-cert		install
nautilus-image-manipulator		install
libnih1		install
libfile-mimeinfo-perl		install
libxrender1		install
libxrender1:i386		install
blueman		install
fonts-tlwg-typo		install
libkdegames6		install
libva1		install
libbluetooth3		install
bluez-cups		install
libnet-http-perl		install
libtidy-0.99-0		install
libschroedinger-1.0-0		install
libslang2		install
python-aptdaemon.gtk3widgets		install
software-center-aptdaemon-plugins		install
python-reportlab-accel		install
libjbig2dec0		install
catfish		install
libdbus-1-3		install
libdbus-1-3:i386		install
libavahi-glib1		install
udev		install
vlc-data		install
fontconfig-config		install
libnl-3-200		install
libgnome-bluetooth11		install
base-files		install
klibc-utils		install
libyaml-tiny-perl		install
xfce4-mixer		install
gnome-exe-thumbnailer		install
patch		install
xfce4-sensors-plugin		install
libdbusmenu-gtk3-4		install
parole		install
rhythmbox-plugin-cdrecorder		install
ifupdown		install
libgpod4		install
libthai0		install
liblangtag1		install
libxv1		install
rtkit		install
alsa-utils		install
libfile-desktopentry-perl		install
liblzma5		install
liblzma5:i386		install
libgnome-control-center1		install
libharfbuzz0a		install
libcolamd2.7.1		install
gnupg		install
gstreamer0.10-pulseaudio		install
libproxy1		install
printer-driver-postscript-hp		install
sox		install
libaudio2		install
xfce4-clipman		install
libunity-scopes-json-def-desktop		install
xfce4-timer-plugin		install
libbrlapi0.6		install
gthumb-data		install
pcmciautils		install
update-notifier-common		install
librtmp0		install
cheese-common		install
gconf-service		install
libimobiledevice4		install
gnumeric-doc		install
pidgin-otr		install
libpixman-1-0		install
libdjvulibre-text		install
xfonts-encodings		install
xserver-xorg-video-vesa		install
g++		install
gir1.2-appindicator3-0.1		install
libgd3		install
libgd3:i386		install
xserver-xorg-video-cirrus		install
linux-sound-base		install
apt-offline		install
libcap2		install
libclucene-core1		install
libnet-libidn-perl		install
libhtml-parser-perl		install
xserver-xorg-video-all		install
system-config-printer-common		install
libraw1394-11		install
libmagickcore5-extra		install
plymouth		install
libservlet3.0-java		install
libjpeg-progs		install
libutempter0		install
libzephyr4		install
network-manager-gnome		install
zeitgeist-datahub		install
libknewstuff3-4		install
libclutter-1.0-0		install
libnm-gtk-common		install
libqpdf10		install
libkmod2		install
grub2-common		install
libsrtp0		install
libwnck-common		install
libmono-system-drawing4.0-cil		install
libwayland-cursor0		install
initramfs-tools		install
bash-completion		install
libatomic1		install
xserver-common		install
libldap-2.4-2		install
libldap-2.4-2:i386		install
python3-cairo		install
pppoeconf		install
mythes-en-au		install
policykit-1		install
libxvidcore4		install
libnet-dns-perl		install
libcairo-gobject2		install
python-reportlab		install
libpam-modules		install
libgphoto2-port10		install
libgphoto2-port10:i386		install
libxss1		install
ghostscript-x		install
hwdata		install
libsqlite3-0		install
libsqlite3-0:i386		install
ubuntu-standard		install
fonts-unfonts-core		install
libnepomukutils4		install
libxtables10		install
openjdk-7-jre-headless		install
xinput		install
libpangoft2-1.0-0		install
lsb-base		install
libswscale2		install
gnome-sudoku		install
libreoffice-style-human		install
thunderbird-locale-en		install
crafty		install
gstreamer0.10-plugins-bad-multiverse		install
libdbusmenu-glib4		install
thunar-data		install
odbcinst1debian2		install
libgtkspell0		install
libreoffice-l10n-en-gb		install
freepats		install
libvte-2.90-common		install
libwww-robotrules-perl		install
python-debian		install
libalgorithm-diff-perl		install
libflite1		install
libglib2.0-data		install
wine1.4-i386:i386		install
gvfs-fuse		install
libtar0		install
xfonts-scalable		install
bluez-alsa		install
libbabl-0.1-0		install
fonts-kacst		install
libflac8		install
libflac8:i386		install
debconf-i18n		install
gir1.2-gudev-1.0		install
libgarcon-common		install
python-gi		install
ristretto		install
libasound2-plugins		install
libasound2-plugins:i386		install
linux-image-extra-3.11.0-13-generic		install
eject		install
libpython3-stdlib		install
qpdf		install
gthumb		install
liblcms1		install
liblcms1:i386		install
libgtop2-common		install
pptp-linux		install
language-selector-gnome		install
libsndfile1		install
libsndfile1:i386		install
libwhoopsie0		install
liburi-perl		install
libmpfr4		install
libsecret-common		install
telnet		install
python-cairo		install
liblircclient0		install
python3-defer		install
xfce4-appfinder		install
libhyphen0		install
indicator-application		install
samba-common-bin		install
brltty		install
kdoctools		install
sgml-data		install
libwww-perl		install
libatk-bridge2.0-0		install
liblockfile-bin		install
libcairo2		install
gstreamer0.10-fluendo-mp3		install
ttf-dejavu-core		install
usbmuxd		install
espeak		install
linux-image-3.11.0-13-generic		install
inputattach		install
libreoffice-report-builder-bin		install
ibus-gtk		install
libappindicator3-1		install
libv4lconvert0		install
libv4lconvert0:i386		install
libunity-protocol-private0		install
libmtp9		install
python3-aptdaemon.gtk3widgets		install
python-xdg		install
libipc-system-simple-perl		install
fonts-sil-padauk		install
mono-runtime		install
xserver-xorg-video-qxl		install
gimp-data		install
krb5-locales		install
libxcb-glx0		install
libxcb-glx0:i386		install
libssh2-1		install
ca-certificates-java		install
cups-browsed		install
libgles2-mesa		install
iputils-arping		install
libclucene-contribs1		install
openoffice.org-hyphenation		install
libhttp-date-perl		install
libmng1		install
libxml2		install
libxml2:i386		install
ndiswrapper-utils-1.9		install
sessioninstaller		install
libkxmlrpcclient4		install
pastebinit		install
g++-4.8		install
gnome-user-guide		install
libwavpack1		install
bash		install
gstreamer0.10-plugins-base		install
libgegl-0.2-0		install
libgksu2-0		install
pulseaudio-utils		install
libkpty4		install
libparted0debian1		install
gir1.2-freedesktop		install
libatk-wrapper-java		install
libopenal-data		install
gvfs		install
libpam-ck-connector		install
indicator-application-gtk2		install
gnome-keyring		install
libmono-i18n4.0-cil		install
libdns99		install
bzip2		install
update-notifier		install
libudev1		install
libudev1:i386		install
libaudit1		install
libmono-system-xml4.0-cil		install
ntfs-3g		install
python-commandnotfound		install
libavahi-common-data		install
libavahi-common-data:i386		install
liblzo2-2		install
python-defer		install
libgl1-mesa-glx		install
libgl1-mesa-glx:i386		install
libxfont1		install
libasn1-8-heimdal		install
libasn1-8-heimdal:i386		install
libkjsembed4		install
libxdmcp6		install
libxdmcp6:i386		install
binutils		install
xfonts-base		install
nautilus		install
libv4l-0		install
libv4l-0:i386		install
printer-driver-gutenprint		install
ibus		install
librest-0.7-0		install
libxatracker1		install
libgconf2-4		install
gcalctool		install
libcmis-0.3-3		install
libcamel-1.2-43		install
libsoup-gnome2.4-1		install
libaudit-common		install
python-lxml		install
libwps-0.2-2		install
libsane		install
libsane:i386		install
python-pycurl		install
libmono-corlib4.0-cil		install
iptables		install
libqt4-designer		install
lsb-release		install
python3-xkit		install
language-pack-gnome-en		install
libgtkmm-3.0-1		install
libtext-wrapi18n-perl		install
xfdesktop4-data		install
libwpd-0.9-9		install
libmjpegutils-2.0-0		install
libreoffice-help-en-us		install
libintl-perl		install
less		install
python3-minimal		install
libexempi3		install
libemail-valid-perl		install
gir1.2-atspi-2.0		install
gstreamer0.10-x		install
libsolid4		install
fonts-tlwg-sawasdee		install
xfce4-settings		install
bsdutils		install
bison		install
libkhtml5		install
mlocate		install
libavahi-client3		install
libavahi-client3:i386		install
libgoa-1.0-0		install
libnm-util2		install
libzeitgeist-1.0-1		install
xfce4		install
dictionaries-common		install
gcc		install
libgupnp-igd-1.0-4		install
libapparmor-perl		install
perl-modules		install
libntrack-qt4-1		install
libwebkitgtk-3.0-0		install
lshw		install
libpurple0		install
syslinux		install
dialog		install
libtwolame0		install
acpid		install
libaa1		install
libmagickwand5		install
gir1.2-glib-2.0		install
gcr		install
rhythmbox		install
vim-tiny		install
logrotate		install
ubuntu-sso-client		install
base-passwd		install
fonts-takao-pgothic		install
libtdb1		install
libfile-copy-recursive-perl		install
command-not-found-data		install
libdvdnav4		install
acpi-support		install
libtext-iconv-perl		install
fonts-freefont-ttf		install
libgxps2		install
libkfile4		install
xfce4-fsguard-plugin		install
cups-bsd		install
libyelp0		install
xserver-xorg-video-intel		install
xfce4-screenshooter		install
libgmp10		install
gdb		install
xfce4-cpugraph-plugin		install
abiword-common		install
libgtop2-7		install
libpoppler-qt4-4		install
libusb-1.0-0		install
libusb-1.0-0:i386		install
openssh-client		install
python-gnomekeyring		install
wget		install
libapt-pkg4.12		install
libevview3-3		install
libzvbi0		install
fonts-sil-gentium-basic		install
libgdbm3		install
libthai-data		install
libfarstream-0.1-0		install
libxfce4util-common		install
python3-piston-mini-client		install
libcanberra-gtk3-0		install
uuid-runtime		install
openjdk-7-jre-lib		install
libwv-1.2-4		install
python3-uno		install
libfile-listing-perl		install
libgcc-4.8-dev		install
libmessaging-menu0		install
python3-apt		install
libcdio-cdda1		install
libpython2.7		install
libburn4		install
libgdome2-0		install
gimp-help-en		install
hunspell-en-ca		install
libgtk2-perl		install
libreoffice-common		install
libunistring0		install
ltrace		install
xserver-xorg-video-ati		install
mysql-common		install
flex		install
libdirac-encoder0		install
python-debtagshw		install
libgtk-3-0		install
python-gi-cairo		install
python-six		install
icoutils		install
xorg-docs-core		install
oneconf-common		install
libnm-glib-vpn1		install
libvisual-0.4-0		install
libnatpmp1		install
libglamor0		install
librsvg2-common		install
libgoffice-0.10-10-common		install
xubuntu-default-settings		install
libdpkg-perl		install
libsdl1.2debian		install
libnspr4-0d		install
python3-aptdaemon.pkcompat		install
libgrip0		install
xfce4-artwork		install
lm-sensors		install
ureadahead		install
libgtk2-notify-perl		install
ndiswrapper-source		install
libmnl0		install
fonts-tlwg-typist		install
libgck-1-0		install
libsub-name-perl		install
lintian		install
ibus-pinyin-db-android		install
libpwquality1		install
obex-data-server		install
tumbler-common		install
cpp		install
libdotconf1.0		install
libglib-perl		install
xchat-common		install
libpostproc52		install
bluez		install
libgsf-1-common		install
python3-httplib2		install
libspectre1		install
libfftw3-3		install
libgconf2.0-cil		install
libcheese-gtk23		install
po-debconf		install
sane-utils		install
gvfs-backends		install
wine1.4		install
liborc-0.4-0		install
liborc-0.4-0:i386		install
libdee-1.0-4		install
libencode-locale-perl		install
policykit-desktop-privileges		install
dnsmasq-base		install
libxfcegui4-4		install
libcroco3		install
libtag1-vanilla		install
xserver-xorg-video-mach64		install
xubuntu-docs		install
fonts-lklug-sinhala		install
libapt-pkg-perl		install
xserver-xorg-video-tdfx		install
gcc-4.8		install
thunar-volman		install
libbonobo2-0		install
libjasper1		install
gstreamer1.0-plugins-ugly		install
libp11-kit0		install
libp11-kit0:i386		install
libatasmart4		install
libgtk2.0-0		install
libt1-5		install
libattica0.4		install
libdca0		install
libsys-hostname-long-perl		install
libsystemd-journal0		install
pidgin-libnotify		install
libpolkit-backend-1-0		install
libasound2		install
libasound2:i386		install
gstreamer1.0-plugins-bad		install
libenca0		install
ca-certificates		install
imagemagick		install
isc-dhcp-client		install
gnome-time-admin		install
libkdesu5		install
kigo		install
libglib2.0-cil		install
libcolord1		install
libjte1		install
libnss3		install
libdrm-nouveau2		install
libdrm-nouveau2:i386		install
gnome-settings-daemon		install
libcupscgi1		install
libfont-afm-perl		install
libnepomukcore4abi1		install
libquvi-scripts		install
libatspi2.0-0		install
libjson-glib-1.0-0		install
libmysqlclient18		install
usb-modeswitch-data		install
libpango1.0-0		install
linux-headers-3.11.0-13		install
libdlrestrictions1		install
libsigsegv2		install
libdconf1		install
xchat-indicator		install
libgarcon-1-0		install
libgrail6		install
libstreams0		install
libheimbase1-heimdal		install
libheimbase1-heimdal:i386		install
fairymax		install
libkidletime4		install
libknotifyconfig4		install
myspell-en-za		install
sysv-rc		install
python-gconf		install
xserver-xorg-video-fbdev		install
syslinux-common		install
netpbm		install
xfce4-smartbookmark-plugin		install
libatkmm-1.6-1		install
linux-headers-3.11.0-13-generic		install
indicator-sound		install
libcloog-isl4		install
libgnomevfs2-common		install
libnotify4		install
libogg0		install
libogg0:i386		install
mtr-tiny		install
unzip		install
docbook-xml		install
libxcb-util0		install
qgo		install
foomatic-filters		install
libgnome2-0		install
iputils-ping		install
libavahi-core7		install
grub-pc-bin		install
pppconfig		install
python-aptdaemon		install
poppler-data		install
ttf-ubuntu-font-family		install
openjdk-7-jre		install
xfce4-notes		install
libxcb-shm0		install
upstart		install
python-gobject-2		install
python-smbc		install
fonts-horai-umefont		install
libgphoto2-6		install
libgphoto2-6:i386		install
modemmanager		install
libgupnp-1.0-4		install
libiec61883-0		install
aptdaemon		install
cups-filters		install
gstreamer1.0-pulseaudio		install
libsub-identify-perl		install
python		install
libfftw3-single3		install
libplymouth2		install
libwayland-client0		install
fonts-khmeros-core		install
gkbd-capplet		install
libkpathsea6		install
xserver-xorg-video-trident		install
memtest86+		install
mono-4.0-gac		install
libexo-helpers		install
libgnutls26		install
libgnutls26:i386		install
python-openssl		install
libslv2-9		install
nautilus-data		install
dconf-cli		install
grub-pc		install
libavahi-common3		install
libavahi-common3:i386		install
libxcb-shape0		install
libvte-common		install
libwnck22		install
gnome-desktop3-data		install
libxmu6		install
time		install
gir1.2-gconf-2.0		install
ubuntu-system-service		install
lsof		install
libipc-run-perl		install
libreoffice-gtk		install
liburl-dispatcher1		install
python-twisted-core		install
b43-fwcutter		install
gir1.2-nautilus-3.0		install
dconf-gsettings-backend		install
libxcb-composite0		install
liblink-grammar4		install
libreoffice-java-common		install
libgsf-1-114		install
smbclient		install
libxml-xpath-perl		install
libpurple-bin		install
libmp3lame0		install
libopenexr6		install
ttf-indic-fonts-core		install
libxcb-randr0		install
manpages-dev		install
libgstreamer-plugins-good1.0-0		install
printer-driver-splix		install
python3-distupgrade		install
libgnomevfs2-extra		install
python3-gi		install
build-essential		install
gettext		install
rhythmbox-plugin-zeitgeist		install
python-zeitgeist		install
libisofs6		install
libkdecore5		install
exo-utils		install
python-chardet		install
libgnomevfs2-0		install
kdelibs-bin		install
libfile-basedir-perl		install
libgbm1		install
libpam-gnome-keyring		install
sgml-base		install
python-gst0.10		install
firmware-b43-installer		install
libpython-stdlib		install
zeitgeist		install
fonts-droid		install
liblocale-gettext-perl		install
libcupsppdc1		install
compiz-plugins-default		install
python-zope.interface		install
printer-driver-hpcups		install
gnuchess		install
libcurl3		install
libopencc1		install
libtalloc2		install
apport-gtk		install
libdevmapper1.02.1		install
libgconf-2-4		install
libkactivities-bin		install
fonts-tlwg-waree		install
libgpod-common		install
libzeitgeist-2.0-0		install
lightdm		install
passwd		install
gpgv		install
libgnome2-bin		install
libspeex1		install
libgtksourceview2.0-0		install
libclutter-gst-2.0-0		install
libgstreamer-plugins-bad0.10-0		install
mscompress		install
apport		install
doc-base		install
libio-socket-inet6-perl		install
shimmer-themes		install
crda		install
libgs9		install
powermgmt-base		install
libva-x11-1		install
brasero		install
libmtp-common		install
nepomuk-core-runtime		install
libnettle4		install
libodbc1		install
libxslt1.1		install
libxslt1.1:i386		install
plasma-scriptengine-javascript		install
libgtk-3-common		install
libdigest-crc-perl		install
libklibc		install
libasyncns0		install
libasyncns0:i386		install
libjpeg-turbo-progs		install
tcl8.5		install
libatk-wrapper-java-jni		install
libgoffice-0.10-10		install
manpages		install
libgstreamer1.0-0		install
libofa0		install
qapt-batch		install
ubuntu-extras-keyring		install
gstreamer1.0-plugins-good		install
libavc1394-0		install
libedataserver-1.2-17		install
extlinux		install
xcursor-themes		install
libfl-dev		install
xserver-xorg-video-openchrome		install
keyboard-configuration		install
libloudmouth1-0		install
libmono-system-security4.0-cil		install
mousepad		install
python-markupsafe		install
kbd		install
libarchive-zip-perl		install
policykit-1-gnome		install
linux-firmware		install
pm-utils		install
python3-crypto		install
gnome-icon-theme		install
gsfonts		install
libexttextcat-data		install
python2.7-minimal		install
cli-common		install
acl		install
libpam-modules-bin		install
libspandsp2		install
gnome-menus		install
wpasupplicant		install
libthunarx-2-0		install
libmpg123-0		install
libmpg123-0:i386		install
libx264-123		install
xfwm4		install
libbluray1		install
libp11-kit-gnome-keyring		install
libp11-kit-gnome-keyring:i386		install
patchutils		install
libnepomuk4		install
xserver-xorg		install
libclass-isa-perl		install
unetbootin		install
libbsd0		install
libzvbi-common		install
libamd2.2.0		install
libmono-cairo4.0-cil		install
xserver-xorg-input-vmmouse		install
python3-aptdaemon		install
xfce4-notes-plugin		install
libpwquality-common		install
odbcinst		install
libwebkitgtk-3.0-common		install
sysvinit-utils		install
software-center		install
libasprintf0c2		install
vlc		install
python-ubuntu-sso-client		install
cups-common		install
libjson0		install
libstreamanalyzer0		install
tumbler		install
libgpg-error0		install
libgpg-error0:i386		install
libwacom-common		install
system-config-printer-gnome		install
libxinerama1		install
libxinerama1:i386		install
xserver-xorg-video-radeon		install
libxcb-xfixes0		install
libvlc5		install
libfaac0		install
libtie-ixhash-perl		install
libmodplug1		install
libmagickcore5		install
libsemanage1		install
ndiswrapper-dkms		install
xfce4-weather-plugin		install
transmission-gtk		install
libblkid1		install
avahi-utils		install
xml-core		install
xserver-xorg-glamoregl		install
docbook-xsl		install
liblightdm-gobject-1-0		install
libmatroska5		install
libsocket6-perl		install
usb-modeswitch		install
libxmuu1		install
libpolkit-gobject-1-0		install
gnome-bluetooth		install
libkntlm4		install
libunity9		install
gzip		install
libsasl2-modules		install
libsasl2-modules:i386		install
system-tools-backends		install
libbison-dev		install
enchant		install
gir1.2-notify-0.7		install
ucf		install
icedtea-7-jre-jamvm		install
libio-pty-perl		install
libpeas-1.0-0		install
login		install
dbus-x11		install
libfaad2		install
libwebkitgtk-1.0-common		install
hicolor-icon-theme		install
init-system-helpers		install
systemd-shim		install
python-configobj		install
xterm		install
gtk2-engines-xfce		install
python3-gdbm		install
libpaper-utils		install
python3-xdg		install
libgdk-pixbuf2.0-0		install
libkdewebkit5		install
libraptor2-0		install
gstreamer1.0-fluendo-mp3		install
java-common		install
libgucharmap-2-90-7		install
liblua5.2-0		install
hplip-data		install
ubuntu-tweak		install
zlib1g		install
zlib1g:i386		install
libxcomposite1		install
libxcomposite1:i386		install
session-migration		install
xfce4-dict		install
libchamplain-0.12-0		install
netcat-openbsd		install
libaccountsservice0		install
libvcdinfo0		install
binfmt-support		install
libreoffice-style-galaxy		install
libclutter-1.0-common		install
makedev		install
gir1.2-gstreamer-1.0		install
xubuntu-restricted-addons		install
gir1.2-gnomebluetooth-1.0		install
findutils		install
libsasl2-2		install
libsasl2-2:i386		install
hdparm		install
libxdamage1		install
libxdamage1:i386		install
libxxf86vm1		install
libxxf86vm1:i386		install
libframe6		install
system-config-printer-udev		install
libgstreamer-plugins-base0.10-0		install
libgstreamer-plugins-base0.10-0:i386		install
xfdesktop4		install
gvfs-libs		install
libevdocument3-4		install
libgdome2-cpp-smart0c2a		install
libkcmutils4		install
libexpat1		install
libexpat1:i386		install
libjbig0		install
libjbig0:i386		install
xserver-xorg-video-sis		install
libfontenc1		install
libpulsedsp		install
python3-apport		install
apparmor		install
wamerican		install
libsecret-1-0		install
tzdata		install
libespeak1		install
xdg-user-dirs-gtk		install
xubuntu-icon-theme		install
software-properties-common		install
openssl		install
libcaca0		install
libelf1		install
libelf1:i386		install
language-pack-en-base		install
friendly-recovery		install
python-cupshelpers		install
libclone-perl		install
colord		install
libglib2.0-bin		install
module-init-tools		install
fonts-tlwg-norasi		install
python3.3-minimal		install
libsoundtouch0		install
gnomine		install
fonts-nanum		install
xfce4-panel		install
libreoffice-l10n-en-za		install
libbrasero-media3-1		install
xfce4-terminal		install
imagemagick-common		install
libtext-levenshtein-perl		install
libaacs0		install
mythes-en-us		install
libpolkit-qt-1-1		install
fonts-tlwg-typewriter		install
language-pack-gnome-en-base		install
libsidplay1		install
python-twisted-web		install
libsidplay2		install
libwbclient0		install
libgssapi3-heimdal		install
libgssapi3-heimdal:i386		install
scrollkeeper		install
xfce4-notifyd		install
python-gtk2		install
locate		install
thunar		install
ufw		install
libepub0		install
librarian0		install
wine-gecko1.4		install
wine-gecko1.4:i386		install
libgtk2-trayicon-perl		install
rsync		install
poppler-utils		install
aspell-en		install
pavucontrol		install
ubuntu-release-upgrader-core		install
cups-ppdc		install
python-oneconf		install
libwacom2		install
ibus-gtk3		install
libmtp-runtime		install
diffutils		install
info		install
gsettings-desktop-schemas		install
libgtkmathview0c2a		install
libhtml-tagset-perl		install
libnice10		install
x11-common		install
libdatrie1		install
libhsqldb1.8.0-java		install
xfce4-goodies		install
libc6-dbg		install
network-manager		install
linux-libc-dev		install
update-manager		install
util-linux		install
libopus0		install
xchat		install
libkactivities-models1		install
python-gdbm		install
eboard		install
iproute		install
yelp		install
libck-connector0		install
tsconf		install
libjavascriptcoregtk-1.0-0		install
zenity-common		install
librdf0		install
media-player-info		install
xserver-xorg-video-s3		install
link-grammar-dictionaries-en		install
libtasn1-3		install
libtasn1-3:i386		install
libpulse0		install
libpulse0:i386		install
transmission-common		install
libdjvulibre21		install
libgcr-base-3-1		install
libmono-system4.0-cil		install
libwrap0		install
libwrap0:i386		install
python-apt-common		install
gstreamer0.10-ffmpeg		install
glib-networking-services		install
libgeoip1		install
libnl-route-3-200		install
fonts-tlwg-garuda		install
printer-driver-sag-gdi		install
ethtool		install
libgtksourceview2.0-common		install
ghostscript		install
gir1.2-rb-3.0		install
libtheora0		install
samba-common		install
libfuse2		install
libxklavier16		install
libkate1		install
playitslowly		install
printer-driver-c2esp		install
libhx509-5-heimdal		install
libhx509-5-heimdal:i386		install
software-properties-gtk		install
xserver-xorg-video-modesetting		install
libstdc++6		install
libstdc++6:i386		install
libpcre3		install
libpcre3:i386		install
libqtgui4		install
libkio5		install
libxml2-utils		install
libhtml-tree-perl		install
libcanberra-pulse		install
kate-data		install
libdrm2		install
libdrm2:i386		install
python-imaging-compat		install
libmono-system-configuration4.0-cil		install
x11-xfs-utils		install
language-pack-en		install
librhythmbox-core7		install
insserv		install
libminiupnpc8		install
xauth		install
network-manager-pptp		install
xubuntu-wallpapers		install
file-roller		install
humanity-icon-theme		install
libgstreamer0.10-0		install
libgstreamer0.10-0:i386		install
plymouth-label		install
fonts-dejavu-core		install
libudisks2-0		install
libkeyutils1		install
libkeyutils1:i386		install
xfce4-diskperf-plugin		install
fonts-kacst-one		install
libpackagekit-glib2-16		install
libx11-6		install
libx11-6:i386		install
libxfce4util6		install
libitm1		install
xserver-xorg-video-r128		install
locales		install
gir1.2-webkit-3.0		install
unattended-upgrades		install
net-tools		install
khelpcenter4		install
sound-theme-freedesktop		install
glib-networking		install
vbetool		install
python-poster		install
kubuntu-debug-installer		install
libspeechd2		install
iso-codes		install
tango-icon-theme		install
libsnmp30		install
libxrandr2		install
libxrandr2:i386		install
python3-dbus		install
fonts-lao		install
libdaemon0		install
libglu1-mesa		install
libglu1-mesa:i386		install
zip		install
libpython2.7-minimal		install
module-assistant		install
shared-desktop-ontologies		install
gir1.2-soup-2.4		install
gigolo		install
libreoffice-math		install
gnome-user-share		install
linux-image-generic		install
libvorbisenc2		install
libvorbisenc2:i386		install
desktop-file-utils		install
vlc-plugin-pulse		install
libkrb5support0		install
libkrb5support0:i386		install
libplasma3		install
libvo-amrwbenc0		install
liborbit2		install
irqbalance		install
libk5crypto3		install
libk5crypto3:i386		install
ncurses-base		install
synaptic		install
libpython3.3-stdlib		install
libisccc90		install
libupower-glib1		install
libfs6		install
libxxf86dga1		install
libgphoto2-l10n		install
libxml-parser-perl		install
strace		install
libcap2-bin		install
avahi-autoipd		install
bc		install
libgcrypt11		install
libgcrypt11:i386		install
dh-apparmor		install
tcpd		install
libc6-dev		install
wbritish		install
onboard		install
dmidecode		install
python-mako		install
libsmbclient		install
libxpm4		install
libxpm4:i386		install
libqt4-declarative		install
libsox2		install
libisc95		install
libgpm2		install
libgpm2:i386		install
libtagc0		install
thunderbird-locale-en-gb		install
libgcr-3-common		install
libgpgme11		install
libmikmod2		install
libreoffice-calc		install
x11-apps		install
libmms0		install
libgstreamer-plugins-bad1.0-0		install
libnm-glib4		install
libcurl3-gnutls		install
libparse-debianchangelog-perl		install
liblangtag-common		install
pidgin		install
libgcr-ui-3-1		install
speech-dispatcher		install
libcairo-perl		install
gksu		install
readline-common		install
rsyslog		install
pkg-config		install
shared-mime-info		install
xfce4-taskmanager		install
libxvmc1		install
tar		install
hunspell-en-us		install
ntpdate		install
libmpcdec6		install
cron		install
crafty-books-medtosmall		install
libshout3		install
fonts-thai-tlwg		install
libglade2.0-cil		install
gir1.2-gmenu-3.0		install
linux-generic		install
libcupsfilters1		install
wireless-tools		install
printer-driver-ptouch		install
gstreamer0.10-plugins-ugly		install
popularity-contest		install
libffi6		install
libffi6:i386		install
libgee2		install
xserver-xorg-video-mga		install
gstreamer0.10-nice		install
libsamplerate0		install
libsamplerate0:i386		install
libopencore-amrnb0		install
xserver-xorg-video-nouveau		install
gnome-control-center-data		install
libhttp-negotiate-perl		install
libjpeg8		install
libjpeg8:i386		install
gnome-mines		install

```

---

### Post by cmcanulty on 2013-11-26
OK I completely purged firefox and reinstalled, no change. Also evince and numerous other apps have no tool bar open, close, file, etc. I guess I would save time by reinstalling xubuntu but then this can randomly occur at any time and there is no fix?

---

### Post by VMC on 2013-11-26
Can you give us a picture of the "lost" decorations? Screenshot.

I've been using Ubuntu all along and only used Xubuntu for a short time, and the only strange decoration, was when I choose GNOME as the theme.

---

### Post by Toz on 2013-11-26
> **cmcanulty said:**
> 
i have 3 of these old laptops and the video and graphics do fine in linux.
There is an existing bug for missing decorations with nvidia cards for themes with 1 pixel borders - I wanted to see if this was affecting you.

> **VMC said:**
> Can you give us a picture of the "lost" decorations? Screenshot.

+1 a screenshot would sure help - at least give us some perspective.

> **cmcanulty said:**
> I guess I would save time by reinstalling xubuntu but then this can randomly occur at any time and there is no fix?
As I understand it, everything worked fine when you first installed, but then went south shortly thereafter. If you do decide to re-install, keep track of which packages you are installing and when it happens again. It might be related to a specific package or update. I couldn't pick out anything specific with the listing you posted.

---

### Post by cmcanulty on 2013-11-26
OK I tried a reinstall and kept my home and that didn't fix so I did a clean reinstall. Ironically I wanted to do Xubuntu to eliminate the lack of menus etc in unity and it appears to have major issues also. But I don't know about how xubuntu is so configurable if configuring causes problems like this with no fix.

---

### Post by Toz on 2013-11-26
> **cmcanulty said:**
> OK I tried a reinstall and kept my home and that didn't fix so I did a clean reinstall. Ironically I wanted to do Xubuntu to eliminate the lack of menus etc in unity and it appears to have major issues also. But I don't know about how xubuntu is so configurable if configuring causes problems like this with no fix.

To be honest, I've installed many instances of Xubuntu over the years and have never seen an issue like this. Keep a close eye on the packages that you install/update and when the issue appears - I think it might be related to one specific package/update.

---

### Post by vasa1 on 2013-11-26
Looking at the list of installed software, it seems that the system is very far from "vanilla" Xubuntu. The first hint came with the mentions of *zeitgeist*. Now, the list of apps has several "kde" entries at least some of which are due to manual, intentional installation of KDE software. My *prejudice* is that KDE doesn't not play well with GNOME. Nor does it uninstall cleanly.
```
[08:16 AM] ~/Desktop $ grep kde temp.txt
        libkde3support4		install
        kdegames-data		install
        kdelibs5-data		install
        libkdeui5		install
        libkdeclarative5		install
        kde-runtime		install
        kde-runtime-data		install
        kdelibs5-plugins		install
        libkdegames6		install
        libkdesu5		install
        libkdecore5		install
        kdelibs-bin		install
        libkdewebkit5		install

```
Who knows what else has been done? There's *oxygen-icon-theme*.

In conclusion, there's enough reason to conclude that the problems noticed here are probably due to installation of software that somehow "breaks" Xubuntu window manager's functionality.

Another non-scientific claim:  even though package managers do their best, the effect of adding software may not be totally reversed by removing the same software.

---

### Post by Toz on 2013-11-26
> **vasa1 said:**
> Looking at the list of installed software, it seems that the system is very far from "vanilla" Xubuntu. The first hint came with the mentions of zeitgeist. Now, the list of apps has several "kde" entries at least some of which are due to manual, intentional installation of KDE software. My prejudice is that KDE doesn't not play well with GNOME. Nor does it uninstall cleanly.
Code:

[08:16 AM] ~/Desktop $ grep kde temp.txt
        libkde3support4		install
        kdegames-data		install
        kdelibs5-data		install
        libkdeui5		install
        libkdeclarative5		install
        kde-runtime		install
        kde-runtime-data		install
        kdelibs5-plugins		install
        libkdegames6		install
        libkdesu5		install
        libkdecore5		install
        kdelibs-bin		install
        libkdewebkit5		install

Who knows what else has been done? There's oxygen-icon-theme.

In conclusion, there's enough reason to conclude that the problems noticed here are probably due to installation of software that somehow "breaks" Xubuntu window manager's functionality.

Another non-scientific claim: even though package managers do their best, the effect of adding software may not be totally reversed by removing the same software. 
Agreed. There are over 1000 additional packages above and beyond the 13.10 manifest (just did a compare):
```
apparmor-easyprof
app--data
app--data-partner
b43-fwcutter
binfmt-support
bleachbit
bluez-alsa
brasero
brasero-cdrkit
brasero-common
build-essential
cabextract
ca-certificates-java
cgoban
cli-common
compiz-core
compiz-plugins-default
consolekit
crafty
crafty-books-medtosmall
dconf-gsettings-backend
debhelper
default-jre
default-jre-headless
desktop-base
dh-apparmor
dkms
docbook-xsl
dpkg-dev
dreamchess
dreamchess-data
dvd+rw-tools
e2fslibs
eboard
espeak-data
ethtool
extlinux
fairymax
fakeroot
firmware-b43-er
flashplugin-er
fonts-dejavu
fonts-dejavu-extra
fonts-horai-umefont
fonts-sil-gentium
fonts-sil-gentium-basic
fonts-unfonts-core
freepats
g++
g++-4.8
gcc-4.8-base
gcc-4.8-base:i386
gimp-help-common
gimp-help-en
gir1.2-gconf-2.0
gir1.2-gexiv2-0.4
gir1.2-gst-plugins-base-1.0
gir1.2-nautilus-3.0
gir1.2-peas-1.0
gir1.2-rb-3.0
gksu
glib-networking
gnome-exe-thumbnailer
gnome-icon-theme-full
gnome-system-monitor
gnuchess
gnuchess-book
gnugo
google-chrome-stable
growisofs
gstreamer0.10-alsa
gstreamer0.10-ffmpeg
gstreamer0.10-fluendo-mp3
gstreamer0.10-gnomevfs
gstreamer0.10-nice
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-base
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-pulseaudio
gstreamer0.10-x
gstreamer1.0-fluendo-mp3
gstreamer1.0-libav
gstreamer1.0-plugins-bad
gstreamer1.0-plugins-base
gstreamer1.0-plugins-good
gstreamer1.0-plugins-ugly
gstreamer1.0-pulseaudio
gstreamer1.0-x
gtk2-engines-murrine
gtk2-engines-pixbuf
gtk2-engines-xfce
gvfs
gvfs-libs
hddtemp
hunspell-en-ca
hyphen-en-us
ibus-gtk
ibus-gtk3
icedtea-7-jre-jamvm
icoutils
imagemagick
imagemagick-common
java-common
kate-data
katepart
kdegames-data
kdelibs5-data
kdelibs5-plugins
kdelibs-bin
kde-runtime
kde-runtime-data
kdoctools
khelpcenter4
kigo
kubuntu-debug-er
leafpad
liba52-0.7.4
libaa1
libaacs0
libabiword-3.0
libacl1
libalgorithm-diff-perl
libalgorithm-diff-xs-perl
libalgorithm-merge-perl
libapt-inst1.5
libapt-pkg4.12
libarchive13
libart-2.0-2
libasan0
libasn1-8-heimdal
libasn1-8-heimdal:i386
libasound2
libasound2:i386
libasound2-plugins
libasound2-plugins:i386
libasprintf0c2
libasprintf-dev
libass4
libassuan0
libasyncns0
libasyncns0:i386
libatasmart4
libatk1.0-0
libatk-bridge2.0-0
libatkmm-1.6-1
libatk-wrapper-java
libatk-wrapper-java-jni
libatomic1
libatspi2.0-0
libattica0.4
libattr1
libaudio2
libaudit1
libavahi-client3
libavahi-client3:i386
libavahi-common3
libavahi-common3:i386
libavahi-common-data
libavahi-common-data:i386
libavahi-core7
libavahi-glib1
libavc1394-0
libavcodec-extra-53
libavformat53
libavutil-extra-51
libbabl-0.1-0
libbison-dev
libblkid1
libbluetooth3
libbluray1
libbonobo2-0
libbonobo2-common
libboost-date-time1.53.0
libboost-system1.53.0
libbrasero-media3-1
libbrlapi0.6
libbsd0
libbz2-1.0
libc6
libc6:i386
libc6-dbg
libc6-dev
libcaca0
libcairo2
libcairo-gobject2
libcairomm-1.0-1
libcanberra0
libcanberra-gtk3-0
libcanberra-gtk3-module
libcanberra-pulse
libcap2
libcapi20-3
libcapi20-3:i386
libcdaudio1
libcddb2
libcdparanoia0
libcdr-0.0-0
libchamplain-0.12-0
libchamplain-gtk-0.12-0
libcheese7
libcheese-gtk23
libchromaprint0
libck-connector0
libcloog-isl4
libclucene-contribs1
libclucene-core1
libclutter-1.0-0
libclutter-gst-2.0-0
libclutter-gtk-1.0-0
libcmis-0.3-3
libcogl12
libcogl-pango12
libcolord1
libcolorhug1
libcomerr2
libcomerr2:i386
libcompizconfig0
libcroco3
libcrypt-passwdmd5-perl
libcrystalhd3
libcups2
libcups2:i386
libcupscgi1
libcupsfilters1
libcupsimage2
libcupsmime1
libcupsppdc1
libcurl3
libcurl3-gnutls
libdatrie1
libdb5.1
libdb5.1:i386
libdbus-1-3
libdbus-1-3:i386
libdbus-glib-1-2
libdbusmenu-glib4
libdbusmenu-gtk3-4
libdbusmenu-gtk4
libdbusmenu-qt2
libdc1394-22
libdca0
libdconf1
libdecoration0
libdevmapper1.02.1
libdirac-encoder0
libdirectfb-1.2-9
libdjvulibre21
libdlrestrictions1
libdmapsharing-3.0-2
libdrm2
libdrm2:i386
libdrm-intel1
libdrm-intel1:i386
libdrm-nouveau2
libdrm-nouveau2:i386
libdrm-radeon1
libdrm-radeon1:i386
libdv4
libdvbpsi8
libdvdnav4
libdvdread4
libebml3
libedit2
libegl1-mesa
libegl1-mesa-drivers
libelf1
libelf1:i386
libelfg0
libenca0
libenchant1c2a
libept1.4.12
libepub0
libespeak1
libevent-2.0-5
libexempi3
libexif12
libexif12:i386
libexo-1-0
libexpat1
libexpat1:i386
libexttextcat-2.0-0
libexttextcat-data
libfaac0
libfaad2
libfarstream-0.1-0
libffi6
libffi6:i386
libfftw3-3
libfftw3-double3
libfftw3-single3
libflac8
libflac8:i386
libfl-dev
libflite1
libfluidsynth1
libfontconfig1
libfontconfig1:i386
libfontembed1
libfontenc1
libframe6
libfreetype6
libfreetype6:i386
libfribidi0
libfs6
libfuse2
libgail18
libgail-3-0
libgbm1
libgcc1
libgcc1:i386
libgcc-4.8-dev
libgck-1-0
libgconf2.0-cil
libgconf2-4
libgconf-2-4
libgcr-3-1
libgcr-base-3-1
libgcr-ui-3-1
libgcrypt11
libgcrypt11:i386
libgd3
libgd3:i386
libgdbm3
libgdiplus
libgdk-pixbuf2.0-0
libgee2
libgegl-0.2-0
libgeis1
libgeoip1
libgettextpo0
libgettextpo-dev
libgexiv2-2
libgif4
libgif4:i386
libgksu2-0
libgl1-mesa-dri
libgl1-mesa-dri:i386
libgl1-mesa-glx
libgl1-mesa-glx:i386
libglade2.0-cil
libglade2-0
libglamor0
libglapi-mesa
libglapi-mesa:i386
libgles2-mesa
libglib2.0-0
libglib2.0-0:i386
libglib2.0-cil
libglibmm-2.4-1c2a
libglu1-mesa
libglu1-mesa:i386
libgme0
libgmime-2.6-0
libgmp10
libgnome2-0
libgnome2-bin
libgnome2-common
libgnome-keyring0
libgnomevfs2-0
libgnomevfs2-extra
libgnutls26
libgnutls26:i386
libgnutls-openssl27
libgoa-1.0-0
libgomp1
libgpg-error0
libgpg-error0:i386
libgpgme11
libgphoto2-6
libgphoto2-6:i386
libgphoto2-port10
libgphoto2-port10:i386
libgpm2
libgpm2:i386
libgpod4
libgpod-common
libgraphite2-3
libgsm1
libgssapi3-heimdal
libgssapi3-heimdal:i386
libgssapi-krb5-2
libgssapi-krb5-2:i386
libgstreamer0.10-0
libgstreamer0.10-0:i386
libgstreamer1.0-0
libgstreamer-plugins-bad0.10-0
libgstreamer-plugins-bad1.0-0
libgstreamer-plugins-base0.10-0
libgstreamer-plugins-base0.10-0:i386
libgstreamer-plugins-base1.0-0
libgstreamer-plugins-good1.0-0
libgtk2.0-0
libgtk2.0-cil
libgtk-3-0
libgtkmm-2.4-1c2a
libgtkmm-3.0-1
libgudev-1.0-0
libgupnp-igd-1.0-4
libgusb2
libgxps2
libharfbuzz0a
libharfbuzz-icu0
libhcrypto4-heimdal
libhcrypto4-heimdal:i386
libheimbase1-heimdal
libheimbase1-heimdal:i386
libheimntlm0-heimdal
libheimntlm0-heimdal:i386
libhsqldb1.8.0-java
libhunspell-1.3-0
libhx509-5-heimdal
libhx509-5-heimdal:i386
libhyphen0
libibus-1.0-5
libice6
libice6:i386
libicu48
libidl0
libidl-common
libidn11
libido-0.1-0
libiec61883-0
libieee1284-3
libieee1284-3:i386
libilmbase6
libisl10
libiso9660-8
libitm1
libiw30
libjack-jackd2-0
libjack-jackd2-0:i386
libjasper1
libjbig0
libjbig0:i386
libjpeg8
libjpeg8:i386
libjpeg-turbo8
libjpeg-turbo8:i386
libjson0
libjson-c2
libjson-c2:i386
libjson-glib-1.0-0
libk5crypto3
libk5crypto3:i386
libkactivities6
libkactivities-bin
libkactivities-models1
libkate1
libkatepartinterfaces4
libkcmutils4
libkde3support4
libkdeclarative5
libkdecore5
libkdegames6
libkdesu5
libkdeui5
libkdewebkit5
libkdnssd4
libkemoticons4
libkeyutils1
libkeyutils1:i386
libkfile4
libkhtml5
libkidletime4
libkio5
libkjsapi4
libkjsembed4
libkmediaplayer4
libkmod2
libknewstuff3-4
libknotifyconfig4
libkntlm4
libkparts4
libkpty4
libkrb5-26-heimdal
libkrb5-26-heimdal:i386
libkrb5-3
libkrb5-3:i386
libkrb5support0
libkrb5support0:i386
libkrosscore4
libktexteditor4
libkxmlrpcclient4
liblangtag1
liblangtag-common
liblcms1
liblcms1:i386
liblcms2-2
libldap-2.4-2
libldap-2.4-2:i386
liblircclient0
libllvm3.3
libllvm3.3:i386
liblockfile1
liblqr-1-0
libltdl7
libltdl7:i386
liblua5.1-0
liblua5.2-0
liblzma5
liblzma5:i386
liblzo2-2
libmad0
libmagic1
libmagickcore5
libmagickcore5-extra
libmagickwand5
libmail-sendmail-perl
libmatroska5
libmikmod2
libmimic0
libmjpegutils-2.0-0
libmms0
libmng1
libmnl0
libmodplug1
libmono-cairo4.0-cil
libmono-corlib4.0-cil
libmono-i18n4.0-cil
libmono-i18n-west4.0-cil
libmono-security4.0-cil
libmono-system4.0-cil
libmono-system-configuration4.0-cil
libmono-system-drawing4.0-cil
libmono-system-security4.0-cil
libmono-system-xml4.0-cil
libmount1
libmp3lame0
libmpc3
libmpcdec6
libmpeg2-4
libmpeg2encpp-2.0-0
libmpfr4
libmpg123-0
libmpg123-0:i386
libmplex2-2.0-0
libmspub-0.0-0
libmtdev1
libmtp9
libmxml1
libmysqlclient18
libmythes-1.2-0
libncurses5
libncurses5:i386
libncursesw5
libneon27-gnutls
libnepomuk4
libnepomukcleaner4
libnepomukcore4abi1
libnepomukquery4a
libnepomukutils4
libnetfilter-conntrack3
libnetpbm10
libnettle4
libnewt0.52
libnfnetlink0
libnice10
libnih1
libnih-dbus1
libnl-3-200
libnl-genl-3-200
libnl-route-3-200
libnotify4
libnspr4
libnspr4-0d
libnss3
libnss3-1d
libntrack0
libntrack-qt4-1
libodbc1
libofa0
libogg0
libogg0:i386
liboil0.3
libopenal1
libopenal1:i386
libopenal-data
libopencc1
libopencore-amrnb0
libopencore-amrwb0
libopenexr6
libopenjpeg2
libopenvg1-mesa
libopus0
liborbit2
liborc-0.4-0
liborc-0.4-0:i386
liborcus-0.6-0
libp11-kit0
libp11-kit0:i386
libp11-kit-gnome-keyring
libp11-kit-gnome-keyring:i386
libpackagekit-glib2-16
libpam0g
libpam-cap
libpam-ck-connector
libpam-gnome-keyring
libpam-modules
libpam-systemd
libpango1.0-0
libpango-1.0-0
libpangocairo-1.0-0
libpangoft2-1.0-0
libpangomm-1.4-1
libpangox-1.0-0
libpangoxft-1.0-0
libpaper1
libparted0debian1
libpcap0.8
libpci3
libpciaccess0
libpciaccess0:i386
libpcre3
libpcre3:i386
libpcsclite1
libpeas-1.0-0
libpeas-common
libphonon4
libpipeline1
libpixman-1-0
libplasma3
libplymouth2
libpng12-0
libpng12-0:i386
libpolkit-agent-1-0
libpolkit-backend-1-0
libpolkit-gobject-1-0
libpolkit-qt-1-1
libpoppler43
libpoppler-glib8
libpoppler-qt4-4
libpopt0
libportaudio2
libpostproc52
libprocps0
libprotobuf7
libproxy1
libpulse0
libpulse0:i386
libpulsedsp
libpulse-mainloop-glib0
libpwquality1
libpython2.7
libpython2.7-minimal
libpython2.7-stdlib
libpython3.3
libpython3.3-minimal
libpython3.3-stdlib
libpython3-stdlib
libpython-stdlib
libqapt2
libqapt2-runtime
libqca2
libqpdf10
libqt4-dbus
libqt4-declarative
libqt4-designer
libqt4-network
libqt4-opengl
libqt4-qt3support
libqt4-script
libqt4-sql
libqt4-sql-mysql
libqt4-svg
libqt4-xml
libqt4-xmlpatterns
libqtcore4
libqtgui4
libqtwebkit4
libquadmath0
libquvi7
libquvi-scripts
libraw1394-11
libreadline5
libreadline6
libreoffice
libreoffice-base
libreoffice-base-core
libreoffice-calc
libreoffice-common
libreoffice-core
libreoffice-draw
libreoffice-gnome
libreoffice-gtk
libreoffice-help-en-gb
libreoffice-help-en-us
libreoffice-impress
libreoffice-java-common
libreoffice-l10n-en-gb
libreoffice-l10n-en-za
libreoffice-math
libreoffice-pdfimport
libreoffice-report-builder-bin
libreoffice-style-galaxy
libreoffice-style-human
libreoffice-writer
libresid-builder0c2a
librest-0.7-0
librhythmbox-core7
libroken18-heimdal
libroken18-heimdal:i386
librsvg2-2
librsvg2-common
librtmp0
libsamplerate0
libsamplerate0:i386
libsane
libsane:i386
libsasl2-2
libsasl2-2:i386
libsasl2-modules
libsasl2-modules:i386
libsasl2-modules-db
libsasl2-modules-db:i386
libsbc1
libschroedinger-1.0-0
libsdl1.2debian
libsdl-image1.2
libsdl-mixer1.2
libsecret-1-0
libselinux1
libselinux1:i386
libsemanage1
libsensors4
libsepol1
libservlet3.0-java
libsgutils2-2
libshout3
libsidplay1
libsidplay2
libsigc++-2.0-0c2a
libsigsegv2
libslang2
libslv2-9
libsm6
libsm6:i386
libsmbclient
libsndfile1
libsndfile1:i386
libsnmp30
libsolid4
libsonic0
libsoprano4
libsoundtouch0
libsoup2.4-1
libsoup-gnome2.4-1
libsox2
libsox-fmt-alsa
libsox-fmt-base
libspandsp2
libspectre1
libspeechd2
libspeex1
libspeexdsp1
libspeexdsp1:i386
libsqlite3-0
libsqlite3-0:i386
libsrtp0
libss2
libssh2-1
libssh-4
libssl1.0.0
libssl1.0.0:i386
libstartup-notification0
libstdc++-4.8-dev
libstdc++6
libstdc++6:i386
libstreamanalyzer0
libstreams0
libswscale2
libsys-hostname-long-perl
libsystemd-daemon0
libsystemd-journal0
libsystemd-login0
libtag1c2a
libtag1-vanilla
libtagc0
libtalloc2
libtar0
libtasn1-3
libtasn1-3:i386
libtdb1
libtelepathy-glib0
libtevent0
libthai0
libtheora0
libthreadweaver4
libtiff5
libtiff5:i386
libtinfo5
libtinfo5:i386
libtotem-plparser17
libts-0.0-0
libtsan0
libtwolame0
libtxc-dxtn-s2tc0
libtxc-dxtn-s2tc0:i386
libudev1
libudev1:i386
libudisks2-0
libunistring0
libunity9
libunity-protocol-private0
libupnp6
libupower-glib1
liburl-dispatcher1
libusb-0.1-4
libusb-1.0-0
libusb-1.0-0:i386
libustr-1.0-1
libuuid1
libuuid1:i386
libv4l-0
libv4l-0:i386
libv4lconvert0
libv4lconvert0:i386
libva1
libva-x11-1
libvcdinfo0
libvirtodbc0
libvisio-0.0-0
libvisual-0.4-0
libvisual-0.4-plugins
libvlc5
libvlccore5
libvo-aacenc0
libvo-amrwbenc0
libvorbis0a
libvorbis0a:i386
libvorbisenc2
libvorbisenc2:i386
libvorbisfile3
libvpx1
libvpx1:i386
libwacom2
libwavpack1
libwayland-client0
libwayland-cursor0
libwayland-server0
libwbclient0
libwebp4
libwildmidi1
libwildmidi-config
libwind0-heimdal
libwind0-heimdal:i386
libwmf0.2-7
libwnck-3-0
libwrap0
libwrap0:i386
libwv-1.2-4
libx11-6
libx11-6:i386
libx11-xcb1
libx11-xcb1:i386
libx264-123
libx86-1
libxatracker1
libxau6
libxau6:i386
libxaw7
libxcb1
libxcb1:i386
libxcb-composite0
libxcb-dri2-0
libxcb-dri2-0:i386
libxcb-glx0
libxcb-glx0:i386
libxcb-keysyms1
libxcb-randr0
libxcb-render0
libxcb-shape0
libxcb-shm0
libxcb-util0
libxcb-xfixes0
libxcb-xv0
libxcomposite1
libxcomposite1:i386
libxcursor1
libxcursor1:i386
libxdamage1
libxdamage1:i386
libxdmcp6
libxdmcp6:i386
libxext6
libxext6:i386
libxfixes3
libxfixes3:i386
libxfont1
libxft2
libxi6
libxi6:i386
libxinerama1
libxinerama1:i386
libxkbcommon0
libxkbfile1
libxml2
libxml2:i386
libxml2-utils
libxmu6
libxmuu1
libxp6
libxpm4
libxpm4:i386
libxrandr2
libxrandr2:i386
libxrender1
libxrender1:i386
libxres1
libxslt1.1
libxslt1.1:i386
libxss1
libxt6
libxt6:i386
libxtst6
libxv1
libxvidcore4
libxxf86dga1
libxxf86vm1
libxxf86vm1:i386
libyajl2
libzbar0
libzeitgeist-1.0-1
libzeitgeist-2.0-0
libzephyr4
libzip2
libzvbi0
libzvbi-common
linux-headers-3.11.0-13
linux-headers-3.11.0-13-generic
linux-image-3.11.0-13-generic
linux-image-extra-3.11.0-13-generic
linux-libc-dev
lm-sensors
media-player-info
menu
module-assistant
mono-4.0-gac
mono-gac
mono-runtime
mtools
myspell-en-au
myspell-en-gb
myspell-en-za
mysql-common
mythes-en-au
mythes-en-us
nautilus
nautilus-image-manipulator
ndisgtk
ndiswrapper-common
ndiswrapper-dkms
ndiswrapper-source
ndiswrapper-utils-1.9
nepomuk-core-data
nepomuk-core-runtime
netpbm
ntrack-module-libnl-0
odbcinst
odbcinst1debian2
openjdk-7-jre
openjdk-7-jre-headless
openjdk-7-jre-lib
openoffice.org-hyphenation
oxygen-icon-theme
p7zip
p7zip-full
pgn-extract
phonon
phonon-backend-gstreamer
plasma-scriptengine-javascript
playitslowly
pm-utils
po-debconf
python3-gdbm
python3-uno
python-commandnotfound
python-compizconfig
python-gdbm
python-gst0.10
python-mako
python-markupsafe
python-nautilus
python-poster
python-support
python-zeitgeist
qapt-batch
qdbus
qgo
qtchooser
rhythmbox
rhythmbox-data
rhythmbox-mozilla
rhythmbox-plugin-cdrecorder
rhythmbox-plugins
rhythmbox-plugin-zeitgeist
sessioner
session-migration
shared-desktop-ontologies
soprano-daemon
sox
synaptic
sysinfo
syslinux
syslinux-common
syslinux-themes-debian
syslinux-themes-debian-wheezy
tango-icon-theme
tcl8.5-lib
thunderbird-locale-en
thunderbird-locale-en-gb
thunderbird-locale-en-us
tsconf
ttf-mscorefonts-er
tzdata-java
ubuntu-tweak
unetbootin
unetbootin-translations
unixodbc
uno-libs3
unrar
ure
vbetool
virtuoso-minimal
virtuoso-opensource-6.1-bin
virtuoso-opensource-6.1-common
vlc
vlc-data
vlc-nox
vlc-plugin-notify
vlc-plugin-pulse
wbritish
winbind
wine
wine1.4
wine1.4-amd64
wine1.4-i386:i386
wine-gecko1.4
wine-gecko1.4:i386
winetricks
wodim
xboard
xfce4
xfce4-artwork
xfce4-battery-plugin
xfce4-clipman
xfce4-clipman-plugin
xfce4-cpufreq-plugin
xfce4-datetime-plugin
xfce4-diskperf-plugin
xfce4-fsguard-plugin
xfce4-genmon-plugin
xfce4-goodies
xfce4-mixer
xfce4-mount-plugin
xfce4-sensors-plugin
xfce4-smartbookmark-plugin
xfce4-timer-plugin
xfce4-wavelan-plugin
xfonts-100dpi
xfonts-75dpi
xfonts-mathml
xfwm4-dbg
xfwm4-themes
xserver-xorg-glamoregl
xubuntu-restricted-addons
xubuntu-restricted-extras
zeitgeist
zeitgeist-core
zeitgeist-datahub
zlib1g
zlib1g:i386

```

@cmcanulty, during the compare, I noticed that you have compiz installed (though it doesn't appear to be running based on previous "ps" report). I'm thinking maybe it might have something to do with the window controls, if its running.

---

### Post by vasa1 on 2013-11-26
> **Toz said:**
> Agreed. There are over 1000 additional packages above and beyond the 13.10 manifest (just did a compare):
....
That list is awesome! There's mono and nautilus as well! I've seen so many posts about how Nautilus tries to take over the desktop. (I know the topic is window decorations.)
I couldn't generate the same list because 
I don't know what the 13.10 manifest is or where it's available
I too don't have a "vanilla" Xubuntu: mine is a "xubuntu-desktop --no-install-recommends" on Lubuntu 13.10 and
I don't know the command to generate such a difference. (I've used *diff* before.)

@OP, Is it possible that the computer in question is used by others with admin rights and that these people have installed software without you knowing it?

---

### Post by Toz on 2013-11-26
> I don't know what the 13.10 manifest is or where it's available
All the manifests (list of packages on the installation CD) for all the isos can be found at cdimage.ubuntu.com, in the same directory as the iso. For Xubuntu 13.10, see: [http://cdimage.ubuntu.com/xubuntu/releases/13.10/release/]("http://cdimage.ubuntu.com/xubuntu/releases/13.10/release/"). It's the .manifest file.

---

### Post by VMC on 2013-11-26
> **cmcanulty said:**
> OK I tried a reinstall and kept my home and that didn't fix so I did a clean reinstall. Ironically I wanted to do Xubuntu to eliminate the lack of menus etc in unity and it appears to have major issues also. But I don't know about how xubuntu is so configurable if configuring causes problems like this with no fix.

That first sentence might be a tell-tale sign. If I'm reading it right. Leaving home intact and still no decorations, but a new install and everything it ok.

I once had decoration issues with KDE, but when I remove my ".kde" folder  and it got rebuilt everything was normal. I needed to find the errant file that caused the mess.

Also those compiz downloads may be the problem. Do you know exactly when this started, or did you just download programs over several days without re-booting and then finally on a re-boot , the decoration issue came up?

Knowing the first sign of the issue would go a long way to find a solution, since you now have +1000 added programs.

---

### Post by vasa1 on 2013-11-26
> **Toz said:**
> All the manifests (list of packages on the installation CD) for all the isos can be found at cdimage.ubuntu.com, in the same directory as the iso. For Xubuntu 13.10, see: [http://cdimage.ubuntu.com/xubuntu/releases/13.10/release/]("http://cdimage.ubuntu.com/xubuntu/releases/13.10/release/"). It's the .manifest file.
Glad I asked :)

So the manifest list will be even longer than the actual list of software on the completion of an installation because the installation has a purge (near the end of the process) which removes quite some software: gparted and ubiquity are two easy examples to remember.

---

### Post by Toz on 2013-11-26
> **VMC said:**
> That first sentence might be a tell-tale sign. If I'm reading it right. Leaving home intact and still no decorations, but a new install and everything it ok.

I once had decoration issues with KDE, but when I remove my ".kde" folder  and it got rebuilt everything was normal. I needed to find the errant file that caused the mess.

Also those compiz downloads may be the problem. Do you know exactly when this started, or did you just download programs over several days without re-booting and then finally on a re-boot , the decoration issue came up?

Knowing the first sign of the issue would go a long way to find a solution, since you now have +1000 added programs.
Agreed. Something in there is muddling the system.

> **vasa1 said:**
> Glad I asked :)

So the manifest list will be even longer than the actual list of software on the completion of an installation because the installation has a purge (near the end of the process) which removes quite some software: gparted and ubiquity are two easy examples to remember.
True. However, using the command:
```
comm -23 <(sort installed_list) <(sort manifest)
```
...will display only those items in his list which are not in the manifest list (effectively ignoring those items).

---

### Post by vasa1 on 2013-11-27
> **Toz said:**
> ...
 However, using the command:
```
comm -23 <(sort installed_list) <(sort manifest)
```
....
Very useful. Thanks!

---

### Post by cmcanulty on 2013-11-27
I gave up on xubuntu wanted less hassles not more. I only had added real mainstream pkgs like libre office and gparted. Will try mate now but that gives keyring issues. Ubuntu used to be sooo good and now everything is difficult.

---

