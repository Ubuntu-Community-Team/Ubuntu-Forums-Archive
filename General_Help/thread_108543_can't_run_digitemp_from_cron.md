---
title: "can't run digitemp from cron"
date: 2005-12-26
forum: General Help
---

### Post by sonium on 2005-12-26
Hi, I'm using Ubuntu Breezy and digitemp 1.3

I'm trying to get digitemp running with cacti.

If I start digitemp as user www-data everything works fine...

```

sonium@ubuntu:~$ sudo su www-data
sh-3.00$ digitemp -r750 -a
DigiTemp v1.3 Copyright 1997-99 by Nexus Computing

Dec 26 00:33:33 Sensor 0 C: 0.69 F: 33.24
sh-3.00$

```

..even if I pipe the output...

```

sh-3.00$ digitemp -r750 -a > /var/log/temperature
sh-3.00$ cat /var/log/temperature
DigiTemp v1.3 Copyright 1997-99 by Nexus Computing

Dec 26 00:35:04 Sensor 0 C: 0.69 F: 33.24
sh-3.00$

```
...but If I embed it to cron...

```

sonium@ubuntu:~$ cat /etc/cron.d/cacti
MAILTO=root
*/1 * * * * www-data digitemp -r750 -a >/var/log/temperature
*/5 * * * * www-data /usr/share/cacti/site/poller.php >/dev/null
2>/var/log/cacti/poller-error.log

```
digitemp stops working (and only digitemp, for example "echo test" does
fine)
and /var/log/temperature is overwritten with whitespace

```

sonium@ubuntu:~$ cat /var/log/temperature
sonium@ubuntu:~$

```

Question: why?

---

