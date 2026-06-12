---
title: "Getting back into init 5"
date: 2006-04-15
forum: Desktop Environments
---

### Post by SimonTheMime on 2006-04-15
I've come across a problem. Wanting to install the latest nvidia driver, going to init 3 through ctrl+alt+f1, and stopping KDE /etc/init.d kdm stop, I've hit a bit of a snag, even before running the nvidia driver installer (so that's probably not the problem).

Now I have installed the drive, yet the problem continues.

It boots into init 3, and even when trying to get into /sbin/init 5, or running /etc/init.d/kdm start, not working.

```
# /etc/init.d/kdm start
Starting K Display Manager: kdm already running.
```

Any ideas? Booting into init 5 stops at:


```
* Checking Battery State... [ ok ]
```

Any ideas?

---

### Post by taurus on 2006-04-15
Try <Ctrl><Atl>F7!!!

---

### Post by SimonTheMime on 2006-04-15
[QUOTE=taurus]Try <Ctrl><Atl>F7!!![/QUOTE]

Already did. Just a blinking underscore :/

---

### Post by taurus on 2006-04-15
Okay, what is the output of this command then?
```

ps -A | more
(Hit the space bar for the next 24 lines...)

```

---

### Post by az on 2006-04-15
runlevel 1 is the single user mode and runlevel 2 is the multiuser mode.  Other distros use runlevel 5 for multiuser mode, AFAIK.

Boot into recovery mode and run

dpkg-reconfigure xserver-xorg
and then
init 2

You borked your video card configuration, that's all.

---

### Post by SimonTheMime on 2006-04-15
[QUOTE=taurus]Okay, what is the output of this command then?
```

ps -A | more
(Hit the space bar for the next 24 lines...)

```[/QUOTE]

/types it all

```

PID TTY CMD
1 ? init
2 ? ksoftirqd/0
3 ? events/0
4 ? khelper
5 ? kthread
7 ? kacpid
95 ? kblockd/0
126 ? pdflush
127 ? pdflush
129 ? aio/0
128 ? ksawpd0
714 ? kseriod
1929 ? ata/0
1932 ? scsi_eh_0
1933 ? scsi_eh_1
1947 ? khubd
3349 ? kjournald2 
3475 ? udevd
5659 ? shpchd_event
6131 ? kgameportd
6906 ? dhclient3
7244 ? acpid
7259 ? syslogd
7276 ? dd
7278 ? klogd
7291 ? dbus-daemon
7304 ? hald
7309 ? hald-addon-acpi
7322 ? hald-addon-stor
7350 ? cupsd
7372 ? hpiod
7383 ? python
7564 ? kdm
7576 ? hcid
7583 ? sdpd
7593 ? krfcommd
7634 ? atd
7647 ? cron
7706 ? vmnet-bridge
7720 ? vment-natd
7753 tty1 login
7754 tty2 getty
7755 tty3 getty
7756 tty4 getty
7757 tty5 getty
7758 tty6 getty
7791 ? vmnet-netifup
7801 ? vment-netifup
7855 ? vmnet-dhcpd
7856 ? vmnet dhcpd
7857 tty1 bash
7881 tty1 ps
7882 tty1 more
```

/cracks neck

Thanks in advance

---

### Post by SimonTheMime on 2006-04-15
> 
Boot into recovery mode and run

How do I get into recovery mode?

---

### Post by taurus on 2006-04-15
[QUOTE=SimonTheMime]How do I get into recovery mode again?[/QUOTE]
At the GRUB prompt, pick the recovery mode!!!

---

### Post by SimonTheMime on 2006-04-15
[QUOTE=taurus]At the GRUB prompt, pick the recovery mode!!![/QUOTE]

Haha, of course. /does

---

### Post by taurus on 2006-04-15
[QUOTE=SimonTheMime]Haha, of course. /does[/QUOTE]
So now you know!  :mrgreen:

---

### Post by SimonTheMime on 2006-04-15
Alright thanks guys, it worked. I'll be referring to this thread the next time I make a mistake installing video card drivers.

Thanks taurus, and azz! /bookmarks.

---

