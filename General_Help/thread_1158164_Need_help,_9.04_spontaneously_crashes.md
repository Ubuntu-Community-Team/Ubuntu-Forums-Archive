---
title: "Need help, 9.04 spontaneously crashes"
date: 2009-05-13
forum: General Help
---

### Post by adt41287 on 2009-05-13
I recently started experiencing a problem with ubuntu crashes.  It seems that it is pretty random (just actually experienced a crash while typing this).  When 9.04 came out I did a fresh install.  Here are some of the log files before it crashes, let me know if you need more information.  Im not sure where to begin right now, but any help is appreciated

kern.log
```
May 13 12:32:39 zion kernel: [   22.240878] vboxdrv: Trying to deactivate the NMI watchdog permanently...
May 13 12:32:39 zion kernel: [   22.240881] vboxdrv: Successfully done.
May 13 12:32:39 zion kernel: [   22.240883] vboxdrv: Found 2 processor cores.
May 13 12:32:39 zion kernel: [   22.240947] vboxdrv: fAsync=1 offMin=0x320182 offMax=0x320182
May 13 12:32:39 zion kernel: [   22.240993] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
May 13 12:32:39 zion kernel: [   22.240994] vboxdrv: Successfully loaded version 2.2.2 (interface 0x000a0009).
May 13 12:32:41 zion kernel: [   23.600015] ivtv 0000:01:07.0: firmware: requesting v4l-cx2341x-enc.fw
May 13 12:32:41 zion kernel: [   23.651263] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
May 13 12:32:41 zion kernel: [   23.848109] ivtv0: Encoder revision: 0x02060039
May 13 12:32:41 zion kernel: [   23.863747] cx25840 2-0044: firmware: requesting v4l-cx25840.fw
May 13 12:32:44 zion kernel: [   27.039707] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
May 13 12:32:47 zion kernel: [   30.070335] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
May 13 12:32:47 zion kernel: [   30.070337] Bluetooth: BNEP filters: protocol multicast
May 13 12:32:47 zion kernel: [   30.106134] Bridge firewalling registered
May 13 12:33:02 zion kernel: [   45.168009] eth0: no IPv6 routers present
May 13 12:33:51 zion kernel: [   94.502161] Clocksource tsc unstable (delta = -201428374 ns)
```

messages
```
May 13 12:32:39 zion kernel: [   22.240947] vboxdrv: fAsync=1 offMin=0x320182 offMax=0x320182
May 13 12:32:39 zion kernel: [   22.240993] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
May 13 12:32:41 zion kernel: [   23.600015] ivtv 0000:01:07.0: firmware: requesting v4l-cx2341x-enc.fw
May 13 12:32:41 zion kernel: [   23.651263] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
May 13 12:32:41 zion kernel: [   23.848109] ivtv0: Encoder revision: 0x02060039
May 13 12:32:41 zion kernel: [   23.863747] cx25840 2-0044: firmware: requesting v4l-cx25840.fw
May 13 12:32:44 zion kernel: [   27.039707] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
May 13 12:32:47 zion kernel: [   30.070335] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
May 13 12:32:47 zion kernel: [   30.070337] Bluetooth: BNEP filters: protocol multicast
May 13 12:32:47 zion kernel: [   30.106134] Bridge firewalling registered
May 13 12:33:51 zion kernel: [   94.502161] Clocksource tsc unstable (delta = -201428374 ns)
```

syslog
```
ay 13 12:32:56 zion ntpd[3154]: ntpd exiting on signal 15
May 13 12:32:57 zion ntpdate[3908]: adjust time server 132.236.56.250 offset 0.301392 sec
May 13 12:32:57 zion ntpd[3941]: ntpd 4.2.4p4@1.1520-o Sat Mar 21 00:50:18 UTC 2009 (1)
May 13 12:32:57 zion ntpd[3942]: precision = 1.000 usec
May 13 12:32:57 zion ntpd[3942]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
May 13 12:32:57 zion ntpd[3942]: Listening on interface #1 wildcard, ::#123 Disabled
May 13 12:32:57 zion ntpd[3942]: Listening on interface #2 lo, ::1#123 Enabled
May 13 12:32:57 zion ntpd[3942]: Listening on interface #3 eth0, fe80::21d:60ff:fe1d:d2c2#123 Enabled
May 13 12:32:57 zion ntpd[3942]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
May 13 12:32:57 zion ntpd[3942]: Listening on interface #5 eth0, 192.168.0.23#123 Enabled
May 13 12:32:57 zion ntpd[3942]: kernel time sync status 0040
May 13 12:32:57 zion ntpd[3942]: frequency initialized -7.035 PPM from /var/lib/ntp/ntp.drift
May 13 12:32:58 zion console-kit-daemon[3181]: WARNING: Couldn't read /proc/3180/environ: Failed to open file '/proc/3180/environ': No such file or directory 
May 13 12:33:01 zion x-session-manager[3959]: EggSMClient-WARNING: Desktop file '/home/adam/.config/autostart/miro.desktop' has malformed Icon key 'miro-72x72.png'(should not include extension) 
May 13 12:33:02 zion kernel: [   45.168009] eth0: no IPv6 routers present
May 13 12:33:51 zion kernel: [   94.502161] Clocksource tsc unstable (delta = -201428374 ns)
```

---

