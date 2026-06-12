---
title: "Text file named 0 that won't go away in my home folder"
date: 2006-07-22
forum: Desktop Environments
---

### Post by Epperly on 2006-07-22
Everytime I try to delete this text file( named 0, 0 byte file), it goes to the trash but the icon flashes a red X and a lock, and the name 0 (copy), then goes back to 0 as it was.
(no processes are using it)
What'd I do? It won't go away.

---

### Post by HAARP on 2006-07-22
Try opening a terminal and type;
```
rm 0
```
If it doesn't work, copy n' paste the output.

---

### Post by Epperly on 2006-07-22
I tried that, there is no output.

---

### Post by ardchoille on 2006-07-22
Have you tried deleting it using: sudo rm /path/filename  ?

---

### Post by Epperly on 2006-07-22
yup, it comes back

---

### Post by ardchoille on 2006-07-22
Where is this file? Try going into the directory that contains this file and do:

```

file filename

```

```

ls -lha filename

```

Can you post the output of those commands? You have my curiousity now :)

---

### Post by jimmygoon on 2006-07-22
> **Epperly said:**
> yup, it comes back

what is the result from
"ps ax"

---

### Post by Epperly on 2006-07-22
> **ardchoille said:**
> Where is this file? Try going into the directory that contains this file and do:

```

file filename

```

```

ls -lha filename

```

Can you post the output of those commands? You have my curiousity now :)
```

sammy@SAMMY:~$ file 0
0: empty
sammy@SAMMY:~$ ls -lha 0

```

[quote=jimmygoon]what is the result from
"ps ax"[/quote]
```

sammy@SAMMY:~$ ps ax
  PID TTY      STAT   TIME COMMAND
    1 ?        S      0:06 init [2]
    2 ?        SN     0:00 [ksoftirqd/0]
    3 ?        S      0:00 [watchdog/0]
    4 ?        S<     0:00 [events/0]
    5 ?        S<     0:00 [khelper]
    6 ?        S<     0:00 [kthread]
    8 ?        S<     0:00 [kblockd/0]
    9 ?        S<     0:00 [kacpid]
  102 ?        S      0:00 [pdflush]
  103 ?        S      0:00 [pdflush]
  105 ?        S<     0:00 [aio/0]
  104 ?        S      0:00 [kswapd0]
  692 ?        S<     0:00 [kseriod]
 1885 ?        S<     0:00 [khubd]
 1999 ?        D      0:00 [kjournald]
 2225 ?        S<s    0:00 /sbin/udevd --daemon
 3110 ?        S      0:00 [shpchpd_event]
 3537 ?        Ss     0:29 /sbin/mount.ntfs-3g /dev/hdc2 /windows -v -o rw,silen 3937 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid 4030 ?        Ss     0:00 /sbin/syslogd -u syslog
 4056 ?        Ss     0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 4058 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 4377 ?        Ss     0:00 /usr/sbin/gdm
 4391 ?        S      0:03 /usr/sbin/gdm
 4411 tty7     Ss+   15:12 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xaut 4420 ?        Ssl    0:00 /usr/sbin/hpiod
 4444 ?        S      0:00 python /usr/sbin/hpssd
 4491 ?        Ss     0:02 /usr/sbin/cupsd
 4516 ?        Ss     0:00 /usr/bin/dbus-daemon --system
 4531 ?        Ss     0:00 /usr/sbin/hald
 4532 ?        S      0:00 hald-runner
 4537 ?        S      0:00 /usr/lib/hal/hald-addon-acpi
 4596 ?        S      0:00 /usr/lib/hal/hald-addon-keyboard
 4601 ?        Ss     0:01 x-session-manager
 4648 ?        S      0:00 /usr/lib/hal/hald-addon-storage
 4651 ?        S      0:00 /usr/lib/hal/hald-addon-storage
 4666 ?        Ss     0:00 /sbin/dhcdbd --system
 4671 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-s 4674 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session x-session-ma 4675 ?        Ss     0:00 dbus-daemon --fork --print-pid 8 --print-address 6 -- 4688 ?        Ssl    0:00 /usr/sbin/NetworkManager --pid-file=/var/run/NetworkM 4704 ?        S      0:01 /usr/lib/libgconf2-4/gconfd-2 5
 4705 ?        Ss     0:00 /usr/sbin/NetworkManagerDispatcher --pid-file=/var/ru 4766 ?        S      0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth0.le 4771 ?        Ss     0:00 /usr/sbin/nmbd -D
 4780 ?        Ss     0:00 /usr/sbin/smbd -D
 4815 ?        S      0:00 /usr/bin/gnome-keyring-daemon
 4817 ?        Ss     0:00 /usr/lib/bonobo-activation/bonobo-activation-server - 4826 ?        Ss     0:00 hcid: processing events
 4830 ?        Ss     0:00 /usr/sbin/sdpd
 4842 ?        S      0:00 /usr/sbin/smbd -D
 4844 ?        S<     0:00 [krfcommd]
 4857 ?        Ss     0:00 /sbin/mdadm -F -i /var/run/mdadm.pid -m root -f -s
 4891 ?        Ss     0:00 /usr/sbin/atd
 4904 ?        Ss     0:00 /usr/sbin/cron
 4927 ?        Sl     0:11 /usr/lib/control-center/gnome-settings-daemon --oaf-a 4995 ?        SL     0:00 /usr/bin/esd -nobeeps
 5023 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 5024 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 5025 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 5026 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 5027 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 5028 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 5030 ?        Ss     0:00 /usr/bin/esd -nobeeps
 5050 ?        Ss     1:50 /usr/bin/metacity --sm-client-id=default0
 5057 ?        Ssl    0:43 gnome-panel --sm-client-id default1
 5059 ?        Ssl    1:13 nautilus --no-default-window --sm-client-id default2
 5062 ?        Ss     0:00 gnome-volume-manager --sm-client-id default4
 5070 ?        Ss     0:01 update-notifier
 5073 ?        Sl     0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon --oaf-activat 5084 ?        Ss     0:02 nm-applet --sm-disable
 5087 ?        Ss     0:04 gnome-cups-icon --sm-client-id default3
 5092 ?        S      0:00 /usr/lib/gnome-applets/multiload-applet-2 --oaf-activ 5094 ?        Ss     0:01 gnome-power-manager
 5099 ?        S      0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
 5109 ?        S     13:12 python /usr/lib/gdesklets/gdesklets-daemon
 5116 ?        S      0:03 /usr/lib/gnome-applets/gweather-applet-2 --oaf-activa 5118 ?        S      0:05 /usr/lib/gnome-applets/geyes_applet2 --oaf-activate-i 5120 ?        S      0:01 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid= 5122 ?        S      0:01 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-i 5124 ?        Sl     0:02 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid 5140 ?        Ss     0:12 gnome-screensaver
15539 ?        S      0:47 /bin/bash /home/sammy/Desktop/amarokNowPlaying
30225 ?        S      0:01 /usr/lib/notification-daemon/notification-daemon
 1051 ?        SLl    1:58 python /usr/bin/quodlibet
23800 ?        Sl     0:06 /usr/lib/firefox/firefox-bin -a firefox http://www.sa25943 ?        S      0:09 /usr/bin/gaim
28940 ?        Sl     0:00 gnome-terminal
28945 ?        S      0:00 gnome-pty-helper
28946 pts/0    Ss     0:00 bash
31264 pts/0    S+     0:01 gedit /home/sammy/myplugin.py
31268 pts/0    S+     0:00 /usr/lib/libgconf2-4/gconfd-2 12
31272 ?        Ss     0:00 /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 18
 3325 ?        S      0:00 /bin/sh /usr/bin/mozilla-thunderbird
 3331 ?        S      0:00 /bin/sh /usr/lib/mozilla-thunderbird/run-mozilla.sh / 3336 ?        Sl     0:02 /usr/lib/mozilla-thunderbird/mozilla-thunderbird-bin
 3894 pts/1    Ss     0:00 bash
 3952 ?        S      0:00 scp /nowPlaying.txt /nowplaying.png @
 3953 ?        R      0:00 /usr/bin/ssh -x -oForwardAgent no -oClearAllForwardin 3954 pts/1    R+     0:00 ps ax

```

---

### Post by jimmygoon on 2006-07-22
hmm... does it do this always, like even after a fresh reboot? or is it just after starting some other type of program?

---

### Post by Epperly on 2006-07-22
actually, I haven't tried to reboot yet, I'll try soon though

---

### Post by Epperly on 2006-07-22
Wow, a reboot was all it took to be able to delete it :(
I hate when things are easy but the easy ways get overlooked trying to do things the hard way.

Thanks for the help, anyway, though!

---

### Post by ardchoille on 2006-07-22
Guess I'll have to remember this the next time someone tells me "rebooting is for Windows".

---

### Post by Epperly on 2006-07-22
haha true dat. I know I will ;)

---

