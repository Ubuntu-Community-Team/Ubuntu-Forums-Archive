---
title: "networking issues"
date: 2005-05-15
forum: Desktop Environments
---

### Post by mindspin on 2005-05-15
Hi, I'm running kubuntu on a thinkpad 600x with a xircom nic/modem card.
I'm not sure wether its more a question for "laptop" or "networking" area, but here we go: When I try to copy files larger than 1MB from a shared folder (fish) from my server to the notebook, networking is going down randomly. After about transferring approximately 30% of the data, networking hangs. sudo /etc/init.d/networking |stop|start|restart works in two out of three cases. 
sometimes the route vanishes, sometimes not. This is a very strange behaviour. Any hints would be appreciated.

thanks, mindspin

---

### Post by nemin on 2005-05-15
[QUOTE=mindspin]Hi, I'm running kubuntu on a thinkpad 600x with a xircom nic/modem card.
I'm not sure wether its more a question for "laptop" or "networking" area, but here we go: When I try to copy files larger than 1MB from a shared folder (fish) from my server to the notebook, networking is going down randomly. After about transferring approximately 30% of the data, networking hangs. sudo /etc/init.d/networking |stop|start|restart works in two out of three cases. 
sometimes the route vanishes, sometimes not. This is a very strange behaviour. Any hints would be appreciated.[/QUOTE]
Did you ever try another OS on this laptop? Did it work well then?

---

### Post by mindspin on 2005-05-15
It worked fine under knoppix hd-install, sorry for not giving that info.....

mindspin

---

### Post by nemin on 2005-05-15
[QUOTE=mindspin]It worked fine under knoppix hd-install, sorry for not giving that info.....[/QUOTE]That sounds like a strange problem indeed. Do you logfiles give some information at the moment when the network hangs? By the way, what do you *exactly* mean with "hanging"? I assume just no data is transmitted anymore?

---

### Post by mindspin on 2005-05-15
"network hangs" means indeed no data is transferred, no machine within the internal network can be pinged or contacted, no default gateway is defined (besides 127.0.0.1 for localhost ;-) anymore.

sylog says: 
.....
May 15 12:24:55 localhost kernel: eth0: MII link partner: 45e1
May 15 12:24:55 localhost kernel: eth0: MII selected
May 15 12:24:55 localhost kernel: eth0: media 100BaseT, silicon revision 5
May 15 12:24:55 localhost postfix/master[5561]: reload configuration
May 15 12:25:06 localhost kernel: eth0: no IPv6 routers present
May 15 12:46:02 localhost -- MARK --
May 15 13:06:05 localhost -- MARK --
May 15 13:17:01 localhost /USR/SBIN/CRON[6990]: (root) CMD (   run-parts --report /etc/cron.hourly)
May 15 13:28:04 localhost cardmgr[5444]: executing: './network check eth0'
May 15 13:28:05 localhost cardmgr[5444]: check cmd exited with status 1
May 15 13:30:06 localhost postfix/master[5561]: reload configuration
May 15 13:30:07 localhost postfix/master[5561]: reload configuration
May 15 13:32:00 localhost cardmgr[5444]: executing: './network check eth0'
May 15 13:32:00 localhost cardmgr[5444]: executing: './serial check ttyS3'
May 15 13:32:00 localhost cardmgr[5444]: executing: './network stop eth0'
May 15 13:32:01 localhost cardmgr[5444]: executing: './serial stop ttyS3'
May 15 13:32:11 localhost kernel: unregister_netdevice: waiting for eth0 to become free. Usage count = 1
May 15 13:32:42 localhost last message repeated 3 times
May 15 13:33:43 localhost last message repeated 6 times
May 15 13:34:44 localhost last message repeated 6 times
May 15 13:35:04 localhost last message repeated 2 times
May 15 13:35:09 localhost udev[7429]: removing device node '/dev/vcs7'
May 15 13:35:09 localhost udev[7431]: removing device node '/dev/vcsa7'
May 15 13:35:09 localhost shutdown[7432]: shutting down for system reboot
.....
after reboot everything works fine, until I try to copy data ( folders with subfolders, mp3z with >= 10 M )

after copying parts of it, anything stops ......

mindspin

I think, the best would be to get a newer version of the driver (xirc2ps_cs, pcmcia) and have a try. But this does not really suit me cause the ubuntu repository/apt system was one of the reasons I installed kubuntu...

---

