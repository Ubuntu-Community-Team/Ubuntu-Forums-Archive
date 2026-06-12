---
title: "Lost taskbar and app title bars upon kde wake up from sleep."
date: 2013-07-16
forum: Desktop Environments
---

### Post by davidonlaptop on 2013-07-16
Hello !

When I put the computer to sleep, and then wake it up, the bottom KDE bar is lost,  and the title bar at the top of each application is gone. The only thing remaining is the desktop widget showing the files in my Desktop directory.

I just installed Kubuntu 13.04 yesterday, I did not do any configuration, besides updating the source server and installing all system updates (up to July 15). The computer is Desktop computer, not a laptop.

Any pointers to get started on this problem?

---

### Post by davidonlaptop on 2013-07-17
It's a bit annoying, anyone has seem this problem before?

When I resume from sleep, there is not even the contextual menu upon a right click. Looks like if the KDE shell is gone.

Some more information about my system:

uname -a
Linux Zalman83 3.8.0-26-generic #38-Ubuntu SMP Mon Jun 17 21:43:33 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
X.Org X Server 1.13.3
kde4-config -kde-version
4.10.4
lspci |grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)

Screenshot after wakeup
[ATTACH=CONFIG]244816[/ATTACH]

lspci
[ATTACH]244815[/ATTACH]

lsusb
[ATTACH]244814[/ATTACH]

lsmod
[ATTACH]244817[/ATTACH]


Is this more a Kubuntu / KDE / Nouveau driver / Video card or Xorg problem ?
Is this the right subforum to ask for this problem ?

---

### Post by dino99 on 2013-07-17
i suppose you'll get more chance by posting on [http://www.kubuntuforums.net/forum.php](http://www.kubuntuforums.net/forum.php)

---

### Post by davidonlaptop on 2013-07-17
I am looking at syslog, and found these messages :

```
Jul 17 05:25:23 Zalman83 kernel: [ 2512.219420] nouveau E[  PGRAPH][0000:01:00.0] TRAP ch 1 [0x023fe00000]
Jul 17 05:25:23 Zalman83 kernel: [ 2512.219435] nouveau E[  PGRAPH][0000:01:00.0] GPC0/TPC0/MP: 0x001beff2 0x0000000f
Jul 17 05:25:23 Zalman83 kernel: [ 2512.219444] nouveau E[  PGRAPH][0000:01:00.0] GPC0/TPC1/MP: 0x001beff2 0x0000000f
Jul 17 05:25:23 Zalman83 kernel: [ 2512.219452] nouveau E[  PGRAPH][0000:01:00.0] GPC0/TPC2/MP: 0x001beff2 0x0000000f
Jul 17 05:25:23 Zalman83 kernel: [ 2512.219460] nouveau E[  PGRAPH][0000:01:00.0] GPC0/TPC3/MP: 0x001beff2 0x0000000f
```

Then, there is a few thousands of these messages  :
```
Jul 17 05:25:23 Zalman83 kernel: [ 2512.252626] nouveau E[  PGRAPH][0000:01:00.0] TRAP ch 1 [0x023fe00000]
Jul 17 05:25:23 Zalman83 kernel: [ 2512.252633] nouveau E[  PGRAPH][0000:01:00.0] SHADER 0xa004021e
```

Full syslog
[ATTACH]244818[/ATTACH]

Timestamps of the events :
21:58:24  boot time
22:39:55  sleep  time
05:25:23  wake up time

Are these  TRAP and SHADER events normal ?

---

### Post by davidonlaptop on 2013-07-17
will do.

---

