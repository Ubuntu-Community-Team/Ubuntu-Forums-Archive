---
title: "Instance running - but where?"
date: 2006-09-14
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-09-14
When trying to start aMule through the terminal, this is the output I get:
```
gabriel@gabriel:~$ amule
Initialising aMule
Checking if there is an instance already running...
There is an instance of aMule already running
Raising current running instance.
gabriel@gabriel:~$
```
And then - nothing is "raised", at least not something I could recognize as "raising"
When looking into the xfce4-taskmanager, I find nothing that looks like aMule (I couldn't find a way to post *that* output here, if anyone thinks it's important and knows how to, please let me know)
How come? Is aMule running or not? If yes, why can't I se it?

Thanks

Gabriel

---

### Post by Jussi Kukkonen on 2006-09-14
Try this:
```
ps ax | grep amule | grep -v grep
```

(firs command gives you a process list, second searches for "amule" in the list. Third one just prevents the previous command from showing up in the list)

---

### Post by GabrielWolff on 2006-09-14
```
gabriel@gabriel:~$ ps ax | grep amule | grep -v grep
gabriel@gabriel:~$ amule
Initialising aMule
Checking if there is an instance already running...
There is an instance of aMule already running
Raising current running instance.
gabriel@gabriel:~$
```
I didn't know if I should start aMule after typing in your command, so I waited a minute. As nothing happened, I tried to start aMule, but...

What is the command about? What should it have done?

Gabriel

---

### Post by Jussi Kukkonen on 2006-09-14
ps lists all your running processes, *ps ax * lists all running processes, even those owned by someone else. If you got no output then there's no process running.

---

### Post by GabrielWolff on 2006-09-14
Well, there's at least my terminal and my browser...
I did them one by one. Here's my output:```
gabriel@gabriel:~$ ps ax
  PID TTY      STAT   TIME COMMAND
    1 ?        S      0:02 init [2]
    2 ?        SN     0:00 [ksoftirqd/0]
    3 ?        S      0:00 [watchdog/0]
    4 ?        S<     0:00 [events/0]
    5 ?        S<     0:00 [khelper]
    6 ?        S<     0:00 [kthread]
    8 ?        S<     0:00 [kblockd/0]
    9 ?        S<     0:00 [kacpid]
   74 ?        S<     0:00 [kacpid-work-0]
   75 ?        S<     0:00 [kacpid-work-1]
   76 ?        S<     0:00 [kacpid-work-2]
   77 ?        S<     0:00 [kacpid-work-3]
   78 ?        S<     0:00 [kacpid-work-4]
   79 ?        S<     0:00 [kacpid-work-5]
   80 ?        S<     0:00 [kacpid-work-6]
   81 ?        S<     0:00 [kacpid-work-7]
   82 ?        S<     0:00 [kacpid-work-8]
   83 ?        S<     0:00 [kacpid-work-9]
  133 ?        S      0:00 [pdflush]
  134 ?        S      0:00 [pdflush]
  136 ?        S<     0:00 [aio/0]
  135 ?        S      0:00 [kswapd0]
  723 ?        S<     0:00 [kseriod]
 1886 ?        S<     0:00 [khubd]
 1892 ?        S      0:00 [khpsbpkt]
 1900 ?        S      0:00 [knodemgrd_0]
 1962 ?        S<     0:00 [scsi_eh_0]
 2008 ?        S      0:00 [kjournald]
 2249 ?        S<s    0:00 /sbin/udevd --daemon
 3022 ?        S      0:00 [shpchpd_event]
 3103 ?        S      0:00 [pccardd]
 3259 ?        S<s    0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib 3563 ?        S      0:00 [kjournald]
 3894 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid 3986 ?        Ss     0:00 /sbin/syslogd -u syslog
 4012 ?        Ss     0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 4014 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 4337 ?        Ss     0:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
 4350 ?        S      0:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
 4363 tty7     Rs+    0:26 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xaut 4380 ?        Ssl    0:00 /usr/sbin/hpiod
 4395 ?        S      0:00 python /usr/sbin/hpssd
 4442 ?        Ss     0:00 /usr/sbin/cupsd
 4468 ?        Ss     0:00 /usr/bin/dbus-daemon --system
 4483 ?        Ss     0:00 /usr/sbin/hald
 4484 ?        S      0:00 hald-runner
 4489 ?        S      0:00 /usr/lib/hal/hald-addon-acpi
 4539 ?        S      0:00 /usr/lib/hal/hald-addon-keyboard
 4554 ?        S      0:00 /usr/lib/hal/hald-addon-storage
 4555 ?        S      0:00 /usr/lib/hal/hald-addon-storage
 4606 ?        SNs    0:00 /usr/sbin/powernowd -q
 4645 ?        Ss     0:00 /sbin/mdadm -F -i /var/run/mdadm.pid -m root -f -s
 4716 ?        Ss     0:00 /usr/sbin/atd
 4729 ?        Ss     0:00 /usr/sbin/cron
 4806 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 4807 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 4808 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 4809 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 4810 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 4811 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 4822 ?        Ss     0:00 /bin/sh /etc/xdg/xfce4/xinitrc
 4859 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-s 4862 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session startxfce4
 4863 ?        Ss     0:00 dbus-daemon --fork --print-pid 8 --print-address 6 -- 4868 ?        S      0:00 /bin/sh /etc/xdg/xfce4/xinitrc
 4871 ?        S      0:00 xscreensaver -no-splash
 4872 ?        S      0:00 /usr/bin/xfce4-session
 4876 ?        Ss     0:00 xfce-mcs-manager
 4878 ?        S      0:00 xfwm4 --sm-client-id 117f0001010001157828199000000482 4880 ?        S      0:02 xfdesktop --sm-client-id 117f000101000115782820100000 4882 ?        R      0:00 /usr/lib/gamin/gam_server
 4886 ?        S      0:01 xfce4-panel --sm-client-id 117f0001010001157828199000 4888 ?        S      0:00 orage --sm-client-id 117f0001010001157829135000000482 4890 ?        S      0:03 Thunar --sm-client-id 117f000101000115782820100000048 4896 ?        S      0:00 /usr/lib/xfdesktop4/xfce4/panel-plugins/xfce4-menu-pl 4897 ?        S      0:00 /usr/lib/xfce4-mixer/xfce4/panel-plugins/xfce4-mixer- 4898 ?        S      0:00 /usr/lib/xfce4-systemload-plugin/xfce4/panel-plugins/ 4899 ?        S      0:00 /usr/lib/xfce4-mount-plugin/xfce4/panel-plugins/xfce4 4900 ?        S      0:00 /usr/lib/xfce4-cpugraph-plugin/xfce4/panel-plugins/xf 4901 ?        S      0:00 /usr/lib/xfce4-verve-plugin/xfce4/panel-plugins/xfce4 4942 ?        Ss     0:00 pppd noipdefault noauth default-asyncmap noipx defaul 4943 ?        S      0:00 /usr/sbin/pptp-linux
 4947 ?        S      0:00 /usr/sbin/pptp-linux
 4962 ?        Rsl    0:54 /usr/lib/firefox/firefox-bin -a firefox
 4967 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2 10
 5155 ?        R      0:00 /usr/bin/Terminal
 5157 ?        S      0:00 gnome-pty-helper
 5158 pts/2    Ss     0:00 bash
 5197 pts/2    R+     0:00 ps ax

```
Both the other commands returned nothing. Or at least not for a few minutes...

Gabriel

---

### Post by Jussi Kukkonen on 2006-09-14
I just checked, amule uses a lock file. It probably crashed and now thinks that there's a version running because of the existing lock file...
```
rm ~/.aMule/muleLock
```
should help

---

### Post by GabrielWolff on 2006-09-14
Bingo :-)

Thanks

Gabriel

---

### Post by 3dxtrip on 2007-06-14
Many thanks!

Works fine, now aMule is running again :D

---

