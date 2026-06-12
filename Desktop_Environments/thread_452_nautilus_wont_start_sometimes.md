---
title: "nautilus wont start sometimes"
date: 2004-10-13
forum: Desktop Environments
---

### Post by rupert on 2004-10-13
Hi,
since today i have the problem that i cant start nautilus and others apps like the gnome-theme-manager.
The loading icon disapears after a while.
when i start it on the console nothing happens, the cursor is blinking,
waiting for some minutes now.
I think one process is hanging but which?

```
root@ubuntu&#58;/home/rupert # ps aux
USER       PID %CPU %MEM   VSZ  RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  1492  512 ?        S    16&#58;15   0&#58;00 init &#91;2&#93;
root         2  0.0  0.0     0    0 ?        S    16&#58;15   0&#58;00 &#91;migration/0&#93;
root         3  0.0  0.0     0    0 ?        SN   16&#58;15   0&#58;00 &#91;ksoftirqd/0&#93;
root         4  0.0  0.0     0    0 ?        S    16&#58;15   0&#58;00 &#91;migration/1&#93;
root         5  0.0  0.0     0    0 ?        SN   16&#58;15   0&#58;00 &#91;ksoftirqd/1&#93;
root         6  0.0  0.0     0    0 ?        S&lt;   16&#58;15   0&#58;00 &#91;events/0&#93;
root         7  0.0  0.0     0    0 ?        S&lt;   16&#58;15   0&#58;00 &#91;events/1&#93;
root         8  0.0  0.0     0    0 ?        S&lt;   16&#58;15   0&#58;00 &#91;khelper&#93;
root         9  0.0  0.0     0    0 ?        S&lt;   16&#58;15   0&#58;00 &#91;kacpid&#93;
root        46  0.0  0.0     0    0 ?        S&lt;   16&#58;15   0&#58;03 &#91;kblockd/0&#93;
root        47  0.0  0.0     0    0 ?        S&lt;   16&#58;15   0&#58;00 &#91;kblockd/1&#93;
root        57  0.0  0.0     0    0 ?        S    16&#58;15   0&#58;00 &#91;pdflush&#93;
root        58  0.0  0.0     0    0 ?        S    16&#58;15   0&#58;01 &#91;pdflush&#93;
root        59  0.0  0.0     0    0 ?        S    16&#58;15   0&#58;04 &#91;kswapd0&#93;
root        60  0.0  0.0     0    0 ?        S&lt;   16&#58;15   0&#58;00 &#91;aio/0&#93;
root        61  0.0  0.0     0    0 ?        S&lt;   16&#58;15   0&#58;00 &#91;aio/1&#93;
root       197  0.0  0.0     0    0 ?        S    16&#58;15   0&#58;00 &#91;kseriod&#93;
root       258  0.0  0.0     0    0 ?        S&lt;   16&#58;15   0&#58;00 &#91;ata/0&#93;
root       259  0.0  0.0     0    0 ?        S&lt;   16&#58;15   0&#58;00 &#91;ata/1&#93;
root       260  0.0  0.0     0    0 ?        S    16&#58;15   0&#58;00 &#91;scsi_eh_0&#93;
root       261  0.0  0.0     0    0 ?        S    16&#58;15   0&#58;00 &#91;scsi_eh_1&#93;
root       267  0.0  0.0     0    0 ?        S    16&#58;15   0&#58;00 &#91;khubd&#93;
root       363  0.0  0.0     0    0 ?        S    16&#58;15   0&#58;00 &#91;kjournald&#93;
root       451  0.0  0.0  1472  376 ?        S&lt;s  16&#58;15   0&#58;00 udevd
root      1353  0.0  0.0     0    0 ?        S    16&#58;15   0&#58;00 &#91;scsi_eh_2&#93;
root      1805  0.0  0.0     0    0 ?        S    16&#58;15   0&#58;00 &#91;kjournald&#93;
root      1806  0.0  0.0     0    0 ?        S    16&#58;15   0&#58;00 &#91;kjournald&#93;
root      1807  0.0  0.0     0    0 ?        S    16&#58;15   0&#58;01 &#91;kjournald&#93;
root      2209  0.0  0.0     0    0 ?        S    16&#58;15   0&#58;00 &#91;pciehpd_event&#93;
root      2224  0.0  0.0     0    0 ?        S    16&#58;15   0&#58;00 &#91;shpchpd_event&#93;
root      3545  0.0  0.0     0    0 ?        S    16&#58;15   0&#58;00 &#91;scsi_eh_4&#93;
root      3551  0.0  0.0     0    0 ?        S    16&#58;15   0&#58;00 &#91;usb-storage&#93;
root      4461  0.0  0.0     0    0 ?        S    16&#58;16   0&#58;00 &#91;khpsbpkt&#93;
root      4480  0.0  0.0     0    0 ?        S    16&#58;16   0&#58;00 &#91;knodemgrd_0&#93;
root      4822  0.0  0.0  2096  988 ?        Ss   16&#58;16   0&#58;00 dhclient3 -pf /var/run/dhclient.eth0.pid
daemon    4834  0.0  0.0  1600  448 ?        Ss   16&#58;16   0&#58;00 /sbin/portmap
root      5153  0.0  0.0  1540  604 ?        Ss   16&#58;16   0&#58;00 /sbin/syslogd
root      5170  0.0  0.1  2392 1480 ?        Ss   16&#58;16   0&#58;00 /sbin/klogd
root      5269  0.0  0.0  1500  600 ?        Ss   16&#58;16   0&#58;00 /usr/sbin/acpid -c /etc/acpi/events -s /vcupsys    5304  0.0  0.2  5436 2528 ?        Ss   16&#58;16   0&#58;13 /usr/sbin/cupsd
message   5324  0.0  0.0  2040  956 ?        Ss   16&#58;16   0&#58;00 /usr/bin/dbus-daemon-1 --system
hal       5328  0.0  0.4  5816 4480 ?        Ss   16&#58;16   0&#58;04 /usr/sbin/hald --drop-privileges
rupert    5348 31.4  0.1  3112 1652 ?        Rs   16&#58;16  71&#58;36 /usr/sbin/famd -T 0
root      5362  0.0  0.0  1492  428 ?        Ss   16&#58;16   0&#58;00 /usr/sbin/inetd
root      5601  0.0  0.1  2904 1124 ?        Ss   16&#58;16   0&#58;00 /usr/lib/postfix/master
postfix   5605  0.0  0.1  2944 1104 ?        S    16&#58;16   0&#58;00 qmgr -l -t fifo -u -c
root      5669  0.0  0.0  1544  364 ?        Ss   16&#58;16   0&#58;00 /sbin/mdadm -F -m root -s
daemon    5680  0.0  0.0  1676  628 ?        Ss   16&#58;16   0&#58;00 /usr/sbin/atd
root      5691  0.0  0.0  1744  712 ?        Ss   16&#58;16   0&#58;00 /usr/sbin/cron
root      5717  0.0  0.2  8912 2352 ?        Ss   16&#58;16   0&#58;00 /usr/bin/gdm
root      5727  0.0  0.2  9484 3000 ?        S    16&#58;16   0&#58;00 /usr/bin/gdm
root      5877  5.2  4.8 118656 49924 ?      RL   16&#58;16  11&#58;59 /usr/X11R6/bin/X &#58;0 -br -audit 0 -auth /vroot      5928  0.0  0.0  1496  460 tty1     Ss+  16&#58;16   0&#58;00 /sbin/getty 38400 tty1
root      5929  0.0  0.0  1496  460 tty2     Ss+  16&#58;16   0&#58;00 /sbin/getty 38400 tty2
root      5930  0.0  0.0  1496  460 tty3     Ss+  16&#58;16   0&#58;00 /sbin/getty 38400 tty3
root      5931  0.0  0.0  1496  460 tty4     Ss+  16&#58;16   0&#58;00 /sbin/getty 38400 tty4
root      5932  0.0  0.0  1496  460 tty5     Ss+  16&#58;16   0&#58;00 /sbin/getty 38400 tty5
root      5933  0.0  0.0  1496  460 tty6     Ss+  16&#58;16   0&#58;00 /sbin/getty 38400 tty6
rupert    6107  0.0  0.9 16900 9692 ?        Ss   16&#58;16   0&#58;02 x-session-manager
rupert    6153  0.0  0.0  2924  872 ?        Ss   16&#58;16   0&#58;00 /usr/bin/ssh-agent /usr/bin/dbus-launch -rupert    6157  0.0  0.0  1936  704 ?        Ss   16&#58;16   0&#58;00 dbus-daemon-1 --fork --print-pid 8 --prinrupert    6159  0.0  0.8 10612 8920 ?        S    16&#58;16   0&#58;02 /usr/lib/gconf2/gconfd-2 5
rupert    6162  0.0  0.0  2220  988 ?        S    16&#58;16   0&#58;00 /usr/bin/gnome-keyring-daemon
rupert    6164  0.2  0.4  5856 4512 ?        Rs   16&#58;16   0&#58;36 /usr/bin/esd -terminate -nobeeps -as 2 -srupert    6166  0.0  0.2  5276 2904 ?        Ss   16&#58;16   0&#58;00 /usr/lib/bonobo-activation/bonobo-activatrupert    6168  0.0  0.8 18092 8948 ?        S    16&#58;16   0&#58;02 /usr/lib/control-center/gnome-settings-darupert    6178  0.0  0.1  3732 1940 ?        S    16&#58;16   0&#58;03 xscreensaver -nosplash
rupert    6202  0.0  0.2  7652 2708 ?        Ss   16&#58;16   0&#58;04 gnome-smproxy --sm-config-prefix /.gnome-rupert    6204  0.3  0.7 12328 8156 ?        Ss   16&#58;16   0&#58;41 metacity --sm-save-file 1097662327-15443-rupert    6210  0.1  1.3 20736 13856 ?       Ss   16&#58;16   0&#58;15 gnome-panel --sm-config-prefix /gnome-panrupert    6212  0.0  0.6 32036 7076 ?        Ss   16&#58;16   0&#58;07 gnome-cups-icon --sm-config-prefix /gnomerupert    6214  0.0  0.8 51852 8332 ?        Ss   16&#58;16   0&#58;00 /usr/lib/evolution/2.0/evolution-alarm-norupert    6218  0.1  1.4 25640 15200 ?       Ss   16&#58;16   0&#58;13 gaim --session 117f0000010001097085233000rupert    6221  0.0  0.3 15740 3760 ?        S    16&#58;16   0&#58;00 /usr/lib/gnome-vfs2/gnome-vfs-daemon --oarupert    6223  0.5  3.1 49260 32376 ?       Ss   16&#58;16   1&#58;20 /usr/bin/python /usr/bin/gdesklets --sm-crupert    6228  0.0  0.8 16592 8552 ?        Ss   16&#58;16   0&#58;03 /usr/lib/gnome-panel/clock-applet
rupert    6236  0.0  0.5 61228 5672 ?        S    16&#58;16   0&#58;00 /usr/lib/evolution/evolution-data-server-rupert    6262  0.2  1.0 17336 10440 ?       S    16&#58;16   0&#58;27 /usr/lib/gnome-panel/wnck-applet --oaf-acrupert    6273  0.0  0.7 14844 7304 ?        S    16&#58;16   0&#58;01 /usr/lib/gnome-panel/notification-area-aprupert    6542  2.6  1.4 20532 14612 ?       S    16&#58;24   5&#58;53 gnome-system-monitor
root      7270  0.0  0.0  1344  296 ?        S    16&#58;32   0&#58;00 /usr/bin/vmnet-bridge -d /var/run/vmnet-broot      7282  0.0  0.0  1632  540 ?        Ss   16&#58;32   0&#58;00 /usr/bin/vmnet-natd -d /var/run/vmnet-natroot      7309  0.0  0.0  1340  292 ?        S    16&#58;33   0&#58;00 /usr/bin/vmnet-netifup -d /var/run/vmnet-root      7316  0.0  0.0  1340  292 ?        S    16&#58;33   0&#58;00 /usr/bin/vmnet-netifup -d /var/run/vmnet-root      7360  0.0  0.0  1664  664 ?        Ss   16&#58;33   0&#58;00 /usr/bin/vmnet-dhcpd -cf /etc/vmware/vmneroot      7361  0.0  0.0  1660  656 ?        Ss   16&#58;33   0&#58;00 /usr/bin/vmnet-dhcpd -cf /etc/vmware/vmneroot      7363  0.0  0.1  2672 1248 ?        Ss   16&#58;33   0&#58;00 /usr/bin/vmware-nmbd -D -l /dev/null -s /root      7399  0.0  0.1  3656 1408 ?        Ss   16&#58;33   0&#58;00 /usr/bin/vmware-smbd -D -l /dev/null -s /rupert    8732  0.0  0.4  9416 4316 ?        S    17&#58;38   0&#58;00 gksudo /usr/sbin/synaptic
root      8733  0.1  2.4 33504 25268 ?       S    17&#58;38   0&#58;15 /usr/sbin/synaptic
rupert   23081  0.0  0.0  1932  736 ?        S    18&#58;15   0&#58;03 /opt/ccxstream/ccxstream -f -F /var/run/croot     23141  0.0  0.0  2172  648 ?        S    18&#58;17   0&#58;00 gnome-pty-helper
rupert   23352  1.1  2.3 83080 24592 ?       S    18&#58;24   1&#58;08 rhythmbox
rupert   24907  0.2  1.1 25528 11528 ?       S    19&#58;25   0&#58;05 xchat
postfix  25204  0.0  0.1  2916 1068 ?        S    19&#58;36   0&#58;00 pickup -l -t fifo -u -c
rupert   25881  7.0  2.9 91012 30860 ?       S    19&#58;58   0&#58;26 /usr/lib/mozilla-firefox/firefox-bin -a froot     25970  0.0  0.2  4188 2512 ?        S    19&#58;59   0&#58;00 /usr/lib/gconf2/gconfd-2 13
rupert   25992  0.5  1.3 37284 14032 ?       S    19&#58;59   0&#58;01 gnome-terminal
rupert   25993  0.0  0.0  2168  652 ?        S    19&#58;59   0&#58;00 gnome-pty-helper
rupert   25994  0.0  0.1  3020 1680 pts/0    Ss+  19&#58;59   0&#58;00 bash
rupert   26025  0.0  0.1  3012 1656 pts/2    Ss   20&#58;00   0&#58;00 bash
root     26028  0.0  0.1  3024 1680 pts/2    S    20&#58;00   0&#58;00 bash
rupert   26100  0.3  0.7 18444 8008 ?        Ss   20&#58;03   0&#58;00 nautilus --sm-config-prefix /nautilus-uI5root     26129  0.0  0.0  2480  832 pts/2    R+   20&#58;04   0&#58;00 ps aux


```
lot of shit runnung, but maybe it helps

when i log off or restart the xserver gnome wont start, it hangs right after the login.

Im so unhappy it took me 2 days to configure my system to my needs and now it wont run :(.
I moved my home and /usr to new partitions but i dont think it has something to do with it, because everthing runs fine, for a while.

---

### Post by rupert on 2004-10-14
no one,
its getting boring some when i try to open some folders it also crashes.

---

### Post by florizs on 2005-01-17
I have the same Problem Concerning Nautilus,
the thing is it keeps getting worse, crashing every 30 minutes at first, and now every 10 minutes.
after restarting X the Splash screen also hangs after logging in again.

I don't know how it is in your case but now Mozilla-Firefox Hangs after downloading and evolution hangs after every "browse" button click.

I'm guessing Nautilus Hangs somewhere since it is in the GNOME and Evolution core.
but since I'm a newbie I just don't know

any advice would be great!

---

### Post by neilmc on 2005-01-19
I wouldn't mind betting that it is the famd process. From memory I think fam is "File Alteration Monitor" and allows Nautilus to auto refresh contents of a window when things happen like addition of files etc.

You can test if it is fam causing the problem by running sudo /etc/init.d/fam restart

And see if nautilus will start. Apart from nautilus not starting I was getting windows mysteriously closing with no message and nautilus crashes offering to restart Nautilus and then it wouldn't start.

While this was going on if I restarted X with Ctrl+Alt+Backspace the desktop wouldn't fully load.

I got tired of restarting fam so just killed it. Everything seems stable and nice now. You will need to Ctrl+r to reload a Nautilus window if you want to make sure that it is showing up to date contents if you kill fam.

---

### Post by florizs on 2005-02-09
@nielmnc
thanks for the tip,
the problem here stops for a couple of times when I delete .gnome and .gnome2 but after a While it returns.
next time it does i'll try your method.
^,^

---

### Post by florizs on 2005-03-17
killing the fam or restarting famd doesn't do anything but,
I've solved the problem for a bit ,nautilus and other programs don't hang as mutch.

It had something to do with a faulty mounted NTFS partition I had my partition mounted writable which caused some process to hang.
anyway i'll keep trying but for now removing .gnome and rebooting is the only real solution.

---

### Post by florizs on 2006-03-02
Update, I have moved to hoary now and the problem is gone.
thanks everyone for the help

---

