---
title: "Clock Applet Using 245Mb!"
date: 2006-07-03
forum: Desktop Environments
---

### Post by firebadger on 2006-07-03
My clock-applet is eating my memory!  I've attached the output of top and just prior to grabbing that I quit Evolution as I thought that might help but it hasn't.  Can anybody advise?  Also, is this a record? ;-)

Tasks:  81 total,   1 running,  80 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.4% us,  0.4% sy,  0.0% ni, 98.2% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:   1554756k total,  1274936k used,   279820k free,   182128k buffers
Swap:   634528k total,    18156k used,   616372k free,   503748k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
31435 alan      16   0  254m 196m 8856 S  0.0 12.9   2:25.94 clock-applet
14339 alan      15   0  163m  69m  40m S  0.0  4.6   0:05.20 soffice.bin
 4256 root      15   0  196m  60m 9.8m S  1.6  4.0  45:03.35 Xorg
31731 alan      15   0  133m  57m  23m S  0.0  3.8   1:31.29 firefox-bin
 4728 tomcat    16   0  241m  47m  12m S  0.0  3.1   0:13.31 java
31914 alan      15   0 47664  23m  12m S  0.0  1.5   0:10.74 gedit
31384 alan      15   0 81600  22m  14m S  0.0  1.5   0:20.13 nautilus
 1103 alan      16   0 63036  22m  13m S  0.0  1.5   0:10.76 gaim
31382 alan      15   0 40076  17m  11m S  0.0  1.2   0:16.53 gnome-panel

---

