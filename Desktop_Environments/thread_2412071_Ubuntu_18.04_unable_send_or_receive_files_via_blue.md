---
title: "Ubuntu 18.04 unable send or receive files via bluetooth"
date: 2019-02-07
forum: Desktop Environments
---

### Post by danjde on 2019-02-07
Hi Friends!
I've just upgraded Ubuntu-Gnome from 16.04 to 18.04,
now I've realized that is not possible send files from my android phone to my linux-box trough Bluetooth.

This is my hardware:

```
lspci -knn | grep Net -A2; lsusb
02:00.0 Network controller [0280]: Intel Corporation Device [8086:24fb] (rev 10)
    Subsystem: Intel Corporation Device [8086:2110]
    Kernel driver in use: iwlwifi
Bus 002 Device 002: ID 0b95:1790 ASIX Electronics Corp. AX88179 Gigabit Ethernet
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:0aa7 Intel Corp. 
Bus 001 Device 002: ID 04f2:b5d6 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Then, this is my /var/log/syslog refer to Bluetooth sending file from phone to computer:

```

Feb  7 23:57:22 cosmogoniA-Book obexd[1976]: CONNECT(0x0), (null)(0xffffffff)
Feb  7 23:57:22 cosmogoniA-Book obexd[1976]: CONNECT(0x0), (null)(0x0)
Feb  7 23:57:22 cosmogoniA-Book obexd[1976]: PUT(0x2), (null)(0xffffffff)
Feb  7 23:57:25 cosmogoniA-Book gsd-media-keys[1764]: Unable to get default source
Feb  7 23:57:52 cosmogoniA-Book bluetoothd[898]: Unable to get io data for Object Push: getpeername: Transport endpoint is not connected (107)
Feb  7 23:57:52 cosmogoniA-Book obexd[1976]: Source ID 48 was not found when attempting to remove it
Feb  7 23:57:52 cosmogoniA-Book obexd[1976]: PUT(0x2), FORBIDDEN(0x43)
Feb  7 23:57:52 cosmogoniA-Book obexd[1976]: disconnected: Transport got disconnected
```


Is this a bug or could I resolve it?

Many thanks!

Davide

---

### Post by mpopov on 2019-08-31
Hello,

I've problems with receiving files on my Ubuntu 18.04 from my smartphone. Sending worked ok. So what I did is installed blueman and obexftp:
>  sudo apt install blueman obexftp 

Then you need to allow Blueman to receive files. Find "Bluetooth Manager" in Dash search to make sure it run, and choose "Local Services..." from tray menu. Navigate to Transfer tab and make sure "Accept files from trusted devices" is on (was disabled on my installation). Now it should receive files from smartphone. Worked like a charm for me.

Sincerely,
Max.

---

### Post by DuckHook on 2019-08-31
Welcome to the forums, mpopov.

Many thanks for your participation and your helpfulness.

Sadly, this thread is months old and the OP has likely long left the building. If you wish to continue helping, I would recommend visiting the "Unanswered Posts" filter under "Quick Links" at the top of your page and helping some more recent poster.

In the interest of not reviving necroposts, I will now *close this thread*.

---

