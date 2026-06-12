---
title: "Why are applications running more than once?"
date: 2006-09-28
forum: Desktop Environments
---

### Post by akshaysrinivasan on 2006-09-28
Hi,
  Well i have been having bad problems with availability of memory.And when i see the list of running applications,many like getty,dbus-daemon,gdm,gconfd are running more than once.Could this be the reason ubuntu is taking so musch memory?How can prevent these processes from launching themselves more than once?

---

### Post by amohanty on 2006-09-28
Well getty will probably have more than two instances and gdm probably two instances depending on your configuration. However afaik dbus and gconf should not really have more than one instance.

Can you post the output of:
**ps -e af**

HTH
AM

---

### Post by akshaysrinivasan on 2006-09-28
Well here it is
pluto@Neptune:~$ ps -e af
  PID TTY      STAT   TIME COMMAND
    1 ?        S      0:01 init [2]
    2 ?        S      0:00 [migration/0]
    3 ?        SN     0:00 [ksoftirqd/0]
    4 ?        S      0:00 [watchdog/0]
    5 ?        S<     0:00 [events/0]
    6 ?        S<     0:00 [khelper]
    7 ?        S<     0:00 [kthread]
    9 ?        S<     0:00  \_ [kblockd/0]
   10 ?        S<     0:00  \_ [kacpid]
  123 ?        S      0:00  \_ [pdflush]
  124 ?        S      0:00  \_ [pdflush]
  126 ?        S<     0:00  \_ [aio/0]
  714 ?        S<     0:00  \_ [kseriod]
 1834 ?        S<     0:00  \_ [khubd]
 3237 ?        S<     0:00  \_ [kgameportd]
  125 ?        S      0:00 [kswapd0]
 1957 ?        S      0:00 [kjournald]
 2356 ?        S<s    0:00 /sbin/udevd --daemon
 3194 ?        S      0:00 [shpchpd_event]
 3901 ?        S      0:00 [kjournald]
 4489 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid 4504 ?        Ss     0:00 /sbin/syslogd -u syslog
 4527 ?        Ss     0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 4529 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 4548 ?        Ss     0:00 /usr/bin/dbus-daemon --system
 4563 ?        Ss     0:01 /usr/sbin/hald
 4564 ?        S      0:00  \_ hald-runner
 4569 ?        S      0:00      \_ /usr/lib/hal/hald-addon-acpi
 4572 ?        S      0:00      \_ /usr/lib/hal/hald-addon-hid-ups
 4621 ?        S      0:00      \_ /usr/lib/hal/hald-addon-keyboard
 4632 ?        S      0:00      \_ /usr/lib/hal/hald-addon-storage
 4633 ?        S      0:00      \_ /usr/lib/hal/hald-addon-storage
 4891 ?        Ss     0:00 /usr/sbin/gdm
 4909 ?        S      0:00  \_ /usr/sbin/gdm
 4926 tty7     Ss+    1:15      \_ /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm 5109 ?        Ss     0:00      \_ /usr/bin/gnome-session
 5152 ?        Ss     0:00          \_ /usr/bin/ssh-agent /usr/bin/dbus-launch - 4935 ?        Ss     0:00 /sbin/mdadm -F -i /var/run/mdadm.pid -m root -f -s
 4970 ?        Ss     0:00 /usr/sbin/atd
 4983 ?        Ss     0:00 /usr/sbin/cron
 5080 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 5081 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 5082 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 5083 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 5084 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 5085 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 5155 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/gno 5156 ?        Ss     0:00 dbus-daemon --fork --print-pid 8 --print-address 6 -- 5158 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2 5
 5161 ?        S      0:00 /usr/bin/gnome-keyring-daemon
 5163 ?        Ss     0:00 /usr/lib/bonobo-activation/bonobo-activation-server - 5165 ?        Sl     0:03 /usr/lib/control-center/gnome-settings-daemon --oaf-a 5167 ?        Ss     0:00 /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 18
 5174 ?        Ss     0:02 /usr/bin/metacity --sm-client-id=default0
 5184 ?        Ssl    0:05 gnome-panel --sm-client-id default1
 5186 ?        Ssl    0:03 nautilus --no-default-window --sm-client-id default2
 5189 ?        Ss     0:00 gnome-volume-manager --sm-client-id default4
 5195 ?        Ss     0:01 gksu firestarter
 5196 ?        Ssl    0:01  \_ firestarter
 5201 ?        Sl     0:02 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon --oaf-activat 5206 ?        S      0:01 /usr/lib/gnome-netstatus/gnome-netstatus-applet --oaf 5210 ?        Sl     0:02 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid 5222 ?        S      0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
 5229 ?        S      0:00 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid= 5231 ?        S      0:05 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-i 5233 ?        S      0:00 xscreensaver -nosplash
 5238 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2 11
 5240 ?        Ss     0:00 /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 14
 5366 ?        Sl     0:39 xmms
 5405 ?        Sl     0:00 /usr/lib/evolution/evolution-data-server-1.6 --oaf-ac 5408 ?        Sl     0:02 gaim
 5431 ?        Sl     0:00 /usr/lib/evolution/2.6/evolution-alarm-notify --oaf-a 6455 ?        Sl     0:08 /usr/lib/firefox/firefox-bin -a firefox
 6568 ?        Sl     0:00 gnome-terminal
 6573 ?        S      0:00  \_ gnome-pty-helper
 6574 pts/0    Ss     0:00  \_ bash
 6582 pts/0    R+     0:00      \_ ps -e af

---

### Post by orb9220 on 2006-09-28
Well a few I see that are not needed are the firestarter. Firestarter is  only the gui for iptables which is always running. Only run firestarter when you need to config iptables firewall settings.

Evolution - 405 ? Sl 0:00 /usr/lib/evolution/evolution-data-server-1.6
usr/lib/evolution/2.6/evolution-alarm-notify -  eats up I think about 25 megs or so.

also do a system monitor and it will list all process click on resident memory twice and all the hog eaters will be at the top,

Like having to many tabs open in firefox,some applets eat quite a bit.

If you are having mem problems then you will have to take a hard look at "Do I really need that running,Do I really use it?"

If the answer is yes then only option is more ram.

---

### Post by amohanty on 2006-09-28
Well I dont see anything unusual in the listing. I would follow orb9220's recommendation regarding evolution and firestarter.

Also install **bum** and turn off stuff that you dont need. 

HTH
AM

---

### Post by noobaholic on 2006-12-07
> **amohanty said:**
> Well getty will probably have more than two instances and gdm probably two instances depending on your configuration.

Why two instances of gdm?

---

