---
title: "[Debian] Crontab errors."
date: 2017-03-23
forum: Debian
---

### Post by caleo2 on 2017-03-23
Hi everyone,

I'm currently encountering some errors with a crontab (and it's not really my field of skills to be honest).

I have a server who keep desync of 30mins every weeks and since it's not connected to the internet, it can't sync by himself.
However, the BIOS clock seems to be accurate, my idea is to make a crontab to sync the system clock with the BIOS clock everyday, so I made this command in a crontab :

00 12 * * * hwclock --hctosys

Which is not working, the logs shows me this (don't mind the time here since I was running tests to see why it's not working, I programmed it to run the command at 14:39) : 

Mar 23 14:39:01 edificio-bouchar /usr/sbin/cron[19640]: (root) RELOAD (crontabs/root)
Mar 23 14:39:01 edificio-bouchar /USR/SBIN/CRON[22225]: (root) CMD (hwclock --hctosys)
Mar 23 14:39:01 edificio-bouchar /USR/SBIN/CRON[22224]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Mar 23 14:39:01 edificio-bouchar /USR/SBIN/CRON[22223]: (CRON) error (grandchild #22225 failed with exit status 127)

Any idea of why it's not working ?

Thanks in advance,
Julien.

P.S : Sorry for the few mistakes I can make, english is not my native langage.

---

### Post by howefield on 2017-03-23
Thread moved to the "*Debian*" forum.

---

### Post by SeijiSensei on 2017-03-23
> **caleo2 said:**
> However, the BIOS clock seems to be accurate, my idea is to make a crontab to sync the system clock with the BIOS clock everyday, so I made this command in a crontab :

00 12 * * * hwclock --hctosys

Which is not working

Only root can run the hwclock command.  So you need to put the line in /var/spool/cron/root, or you need to edit /etc/crontab in which case the correct syntax is
```
0 12 * * * **root** /sbin/hwclock --hctosys
```

Note that I added the username, root, and the full path to hwclock.  Always use full paths in crontabs since they run with a reduced environment and path.

However if you really want to sync your computer's time, you should use the ntpd daemon.  It will get the time from servers on the Internet: [https://help.ubuntu.com/lts/serverguide/NTP.html#ntpd](https://help.ubuntu.com/lts/serverguide/NTP.html#ntpd)

---

### Post by caleo2 on 2017-03-29
Hi again, 

I've just tested your solution this morning and it seems to work.

I just put the line "00 12 * * * /sbin/hwclock --hctosys" in /var/spool/cron/crontabs. Btw, I had to edit the crontab using "crontab -u root -e" instead of "crontab-e" because it was not working with crontab-e alone even since I was connected as root and it was installing the cron without any warning or error.

Anyway thanks a lot for your help. :)

P.S : I can't use the ntpd daemon solution since this server is not connected on the internet. It's on a private network and since I'm not admin of this network, I don't know if there is a sync server I can use.

---

