---
title: "X server died during startup"
date: 2008-01-16
forum: Desktop Environments
---

### Post by djgenesis on 2008-01-16
Booo hoooo hooooooo :(

I don' know what I installed but my system is really messed up. Can anyone see what  went wrong? 

```

Jan 16 20:37:05 localhost kernel: [17179727.500000] Bluetooth: L2CAP socket layer initialized
Jan 16 20:37:05 localhost hcid[4900]: Starting security manager 0
Jan 16 20:37:05 localhost kernel: [17179727.508000] Bluetooth: RFCOMM socket layer initialized
Jan 16 20:37:05 localhost kernel: [17179727.508000] Bluetooth: RFCOMM TTY layer initialized
Jan 16 20:37:05 localhost kernel: [17179727.508000] Bluetooth: RFCOMM ver 1.7
Jan 16 20:37:05 localhost sdpd[4903]: Bluetooth SDP daemon 
Jan 16 20:37:05 localhost anacron[4954]: Anacron 2.3 started on 2008-01-16
Jan 16 20:37:05 localhost anacron[4954]: Normal exit (0 jobs run)
Jan 16 20:37:05 localhost /usr/sbin/cron[4985]: (CRON) INFO (pidfile fd = 3)
Jan 16 20:37:05 localhost /usr/sbin/cron[4986]: (CRON) STARTUP (fork ok)
Jan 16 20:37:05 localhost /usr/sbin/cron[4986]: (CRON) INFO (Running @reboot jobs)
Jan 16 20:37:06 localhost kdm[5036]: X server died during startup
Jan 16 20:37:06 localhost kdm[5036]: X server for display :0 can't be started, session disabled
Jan 16 20:39:11 localhost dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
Jan 16 20:39:11 localhost kdm[5223]: X server died during startup
Jan 16 20:39:11 localhost kdm[5223]: X server for display :0 can't be started, session disabled
Jan 16 20:39:18 localhost dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
Jan 16 20:39:32 localhost dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
Jan 16 20:39:42 localhost dhclient: No DHCPOFFERS received.
Jan 16 20:39:42 localhost dhclient: No working leases in persistent database - sleeping.
Jan 16 20:42:33 localhost dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
Jan 16 20:42:39 localhost dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
Jan 16 20:42:51 localhost dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
Jan 16 20:43:04 localhost dhclient: No DHCPOFFERS received.
Jan 16 20:43:04 localhost dhclient: No working leases in persistent database - sleeping.
```

I am quite scared of this log line in particular:
**Jan 16 20:37:06 localhost kdm[5036]: X server for display :0 can't be started, session disabled**

---

### Post by sumguy231 on 2008-01-17
Hit Ctrl+Alt+F1 to see if you can get to a terminal, then run
```
startx
``` 
To get error output and find out exactly why the X server can't be started. Also provide information about your video hardware.

---

### Post by djgenesis on 2008-01-17
```
 
Fatal Server Error:
Requested entity already in use!

XIO: fatal IO error 104 (Connection Reset By Peer) on X server "0:0" 
after 0 requests (0 known processed) with 0 events remaining

```

I have a ATi Radeon 9500 and it was running fine on dual head. 

After runnuing:

```
 sudo dpkg-reconfigure xserver-xorg 
``` and trying to startx I got:

```
 Fatal Server Error 
could not open default font 'fixed'
disable montype:1 
disable montype:1 
Entering Restore TV

XIO: fatal IO error 104 (Connection Reset By Peer) on X server "0:0" 
after 0 requests (0 known processed) with 0 events remaining

```

I think something serious is going on...

---

