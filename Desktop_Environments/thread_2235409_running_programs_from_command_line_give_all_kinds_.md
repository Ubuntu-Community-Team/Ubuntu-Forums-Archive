---
title: "running programs from command line give all kinds of &quot;scary&quot; messages"
date: 2014-07-20
forum: Desktop Environments
---

### Post by mctiew on 2014-07-20
I noticed that my desktop system with xubuntu 14.04 compiz will gives various "scary" messages when I run programs from command line :-

eg :-
> 
$ firefox

(process:24931): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed


> 
$ qemu-system-x86_64 -display gtk 
(qemu-system-i386:25169): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion 'G_IS_DBUS_CONNECTION (connection)' failed

(qemu-system-i386:25169): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion 'G_IS_DBUS_CONNECTION (connection)' failed

(qemu-system-i386:25169): GLib-GIO-CRITICAL **: g_dbus_connection_get_unique_name: assertion 'G_IS_DBUS_CONNECTION (connection)' failed


This above qemu messages comes from :-

DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-8CMMJ1Q9rp

If I unset DBUS_SESSION_BUS_ADDRESS, then the program will run without the about messages.

All the programs seem to work fine despite giving those messages. But it's not comforting to see those messages appearing from the command line, seems an indicaton of something is not right.

---

### Post by tgalati4 on 2014-07-20
You should see the messages the kernel generates.  If it ain't broke, it don't need fixing.

The second example are messages which are related to temporary storage of DBUS messages (a process-to-process messaging system) in the /tmp directory.  Perhaps qemu doesn't have rights it needs to access them.  Not sure what the first one is.

You can run many programs with the --debug switch to get more descriptive messages.  Normally you only need to run in a terminal when you are having problems and you need to see what is going on.  Otherwise those messages get dumped to the bit bucket.

If a program is running really slowly, then checking terminal messages can reveal what is happening for that application.

---

### Post by yancek on 2014-07-21
The message you are seeing when you open firefox has been around for a long time and I see it on some of my systems every time I open firefox from a  terminal.  It's a known problem but doesn't prevent use of firefox.

---

### Post by mooreted on 2014-07-21
For that matter, you should see all the errors Windows doesn't show you. Operating systems are far from perfect.

---

### Post by grahammechanical on 2014-07-21
If you do not want to be scared, do not run those programs from the terminal. They are programs designed to run from a GUI. Programs that are by design "terminal" programs do not usually printout scary messages.

Regards.

---

### Post by tgalati4 on 2014-07-21
There should be a Halloween mode, where all error messages from every application get thrown up on the screen in a random fashion with sound effects like creaking doors.

If you lift the hood of your car, you hear all sorts of scary sounds.  As long as you get where you want to go, who cares?  But realize it is illegal to drive around (in [California]("http://honda-tech.com/showthread.php?t=1524897")) without a hood.

---

### Post by mctiew on 2014-07-21
> **tgalati4 said:**
> 
If you lift the hood of your car, you hear all sorts of scary sounds.  As long as you get where you want to go, who cares?  But realize it is illegal to drive around (in [California]("http://honda-tech.com/showthread.php?t=1524897")) without a hood.

So you knowledge that linux or rather ubuntu is likened to a car which makes all sorts of queaky sound but nevertheless reaches where we want to go ?  ;) 

That's the driving experience I will get on a 10-20 year old car. I won't want to get that from a new car.

---

### Post by tgalati4 on 2014-07-21
If you spend enough time, you can trace each error message and its source.  Fixing them is another matter.

---

### Post by mooreted on 2014-07-22
We would all like a brand new Ferrari however, the only cars on the market are Ford, Chevy and VolksWagen.

---

### Post by vasa1 on 2014-07-22
> **yancek said:**
> The message you are seeing when you open firefox has been around for a long time and I see it on some of my systems every time I open firefox from a  terminal.  It's a known problem but doesn't prevent use of firefox.
+1

[https://bugzilla.mozilla.org/show_bug.cgi?id=833117](https://bugzilla.mozilla.org/show_bug.cgi?id=833117)

I stick "2>/dev/null" to the end of the command.

---

### Post by vasa1 on 2014-07-22
> **grahammechanical said:**
> If you do not want to be scared, do not run those programs from the terminal. They are programs designed to run from a GUI. Programs that are by design "terminal" programs do not usually printout scary messages.

Regards.
Some nice links are here: [http://askubuntu.com/a/422400](http://askubuntu.com/a/422400)

---

### Post by mctiew on 2014-07-22
Regarding the second "scary" message about dbus, what I worry is that could it be dbus is not set up correctly ?

> 
$ ps aux |grep dbus
message+   833  0.0  0.0  40380  2496 ?        Ss   15:20   0:00 dbus-daemon --system --fork
mctiew    1521  0.0  0.0  24440   576 ?        S    15:20   0:00 dbus-launch --autolaunch=0c423c376dd8c403050b8ad353a83564 --binary-syntax --close-stderr
mctiew    1522  0.0  0.0  39116   552 ?        Ss   15:20   0:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
mctiew    1544  0.0  0.0  41252  2572 ?        Ss   15:20   0:00 dbus-daemon --fork --session --address=unix:abstract=/tmp/dbus-8Ky1ZPjLAQ
mctiew    1580  0.0  0.0  22328   424 ?        S    15:20   0:00 upstart-dbus-bridge --daemon --system --user --bus-name system
mctiew    1586  0.0  0.0  22328   644 ?        S    15:20   0:00 upstart-dbus-bridge --daemon --session --user --bus-name session
mctiew    1602  0.0  0.0  39516  1680 ?        Ss   15:20   0:00 //bin/dbus-daemon --fork --print-pid 7 --print-address 9 --config-file /usr/share/fcitx/dbus/daemon.conf
mctiew    1606  0.0  0.0  13028   608 ?        SN   15:20   0:00 /usr/bin/fcitx-dbus-watcher unix:abstract=/tmp/dbus-FZoEv2jMsd,guid=9c18319aefc5e7b69818435453ce10cc 1602
mctiew    1666  0.0  0.0  39248  1992 ?        S    15:20   0:00 /bin/dbus-daemon --config-file=/etc/at-spi2/accessibility.conf --nofork --print-address 3
nobody    3764  0.0  0.0  35244  1540 ?        S    15:21   0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.1.1 --conf-file=/var/run/NetworkManager/dnsmasq.conf --cache-size=0 --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
mctiew    4124  0.0  0.0  15964   952 pts/1    S+   15:30   0:00 grep --color=auto dbus


So many dbus related processes. Is it normal ?

> 
$ env |grep DBUS
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-8Ky1ZPjLAQ
$ ls /tmp/dbus-8Ky1ZPjLAQ
ls: cannot access /tmp/dbus-8Ky1ZPjLAQ: No such file or directory


---

