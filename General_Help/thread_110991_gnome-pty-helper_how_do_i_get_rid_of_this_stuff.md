---
title: "gnome-pty-helper how do i get rid of this stuff?"
date: 2006-01-01
forum: General Help
---

### Post by sapo on 2006-01-01
My process list after 33 days of uptime:

```
sapo@ubuntu:~$ ps x
  PID TTY      STAT   TIME COMMAND
 9124 ?        S      2:35 esd -nobeeps
 9291 ?        S      0:00 gnome-pty-helper
10956 ?        S      0:00 gnome-pty-helper
10982 ?        S      0:00 gnome-pty-helper
15056 ?        S      0:00 gnome-pty-helper
 1420 ?        S      0:00 gnome-pty-helper
 1458 ?        S      0:00 gnome-pty-helper
 1578 ?        S      0:00 gnome-pty-helper
 1806 ?        S      0:00 gnome-pty-helper
 9870 ?        S      0:00 gnome-pty-helper
 8474 ?        S      0:00 gnome-pty-helper
21952 ?        S      0:00 gnome-pty-helper
22073 ?        S      0:00 gnome-pty-helper
22095 ?        S      0:00 gnome-pty-helper
10937 ?        S      0:00 ivman &
18358 ?        S      0:00 gnome-pty-helper
15303 ?        S      0:00 gnome-pty-helper
18250 ?        S      0:00 gnome-pty-helper
21250 ?        S      0:00 gnome-pty-helper
23368 ?        S      0:00 gnome-pty-helper
23801 ?        Ss     0:00 SCREEN
23802 pts/1    Ss+    0:00 /bin/bash
26684 ?        S      0:00 gnome-pty-helper
26811 ?        S      0:00 gnome-pty-helper
28766 ?        S      0:00 gnome-pty-helper
 1351 ?        S      0:00 gnome-pty-helper
 5555 ?        S      0:00 gnome-pty-helper
 5598 ?        S      0:00 gnome-pty-helper
 6194 ?        S      0:00 gnome-pty-helper
13497 ?        S      0:00 gnome-pty-helper
29585 ?        S      0:00 gnome-pty-helper
29610 ?        S      0:00 gnome-pty-helper
30243 ?        S      0:00 gnome-pty-helper
 4368 ?        S      0:00 gnome-pty-helper
 4565 ?        S      0:00 gnome-pty-helper
 5679 ?        S      0:00 gnome-pty-helper
 5774 ?        S      0:00 gnome-pty-helper
 6153 ?        S      0:00 gnome-pty-helper
 6571 ?        S      0:00 gnome-pty-helper
 6758 ?        S      0:00 gnome-pty-helper
 6874 ?        S      0:00 gnome-pty-helper
 8184 ?        S      0:00 gnome-pty-helper
 8834 ?        S      0:00 gnome-pty-helper
10635 ?        S      0:00 gnome-pty-helper
10815 ?        S      0:00 gnome-pty-helper
10829 ?        S      0:00 gnome-pty-helper
11338 ?        S      0:00 gnome-pty-helper
11590 ?        S      0:00 gnome-pty-helper
15557 ?        S      0:00 gnome-pty-helper
25098 ?        S      0:00 gnome-pty-helper
  738 ?        S      0:00 gnome-pty-helper
 5233 ?        S      0:00 gnome-pty-helper
 7328 ?        S      0:00 gnome-pty-helper
 9038 ?        S      0:00 gnome-pty-helper
10548 ?        S      0:00 gnome-pty-helper
11354 ?        S      0:00 gnome-pty-helper
14465 ?        S      0:00 gnome-pty-helper
15723 ?        S      0:00 gnome-pty-helper
13062 ?        S      0:00 gnome-pty-helper
13476 ?        S      0:00 gnome-pty-helper
32328 ?        S      0:00 gnome-pty-helper
32369 ?        S      0:00 gnome-pty-helper
32487 ?        S      0:00 gnome-pty-helper
32679 ?        S      0:18 /usr/lib/gconf2/gconfd-2 13
32727 ?        S      0:00 gnome-pty-helper
32765 ?        Ss     0:00 /bin/sh /etc/xdg/xfce4/xinitrc
  336 ?        Ss     0:01 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session startxfce4
  339 ?        Ss     0:00 dbus-daemon --fork --print-pid 8 --print-address 6 --session
  340 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session startxfce4
  344 ?        S      0:00 /bin/sh /etc/xdg/xfce4/xinitrc
  345 ?        S      1:36 xscreensaver -no-splash
  349 ?        S      0:28 /usr/bin/xfce4-session
  352 ?        Ss     1:06 xfce-mcs-manager
  355 ?        S    502:21 xfce4-panel --sm-client-id 10fb4b7ef5000113310264200000066240002 --display :0.0
  357 ?        S     12:34 gnome-cups-icon --sm-config-prefix /gnome-cups-icon-APlLgA/ --sm-client-id 10dff4d848000113399867000000293320070 --screen 0
  362 ?        Ss     0:01 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=17
 1799 ?        S      0:00 gnome-pty-helper
 3975 ?        S      0:00 gnome-pty-helper
 8004 ?        S      0:00 gnome-pty-helper
 8407 ?        S      0:00 gnome-pty-helper
 8954 ?        S      0:00 gnome-pty-helper
11021 ?        S      0:00 gnome-pty-helper
11782 ?        S      0:17 gnome-volume-manager
14201 ?        S      0:00 gnome-pty-helper
 3351 ?        S      0:00 gnome-pty-helper
 7521 ?        S      0:00 gnome-pty-helper
 9060 ?        Sl     0:13 /usr/lib/evolution/2.4/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_BookFactory:2.4 --oaf-i11046 ?        S      0:00 gnome-pty-helper
11698 ?        S      0:00 gnome-pty-helper
22552 ?        S      0:00 gnome-pty-helper
27405 ?        S      0:00 gnome-pty-helper
17973 ?        S      0:00 gnome-pty-helper
18536 ?        S      0:00 gnome-pty-helper
22001 ?        S      0:00 gnome-pty-helper
22105 ?        S      0:00 gnome-pty-helper
 1282 ?        S      0:00 gnome-pty-helper
 4455 ?        S      0:00 gnome-pty-helper
 7065 ?        S      0:00 gnome-pty-helper
 7605 ?        S      0:00 gnome-pty-helper
17785 ?        S      0:00 gnome-pty-helper
 3321 ?        S      0:00 gnome-pty-helper
18730 ?        S      0:00 gnome-pty-helper
32100 ?        S     39:26 enlightenment
19047 ?        Sl     0:00 /usr/lib/evolution/evolution-data-server-1.4 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_InterfaceCheck --oaf-ior-fd=30
19052 ?        Sl     0:11 /usr/lib/evolution/2.4/evolution-alarm-notify --oaf-activate-iid=OAFIID:GNOME_Evolution_Calendar_AlarmNotify_Factory:2.4 --oaf-ior-fd= 8501 ?        S      0:00 gnome-pty-helper
13884 ?        S      0:00 gnome-pty-helper
16024 ?        S      0:00 gnome-pty-helper
16737 ?        S      0:00 gnome-pty-helper
17764 ?        S      0:00 gnome-pty-helper
10604 ?        S      0:00 gnome-pty-helper
11140 ?        S      0:00 gnome-pty-helper
18412 ?        S      0:00 gnome-pty-helper
25886 ?        S      0:00 gnome-pty-helper
22112 ?        S      0:00 gnome-pty-helper
22833 ?        S      0:00 gnome-pty-helper
29098 ?        S      0:00 gnome-pty-helper
29743 ?        S      0:00 gnome-pty-helper
25056 ?        S      0:00 gnome-pty-helper
17699 ?        S      5:34 gaim
17714 ?        S      0:00 gnome-pty-helper
23859 ?        S      0:04 xfcalendar
12448 ?        S      0:00 gnome-pty-helper
13544 ?        S      0:00 gnome-pty-helper
15762 ?        Sl     2:33 xchat
32468 ?        S      0:00 gnome-pty-helper
14958 ?        S      0:00 gnome-pty-helper
14992 ?        S      0:00 gnome-pty-helper
23572 ?        S      0:00 gnome-pty-helper
23774 ?        S      0:00 gnome-pty-helper
29174 ?        S      0:00 /usr/bin/kdesud
31586 ?        S      0:00 gnome-pty-helper
32067 ?        S      0:00 /bin/bash /home/sapo/azureus/azureus
32072 ?        Sl     0:55 /usr/java/bin/java -Xms16m -Xmx128m -cp /home/sapo/azureus/Azureus2.jar:/home/sapo/azureus/swt.jar:/home/sapo/azureus/swt-mozilla.jar:  619 ?        S      0:00 gnome-pty-helper
  635 ?        Rl     0:02 gnome-terminal -t Terminal
  636 ?        S      0:00 gnome-pty-helper
  637 pts/2    Ss     0:00 bash
  715 pts/2    R+     0:00 ps x

```

How do i get rid of all these gnome-pty-helper?

I think that this stuff is useless, but i cant get rid of them :(

thanx for any help.

---

### Post by sapo on 2006-01-01
Answering my own question:

```
killall -v -s 9 gnome-pty-helper
```

This killed them all, killall gnome-pty-helper wasnt working.. so i read the killall manual and was able to get rid of those annoying pests :mrgreen:

---

