---
title: "Switching Between Kodi and Steam via multiple user sessions"
date: 2015-01-15
forum: Desktop Environments
---

### Post by jorge8 on 2015-01-15
Hi all,

I've come up with a simple way to switch between Kodi (XBMC) and Steam using lightdm.  I know there's some Kodi plug-ins that launch Steam for you, but they didn't work well for me because Kodi would resume on the top-left corner in a small screen after quitting Steam. Apparently the plug-in didn't reconfigure the Xsession back to how Kodi likes it after quitting steam.  I also had sound issues because I run Kodi without pulseaudio so that I can run passthrough audio from Kodi to my AVR... this would prevent Steam from running audio to my receiver since it'd be owned exclusively by Kodi.  I didn't want to use pulseaudio under Kodi, so the best solution is to run Steam under its own session without Kodi in the background.

So, I'm using lightdm to help me switch between user accounts via linux scripts.  To do this, I created a new user account (named "steam") that automatically boots into the steam app.  This steam user session launches openbox on top of lightdm, and steam on top of openbox. I've read somewhere that steam runs more stable when on top of openbox (as opposed to running steam as a standalone app).  I'm running Ubuntu 14.04, lightdm 1.10.3, and openbox 3.5.2.

Let me know how well this setup works for you!  Post any issues you may have here and I'll do my best to help.

_More details on my setup is below:_

My setup has Kodi launch to Steam by having LightDM switch the user session to a dedicated "steam" user session with a desktop session named "Steam."  I configured lightdm to launch openbox into this "steam" user session, and configured openbox to launch steam as its startup configuration.  To make this transition into steam from Kodi, I set up a favourites entry in the Kodi ".kodi/userdata/favourites.xml" file:[INDENT]<favourite name="STEAM">System.ExecWait("**[FONT=courier new]/usr/local/bin/LightDMSwitchToSteam.sh[/FONT]**")</favourite>
[/INDENT]

I created the LightDMSwitchToSteam.sh script to include:
```
#!/bin/bash

dm-tool switch-to-user steam Steam

until [[ $(pidof openbox) ]] ; do
        sleep 1
done

pkill -KILL -u xbmc
```

Notice that this script waits for openbox to open fully before killing the xbmc user session (under which Kodi runs).

Also, in the Titan theme in Kodi, I created a top menu option "STEAM" that runs the LightDMSwitchToSteam.sh script. Selecting the STEAM menu option under Kodi switches to the lightdm session to the Steam user session without any issues for me.  I also have the steam session configured to return to Kodi as soon as the steam app quits.  To do this, I configured the "~/.config/openbox/autostart.sh" script in my "steam" user account to:

```
#!/bin/bash

pulseaudio --start

xsetroot -solid black &
/usr/games/steam &

/usr/local/bin/LightDMSwitchToKodi.sh &
```

The LightDMSwitchToKodi.sh script is as follows:
```
#!/bin/bash

until [[ $(pidof steam) ]] ; do
        sleep 1
done

while [[ $(pidof steam) ]] ; do
        sleep 1
done

dm-tool switch-to-user xbmc Kodi

until [[ $(pidof kodi.bin) ]] ; do
        sleep 1
done

pkill -KILL -u steam
```

Notice that the first loop waits for steam to launch fully before running the rest of the script.  Then, then the second loop waits for the steam app to quit before switching the user session back to xbmc (with the Kodi desktop session).  This second loop essentially waits for the user to quit the steam app, after which it returns to Kodi and stops the steam user session.

Note that you should use chown to configure the LightDMSwitchToSteam.sh script to belong to your Kodi user session and group (in my case "xbmc"), and also use chown to configure the LightDMSwitchToKodi.sh script to belong to your Steam user session and group (in my case "steam").  Also, use chmod to make both of these scripts executable.

Some other configuration files:

/etc/lightdm/lightdm.conf:
```
[LightDM]minimum-vt=1
run-directory=/run/lightdm

[SeatDefaults]
session-wrapper=/etc/X11/Xsession
pam-service=lightdm-autologin
autologin-user=xbmc
autologin-user-timeout=0
```

/usr/share/xsessions/xbmc.desktop:
```
[Desktop Entry]Name=Kodi
Comment=This session will start Kodi Media Center
Exec=kodi-standalone
TryExec=kodi-standalone
Type=Application
```

/usr/share/xsessions/steam.desktop:
```
[Desktop Entry]Name=Steam
Comment=This session will start the Steam app under Openbox
Exec=/usr/bin/openbox-session
TryExec=/usr/bin/openbox-session
Type=Application
```

Side note: I was having trouble setting up my new steam session properly at first.  When I would start the session (either via Kodi or as the initial session after booting up), I would get a black screen.  I'd see that Xorg was running, but openbox wasn't.  However, if I killed Xorg, I would get the lightdm greeter.  After a lot of digging around, I noticed that the steam user session wasn't initializing correctly, likely due to some upstart issues.  My friend and I stumbled upon the solution by installing and launching the i3 window manager under the "steam" user session (instead of launching openbox), then launching the steam app under i3.  It seems that running i3 did something to configure the steam user session to launch window managers properly.  After this, I returned the steam session's configuration to launch openbox instead of i3, and it successfully launched steam after logging in. :)

The following posts show some of the issues I was seeing before fixing the steam user session.

---

### Post by jorge8 on 2015-01-16
In case it helps, below are my running processes while the screen is black after booting into the steam session.  Am I having a problem with a failed or missing upstart process that isn't booting things all the way?  Any help is much appreciated!

```

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.1  0.0  33912  4392 ?        Ss   20:58   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    20:58   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    20:58   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   20:58   0:00 [kworker/0:0H]
root         7  0.0  0.0      0     0 ?        S    20:58   0:00 [rcu_sched]
root         8  0.0  0.0      0     0 ?        S    20:58   0:00 [rcuos/0]
root         9  0.0  0.0      0     0 ?        S    20:58   0:00 [rcuos/1]
root        10  0.0  0.0      0     0 ?        S    20:58   0:00 [rcuos/2]
root        11  0.0  0.0      0     0 ?        S    20:58   0:00 [rcuos/3]
root        12  0.0  0.0      0     0 ?        S    20:58   0:00 [rcu_bh]
root        13  0.0  0.0      0     0 ?        S    20:58   0:00 [rcuob/0]
root        14  0.0  0.0      0     0 ?        S    20:58   0:00 [rcuob/1]
root        15  0.0  0.0      0     0 ?        S    20:58   0:00 [rcuob/2]
root        16  0.0  0.0      0     0 ?        S    20:58   0:00 [rcuob/3]
root        17  0.0  0.0      0     0 ?        S    20:58   0:00 [migration/0]
root        18  0.0  0.0      0     0 ?        S    20:58   0:00 [watchdog/0]
root        19  0.0  0.0      0     0 ?        S    20:58   0:00 [watchdog/1]
root        20  0.0  0.0      0     0 ?        S    20:58   0:00 [migration/1]
root        21  0.0  0.0      0     0 ?        S    20:58   0:00 [ksoftirqd/1]
root        22  0.0  0.0      0     0 ?        S    20:58   0:00 [kworker/1:0]
root        23  0.0  0.0      0     0 ?        S<   20:58   0:00 [kworker/1:0H]
root        24  0.0  0.0      0     0 ?        S    20:58   0:00 [watchdog/2]
root        25  0.0  0.0      0     0 ?        S    20:58   0:00 [migration/2]
root        26  0.0  0.0      0     0 ?        S    20:58   0:00 [ksoftirqd/2]
root        27  0.0  0.0      0     0 ?        S    20:58   0:00 [kworker/2:0]
root        28  0.0  0.0      0     0 ?        S<   20:58   0:00 [kworker/2:0H]
root        29  0.0  0.0      0     0 ?        S    20:58   0:00 [watchdog/3]
root        30  0.0  0.0      0     0 ?        S    20:58   0:00 [migration/3]
root        31  0.0  0.0      0     0 ?        S    20:58   0:00 [ksoftirqd/3]
root        32  0.0  0.0      0     0 ?        S    20:58   0:00 [kworker/3:0]
root        33  0.0  0.0      0     0 ?        S<   20:58   0:00 [kworker/3:0H]
root        34  0.0  0.0      0     0 ?        S<   20:58   0:00 [khelper]
root        35  0.0  0.0      0     0 ?        S    20:58   0:00 [kdevtmpfs]
root        36  0.0  0.0      0     0 ?        S<   20:58   0:00 [netns]
root        37  0.0  0.0      0     0 ?        S    20:58   0:00 [khungtaskd]
root        38  0.0  0.0      0     0 ?        S<   20:58   0:00 [writeback]
root        39  0.0  0.0      0     0 ?        SN   20:58   0:00 [ksmd]
root        40  0.0  0.0      0     0 ?        SN   20:58   0:00 [khugepaged]
root        41  0.0  0.0      0     0 ?        S<   20:58   0:00 [crypto]
root        42  0.0  0.0      0     0 ?        S<   20:58   0:00 [kintegrityd]
root        43  0.0  0.0      0     0 ?        S<   20:58   0:00 [bioset]
root        44  0.0  0.0      0     0 ?        S<   20:58   0:00 [kblockd]
root        45  0.0  0.0      0     0 ?        S<   20:58   0:00 [ata_sff]
root        46  0.0  0.0      0     0 ?        S    20:58   0:00 [khubd]
root        47  0.0  0.0      0     0 ?        S<   20:58   0:00 [md]
root        48  0.0  0.0      0     0 ?        S<   20:58   0:00 [devfreq_wq]
root        50  0.0  0.0      0     0 ?        S    20:58   0:00 [kworker/0:1]
root        52  0.0  0.0      0     0 ?        S    20:58   0:00 [kswapd0]
root        53  0.0  0.0      0     0 ?        S    20:58   0:00 [fsnotify_mark]
root        54  0.0  0.0      0     0 ?        S    20:58   0:00 [ecryptfs-kthrea]
root        66  0.0  0.0      0     0 ?        S<   20:58   0:00 [kthrotld]
root        67  0.0  0.0      0     0 ?        S<   20:58   0:00 [acpi_thermal_pm]
root        68  0.0  0.0      0     0 ?        S    20:58   0:00 [kworker/1:1]
root        69  0.0  0.0      0     0 ?        S<   20:58   0:00 [ipv6_addrconf]
root        70  0.0  0.0      0     0 ?        S    20:58   0:00 [kworker/0:2]
root        89  0.0  0.0      0     0 ?        S<   20:58   0:00 [deferwq]
root        90  0.0  0.0      0     0 ?        S<   20:58   0:00 [charger_manager]
root       102  0.0  0.0      0     0 ?        S    20:58   0:00 [kworker/2:1]
root       148  0.0  0.0      0     0 ?        S<   20:58   0:00 [kpsmoused]
root       149  0.0  0.0      0     0 ?        S<   20:58   0:00 [raid5wq]
root       166  0.0  0.0      0     0 ?        S    20:58   0:00 [kworker/3:1]
root       168  0.0  0.0      0     0 ?        S    20:58   0:00 [scsi_eh_0]
root       169  0.0  0.0      0     0 ?        S<   20:58   0:00 [scsi_tmf_0]
root       170  0.0  0.0      0     0 ?        S    20:58   0:00 [scsi_eh_1]
root       171  0.0  0.0      0     0 ?        S<   20:58   0:00 [scsi_tmf_1]
root       172  0.0  0.0      0     0 ?        S    20:58   0:00 [scsi_eh_2]
root       173  0.0  0.0      0     0 ?        S<   20:58   0:00 [scsi_tmf_2]
root       174  0.0  0.0      0     0 ?        S    20:58   0:00 [scsi_eh_3]
root       175  0.0  0.0      0     0 ?        S<   20:58   0:00 [scsi_tmf_3]
root       176  0.0  0.0      0     0 ?        S    20:58   0:00 [scsi_eh_4]
root       177  0.0  0.0      0     0 ?        S<   20:58   0:00 [scsi_tmf_4]
root       178  0.0  0.0      0     0 ?        S    20:58   0:00 [scsi_eh_5]
root       179  0.0  0.0      0     0 ?        S<   20:58   0:00 [scsi_tmf_5]
root       180  0.0  0.0      0     0 ?        S    20:58   0:00 [kworker/u8:3]
root       183  0.0  0.0      0     0 ?        S    20:58   0:00 [kworker/u8:6]
root       185  0.0  0.0      0     0 ?        S    20:58   0:00 [scsi_eh_6]
root       186  0.0  0.0      0     0 ?        S<   20:58   0:00 [scsi_tmf_6]
root       187  0.0  0.0      0     0 ?        S    20:58   0:00 [scsi_eh_7]
root       188  0.0  0.0      0     0 ?        S<   20:58   0:00 [scsi_tmf_7]
root       206  0.0  0.0      0     0 ?        S    20:58   0:00 [jbd2/sda1-8]
root       207  0.0  0.0      0     0 ?        S<   20:58   0:00 [ext4-rsv-conver]
root       347  0.0  0.0  19748  2056 ?        S    20:58   0:00 upstart-udev-bridge --daemon
root       353  0.0  0.0  52016  4012 ?        Ss   20:58   0:00 /lib/systemd/systemd-udevd --daemon
root       386  0.0  0.0      0     0 ?        S    20:58   0:00 [irq/51-mei_me]
root       388  0.0  0.0      0     0 ?        S<   20:58   0:00 [kworker/2:1H]
root       393  0.0  0.0      0     0 ?        S<   20:58   0:00 [kworker/0:1H]
root       396  0.0  0.0      0     0 ?        S<   20:58   0:00 [kworker/3:1H]
root       424  0.0  0.0      0     0 ?        S<   20:58   0:00 [cfg80211]
root       429  0.0  0.0      0     0 ?        S<   20:58   0:00 [hd-audio0]
root       430  0.0  0.0      0     0 ?        S<   20:58   0:00 [hd-audio1]
root       460  0.0  0.0      0     0 ?        S<   20:58   0:00 [kvm-irqfd-clean]
root       464  0.0  0.0      0     0 ?        S<   20:58   0:00 [kworker/1:1H]
root       559  0.0  0.0      0     0 ?        S<   20:58   0:00 [led_workqueue]
root       791  0.0  0.0      0     0 ?        S<   20:58   0:00 [bioset]
root       792  0.0  0.0      0     0 ?        S    20:58   0:00 [md0_raid5]
root       796  0.0  0.0      0     0 ?        S<   20:58   0:00 [bioset]
root       797  0.0  0.0      0     0 ?        S    20:58   0:00 [md1_raid5]
root       800  0.0  0.0  15400  1864 ?        S    20:58   0:00 upstart-socket-bridge --daemon
root       910  0.0  0.0      0     0 ?        S    20:58   0:00 [jbd2/md1-8]
root       911  0.0  0.0      0     0 ?        S<   20:58   0:00 [ext4-rsv-conver]
root      1016  0.0  0.0      0     0 ?        S    20:58   0:00 [jbd2/md0-8]
root      1017  0.0  0.0      0     0 ?        S<   20:58   0:00 [ext4-rsv-conver]
root      1021  0.0  0.0      0     0 ?        S    20:58   0:00 [jbd2/sdg1-8]
root      1022  0.0  0.0      0     0 ?        S<   20:58   0:00 [ext4-rsv-conver]
root      1026  0.0  0.0      0     0 ?        S    20:58   0:00 [jbd2/sdf1-8]
root      1027  0.0  0.0      0     0 ?        S<   20:58   0:00 [ext4-rsv-conver]
message+  1082  0.0  0.0  39540  3128 ?        Ss   20:58   0:00 dbus-daemon --system --fork
root      1129  0.0  0.0  19300  2616 ?        Ss   20:58   0:00 /usr/sbin/bluetoothd
root      1147  0.0  0.0  43544  3308 ?        Ss   20:58   0:00 /lib/systemd/systemd-logind
root      1168  0.0  0.0      0     0 ?        S<   20:58   0:00 [krfcommd]
syslog    1169  0.0  0.0 256012  2800 ?        Ssl  20:58   0:00 rsyslogd
avahi     1194  0.0  0.0  32356  2884 ?        S    20:58   0:00 avahi-daemon: running [XBMCLivingRoom.local]
avahi     1195  0.0  0.0  32232   252 ?        S    20:58   0:00 avahi-daemon: chroot helper
root      1228  0.0  0.0  15412  1776 ?        S    20:58   0:00 upstart-file-bridge --daemon
root      1307  0.0  0.0  10240  3172 ?        Ss   20:58   0:00 dhclient -1 -v -pf /run/dhclient.em1.pid -lf /var/lib/dhcp/dhclient.em1.leases em1
root      1408  0.0  0.0 330244  7476 ?        Ssl  20:58   0:00 /usr/sbin/ModemManager
root      1474  0.0  0.0 345704 11752 ?        Ssl  20:58   0:00 NetworkManager
root      1486  0.0  0.0 279768  7840 ?        Sl   20:58   0:00 /usr/lib/policykit-1/polkitd --no-debug
root      1538  0.0  0.0  15828  2140 tty4     Ss+  20:58   0:00 /sbin/getty -8 38400 tty4
root      1541  0.0  0.0  15828  2060 tty5     Ss+  20:58   0:00 /sbin/getty -8 38400 tty5
root      1551  0.0  0.0  15828  2056 tty2     Ss+  20:58   0:00 /sbin/getty -8 38400 tty2
root      1552  0.0  0.0  15828  2052 tty3     Ss+  20:58   0:00 /sbin/getty -8 38400 tty3
root      1556  0.0  0.0  15828  2084 tty6     Ss+  20:58   0:00 /sbin/getty -8 38400 tty6
root      1557  0.0  0.0  30616  4972 ?        Ss   20:58   0:00 /sbin/wpa_supplicant -B -P /run/sendsigs.omit.d/wpasupplicant.pid -u -s -O /var/run/wpa_supplicant
root      1598  0.0  0.0  23664  2256 ?        Ss   20:58   0:00 cron
daemon    1605  0.0  0.0  19148   160 ?        Ss   20:58   0:00 atd
root      1625  0.0  0.0  61372  5328 ?        Ss   20:58   0:00 /usr/sbin/sshd -D
root      1631  0.0  0.0  19268  2184 ?        Ss   20:58   0:00 /usr/sbin/irqbalance
root      1689  0.0  0.0  13408  1788 ?        Ss   20:58   0:00 /sbin/mdadm --monitor --pid-file /run/mdadm/monitor.pid --daemonise --scan --syslog
root      1736  0.0  0.0  75360  5956 ?        Ss   20:58   0:00 /usr/sbin/cups-browsed
root      1750  0.0  0.0   4376  1704 ?        Ss   20:58   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
mysql     1774  0.4  0.4 1090440 76992 ?       Ssl  20:58   0:02 /usr/sbin/mysqld
root      1808  0.0  0.0 351596  8060 ?        Ssl  20:58   0:00 lightdm
root      1818  0.0  0.0 287888  7072 ?        Sl   20:58   0:00 /usr/lib/accountsservice/accounts-daemon
root      1835  0.1  0.3 174984 59744 tty7     Ss+  20:58   0:00 /usr/bin/X -core :0 -seat seat0 -auth /run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
nvidia-+  1849  0.0  0.0  17064  1716 ?        Ss   20:58   0:00 /usr/bin/nvidia-persistenced --user nvidia-persistenced
root      1878  0.0  0.0 168312  6636 ?        Sl   20:58   0:00 lightdm --session-child 12 15
root      1879  0.0  0.0      0     0 ?        S    20:58   0:00 [kauditd]
steam     1893  0.0  0.0  35740  3980 ?        Ss   20:58   0:00 init --user
steam     1947  0.0  0.0  39256  2536 ?        Ss   20:58   0:00 dbus-daemon --fork --session --address=unix:abstract=/tmp/dbus-aXfADnReyj
steam     1955  0.0  0.0  18112  2272 ?        Ss   20:58   0:00 upstart-event-bridge
steam     1969  0.0  0.0  18120   196 ?        S    20:58   0:00 upstart-dbus-bridge --daemon --session --user --bus-name session
steam     1971  0.0  0.0  18120   200 ?        S    20:58   0:00 upstart-dbus-bridge --daemon --system --user --bus-name system
steam     1973  0.0  0.0  26596   268 ?        S    20:58   0:00 upstart-file-bridge --daemon --user
steam     1974  0.0  0.0 218784 10604 ?        Sl   20:58   0:00 gnome-keyring-daemon --start
steam     1986  0.0  0.0 357268  6748 ?        Ssl  20:58   0:00 /usr/bin/ibus-daemon --daemonize --xim
steam     2000  0.0  0.0 192452  5412 ?        Sl   20:58   0:00 /usr/lib/gvfs/gvfsd
mythtv    2001  0.2  0.4 4202148 66604 ?       Ssl  20:58   0:01 /usr/bin/mythbackend --syslog local7 --user mythtv --daemon
steam     2011  0.0  0.0 276680  8464 ?        Sl   20:58   0:00 /usr/lib/ibus/ibus-dconf
steam     2012  0.0  0.1 382736 20048 ?        Sl   20:58   0:00 /usr/lib/ibus/ibus-ui-gtk3
steam     2014  0.0  0.0 280856 13436 ?        Sl   20:58   0:00 /usr/lib/ibus/ibus-x11 --kill-daemon
steam     2029  0.0  0.0 337396  5520 ?        Sl   20:58   0:00 /usr/lib/at-spi2-core/at-spi-bus-launcher
steam     2033  0.0  0.0  39124  3256 ?        S    20:58   0:00 /bin/dbus-daemon --config-file=/etc/at-spi2/accessibility.conf --nofork --print-address 3
steam     2036  0.0  0.0 124920  4904 ?        Sl   20:58   0:00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
steam     2043  0.0  0.0 200832  6224 ?        Sl   20:58   0:00 /usr/lib/ibus/ibus-engine-simple
root      2097  0.0  0.1  89024 27048 ?        Ss   20:58   0:00 /usr/bin/perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf
root      2103  0.0  0.0  15828  2084 tty1     Ss+  20:58   0:00 /sbin/getty -8 38400 tty1
ntp       2394  0.0  0.0  33512  4444 ?        Ss   20:58   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 114:123
root      2434  0.0  0.0  76860  6076 ?        Ss   20:59   0:00 /usr/sbin/cupsd -f
root      2449  0.0  0.0 109792  6528 ?        Ss   21:00   0:00 sshd: steam [priv]  
steam     2497  0.0  0.0 109792  4768 ?        S    21:00   0:00 sshd: steam@pts/3   
steam     2498  0.0  0.0  22840  5596 pts/3    Ss   21:00   0:00 -bash
root      2656  0.0  0.0      0     0 ?        S    21:04   0:00 [kworker/u8:0]
steam     2657  0.0  0.0  18204  2856 pts/3    S+   21:05   0:00 man ps
steam     2668  0.0  0.0   9556  2160 pts/3    S+   21:05   0:00 pager -s
root      2781  0.0  0.0      0     0 ?        S    21:06   0:00 [kworker/2:2]
root      3124  0.0  0.0      0     0 ?        S    21:07   0:00 [kworker/0:0]
root      3125  0.0  0.0      0     0 ?        S    21:07   0:00 [kworker/1:2]
root      3157  0.0  0.0 109792  6648 ?        Ss   21:07   0:00 sshd: steam [priv]  
steam     3205  0.0  0.0 109792  4252 ?        S    21:07   0:00 sshd: steam@pts/5   
steam     3206  1.0  0.0  22840  5580 pts/5    Ss   21:07   0:00 -bash
steam     3232  0.0  0.0  18456  2564 pts/5    R+   21:07   0:00 ps axu

```

---

### Post by jorge8 on 2015-01-21
I've looked a little deeper and noticed that there's a difference at end of the process stack between my *xbmc* session (which loads fine) and my *steam* session (which boots to a black screen).  Can someone explain to me why the *steam* user session is booting to a black screen?

**XBMC**:
```
root      1806  0.2  0.0 351596  6020 ?        Ssl  20:43   0:00 lightdmroot      1807  0.0  0.0   4452   760 ?        Ss   20:43   0:00 /bin/sh -e /proc/self/fd/9
root      1808  0.0  0.0   4352   656 ?        S    20:43   0:00 sleep 5
root      1816  1.4  0.0 287888  6972 ?        Sl   20:43   0:00 /usr/lib/accountsservice/accounts-daemon
root      1838 13.0  0.4 175380 67412 tty7     Ss+  20:43   0:00 /usr/bin/X -core :0 -seat seat0 -auth /run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
nvidia-+  1844  0.0  0.0  17064  1732 ?        Ss   20:43   0:00 /usr/bin/nvidia-persistenced --user nvidia-persistenced
root      1876  0.0  0.0 166252  6620 ?        Sl   20:43   0:00 lightdm --session-child 16 19
root      1889  0.0  0.0      0     0 ?        S    20:43   0:00 [kauditd]
root      1891  0.2  0.0 109792  6532 ?        Ss   20:43   0:00 sshd: xbmc [priv]   
lightdm   1893  0.0  0.0  57944   472 ?        Sl   20:43   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
lightdm   1896  0.0  0.0   4452   688 ?        Ss   20:43   0:00 /bin/sh /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
lightdm   1901  0.2  0.0  39340  2584 ?        Ss   20:43   0:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
lightdm   1902  4.7  0.1 601884 26676 ?        Sl   20:43   0:00 /usr/sbin/unity-greeter
lightdm   1904  0.0  0.0 337396  7420 ?        Sl   20:43   0:00 /usr/lib/at-spi2-core/at-spi-bus-launcher --launch-immediately
lightdm   1908  0.0  0.0  39124  3320 ?        S    20:43   0:00 /bin/dbus-daemon --config-file=/etc/at-spi2/accessibility.conf --nofork --print-address 3
lightdm   1911  0.0  0.0 124920  4828 ?        Sl   20:43   0:00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
lightdm   1915  0.0  0.0 192452  5524 ?        Sl   20:43   0:00 /usr/lib/gvfs/gvfsd
lightdm   1922  0.2  0.0 178184  6740 ?        Sl   20:43   0:00 /usr/lib/dconf/dconf-service
mythtv    1941  3.6  0.2 1198212 44836 ?       Ssl  20:43   0:00 /usr/bin/mythbackend --syslog local7 --user mythtv --daemon
root      1945  0.0  0.0 168312  5256 ?        Sl   20:43   0:00 lightdm --session-child 12 19
lightdm   1953  0.0  0.0  35480  3704 ?        S    20:43   0:00 init --user --startup-event indicator-services-start
lightdm   1963  1.3  0.1 443452 23540 ?        Sl   20:43   0:00 nm-applet
lightdm   1967  5.6  0.1 442168 26108 ?        Sl   20:43   0:00 /usr/lib/x86_64-linux-gnu/indicator-keyboard-service --use-gtk
lightdm   1971  1.3  0.1 661188 19680 ?        Sl   20:43   0:00 /usr/lib/unity-settings-daemon/unity-settings-daemon
lightdm   1980  0.0  0.0 330716  6276 ?        Ssl  20:43   0:00 /usr/lib/x86_64-linux-gnu/indicator-messages/indicator-messages-service
lightdm   1984  0.0  0.0 259136  4884 ?        Ssl  20:43   0:00 /usr/lib/x86_64-linux-gnu/indicator-bluetooth/indicator-bluetooth-service
lightdm   1990  0.0  0.0 274084  5608 ?        Ssl  20:43   0:00 /usr/lib/x86_64-linux-gnu/indicator-power/indicator-power-service
lightdm   2005  0.0  0.0 522664 11844 ?        Ssl  20:43   0:00 /usr/lib/x86_64-linux-gnu/indicator-datetime/indicator-datetime-service
lightdm   2008  0.3  0.0 700948  6856 ?        Ssl  20:43   0:00 /usr/lib/x86_64-linux-gnu/indicator-session/indicator-session-service
root      2010  0.6  0.0 239380  7456 ?        Sl   20:43   0:00 /usr/lib/upower/upowerd
lightdm   2013  0.0  0.0 286756  8048 ?        Ssl  20:43   0:00 /usr/lib/x86_64-linux-gnu/indicator-application/indicator-application-service
lightdm   2058  0.0  0.0  52916  5228 ?        S    20:43   0:00 /usr/lib/x86_64-linux-gnu/gconf/gconfd-2
root      2084  0.0  0.0 178000  6100 ?        Sl   20:43   0:00 /usr/lib/x86_64-linux-gnu/systemd-shim
root      2102  0.0  0.1  89000 26840 ?        Ss   20:43   0:00 /usr/bin/perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf
root      2106  0.0  0.0  15828  2140 tty1     Ss+  20:43   0:00 /sbin/getty -8 38400 tty1
colord    2112  1.6  0.0 301520  8596 ?        Sl   20:43   0:00 /usr/lib/colord/colord
xbmc      2478  0.0  0.0 109792  4056 ?        S    20:43   0:00 sshd: xbmc@pts/6    
xbmc      2479  2.0  0.0  22896  5468 pts/6    Ss   20:43   0:00 -bash
root      2555  0.0  0.0   4352   640 ?        S    20:43   0:00 sleep 0.5
xbmc      2556  0.0  0.0  18456  2596 pts/6    R+   20:43   0:00 ps -aux
```

**Steam**:
```
root      1865  0.0  0.0 277864  6000 ?        Ssl  20:33   0:00 lightdmroot      1874  0.2  0.0 287880  7012 ?        Sl   20:33   0:00 /usr/lib/accountsservice/accounts-daemon
root      1891  3.4  0.3 174988 59544 tty7     Ss+  20:33   0:00 /usr/bin/X -core :0 -seat seat0 -auth /run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
nvidia-+  1899  0.0  0.0  17064  1772 ?        Ss   20:33   0:00 /usr/bin/nvidia-persistenced --user nvidia-persistenced
root      1927  0.0  0.0 168312  6640 ?        Sl   20:33   0:00 lightdm --session-child 12 15
root      1929  0.0  0.0      0     0 ?        S    20:33   0:00 [kauditd]
steam     1943  0.1  0.0  35740  3840 ?        Ss   20:33   0:00 init --user
mythtv    1978  1.5  0.3 4128416 55468 ?       Ssl  20:33   0:00 /usr/bin/mythbackend --syslog local7 --user mythtv --daemon
steam     2004  0.0  0.0   4452   688 ?        Ss   20:33   0:00 /bin/sh -e /proc/self/fd/9
steam     2006  0.0  0.0   7204   756 ?        S    20:33   0:00 sleep 60
steam     2008  0.0  0.0  39256  2404 ?        Ss   20:33   0:00 dbus-daemon --fork --session --address=unix:abstract=/tmp/dbus-S0cZFZ3Xa9
steam     2016  0.0  0.0  18112  2304 ?        Ss   20:33   0:00 upstart-event-bridge
steam     2027  0.0  0.0 218784  6504 ?        Sl   20:33   0:00 gnome-keyring-daemon --start
steam     2034  0.0  0.0  18120   200 ?        S    20:33   0:00 upstart-dbus-bridge --daemon --system --user --bus-name system
steam     2038  0.0  0.0  26596   272 ?        S    20:33   0:00 upstart-file-bridge --daemon --user
steam     2041  0.0  0.0  18120   204 ?        S    20:33   0:00 upstart-dbus-bridge --daemon --session --user --bus-name session
steam     2048  0.0  0.0 357268  6588 ?        Ssl  20:33   0:00 /usr/bin/ibus-daemon --daemonize --xim
steam     2062  0.0  0.0 192452  5376 ?        Sl   20:33   0:00 /usr/lib/gvfs/gvfsd
steam     2069  0.0  0.0 276680  6128 ?        Sl   20:33   0:00 /usr/lib/ibus/ibus-dconf
steam     2070  0.2  0.1 382736 20088 ?        Sl   20:33   0:00 /usr/lib/ibus/ibus-ui-gtk3
steam     2072  0.0  0.0 280856 11308 ?        Sl   20:33   0:00 /usr/lib/ibus/ibus-x11 --kill-daemon
steam     2080  0.0  0.0 337396  5560 ?        Sl   20:33   0:00 /usr/lib/at-spi2-core/at-spi-bus-launcher
steam     2084  0.0  0.0  39124  3264 ?        S    20:33   0:00 /bin/dbus-daemon --config-file=/etc/at-spi2/accessibility.conf --nofork --print-address 3
steam     2087  0.0  0.0 124920  4956 ?        Sl   20:33   0:00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
steam     2094  0.0  0.0 200832  6376 ?        Sl   20:33   0:00 /usr/lib/ibus/ibus-engine-simple
root      2101  0.0  0.0 109792  6624 ?        Ss   20:33   0:00 sshd: steam [priv]  
root      2355  0.0  0.1  88976 26976 ?        Ss   20:33   0:00 /usr/bin/perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf
root      2360  0.0  0.0  15828  2080 tty1     Ss+  20:33   0:00 /sbin/getty -8 38400 tty1
steam     2460  0.0  0.0 109792  4064 ?        S    20:33   0:00 sshd: steam@pts/7   
steam     2461  0.3  0.0  22880  5856 pts/7    Ss   20:33   0:00 -bash
root      2496  0.0  0.0      0     0 ?        S    20:33   0:00 [kworker/1:2]
ntp       2570  0.0  0.0  33512  4420 ?        Ss   20:33   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 114:123
root      2585  0.0  0.0   4352   636 ?        S    20:33   0:00 sleep 0.5
steam     2586  0.0  0.0  18456  2644 pts/7    R+   20:33   0:00 ps -aux
```

The first difference that I see is that the *steam* session makes a call to: gnome-keyring-daemon --start
whereas the *xbmc* session makes a call to: /usr/bin/gnome-keyring-daemon --daemonize --login

After this, the *steam* session seems to be stuck executing some upstart scripts, whereas the *xbmc* session loads the greeter.  So is the problem in the way my *steam* user session is calling gnome-keyring-daemon?  Does anyone know how I can fix this?

---

