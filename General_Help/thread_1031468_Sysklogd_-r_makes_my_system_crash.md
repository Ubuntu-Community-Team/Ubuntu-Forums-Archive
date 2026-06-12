---
title: "Sysklogd -r makes my system crash"
date: 2009-01-05
forum: General Help
---

### Post by rasup on 2009-01-05
Hi

I've set up my openwrt router to log to my Ubuntu 8.10 laptop.

On my Ubuntu laptop I've edited /etc/default/syslogd so SYSLOGD="-r".
The problem is that when I restart my laptop and want to see the log with: ```
tail -f /var/log/syslog
``` only one or two new log messages appear and then logging stops (including logs on my laptop). If I then try to restart sysklogd with: ```
sudo /etc/init.d/sysklogd restart
``` nothing happens after I've entered my password, actually I can't do anything with sudo. I can't even shutdown my laptop.

If I quickly after restart change /etc/default/syslog so SYSLOGD="" and then restart sysklogd, my system is fine again. If I later restart sysklogd with SYSLOGD="-r" logging works fine and my system doesn't crash.

---

