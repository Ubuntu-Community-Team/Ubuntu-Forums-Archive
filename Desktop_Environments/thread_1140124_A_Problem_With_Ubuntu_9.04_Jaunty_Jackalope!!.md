---
title: "A Problem With Ubuntu 9.04 Jaunty Jackalope!!"
date: 2009-04-27
forum: Desktop Environments
---

### Post by delphiexile on 2009-04-27
Hi everybody;

I've installed the new ubuntu distribution , Jaunty Jackalope, and I encounter some problems:

1- The system is so Fast , this is good !! But not for a long time , because after a short time of using fully my pc resources (1Gb of RAM and 2Gb of SWAP , a CPU of 3.0GB Intel Pentium, with an Intel Graphic Card of 256Mb of memory) , I feel that the system becomes slow , I tried to check up why , and I found that a process named 'mono' takes 450-500 Mb of my RAM.. I wanted to know which file is running that process and I found it in this directory: /tmp/orbit-fethi     (Note: fethi is the username). The problem is that I didn't have this problem with Interpid.

2- The second problem is that Alarm Clock blocks my operating system when I run it , I mean that the system doesn't respond after 1sec of running this last; The program worked perfectly with Interpid , I have removed it because Ctrl+Alt+Backspace is deactivated in This distribution and I can't fix this problem too.

3- Other things in this version are awesome and work perfect, except GNOME , I think it is a little bit slower than the previous version , and I don't know whether there is a solution to make it faster !!! (Compiz Fusion Window Animation Effects is activated)

And Thank you for helping me.

---

### Post by delphiexile on 2009-04-27
Is there anyone here!!!!!

---

### Post by cariboo on 2009-04-27
Please don't bump a thread until 24 hours has elapsed. Read the [thread=885580]Forum Do's and Don't's[/thread].

To answer your question, your problem is more that likely video driver problems, have a look at this [thread=1136738]thread[/thread] and [thread=1130582]this one[/thread] for help in solving your problem.

Is your alarm clock program compatible with python 2.6?

If you repair the graphics, gnome will run faser.

---

### Post by directhex on 2009-04-27
> **delphiexile said:**
> 1- The system is so Fast , this is good !! But not for a long time , because after a short time of using fully my pc resources (1Gb of RAM and 2Gb of SWAP , a CPU of 3.0GB Intel Pentium, with an Intel Graphic Card of 256Mb of memory) , I feel that the system becomes slow , I tried to check up why , and I found that a process named 'mono' takes 450-500 Mb of my RAM.. I wanted to know which file is running that process and I found it in this directory: /tmp/orbit-fethi     (Note: fethi is the username). The problem is that I didn't have this problem with Interpid.

There should be no mono processes running by default on your system. Can you paste the full output of "ps -ef" from during one of these problematic periods?

---

### Post by delphiexile on 2009-04-29
> **directhex said:**
> There should be no mono processes running by default on your system. Can you paste the full output of "ps -ef" from during one of these problematic periods?

OK, I could stop this mono process now , but i still have a problem : the pc is slow (means it doesn't respond instantly) without using all the system ressource, this is the result of the ps -ef command:

```

UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 04:12 ?        00:00:01 /sbin/init
root         2     0  0 04:12 ?        00:00:00 [kthreadd]
root         3     2  0 04:12 ?        00:00:00 [migration/0]
root         4     2  0 04:12 ?        00:00:02 [ksoftirqd/0]
root         5     2  0 04:12 ?        00:00:00 [watchdog/0]
root         6     2  0 04:12 ?        00:00:00 [migration/1]
root         7     2  0 04:12 ?        00:00:01 [ksoftirqd/1]
root         8     2  0 04:12 ?        00:00:00 [watchdog/1]
root         9     2  0 04:12 ?        00:00:00 [events/0]
root        10     2  0 04:12 ?        00:00:00 [events/1]
root        11     2  0 04:12 ?        00:00:00 [khelper]
root        12     2  0 04:12 ?        00:00:00 [kstop/0]
root        13     2  0 04:12 ?        00:00:00 [kstop/1]
root        14     2  0 04:12 ?        00:00:00 [kintegrityd/0]
root        15     2  0 04:12 ?        00:00:00 [kintegrityd/1]
root        16     2  0 04:12 ?        00:00:00 [kblockd/0]
root        17     2  0 04:12 ?        00:00:00 [kblockd/1]
root        18     2  0 04:12 ?        00:00:00 [kacpid]
root        19     2  0 04:12 ?        00:00:00 [kacpi_notify]
root        20     2  0 04:12 ?        00:00:00 [cqueue]
root        21     2  0 04:12 ?        00:00:00 [ata/0]
root        22     2  0 04:12 ?        00:00:00 [ata/1]
root        23     2  0 04:12 ?        00:00:00 [ata_aux]
root        24     2  0 04:12 ?        00:00:00 [ksuspend_usbd]
root        25     2  0 04:12 ?        00:00:00 [khubd]
root        26     2  0 04:12 ?        00:00:00 [kseriod]
root        27     2  0 04:12 ?        00:00:00 [kmmcd]
root        28     2  0 04:12 ?        00:00:00 [btaddconn]
root        29     2  0 04:12 ?        00:00:00 [btdelconn]
root        31     2  0 04:12 ?        00:00:02 [pdflush]
root        32     2  0 04:12 ?        00:00:15 [kswapd0]
root        33     2  0 04:12 ?        00:00:00 [aio/0]
root        34     2  0 04:12 ?        00:00:00 [aio/1]
root        35     2  0 04:12 ?        00:00:00 [ecryptfs-kthrea]
root        38     2  0 04:12 ?        00:00:00 [scsi_eh_0]
root        39     2  0 04:12 ?        00:00:01 [scsi_eh_1]
root        40     2  0 04:12 ?        00:00:00 [kstriped]
root        41     2  0 04:12 ?        00:00:00 [kmpathd/0]
root        42     2  0 04:12 ?        00:00:00 [kmpathd/1]
root        43     2  0 04:12 ?        00:00:00 [kmpath_handlerd]
root        44     2  0 04:12 ?        00:00:00 [ksnapd]
root        45     2  0 04:12 ?        00:00:06 [kondemand/0]
root        46     2  0 04:12 ?        00:00:04 [kondemand/1]
root        47     2  0 04:12 ?        00:00:00 [krfcommd]
root       707     2  0 04:12 ?        00:00:07 [kjournald2]
root       841     1  0 04:12 ?        00:00:00 /sbin/udevd --daemon
root      1455     2  0 04:12 ?        00:00:00 [kpsmoused]
root      1852     2  0 04:12 ?        00:00:00 [kjournald2]
root      2472     1  0 04:12 tty4     00:00:00 /sbin/getty 38400 tty4
root      2473     1  0 04:12 tty5     00:00:00 /sbin/getty 38400 tty5
root      2476     1  0 04:12 tty2     00:00:00 /sbin/getty 38400 tty2
root      2479     1  0 04:12 tty3     00:00:00 /sbin/getty 38400 tty3
root      2480     1  0 04:12 tty6     00:00:00 /sbin/getty 38400 tty6
root      2553     1  0 04:12 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
syslog    2598     1  0 04:12 ?        00:00:00 /sbin/syslogd -u syslog
root      2621     1  0 04:12 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      2623     1  0 04:12 ?        00:00:00 /sbin/klogd -P /var/run/klogd/kmsg
108       2646     1  0 04:12 ?        00:00:02 /bin/dbus-daemon --system
root      2674     1  0 04:12 ?        00:00:00 /usr/sbin/console-kit-daemon
chipcard  2773     1  0 04:12 ?        00:00:00 /usr/sbin/chipcardd4 --pidfile /var/run/chipcard/chipcardd4.pid --exit-on-err
root      2823     1  0 04:12 ?        00:00:00 /usr/sbin/winbindd
111       2845     1  0 04:12 ?        00:00:01 /usr/sbin/hald
root      2846  2845  0 04:12 ?        00:00:00 hald-runner
root      2879  2846  0 04:12 ?        00:00:00 hald-addon-input: Listening on /dev/input/event1 /dev/input/event0 /dev/input
root      2916  2823  0 04:12 ?        00:00:00 /usr/sbin/winbindd
root      2922  2846  0 04:12 ?        00:00:01 hald-addon-storage: polling /dev/sr0 (every 2 sec)
root      2923  2846  0 04:12 ?        00:00:00 /usr/lib/hal/hald-addon-cpufreq
111       2924  2846  0 04:12 ?        00:00:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      2945     1  0 04:12 ?        00:00:00 /usr/sbin/bluetoothd
root      2978     1  0 04:12 ?        00:00:00 /usr/sbin/gdm
root      2981  2978  0 04:12 ?        00:00:00 /usr/sbin/gdm
root      3007     1  0 04:12 ?        00:00:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pi
root      3026     1  0 04:12 ?        00:00:00 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log
root      3028     1  0 04:12 ?        00:00:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.
avahi     3031     1  0 04:12 ?        00:00:00 avahi-daemon: registering [fethi-desktop.local]
avahi     3032  3031  0 04:12 ?        00:00:00 avahi-daemon: chroot helper
root      3055     1  0 04:12 ?        00:00:00 /usr/sbin/cupsd
root      3083     1  0 04:12 ?        00:00:00 /usr/bin/system-tools-backends
daemon    3162     1  0 04:12 ?        00:00:00 /usr/sbin/atd
root      3190     1  0 04:12 ?        00:00:00 /usr/sbin/cron
root      3233     1  0 04:12 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  3235  3233  0 04:12 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  3236  3233  0 04:12 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  3240  3233  0 04:12 ?        00:00:00 /usr/sbin/apache2 -k start
root      3387     1  0 04:12 ?        00:00:00 /usr/bin/timidity -Os -iAD
root      3393     1  0 04:12 tty1     00:00:00 /sbin/getty 38400 tty1
chipcard  3394  2773  0 04:12 ?        00:00:39 /usr/sbin/chipcardd4 --pidfile /var/run/chipcard/chipcardd4.pid --exit-on-err
root      4334  2981  7 04:15 tty7     00:09:37 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt
gdm       4358     1  0 04:15 ?        00:00:00 dbus-launch --autolaunch 950c8bae20f874b4be280b9249f21b88 --binary-syntax --c
gdm       4359     1  0 04:15 ?        00:00:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
fethi     4366     1  0 04:15 ?        00:00:00 /usr/bin/gnome-keyring-daemon --daemonize --login
fethi     4378  2981  0 04:15 ?        00:00:00 x-session-manager
fethi     4476  4378  0 04:15 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-se
fethi     4479     1  0 04:15 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seah
fethi     4480     1  0 04:15 ?        00:00:59 //bin/dbus-daemon --fork --print-pid 6 --print-address 9 --session
fethi     4488     1  0 04:15 ?        00:00:01 /usr/lib/libgconf2-4/gconfd-2
fethi     4499  4378  0 04:15 ?        00:00:00 /usr/bin/seahorse-agent --execute x-session-manager
fethi     4502     1  0 04:15 ?        00:00:00 /usr/lib/gvfs/gvfsd
fethi     4508     1  0 04:15 ?        00:00:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/fethi/.gvfs
fethi     4517     1  0 04:15 ?        00:00:02 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
fethi     4523  4378  0 04:15 ?        00:00:00 /bin/sh /usr/bin/compiz
fethi     4581  4523  0 04:15 ?        00:00:22 /usr/bin/compiz.real --ignore-desktop-hints --replace --indirect-rendering --
fethi     4582  4378  0 04:15 ?        00:00:27 gnome-panel
fethi     4583  4378  1 04:15 ?        00:02:02 nautilus
fethi     4585     1  0 04:15 ?        00:00:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-outpu
fethi     4590  4378  0 04:15 ?        00:00:00 python /usr/share/system-config-printer/applet.py
fethi     4596  4378  0 04:15 ?        00:00:00 bluetooth-applet
fethi     4598     1  0 04:15 ?        00:00:00 /usr/lib/gvfs/gvfs-hal-volume-monitor
fethi     4600     1  0 04:15 ?        00:00:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_Tras
fethi     4605     1  0 04:15 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
fethi     4606  4378  0 04:15 ?        00:00:02 tracker-applet
fethi     4607  4378  0 04:15 ?        00:00:00 nm-applet --sm-disable
fethi     4610     1  0 04:15 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.5 /org/gtk/gvfs/exec_spaw/0
fethi     4611  4378  0 04:15 ?        00:00:00 update-notifier --startup-delay=60
fethi     4614     1  0 04:15 ?        00:00:00 gnome-power-manager
fethi     4618     1  0 04:15 ?        00:00:00 /usr/lib/notify-osd/notify-osd
fethi     4634     1  0 04:15 ?        00:00:01 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_In
fethi     4638     1  0 04:15 ?        00:00:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApp
fethi     4639     1  0 04:15 ?        00:00:00 /usr/lib/fast-user-switch-applet/fast-user-switch-applet --oaf-activate-iid=O
fethi     4640  4581  0 04:15 ?        00:00:00 /bin/sh -c /usr/bin/compiz-decorator
fethi     4641  4640  0 04:15 ?        00:00:00 /bin/sh /usr/bin/compiz-decorator
fethi     4643  4641  0 04:15 ?        00:00:08 /usr/bin/gtk-window-decorator
fethi     4649     1  0 04:15 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.5 /org/gtk/gvfs/exec_spaw/1
fethi     4660     1  0 04:15 ?        00:00:01 minbar
fethi     4668     1  0 04:16 ?        00:00:08 gnome-screensaver
fethi     4838     1  3 04:18 ?        00:03:56 /usr/lib/firefox-3.0.9/firefox
root      5889     1  0 05:20 ?        00:00:00 /usr/bin/perl /usr/share/system-tools-backends-2.0/scripts/SystemToolsBackend
fethi    18880     1  0 05:31 ?        00:00:00 /usr/lib/evolution/2.26/evolution-exchange-storage --oaf-activate-iid=OAFIID:
fethi    19907     1  0 05:43 ?        00:00:00 /usr/bin/pulseaudio --start --log-target=syslog
fethi    19908 19907  0 05:43 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-helper
fethi    23360     1  0 06:02 ?        00:00:01 gnome-terminal
fethi    23361 23360  0 06:02 ?        00:00:00 gnome-pty-helper
fethi    23362 23360  0 06:02 pts/0    00:00:00 bash
root     23984     2  0 06:08 ?        00:00:00 [pdflush]
root     24293     1  0 06:10 ?        00:00:00 dbus-launch --autolaunch 950c8bae20f874b4be280b9249f21b88 --binary-syntax --c
root     24294     1  0 06:10 ?        00:00:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
fethi    24371     1  0 06:13 ?        00:00:01 /usr/lib/tracker/tracker-extract
fethi    25486     1 37 06:17 ?        00:00:05 pdftotext -enc UTF-8 -q -nopgbrk /media/Works/Private/Fethi/My Library/Books/
fethi    25487 23362  0 06:17 pts/0    00:00:00 ps -ef
root     31647     1  0 05:14 ?        00:00:00 /usr/sbin/pppd call dsl-provider
fethi    31826     1  0 05:15 ?        00:00:00 /bin/bash /usr/bin/realplay
fethi    31832 31826  5 05:15 ?        00:03:30 /opt/real/RealPlayer/realplay.bin
fethi    31834     1  0 05:15 ?        00:00:19 /usr/lib/tracker/trackerd
fethi    31836 31832  0 05:15 ?        00:00:00 /opt/real/RealPlayer/realplay.bin
fethi    31837 31832  0 05:15 ?        00:00:00 /opt/real/RealPlayer/realplay.bin
fethi    32033     1 21 05:16 ?        00:12:59 /usr/lib/tracker/tracker-indexer

```

[COLOR="Red"]**[It is slow not because of tracker I have just activated it now while I'm posting]**[/COLOR]

And this image shows that I'm not using all the system ressource:

[IMG]http://img114.imageshack.us/img114/6261/screenshot1a.png[/IMG]

---

### Post by delphiexile on 2009-04-29
> **cariboo907 said:**
> Please don't bump a thread until 24 hours has elapsed. Read the [thread=885580]Forum Do's and Don't's[/thread].

To answer your question, your problem is more that likely video driver problems, have a look at this [thread=1136738]thread[/thread] and [thread=1130582]this one[/thread] for help in solving your problem.

Is your alarm clock program compatible with python 2.6?

If you repair the graphics, gnome will run faser.

OK , I read the rules , and I read the thread about my Graphic Card , I'm trying it now , i'll post my reply about it later!!

---

### Post by directhex on 2009-04-29
> **delphiexile said:**
> OK, I could stop this mono process now , but i still have a problem : the pc is slow (means it doesn't respond instantly) without using all the system ressource, this is the result of the ps -ef command:


Um... I don't see any mono processes in that list

---

### Post by delphiexile on 2009-05-04
> **directhex said:**
> Um... I don't see any mono processes in that list

Now I know when this process starts , it starts when I try to run Desktop Drapes (but the latter doesn't run). I can't understand why ??? This time there is the result of the ps -ef' command :

```

UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 12:59 ?        00:00:01 /sbin/init
root         2     0  0 12:59 ?        00:00:00 [kthreadd]
root         3     2  0 12:59 ?        00:00:00 [migration/0]
root         4     2  0 12:59 ?        00:00:00 [ksoftirqd/0]
root         5     2  0 12:59 ?        00:00:00 [watchdog/0]
root         6     2  0 12:59 ?        00:00:00 [migration/1]
root         7     2  0 12:59 ?        00:00:00 [ksoftirqd/1]
root         8     2  0 12:59 ?        00:00:00 [watchdog/1]
root         9     2  0 12:59 ?        00:00:00 [events/0]
root        10     2  0 12:59 ?        00:00:00 [events/1]
root        11     2  0 12:59 ?        00:00:00 [khelper]
root        12     2  0 12:59 ?        00:00:00 [kstop/0]
root        13     2  0 12:59 ?        00:00:00 [kstop/1]
root        14     2  0 12:59 ?        00:00:00 [kintegrityd/0]
root        15     2  0 12:59 ?        00:00:00 [kintegrityd/1]
root        16     2  0 12:59 ?        00:00:00 [kblockd/0]
root        17     2  0 12:59 ?        00:00:00 [kblockd/1]
root        18     2  0 12:59 ?        00:00:00 [kacpid]
root        19     2  0 12:59 ?        00:00:00 [kacpi_notify]
root        20     2  0 12:59 ?        00:00:00 [cqueue]
root        21     2  0 12:59 ?        00:00:00 [ata/0]
root        22     2  0 12:59 ?        00:00:00 [ata/1]
root        23     2  0 12:59 ?        00:00:00 [ata_aux]
root        24     2  0 12:59 ?        00:00:00 [ksuspend_usbd]
root        25     2  0 12:59 ?        00:00:00 [khubd]
root        26     2  0 12:59 ?        00:00:00 [kseriod]
root        27     2  0 12:59 ?        00:00:00 [kmmcd]
root        28     2  0 12:59 ?        00:00:00 [btaddconn]
root        29     2  0 12:59 ?        00:00:00 [btdelconn]
root        30     2  0 12:59 ?        00:00:00 [pdflush]
root        31     2  0 12:59 ?        00:00:00 [pdflush]
root        32     2  0 12:59 ?        00:00:05 [kswapd0]
root        33     2  0 12:59 ?        00:00:00 [aio/0]
root        34     2  0 12:59 ?        00:00:00 [aio/1]
root        35     2  0 12:59 ?        00:00:00 [ecryptfs-kthrea]
root        38     2  0 12:59 ?        00:00:00 [scsi_eh_0]
root        39     2  0 12:59 ?        00:00:01 [scsi_eh_1]
root        40     2  0 12:59 ?        00:00:00 [kstriped]
root        41     2  0 12:59 ?        00:00:00 [kmpathd/0]
root        42     2  0 12:59 ?        00:00:00 [kmpathd/1]
root        43     2  0 12:59 ?        00:00:00 [kmpath_handlerd]
root        44     2  0 12:59 ?        00:00:00 [ksnapd]
root        45     2  0 12:59 ?        00:00:03 [kondemand/0]
root        46     2  0 12:59 ?        00:00:02 [kondemand/1]
root        47     2  0 12:59 ?        00:00:00 [krfcommd]
root       711     2  0 12:59 ?        00:00:00 [kjournald2]
root       845     1  0 12:59 ?        00:00:00 /sbin/udevd --daemon
root      1329     2  0 12:59 ?        00:00:00 [kpsmoused]
root      1857     2  0 12:59 ?        00:00:00 [kjournald2]
root      2340     1  0 12:59 ?        00:00:00 /usr/sbin/pppd call dsl-provider
root      2478     1  0 12:59 tty4     00:00:00 /sbin/getty 38400 tty4
root      2479     1  0 12:59 tty5     00:00:00 /sbin/getty 38400 tty5
root      2482     1  0 12:59 tty2     00:00:00 /sbin/getty 38400 tty2
root      2485     1  0 12:59 tty3     00:00:00 /sbin/getty 38400 tty3
root      2486     1  0 12:59 tty6     00:00:00 /sbin/getty 38400 tty6
root      2558     1  0 12:59 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
syslog    2603     1  0 12:59 ?        00:00:00 /sbin/syslogd -u syslog
root      2626     1  0 12:59 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      2628     1  0 12:59 ?        00:00:00 /sbin/klogd -P /var/run/klogd/kmsg
108       2651     1  0 12:59 ?        00:00:02 /bin/dbus-daemon --system
root      2676     1  0 12:59 ?        00:00:00 /usr/bin/avgscan -d -pid /var/run/avgd.pgrp
root      2706     1  0 12:59 ?        00:00:00 /usr/sbin/console-kit-daemon
chipcard  2805     1  0 12:59 ?        00:00:00 /usr/sbin/chipcardd4 --pidfile /var/run/chipcard/chipcardd4.pid --exit-on-err
root      2855     1  0 12:59 ?        00:00:00 /usr/sbin/winbindd
111       2881     1  0 12:59 ?        00:00:01 /usr/sbin/hald
root      2882  2881  0 12:59 ?        00:00:00 hald-runner
root      2911  2882  0 12:59 ?        00:00:00 hald-addon-input: Listening on /dev/input/event1 /dev/input/event0 /dev/input
root      2923  2855  0 12:59 ?        00:00:00 /usr/sbin/winbindd
root      2953  2882  0 12:59 ?        00:00:01 hald-addon-storage: polling /dev/sr0 (every 2 sec)
root      2954  2882  0 12:59 ?        00:00:00 /usr/lib/hal/hald-addon-cpufreq
111       2955  2882  0 12:59 ?        00:00:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      2976     1  0 12:59 ?        00:00:00 /usr/sbin/bluetoothd
root      3009     1  0 12:59 ?        00:00:00 /usr/sbin/gdm
root      3012  3009  0 12:59 ?        00:00:00 /usr/sbin/gdm
root      3017  3012 10 12:59 tty7     00:07:55 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt
root      3036     1  0 12:59 ?        00:00:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pi
root      3051     1  0 12:59 ?        00:00:00 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log
root      3053     1  0 12:59 ?        00:00:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.
avahi     3060     1  0 12:59 ?        00:00:00 avahi-daemon: registering [fethi-desktop.local]
avahi     3061  3060  0 12:59 ?        00:00:00 avahi-daemon: chroot helper
root      3084     1  0 12:59 ?        00:00:00 /usr/sbin/cupsd
root      3118     1  0 12:59 ?        00:00:00 /usr/bin/system-tools-backends
daemon    3191     1  0 12:59 ?        00:00:00 /usr/sbin/atd
root      3219     1  0 12:59 ?        00:00:00 /usr/sbin/cron
root      3262     1  0 12:59 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  3265  3262  0 12:59 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  3274  3262  0 12:59 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  3277  3262  0 12:59 ?        00:00:00 /usr/sbin/apache2 -k start
root      3411     1  0 12:59 ?        00:00:00 /usr/bin/timidity -Os -iAD
chipcard  3422  2805  0 12:59 ?        00:00:22 /usr/sbin/chipcardd4 --pidfile /var/run/chipcard/chipcardd4.pid --exit-on-err
root      3424     1  0 12:59 tty1     00:00:00 /sbin/getty 38400 tty1
fethi     3427  3012  0 12:59 ?        00:00:00 x-session-manager
fethi     3539  3427  0 12:59 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-se
fethi     3542     1  0 12:59 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seah
fethi     3543     1  0 12:59 ?        00:00:03 //bin/dbus-daemon --fork --print-pid 6 --print-address 9 --session
fethi     3548     1  0 12:59 ?        00:00:01 /usr/bin/pulseaudio --start
fethi     3549  3548  0 12:59 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-helper
fethi     3551     1  0 12:59 ?        00:00:01 /usr/lib/libgconf2-4/gconfd-2
fethi     3563  3427  0 12:59 ?        00:00:00 /usr/bin/seahorse-agent --execute x-session-manager
fethi     3599     1  0 12:59 ?        00:00:00 /usr/lib/gvfs/gvfsd
fethi     3605     1  0 12:59 ?        00:00:01 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
fethi     3609     1  0 12:59 ?        00:00:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/fethi/.gvfs
fethi     3614     1  0 12:59 ?        00:00:00 gnome-keyring-daemon --start
fethi     3620  3427  0 12:59 ?        00:00:00 /bin/sh /usr/bin/compiz
fethi     3673  3620  0 12:59 ?        00:00:45 /usr/bin/compiz.real --ignore-desktop-hints --replace --sm-client-id 10204c7f
fethi     3674  3427  0 12:59 ?        00:00:11 gnome-panel
fethi     3675  3427  0 12:59 ?        00:00:06 nautilus
fethi     3677     1  0 12:59 ?        00:00:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-outpu
fethi     3679  3427  0 12:59 ?        00:00:00 minbar
fethi     3686  3427  0 12:59 ?        00:00:00 python /usr/share/system-config-printer/applet.py
fethi     3687  3427  0 12:59 ?        00:00:00 bluetooth-applet
fethi     3690  3427  0 12:59 ?        00:00:00 tracker-applet
fethi     3697     1  0 12:59 ?        00:00:00 /usr/lib/gvfs/gvfs-hal-volume-monitor
fethi     3700  3427  0 12:59 ?        00:00:00 nm-applet --sm-disable
fethi     3702     1  0 12:59 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
fethi     3703  3427  0 12:59 ?        00:00:15 /usr/lib/tracker/trackerd
fethi     3704  3427  0 12:59 ?        00:00:00 update-notifier --startup-delay=60
fethi     3706     1  0 12:59 ?        00:00:00 gnome-power-manager
fethi     3709     1  0 12:59 ?        00:00:00 /usr/lib/notify-osd/notify-osd
fethi     3720     1  0 12:59 ?        00:00:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_Tras
fethi     3723     1  0 12:59 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.5 /org/gtk/gvfs/exec_spaw/0
fethi     3731     1  0 12:59 ?        00:00:01 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_In
fethi     3733     1  0 12:59 ?        00:00:00 /usr/lib/fast-user-switch-applet/fast-user-switch-applet --oaf-activate-iid=O
fethi     3735     1  0 12:59 ?        00:00:01 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApp
fethi     3740     1  0 12:59 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.5 /org/gtk/gvfs/exec_spaw/2
fethi     3742  3673  0 12:59 ?        00:00:00 /bin/sh -c /usr/bin/compiz-decorator
fethi     3743  3742  0 12:59 ?        00:00:00 /bin/sh /usr/bin/compiz-decorator
fethi     3745  3743  0 12:59 ?        00:00:05 /usr/bin/gtk-window-decorator
fethi     4102     1  0 13:00 ?        00:00:10 gnome-screensaver
fethi     4440     1  6 13:02 ?        00:05:13 /usr/lib/firefox-3.0.10/firefox
root      5269     1  0 13:15 ?        00:00:00 /usr/bin/python /usr/lib/system-service/system-service-d
fethi     6358     1  0 13:30 ?        00:00:00 /bin/bash /usr/bin/realplay /media/Works/Private/Fethi/My Sound Files/Al Afas
fethi     6364  6358 97 13:30 ?        00:46:16 /opt/real/RealPlayer/realplay.bin /media/Works/Private/Fethi/My Sound Files/A
fethi     6365  6364  0 13:30 ?        00:00:00 /opt/real/RealPlayer/realplay.bin /media/Works/Private/Fethi/My Sound Files/A
fethi     6366  6364  0 13:30 ?        00:00:00 /opt/real/RealPlayer/realplay.bin /media/Works/Private/Fethi/My Sound Files/A
fethi     6625     1  2 13:46 ?        00:00:40 skype
fethi     7226     1 49 14:06 ?        00:05:48 drapes /usr/lib/drapes/drapes.exe --tray
fethi     7522     1 13 14:11 ?        00:00:50 gnome-system-monitor
fethi     7524     1  0 14:12 ?        00:00:02 gnome-terminal
fethi     7525  7524  0 14:12 ?        00:00:00 gnome-pty-helper
fethi     7526  7524  0 14:12 pts/0    00:00:00 bash
fethi     7546     1 41 14:13 ?        00:01:40 drapes /usr/lib/drapes/drapes.exe --tray
fethi     7641  7526  3 14:17 pts/0    00:00:00 ps -ef

```

... and to show it clearly , these are 2 screen captures of my computer:
[http://img133.imageshack.us/img133/7050/41514171.png](http://img133.imageshack.us/img133/7050/41514171.png)
&
[http://img133.imageshack.us/img133/8284/65850546.png](http://img133.imageshack.us/img133/8284/65850546.png)

---

### Post by directhex on 2009-05-04
Drapes seems to work here - it starts in the system tray. Perhaps it's choking on one of your wallpapers for some reason?

---

### Post by delphiexile on 2009-05-07
hhhhhhhhh , my Wallpapers are just nature pictures!!! I'm going to reinstall it and I will see .

---

### Post by delphiexile on 2009-05-07
... I've reinstalled it , always the same problem with drapes.

---

### Post by directhex on 2009-05-07
Try temporarily moving the folder drapes is reading from, and see if it starts without any of your pictures there

I think this sounds like a serious bug with image loading, but we need to track down WHERE the bug is.

---

### Post by delphiexile on 2009-05-10
OK, I'm going to rename it !!

---

### Post by delphiexile on 2009-05-10
Same problemm ; I tried that to rename the folder , but the same mono process loads itself!! I'm going to delete the configuration file of drapes!!

---

### Post by delphiexile on 2009-05-10
THE PROBLEM IS SOLVED THANKS TO EVERYONE , I've reset the configuration of this program to standard using GConf. and it has run!!

---

### Post by directhex on 2009-05-10
> **delphiexile said:**
> THE PROBLEM IS SOLVED THANKS TO EVERYONE , I've reset the configuration of this program to standard using GConf. and it has run!!

Do you know what was wrong with it? If someone else were able to reproduce it, they could look to fixing it in future for others

---

### Post by delphiexile on 2009-05-10
OK , I have chosen a big directory which contains many files and many subdirectories , and I thought that I've chosen the right one ; The program stalled and I couldn't ran it another time till today.

I've reinstalled this latter , but it doesn't correct this error. I've renamed a subdirectory but without any effect . So I concluded that the problem was in its configuration. So I've opened GConf and seeked for "drapes", and I could modify the wrong value of photos directory manually. 

This is all !!

---

