---
title: "Gutsy freezing. Can't find anything in syslog or messages"
date: 2008-04-15
forum: Desktop Environments
---

### Post by ac251404 on 2008-04-15
I have a fileserver/HTPC setup and am running into a problem where it will occasionally freeze. The 2 times I noticed it I was streaming a video from the server to my PC, but it has happened at other times as well. 

What is installed/running:
  - Apache2, MySQL, PHP
  - TorrentFlux-b4rt
  - XBMC (Xbox Media Center) alpha release 2 


I have checked out the apache access and error logs and dont see any problems. I have also looked through the XBMC log (with debugging enabled) and also see no problems. The syslog also looks uneventful and just shows a few cron jobs that ran. The message log is showing no obvious errors but is also beyond the scope of my understanding so I was hoping someone here could take a look.

The last freeze occurred at 1:17am so I am just pasting the corresponding part of the log.

messages
```

Apr 15 01:01:04 ODIN kernel: [20589.744814]  [kobject_set_name+55/192] kobject_set_name+0x37/0xc0
Apr 15 01:01:04 ODIN kernel: [20589.744828]  [device_add+196/1392] device_add+0xc4/0x570
Apr 15 01:01:04 ODIN kernel: [20589.744848]  [<f89ae080>] add_conn+0x0/0x80 [bluetooth]
Apr 15 01:01:04 ODIN kernel: [20589.744864]  [<f89ae091>] add_conn+0x11/0x80 [bluetooth]
Apr 15 01:01:04 ODIN kernel: [20589.744879]  [run_workqueue+129/272] run_workqueue+0x81/0x110
Apr 15 01:01:04 ODIN kernel: [20589.744889]  [prepare_to_wait+32/112] prepare_to_wait+0x20/0x70
Apr 15 01:01:04 ODIN kernel: [20589.744898]  [worker_thread+0/256] worker_thread+0x0/0x100
Apr 15 01:01:04 ODIN kernel: [20589.744906]  [worker_thread+160/256] worker_thread+0xa0/0x100
Apr 15 01:01:04 ODIN kernel: [20589.744914]  [autoremove_wake_function+0/80] autoremove_wake_function+0x0/0x50
Apr 15 01:01:04 ODIN kernel: [20589.744925]  [worker_thread+0/256] worker_thread+0x0/0x100
Apr 15 01:01:04 ODIN kernel: [20589.744930]  [kthread+66/112] kthread+0x42/0x70
Apr 15 01:01:04 ODIN kernel: [20589.744935]  [kthread+0/112] kthread+0x0/0x70
Apr 15 01:01:04 ODIN kernel: [20589.744943]  [kernel_thread_helper+7/16] kernel_thread_helper+0x7/0x10
Apr 15 01:01:04 ODIN kernel: [20589.744955]  =======================
Apr 15 01:17:07 ODIN kernel: [21551.760308]  [kobject_shadow_add+277/416] kobject_shadow_add+0x115/0x1a0
Apr 15 01:17:07 ODIN kernel: [21551.760323]  [kobject_set_name+55/192] kobject_set_name+0x37/0xc0
Apr 15 01:17:07 ODIN kernel: [21551.760335]  [device_add+196/1392] device_add+0xc4/0x570
Apr 15 01:17:07 ODIN kernel: [21551.760356]  [<f89ae080>] add_conn+0x0/0x80 [bluetooth]
Apr 15 01:17:07 ODIN kernel: [21551.760373]  [<f89ae091>] add_conn+0x11/0x80 [bluetooth]
Apr 15 01:17:07 ODIN kernel: [21551.760388]  [run_workqueue+129/272] run_workqueue+0x81/0x110
Apr 15 01:17:07 ODIN kernel: [21551.760397]  [prepare_to_wait+32/112] prepare_to_wait+0x20/0x70
Apr 15 01:17:07 ODIN kernel: [21551.760407]  [worker_thread+0/256] worker_thread+0x0/0x100
Apr 15 01:17:07 ODIN kernel: [21551.760414]  [worker_thread+160/256] worker_thread+0xa0/0x100
Apr 15 01:17:07 ODIN kernel: [21551.760422]  [autoremove_wake_function+0/80] autoremove_wake_function+0x0/0x50
Apr 15 01:17:07 ODIN kernel: [21551.760433]  [worker_thread+0/256] worker_thread+0x0/0x100
Apr 15 01:17:07 ODIN kernel: [21551.760437]  [kthread+66/112] kthread+0x42/0x70
Apr 15 01:17:07 ODIN kernel: [21551.760442]  [kthread+0/112] kthread+0x0/0x70
Apr 15 01:17:07 ODIN kernel: [21551.760450]  [kernel_thread_helper+7/16] kernel_thread_helper+0x7/0x10
Apr 15 01:17:07 ODIN kernel: [21551.760463]  =======================
Apr 15 11:54:46 ODIN syslogd 1.4.1#21ubuntu3: restart.

```

syslog (for the heck of it)
```

Apr 15 12:00:07 ODIN syslogd 1.4.1#21ubuntu3: restart.
Apr 15 12:00:07 ODIN anacron[5637]: Job `cron.daily' terminated (mailing output)
Apr 15 12:00:07 ODIN anacron[5637]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Apr 15 12:00:07 ODIN anacron[5637]: Normal exit (1 job run)
Apr 15 12:09:01 ODIN /USR/SBIN/CRON[6446]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr 15 12:11:30 ODIN kernel: [ 1106.205285] UDP: bad checksum. From 24.77.18.179:8722 to 192.168.1.215:49230 ulen 26
Apr 15 12:17:02 ODIN /USR/SBIN/CRON[6733]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 15 12:34:46 ODIN -- MARK --
Apr 15 12:39:01 ODIN /USR/SBIN/CRON[6742]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr 15 12:54:46 ODIN -- MARK --
Apr 15 13:09:01 ODIN /USR/SBIN/CRON[6782]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr 15 13:17:01 ODIN /USR/SBIN/CRON[6798]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 15 13:34:46 ODIN -- MARK --
Apr 15 13:39:01 ODIN /USR/SBIN/CRON[7132]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr 15 13:54:46 ODIN -- MARK --
Apr 15 14:09:01 ODIN /USR/SBIN/CRON[7263]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)

```

It doesn't look like much to go off of but I'm crossing my fingers that somebody sees something or can point me in another direction to possibly diagnose this.

Thanks,
ac

---

