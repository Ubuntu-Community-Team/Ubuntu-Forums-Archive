---
title: "Does anyone else experience this problem with lighttpd?"
date: 2009-03-16
forum: General Help
---

### Post by fontenot_1031 on 2009-03-16
I'm running lighttpd, postgresql and php using fastcgi on my laptop. I was looking at my processes and wondering why I have so many php5-cgi processes running at once. Here's my process table:
```

 6443 ?        S      0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid
 6452 ?        Sl     0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-i
 6455 ?        S      0:14 python /usr/lib/gcdemu/gcdemu --oaf-activate-iid=OAFI
 6481 ?        S      0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp
 6499 ?        S      0:05 /usr/lib/notification-daemon/notification-daemon
 7272 ?        SN     0:00 /usr/sbin/lighttpd -f /etc/lighttpd/lighttpd.conf
 7273 ?        SNs    0:00 /usr/bin/php5-cgi
 7277 ?        SNs    0:00 /usr/bin/php5-cgi
 7279 ?        SNs    0:00 /usr/bin/php5-cgi
 7282 ?        SNs    0:00 /usr/bin/php5-cgi
 7296 ?        SN     0:00 /usr/bin/php5-cgi
 7298 ?        SN     0:00 /usr/bin/php5-cgi
 7299 ?        SN     0:00 /usr/bin/php5-cgi
 7300 ?        SN     0:00 /usr/bin/php5-cgi
 9361 ?        Sl     9:26 /usr/lib/firefox-3.0.7/firefox
 9426 ?        Sl     0:09 pidgin
11146 ?        S      0:00 [pdflush]
11672 ?        Sl     3:29 python /usr/lib/exaile/exaile.py
12210 ?        S      0:03 gimp-2.6
12212 ?        Sl     0:00 /usr/bin/python /usr/bin/terminator
12216 ?        S      0:00 /usr/lib/gimp/2.0/plug-ins/script-fu -gimp 11 10 -run
12217 ?        S      0:00 gnome-pty-helper
12218 pts/0    Ss     0:00 /bin/bash
12286 pts/0    S+     0:00 python /usr/bin/pykill

```

just wondering if that's normal (I'm not currently using the php interpreter by the way). By the way php5 isn't extra-laggy when I do use it.

---

