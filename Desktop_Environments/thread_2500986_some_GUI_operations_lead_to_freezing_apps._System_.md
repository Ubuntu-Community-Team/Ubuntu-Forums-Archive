---
title: "some GUI operations lead to freezing apps. System not usable."
date: 2024-09-18
forum: Desktop Environments
---

### Post by franknfurter2 on 2024-09-18
Yesterday I did a release upgrade from 22.04. to 24.04. Years ago I had setup the system with an ubuntu studio installation, maybe starting with 16.04. or 18.04. Most of the time in the past all went fine or had litte bugs which I could solve myself. But now I am stuck.

The 24.04 system boots normal and I am able to login into Wayland or X11. But in both of them apps hang while doing special operations. I.e. I can start the terminal app normal but when I add another tab in it it freezes for a while (one minute or so) and a information box is displayed telling that terminal is not responding, asking if I want to wait or kill terminal.

Another example is firfox which works normal unless you klick on a drop down box in an html form. Then it freezes also and the same box appears asking the same questions for firefox. journalctl -f or dmesg does not give any information. I do not know what the apps are waiting for. At the moment, the system worth nothing.

My system is Ubuntu 24.04.1 LTS on a Intel Core i5 system without an extra graphic card. There is enough swap space configured. Kernel is 6.8.0-45-lowlatency but behavior is the same with generic kernel.

 I tried to run with a fresh downloaded live iso of ubuntustudio from usb device and all seems to work fine with it. So how to investigate what is going on here and solve it.

---

### Post by Holger_Gehrke on 2024-09-19
Try setting up a new user. If logging in as that user doesn't show the problem then you know that it's a problem with your user-specific configuration.

Holger

---

### Post by franknfurter2 on 2024-09-19
Dear Holger,

i have set up a new user with gnome-system-utils but the behavior is the same. So I switched back to my main user and did an strace of the gnome-terminal-server process. I had to terminal windows open. in the first I started sudo strace -Ff -tt -p <pid> 2>&1 | tee strace-term-serv.log and in the second terminal window I clicked on the plus sign to open another tab. As you can see, between [pid 11942] 10:57:33.161984 and [pid 12882] 10:58:03.190988 there was a lack of 30 seconds where nothing happens in the trace. Of course, problem here is that the same application is freezing and might be strace freezes as well. But I have no other app to test at the moment. Firefox has same behavior but it has many process ids so I not not know which of them i should strace. 

> [pid 12882] 10:57:33.161509 read(21, "WWWW", 10) = 4
[pid 12882] 10:57:33.161662 read(21, 0x7e54819ff5ce, 10) = -1 EAGAIN (Die Ressource ist zur Zeit nicht verfügbar)
[pid 12882] 10:57:33.161766 futex(0x59e3c06e4320, FUTEX_UNLOCK_PI_PRIVATE) = 0
[pid 11942] 10:57:33.161823 <... futex resumed>) = 0
[pid 12882] 10:57:33.161850 poll([{fd=21, events=POLLIN}, {fd=25, events=POLLIN}], 2, 29999 <unfinished ...>
[pid 11942] 10:57:33.161930 futex(0x59e3c06e4320, FUTEX_UNLOCK_PI_PRIVATE) = 0
[pid 11942] 10:57:33.161984 futex(0x59e3c0874978, FUTEX_WAIT_BITSET_PRIVATE|FUTEX_CLOCK_REALTIME, 0, NULL, FUTEX_BITSET_MATCH_ANY <unfinished ...>
[pid 12882] 10:58:03.190988 <... poll resumed>) = 0 (Timeout)
[pid 12882] 10:58:03.192265 futex(0x59e3c0874978, FUTEX_WAKE_PRIVATE, 2147483647) = 1
[pid 11942] 10:58:03.192390 <... futex resumed>) = 0
[pid 12882] 10:58:03.192439 write(23, "W", 1 <unfinished ...>
[pid 11942] 10:58:03.192493 futex(0x59e3c06e4320, FUTEX_LOCK_PI_PRIVATE, NULL <unfinished ...>

---

