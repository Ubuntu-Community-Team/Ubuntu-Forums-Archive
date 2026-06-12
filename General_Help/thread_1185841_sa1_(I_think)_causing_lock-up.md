---
title: "sa1 (I think) causing lock-up"
date: 2009-06-12
forum: General Help
---

### Post by IainPurdie on 2009-06-12
Folks,

This one's been bothering me for a few weeks now and I'm seeking any help.

Every so often (can be once a day, can be 2-3 times) my hard drive just goes mental to the point where the PC is as good as frozen.If I wiggle the mouse, maybe once every 20-30 seconds it moves an inch so it's responsive but clogged down with hard drive activity.

There's no correlation with applications running - everything is the same as it was before I started having the problem, at least as far as I know. I'm on Ubuntu 9.04 32-bit.

The only way out is to hold the power switch down for a 4-count and hard reset. Not ideal as I tend to save torrents and the like to a FAT32 partition (so I can access it from the XP and Win7 installs). As a result, when the system keels I often end up with corrupt files which means a reboot into Windows to run a disc scan before I can continue downloads in Ubuntu. More wasted time.

I've checked the system log and it does seem that more often than not the system's running some cron job before it keels over. I can't find the crontab anywhere - there are only two users on the machine that I've set up: root and my own login. Neither of these have the commands in so I'm assuming it's a system crontab that's kicking in (I've attached some lines below). The commands run hourly, and don't seem to cause any issues most times.

Don't know if it's relevant, but if I leave the system for a minute or two then my wi-fi disconnects. Once or twice I've been informed on the screen that this has happen - I normally notice as the light on my laptop case tells me. I'm assuming this is because the system's too locked up to inform me via software.

Any ideas? Lines from syslog immediately prior to the most recent failure follow. If you need any more info, please just ask.

```
Jun 12 22:00:01 iain-laptop /USR/SBIN/CRON[23509]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Jun 12 22:00:01 iain-laptop /USR/SBIN/CRON[23531]: (root) CMD (cd /usr/share/prey; ./prey.sh)
Jun 12 22:00:01 iain-laptop /USR/SBIN/CRON[23534]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun 12 22:03:41 iain-laptop ntpd[4178]: kernel time sync status change 0001
Jun 12 22:05:01 iain-laptop /USR/SBIN/CRON[23747]: (root) CMD ([ -x /usr/lib/sysstat/sa1 ] && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; [ "$ENABLED" = "true" ] && exec /usr/lib/sysstat/sa1 $SA1_OPTIONS 1 1 ; })
Jun 12 22:10:01 iain-laptop /USR/SBIN/CRON[23847]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun 12 22:10:01 iain-laptop /USR/SBIN/CRON[23850]: (root) CMD (cd /usr/share/prey; ./prey.sh)
Jun 12 22:15:01 iain-laptop /USR/SBIN/CRON[24139]: (root) CMD ([ -x /usr/lib/sysstat/sa1 ] && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; [ "$ENABLED" = "true" ] && exec /usr/lib/sysstat/sa1 $SA1_OPTIONS 1 1 ; })
Jun 12 22:17:02 iain-laptop /USR/SBIN/CRON[24192]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 12 22:20:01 iain-laptop /USR/SBIN/CRON[24258]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun 12 22:20:01 iain-laptop /USR/SBIN/CRON[24259]: (root) CMD (cd /usr/share/prey; ./prey.sh)
Jun 12 22:25:01 iain-laptop /USR/SBIN/CRON[24596]: (root) CMD ([ -x /usr/lib/sysstat/sa1 ] && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; [ "$ENABLED" = "true" ] && exec /usr/lib/sysstat/sa1 $SA1_OPTIONS 1 1 ; })
Jun 12 22:30:04 iain-laptop /USR/SBIN/CRON[25095]: (root) CMD (cd /usr/share/prey; ./prey.sh)
Jun 12 22:30:04 iain-laptop /USR/SBIN/CRON[25096]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun 12 22:35:03 iain-laptop /USR/SBIN/CRON[25900]: (root) CMD ([ -x /usr/lib/sysstat/sa1 ] && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; [ "$ENABLED" = "true" ] && exec /usr/lib/sysstat/sa1 $SA1_OPTIONS 1 1 ; })
Jun 12 22:37:50 iain-laptop ntpd[4178]: kernel time sync status change 4001
Jun 12 22:40:03 iain-laptop NetworkManager: <WARN>  killswitch_getpower_reply(): Error getting killswitch power: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.. 
Jun 12 22:40:04 iain-laptop NetworkManager: <WARN>  killswitch_getpower_reply(): HAL did not reply to killswitch power request; assuming radio is blocked. 
Jun 12 22:40:04 iain-laptop NetworkManager: <info>  Wireless now disabled by radio killswitch 
Jun 12 22:40:04 iain-laptop NetworkManager: <info>  (wlan0): device state change: 8 -> 2 
Jun 12 22:40:04 iain-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
Jun 12 22:40:13 iain-laptop NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 3987 
Jun 12 22:40:30 iain-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess  
Jun 12 22:40:32 iain-laptop avahi-daemon[2854]: Withdrawing address record for 192.168.1.4 on wlan0.
Jun 12 22:40:33 iain-laptop avahi-daemon[2854]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.4.
Jun 12 22:40:33 iain-laptop avahi-daemon[2854]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jun 12 22:40:34 iain-laptop NetworkManager: <info>  (wlan0): taking down device. 
Jun 12 22:40:34 iain-laptop avahi-daemon[2854]: Withdrawing address record for fe80::214:a4ff:fe2d:be4 on wlan0.
Jun 12 22:41:56 iain-laptop syslogd 1.5.0#5ubuntu3: restart.
```

---

