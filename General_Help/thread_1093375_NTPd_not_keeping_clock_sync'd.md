---
title: "NTPd not keeping clock sync'd"
date: 2009-03-11
forum: General Help
---

### Post by txr13 on 2009-03-11
I am using Ubuntu 8.04.2 LTS Server (no GUI installed) on the machines in my farm. Because I don't want to be excessive, I have two of my servers syncing with external NTP sources and serving NTP data to the rest of the subnet.

Most of the subnet is keeping time just fine, as are the master servers themselves. However, one of the servers isn't keeping time properly. After it got more than an hour out of sync, I stopped ntpd and ran ntpdate against the master servers on my network. This correctly resync'd the clock on the problem server.

I restarted ntpd and decided to watch its behavior via "ntpq -p" for a little bit. This is what I saw:

```
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 192.168.1.7     132.246.168.148  3 u   31   64    1    0.443  119.598   0.001
 192.168.1.10    132.246.168.164  3 u   30   64    1    0.557  132.617   0.001

```

After a couple minutes, I checked again.

```
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 192.168.1.7     132.246.168.148  3 u   24   64    7    0.463  1299.87 932.972
 192.168.1.10    132.246.168.164  3 u   19   64    7    0.600  1350.31 962.553

```

A third check:

```
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 192.168.1.7     132.246.168.148  3 u   47   64   17    0.426  1889.25 1274.01
 192.168.1.10    132.246.168.164  3 u   44   64   17    0.533  1930.70 1288.83

```

The offset and jitter parameters continue to increase, and I figure that's why ntpd isn't keeping time on this machine--it goes past ntpd's ability to correct, requiring me to eventually use ntpdate to set it properly.

My question is this: why does ntpd on this machine think the offset is climbing so fast? I've checked the clock on the server, and it's fine, if a bit slow. In the last half hour, the clocks on master and problem machines have diverged by 14 seconds, but this behavior isn't being exhibited by any other machines in the farm.

Is NTP's attempt to control the drift on this machine gone badly out of whack? Or is it somehow not understanding the time reference on the master server? I'm really at a loss to explain this, or solve it.

Any help would be appreciated. Thanks!

---

### Post by jonobr on 2009-03-11
THis sounds like an oscillator going out of kilter.
SOunds like it may require changing a motherboard.

If I remember rightly, the thing can cope with up to 50 seconds delay, however, it sounds as if you reaching and going beyond that really fast with no correction, again, from my part , looks hardware related.

---

### Post by pennacook on 2009-03-11
Is messages showing anything? 
how about ntpq -p?
I'd also suggest checking your hardware clock (hwclock) to make sure it is keeping time.

---

### Post by txr13 on 2009-03-11
```
joe@Problem:~$ ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 192.168.1.7     132.246.168.148  3 u   53   64  377    0.383  47736.3 2676.13
 192.168.1.10    132.246.168.164  3 u   48   64  377    0.524  47798.8 2671.75

joe@Problem:~$ hwclock
Wed 11 Mar 2009 10:51:59 AM PDT  -0.354660 seconds

joe@Problem:~$ date
Wed Mar 11 11:53:58 PDT 2009
```

This compares to the master:
```
joe@Master:~$ date
Wed Mar 11 11:55:00 PDT 2009
```

I didn't know about the hwclock command - thankee. :) Looks like the hardware clock is still on standard time (expected), but beyond that, it seems the lag is continuing to increase.

EDIT: And no, messages isn't showing anything beyond the occasional syslogd restart and the general --MARK-- status messages.

---

### Post by pennacook on 2009-03-11
your hardware clock is on PDT, so it is an hour off (incorrectly). I'd suggest running a hwclock --systohc and then seeing if the drifting still occurs.

---

### Post by txr13 on 2009-03-12
Right, so here's what I've done:

1. Stopped ntpd.
2. Deleted NTP's drift file (just in case).
3. Re-ran ntpdate against the master server.
4. Ran hwclock --systohc.
5. Restarted NTP.

Immediately thereafter, this was the result:

```
joe@Problem:~# hwclock
Thu 12 Mar 2009 01:51:33 AM PDT  -0.242885 seconds

joe@Problem:~# date
Thu Mar 12 01:51:35 PDT 2009

joe@Problem:~# ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 192.168.1.7     132.246.168.148  3 u    5   64    1    0.386  269.334   0.001
 192.168.1.10    132.246.168.164  3 u    4   64    1    0.544  290.923   0.001
```

Also, for reference, I then logged into my master server to get the output of date for reference:

```
joe@Master:~# date
Thu Mar 12 01:52:15 PDT 2009
```


After giving the clock a few minutes, the problem server now shows this:

```
joe@Problem:~# hwclock
Thu 12 Mar 2009 01:57:14 AM PDT  -0.771099 seconds

joe@Problem:~# date
Thu Mar 12 01:57:12 PDT 2009

joe@Problem:~# ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 192.168.1.7     132.246.168.148  3 u   14   64   77    0.408  3254.42 1976.71
 192.168.1.10    132.246.168.164  3 u   11   64   77    0.534  3293.13 2000.46
```

Note that in just a few minutes, the system time has fallen behind the hardware clock, as the offset and jitter parameters in NTP continue to rise.

What in tarnation is this? If it was the system board's oscillator, wouldn't it be affecting the hardware clock too? Or am I not quite getting this one right?

---

### Post by kpatz on 2009-03-12
Sounds to me like the kernel's clock interrupt frequency is out of sync with reality.

Is this machine different, hardware or software wise from your other machines?  Is it running in a virtual machine?  Does it have a different kernel?  Try this:

> 
  uname -a (note kernel version that's running, such as 2.6.27-11-server)
  grep HZ /boot/config-(whatever kernel version you got above), for example, grep HZ /boot/config-2.6.27-11-server

See what you get.

Just for kicks, try booting a live CD (maybe try different distros) in the problem machine and see if the clock drifts then.  Maybe there's some disconnect between the kernel and the hardware.

---

### Post by txr13 on 2009-03-12
```
joe@Problem:~# uname -a
Linux Problem 2.6.24-23-server #1 SMP Mon Jan 26 00:55:21 UTC 2009 i686 GNU/Linux

joe@Problem:~# grep HZ /boot/config-2.6.24-23-server
# CONFIG_HZ_1000 is not set
# CONFIG_HZ_300 is not set
CONFIG_HZ=100
CONFIG_HZ_100=y
# CONFIG_HZ_250 is not set
CONFIG_MACHZ_WDT=m
CONFIG_NO_HZ=y
```

It's the same kernel as used everywhere else in my farm, running the same software as all the other machines. I've also checked the other machines that are identical hardware, and they don't exhibit this problem. The output of the above two commands are the same on the other machines, as well.

Booting a live CD could be done, but it would be problematic. I'd rather not go to that trouble unless I'm definitely in pursuit of a bug and trying to gather more information for developers. I guess I'm just wondering if there's anything else that can be checked before taking the machine offline and out of the stack for that kind of troubleshooting.

---

### Post by txr13 on 2009-03-13
Currently:

```
joe@Problem:~# hwclock
Fri 13 Mar 2009 08:05:41 AM PDT  -0.057157 seconds

joe@Problem:~# date
Fri Mar 13 07:49:19 PDT 2009

joe@Problem:~# ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 192.168.1.7     132.246.168.148  3 u   56   64  377    0.396  995299. 2632.89
 192.168.1.10    132.246.168.164  3 u   25   64  377    0.475  995594. 2647.05
```

No actions have been taken since my last post, I've just been letting the machine run. This issue clearly hasn't gone away. Any thoughts?

---

### Post by Tiler on 2009-04-10
**txr13:**

Did you ever get this resolved?  I have a similar issue and am not yet ready to post it.

Thanks,

Tiler

---

### Post by txr13 on 2009-04-10
No, I never got it fixed. As a stopgap, I setup a cronjob that uses ntpdate to sync the clock once per hour.

---

### Post by Tiler on 2009-04-10
[COLOR="Purple"]**Let's see how similar our issues are.  My problem began on my most recent reinstall. I was testing another distro and wanted to clean up my packages with a reinstall.**[/COLOR]

```

Eee PC 1000
2gb RAM


user@computer:~$ uname -a
Linux computer 2.6.24-21-eeepc #1 SMP Thu Aug 7 22:18:05 MDT 2008 i686 GNU/Linux


user@computer:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.2
Release:        8.04
Codename:       hardy
user@computer:~$ apt-cache policy ntp
ntp:
  Installed: 1:4.2.4p4+dfsg-3ubuntu2.1
  Candidate: 1:4.2.4p4+dfsg-3ubuntu2.1
  Version table:
 *** 1:4.2.4p4+dfsg-3ubuntu2.1 0
        500 http://us.archive.ubuntu.com hardy-updates/main Packages
        500 http://security.ubuntu.com hardy-security/main Packages
        100 /var/lib/dpkg/status
     1:4.2.4p4+dfsg-3ubuntu2 0
        500 http://us.archive.ubuntu.com hardy/main Packages
user@computer:~$ user@computer:~$

```

[COLOR="Purple"][B]I have found bug report after bug report in launchpad about this issue but I believe mine is unique because I cannot restart NTP and get it to update.

I have removed and reinstalled a couple of times and removed the NOMODIFY flag from ntp.conf with no result.  I am including daemon.log, ntpd, peerstats and ntpq -p.  All are from a recent reboot.

This is my third Hardy install on this machine and it hasn't occurred on any previous installs.  The prior installs were elective, worked well and involved in testing various platforms, not related to other issues, for purposes of disclosure.
[/B][/COLOR]

daemon.log
```
Apr 10 14:17:45 computer NetworkManager: <info>  starting... 
Apr 10 14:17:46 computer avahi-daemon[4925]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Apr 10 14:17:46 computer avahi-daemon[4925]: Successfully dropped root privileges.
Apr 10 14:17:46 computer avahi-daemon[4925]: avahi-daemon 0.6.22 starting up.
Apr 10 14:17:46 computer avahi-daemon[4925]: Successfully called chroot().
Apr 10 14:17:46 computer avahi-daemon[4925]: Successfully dropped remaining capabilities.
Apr 10 14:17:46 computer avahi-daemon[4925]: No service file found in /etc/avahi/services.
Apr 10 14:17:46 computer avahi-daemon[4925]: Network interface enumeration completed.
Apr 10 14:17:46 computer avahi-daemon[4925]: Registering HINFO record with values 'I686'/'LINUX'.10 Apr 14:17:52 ntpd[5349]: bind() fd 20, family 10, port 123, scope 3, addr fe80::215:afff:fee6:99f7, in6_is_addr_multicast=0 flags=0x11 fails: Cannot assign requested address
10 Apr 14:17:52 ntpd[5349]: unable to create socket on ra0 (6) for fe80::215:afff:fee6:99f7#123
10 Apr 14:17:52 ntpd[5349]: failed to initialize interface for address fe80::215:afff:fee6:99f7
10 Apr 14:17:52 ntpd[5349]: bind() fd 20, family 10, port 123, scope 2, addr fe80::222:15ff:fe65:272e, in6_is_addr_multicast=0 flags=0x11 fails: Cannot assign requested address
10 Apr 14:17:52 ntpd[5349]: unable to create socket on eth0 (7) for fe80::222:15ff:fe65:272e#123
10 Apr 14:17:52 ntpd[5349]: failed to initialize interface for address fe80::222:15ff:fe65:272e
10 Apr 14:17:53 ntpd[5390]: host name not found: ntp.tmc.edu
10 Apr 14:17:53 ntpd[5390]: couldn't resolve `ntp.tmc.edu', giving up on it
10 Apr 14:17:53 ntpd[5390]: host name not found: ntp.cox.smu.edu
10 Apr 14:17:53 ntpd[5390]: couldn't resolve `ntp.cox.smu.edu', giving up on it
10 Apr 14:17:53 ntpd[5390]: host name not found: ntp.ubuntu.com
10 Apr 14:17:53 ntpd[5390]: couldn't resolve `ntp.ubuntu.com', giving up on it
10 Apr 14:17:53 ntpd[5390]: host name not found: constellation.ecn.uoknor.edu
10 Apr 14:17:53 ntpd[5390]: couldn't resolve `constellation.ecn.uoknor.edu', giving up on it
10 Apr 14:17:53 ntpd[5390]: host name not found: clock.tricity.wsu.edu
10 Apr 14:17:53 ntpd[5390]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
10 Apr 14:17:53 ntpd[5390]: host name not found: ntp.cmr.gov
10 Apr 14:17:53 ntpd[5390]: couldn't resolve `ntp.cmr.gov', giving up on it
10 Apr 14:17:53 ntpd[5390]: host name not found: ntp0.cornell.edu
10 Apr 14:17:53 ntpd[5390]: couldn't resolve `ntp0.cornell.edu', giving up on it
10 Apr 14:17:53 ntpd[5390]: host name not found: louie.udel.edu
10 Apr 14:17:53 ntpd[5390]: couldn't resolve `louie.udel.edu', giving up on it
10 Apr 14:17:53 ntpd[5390]: host name not found: libra.rice.edu
10 Apr 14:17:53 ntpd[5390]: couldn't resolve `libra.rice.edu', giving up on it
10 Apr 14:17:53 ntpd[5390]: host name not found: gilbreth.ecn.purdue.edu
10 Apr 14:17:53 ntpd[5390]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
10 Apr 14:17:53 ntpd[5390]: host name not found: molecule.ecn.purdue.edu
10 Apr 14:17:53 ntpd[5390]: couldn't resolve `molecule.ecn.purdue.edu', giving up on it
10 Apr 14:17:53 ntpd[5390]: host name not found: ntp1.cmc.ec.gc.ca
10 Apr 14:17:53 ntpd[5390]: couldn't resolve `ntp1.cmc.ec.gc.ca', giving up on it
10 Apr 14:17:56 ntpd[5349]: ntpd exiting on signal 15
10 Apr 14:17:57 ntpd[5782]: host name not found: ntp.cox.smu.edu
10 Apr 14:17:57 ntpd[5782]: couldn't resolve `ntp.cox.smu.edu', giving up on it
10 Apr 14:17:57 ntpd[5782]: host name not found: constellation.ecn.uoknor.edu
10 Apr 14:17:57 ntpd[5782]: couldn't resolve `constellation.ecn.uoknor.edu', giving up on it
10 Apr 14:17:57 ntpd[5782]: host name not found: clock.tricity.wsu.edu
10 Apr 14:17:57 ntpd[5782]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
10 Apr 14:18:06 ntpd[5782]: host name not found: ntp.cmr.gov
10 Apr 14:18:06 ntpd[5782]: couldn't resolve `ntp.cmr.gov', giving up on it
10 Apr 14:18:06 ntpd[5782]: host name not found: libra.rice.edu
10 Apr 14:18:06 ntpd[5782]: couldn't resolve `libra.rice.edu', giving up on it
Apr 10 14:17:46 computer avahi-daemon[4925]: Server startup complete. Host name is computer.local. Local service cookie is 2819572863.
Apr 10 14:17:49 computer hcid[5173]: Bluetooth HCI daemon
Apr 10 14:17:49 computer NetworkManager: <info>  ra0: Device is fully-supported using driver 'rt2860'. 
Apr 10 14:17:49 computer NetworkManager: <info>  ra0: driver does not support SSID scans (scan_capa 0x00). 
Apr 10 14:17:49 computer NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr 10 14:17:49 computer NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr 10 14:17:49 computer NetworkManager: <info>  Now managing wireless (802.11) device 'ra0'. 
Apr 10 14:17:49 computer NetworkManager: <info>  Deactivating device ra0. 
Apr 10 14:17:49 computer hcid[5173]: Starting SDP server
Apr 10 14:17:49 computer NetworkManager: <info>  eth0: Device is fully-supported using driver 'ATL1e'. 
Apr 10 14:17:49 computer NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr 10 14:17:49 computer NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr 10 14:17:49 computer NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Apr 10 14:17:49 computer NetworkManager: <info>  Deactivating device eth0. 
Apr 10 14:17:49 computer hcid[5173]: Created local server at unix:abstract=/var/run/dbus-9t7I80d7Sk,guid=1335b779cf329c1df69704e249df9b5d
Apr 10 14:17:49 computer NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr 10 14:17:49 computer network[5196]: Bluetooth Network daemon
Apr 10 14:17:49 computer network[5196]: /etc/bluetooth/network.conf: Key file does not have key 'Disable'
Apr 10 14:17:49 computer network[5196]: /etc/bluetooth/network.conf: Key file does not have key 'DisableSecurity'
Apr 10 14:17:49 computer network[5196]: /etc/bluetooth/network.conf: Key file does not have key 'Interface'
Apr 10 14:17:49 computer last message repeated 2 times
Apr 10 14:17:49 computer network[5196]: Config options: InterfacePrefix=bnep%d, PANU_Script=/usr/bin/blueman-ifup, GN_Script=/usr/bin/blueman-ifup, NAP_Script=/usr/bin/blueman-ifup, GN_Interface=pan0, NAP_Interface=pan1, Security=true
Apr 10 14:17:49 computer NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr 10 14:17:49 computer NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Apr 10 14:17:49 computer NetworkManager: <info>  Will activate connection 'eth0'. 
Apr 10 14:17:49 computer NetworkManager: <info>  Device eth0 activation scheduled... 
Apr 10 14:17:49 computer NetworkManager: <info>  Activation (eth0) started... 
Apr 10 14:17:49 computer NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 10 14:17:49 computer NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr 10 14:17:49 computer NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr 10 14:17:49 computer NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr 10 14:17:49 computer NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr 10 14:17:49 computer NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr 10 14:17:49 computer NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr 10 14:17:49 computer NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr 10 14:17:49 computer NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr 10 14:17:49 computer input[5200]: Bluetooth Input daemon
Apr 10 14:17:49 computer NetworkManager: <debug> [1239391069.276827] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Apr 10 14:17:49 computer input[5200]: Registered input manager path:/org/bluez/input
Apr 10 14:17:49 computer audio[5210]: Bluetooth Audio daemon
Apr 10 14:17:49 computer audio[5210]: Unix socket created: 5
Apr 10 14:17:49 computer audio[5210]: audio.conf: Key file does not have key 'Enable'
Apr 10 14:17:49 computer audio[5210]: audio.conf: Key file does not have key 'Disable'
Apr 10 14:17:49 computer serial[5206]: Bluetooth Serial Port daemon
Apr 10 14:17:49 computer audio[5210]: add_service_record: got record id 0x10000
Apr 10 14:17:49 computer audio[5210]: audio.conf: Key file does not have key 'Disable'
Apr 10 14:17:49 computer audio[5210]: audio.conf: Key file does not have group 'A2DP'
Apr 10 14:17:49 computer last message repeated 3 times
Apr 10 14:17:49 computer audio[5210]: SEP 0x806d318 registered: type:0 codec:0 seid:1
Apr 10 14:17:49 computer network[5196]: Registered manager path:/org/bluez/network
Apr 10 14:17:49 computer network[5196]: Registered server path:/org/bluez/network/nap
Apr 10 14:17:49 computer audio[5210]: add_service_record: got record id 0x10001
Apr 10 14:17:49 computer network[5196]: Registered server path:/org/bluez/network/gn
Apr 10 14:17:49 computer audio[5210]: add_service_record: got record id 0x10002
Apr 10 14:17:49 computer network[5196]: Registered server path:/org/bluez/network/panu
Apr 10 14:17:49 computer audio[5210]: add_service_record: got record id 0x10003
Apr 10 14:17:49 computer audio[5210]: Registered manager path:/org/bluez/audio
Apr 10 14:17:49 computer audio[5210]: Loading device 00:17:53:06:CE:30 (sink )
Apr 10 14:17:49 computer serial[5206]: Registered manager path:/org/bluez/serial
Apr 10 14:17:50 computer NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Apr 10 14:17:50 computer NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr 10 14:17:50 computer NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Apr 10 14:17:51 computer NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Apr 10 14:17:51 computer ntpd[5348]: ntpd 4.2.4p4@1.1520-o Tue Jan  6 15:51:34 UTC 2009 (1)
Apr 10 14:17:51 computer ntpd[5349]: precision = 1.000 usec
Apr 10 14:17:51 computer ntpd[5349]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Apr 10 14:17:51 computer ntpd[5349]: Listening on interface #1 wildcard, ::#123 Disabled
Apr 10 14:17:51 computer ntpd[5349]: Listening on interface #2 lo, ::1#123 Enabled
Apr 10 14:17:51 computer ntpd[5349]: bind() fd 19, family 10, port 123, scope 3, addr fe80::215:afff:fee6:99f7, in6_is_addr_multicast=0 flags=0x11 fails: Cannot assign requested address
Apr 10 14:17:51 computer ntpd[5349]: unable to create socket on ra0 (3) for fe80::215:afff:fee6:99f7#123
Apr 10 14:17:51 computer ntpd[5349]: failed to initialize interface for address fe80::215:afff:fee6:99f7
Apr 10 14:17:51 computer ntpd[5349]: bind() fd 19, family 10, port 123, scope 2, addr fe80::222:15ff:fe65:272e, in6_is_addr_multicast=0 flags=0x11 fails: Cannot assign requested address
Apr 10 14:17:51 computer ntpd[5349]: unable to create socket on eth0 (4) for fe80::222:15ff:fe65:272e#123
Apr 10 14:17:51 computer ntpd[5349]: failed to initialize interface for address fe80::222:15ff:fe65:272e
Apr 10 14:17:51 computer ntpd[5349]: Listening on interface #5 lo, 127.0.0.1#123 Enabled
Apr 10 14:17:51 computer ntpd[5349]: kernel time sync status 0040
Apr 10 14:17:51 computer ntpd[5349]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Apr 10 14:17:52 computer NetworkManager: <debug> [1239391072.689078] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ae_drm_i915_card0'). 
Apr 10 14:17:53 computer avahi-daemon[4925]: Registering new address record for fe80::215:afff:fee6:99f7 on ra0.*.
Apr 10 14:17:53 computer avahi-daemon[4925]: Registering new address record for fe80::222:15ff:fe65:272e on eth0.*.
Apr 10 14:17:54 computer dhclient: DHCPREQUEST of 129.120.52.226 on eth0 to 255.255.255.255 port 67
Apr 10 14:17:54 computer dhclient: DHCPACK of 129.120.52.226 from 129.120.53.250
Apr 10 14:17:54 computer avahi-daemon[4925]: Joining mDNS multicast group on interface eth0.IPv4 with address 129.120.52.226.
Apr 10 14:17:54 computer avahi-daemon[4925]: New relevant interface eth0.IPv4 for mDNS.
Apr 10 14:17:54 computer avahi-daemon[4925]: Registering new address record for 129.120.52.226 on eth0.IPv4.
Apr 10 14:17:54 computer avahi-daemon[4925]: Withdrawing address record for 129.120.52.226 on eth0.
Apr 10 14:17:54 computer avahi-daemon[4925]: Leaving mDNS multicast group on interface eth0.IPv4 with address 129.120.52.226.
Apr 10 14:17:54 computer avahi-daemon[4925]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 10 14:17:54 computer avahi-daemon[4925]: Joining mDNS multicast group on interface eth0.IPv4 with address 129.120.52.226.
Apr 10 14:17:54 computer avahi-daemon[4925]: New relevant interface eth0.IPv4 for mDNS.
Apr 10 14:17:54 computer avahi-daemon[4925]: Registering new address record for 129.120.52.226 on eth0.IPv4.
Apr 10 14:17:54 computer NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth0 
Apr 10 14:17:54 computer NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Apr 10 14:17:54 computer NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Apr 10 14:17:54 computer dhclient: bound to 129.120.52.226 -- renewal in 19686 seconds.
Apr 10 14:17:54 computer NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Apr 10 14:17:54 computer NetworkManager: <info>    address 129.120.52.226 
Apr 10 14:17:54 computer NetworkManager: <info>    netmask 255.255.254.0 
Apr 10 14:17:54 computer NetworkManager: <info>    broadcast 129.120.53.255 
Apr 10 14:17:54 computer NetworkManager: <info>    gateway 129.120.53.250 
Apr 10 14:17:54 computer NetworkManager: <info>    nameserver 129.120.210.254 
Apr 10 14:17:54 computer NetworkManager: <info>    hostname 'computer' 
Apr 10 14:17:54 computer NetworkManager: <info>    domain name 'unt.edu' 
Apr 10 14:17:54 computer NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr 10 14:17:54 computer NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Apr 10 14:17:54 computer NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Apr 10 14:17:54 computer avahi-daemon[4925]: Withdrawing address record for 129.120.52.226 on eth0.
Apr 10 14:17:54 computer avahi-daemon[4925]: Leaving mDNS multicast group on interface eth0.IPv4 with address 129.120.52.226.
Apr 10 14:17:54 computer avahi-daemon[4925]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 10 14:17:54 computer avahi-daemon[4925]: Withdrawing address record for fe80::222:15ff:fe65:272e on eth0.
Apr 10 14:17:54 computer avahi-daemon[4925]: Joining mDNS multicast group on interface eth0.IPv4 with address 129.120.52.226.
Apr 10 14:17:54 computer avahi-daemon[4925]: New relevant interface eth0.IPv4 for mDNS.
Apr 10 14:17:54 computer avahi-daemon[4925]: Registering new address record for 129.120.52.226 on eth0.IPv4.
Apr 10 14:17:55 computer NetworkManager: <info>  Clearing nscd hosts cache. 
Apr 10 14:17:55 computer NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Apr 10 14:17:55 computer NetworkManager: <info>  Activation (eth0) successful, device activated. 
Apr 10 14:17:55 computer NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Apr 10 14:17:55 computer NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Apr 10 14:17:56 computer ntpdate[5607]: can't find host ntp.cox.smu.edu 
Apr 10 14:17:56 computer ntpdate[5607]: can't find host constellation.ecn.uoknor.edu 
Apr 10 14:17:56 computer ntpdate[5607]: can't find host clock.tricity.wsu.edu 
Apr 10 14:17:57 computer avahi-daemon[4925]: Registering new address record for fe80::222:15ff:fe65:272e on eth0.*.
Apr 10 14:18:06 computer ntpdate[5607]: can't find host ntp.cmr.gov 
Apr 10 14:18:06 computer ntpdate[5607]: can't find host libra.rice.edu 
Apr 10 14:18:11 computer ntpdate[5607]: step time server 132.236.56.250 offset -26.375736 sec
Apr 10 14:17:45 computer ntpd[5649]: ntpd 4.2.4p4@1.1520-o Tue Jan  6 15:51:34 UTC 2009 (1)
Apr 10 14:17:45 computer ntpd[5650]: precision = 1.000 usec
Apr 10 14:17:45 computer ntpd[5650]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Apr 10 14:17:45 computer ntpd[5650]: Listening on interface #1 wildcard, ::#123 Disabled
Apr 10 14:17:45 computer ntpd[5650]: Listening on interface #2 lo, ::1#123 Enabled
Apr 10 14:17:45 computer ntpd[5650]: Listening on interface #3 ra0, fe80::215:afff:fee6:99f7#123 Enabled
Apr 10 14:17:45 computer ntpd[5650]: Listening on interface #4 eth0, fe80::222:15ff:fe65:272e#123 Enabled
Apr 10 14:17:45 computer ntpd[5650]: Listening on interface #5 lo, 127.0.0.1#123 Enabled
Apr 10 14:17:45 computer ntpd[5650]: Listening on interface #6 eth0, 129.120.52.226#123 Enabled
Apr 10 14:17:45 computer ntpd[5650]: kernel time sync status 0040
Apr 10 14:17:45 computer ntpd[5650]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Apr 10 14:17:56 computer hcid[5173]: Default passkey agent (:1.24, /org/bluez/passkey) registered
Apr 10 14:17:56 computer hcid[5173]: Default authorization agent (:1.24, /org/bluez/auth) registered
Apr 10 14:18:04 computer NetworkManager: <info>  Updating allowed wireless network lists. 
```

NTPD:
```

10 Apr 14:17:52 ntpd[5349]: bind() fd 20, family 10, port 123, scope 3, addr fe80::215:afff:fee6:99f7, in6_is_addr_multicast=0 flags=0x11 fails: Cannot assign requested address
10 Apr 14:17:52 ntpd[5349]: unable to create socket on ra0 (6) for fe80::215:afff:fee6:99f7#123
10 Apr 14:17:52 ntpd[5349]: failed to initialize interface for address fe80::215:afff:fee6:99f7
10 Apr 14:17:52 ntpd[5349]: bind() fd 20, family 10, port 123, scope 2, addr fe80::222:15ff:fe65:272e, in6_is_addr_multicast=0 flags=0x11 fails: Cannot assign requested address
10 Apr 14:17:52 ntpd[5349]: unable to create socket on eth0 (7) for fe80::222:15ff:fe65:272e#123
10 Apr 14:17:52 ntpd[5349]: failed to initialize interface for address fe80::222:15ff:fe65:272e
10 Apr 14:17:53 ntpd[5390]: host name not found: ntp.tmc.edu
10 Apr 14:17:53 ntpd[5390]: couldn't resolve `ntp.tmc.edu', giving up on it
10 Apr 14:17:53 ntpd[5390]: host name not found: ntp.cox.smu.edu
10 Apr 14:17:53 ntpd[5390]: couldn't resolve `ntp.cox.smu.edu', giving up on it
10 Apr 14:17:53 ntpd[5390]: host name not found: ntp.ubuntu.com
10 Apr 14:17:53 ntpd[5390]: couldn't resolve `ntp.ubuntu.com', giving up on it
10 Apr 14:17:53 ntpd[5390]: host name not found: constellation.ecn.uoknor.edu
10 Apr 14:17:53 ntpd[5390]: couldn't resolve `constellation.ecn.uoknor.edu', giving up on it
10 Apr 14:17:53 ntpd[5390]: host name not found: clock.tricity.wsu.edu
10 Apr 14:17:53 ntpd[5390]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
10 Apr 14:17:53 ntpd[5390]: host name not found: ntp.cmr.gov
10 Apr 14:17:53 ntpd[5390]: couldn't resolve `ntp.cmr.gov', giving up on it
10 Apr 14:17:53 ntpd[5390]: host name not found: ntp0.cornell.edu
10 Apr 14:17:53 ntpd[5390]: couldn't resolve `ntp0.cornell.edu', giving up on it
10 Apr 14:17:53 ntpd[5390]: host name not found: louie.udel.edu
10 Apr 14:17:53 ntpd[5390]: couldn't resolve `louie.udel.edu', giving up on it
10 Apr 14:17:53 ntpd[5390]: host name not found: libra.rice.edu
10 Apr 14:17:53 ntpd[5390]: couldn't resolve `libra.rice.edu', giving up on it
10 Apr 14:17:53 ntpd[5390]: host name not found: gilbreth.ecn.purdue.edu
10 Apr 14:17:53 ntpd[5390]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
10 Apr 14:17:53 ntpd[5390]: host name not found: molecule.ecn.purdue.edu
10 Apr 14:17:53 ntpd[5390]: couldn't resolve `molecule.ecn.purdue.edu', giving up on it
10 Apr 14:17:53 ntpd[5390]: host name not found: ntp1.cmc.ec.gc.ca
10 Apr 14:17:53 ntpd[5390]: couldn't resolve `ntp1.cmc.ec.gc.ca', giving up on it
10 Apr 14:17:56 ntpd[5349]: ntpd exiting on signal 15
10 Apr 14:17:57 ntpd[5782]: host name not found: ntp.cox.smu.edu
10 Apr 14:17:57 ntpd[5782]: couldn't resolve `ntp.cox.smu.edu', giving up on it
10 Apr 14:17:57 ntpd[5782]: host name not found: constellation.ecn.uoknor.edu
10 Apr 14:17:57 ntpd[5782]: couldn't resolve `constellation.ecn.uoknor.edu', giving up on it
10 Apr 14:17:57 ntpd[5782]: host name not found: clock.tricity.wsu.edu
10 Apr 14:17:57 ntpd[5782]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
10 Apr 14:18:06 ntpd[5782]: host name not found: ntp.cmr.gov
10 Apr 14:18:06 ntpd[5782]: couldn't resolve `ntp.cmr.gov', giving up on it
10 Apr 14:18:06 ntpd[5782]: host name not found: libra.rice.edu
10 Apr 14:18:06 ntpd[5782]: couldn't resolve `libra.rice.edu', giving up on it
```

Peerstats:```

54931 69476.170 128.249.1.10 9014 -0.735167347 0.012008005 7.937501044 0.000000954
54931 69477.272 91.189.94.4 9014 -0.788913314 0.114402695 7.937501812 0.000000954
54931 69478.215 132.236.56.250 9014 -0.834369478 0.056959012 7.937501023 0.000000954
54931 69479.226 128.4.40.12 9014 -0.884853641 0.059391299 7.937501042 0.000000954
54931 69482.230 199.212.17.21 9014 -1.029631764 0.069932139 7.937501478 0.000000954

```
From Terminal:```

user@computer:~$ sudo ntpq -p
[sudo] password for user: 
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 ntp.tmc.edu     129.7.1.66       2 u   32   64  377   12.495  -28134. 13615.5
 europium.canoni 193.79.237.14    2 u   23   64  377  114.616  -28570. 13760.3
 cudns.cit.corne 128.118.25.12    2 u   29   64  377   56.471  -28282. 13567.4
 louie.udel.edu  128.4.1.1        2 u   29   64  377   59.493  -28284. 13632.4
 gilbreth.ecn.pu .INIT.          16 u    -   64    0    0.000    0.000   0.000
 molecule.ecn.pu .INIT.          16 u    -   64    0    0.000    0.000   0.000
 ecmail1.cmc.ec. 18.26.4.105      2 u   23   64  377   70.574  -28572. 13658.2
user@computer:~$ sudo ntpdate ntp.ubuntu.com
10 Apr 14:28:12 ntpdate[6128]: the NTP socket is in use, exiting
user@computer:~$ sudo /etc/init.d/ntp restart
 * Stopping NTP server ntpd                                              [ OK ] 
 * Starting NTP server ntpd                                              [ OK ] 
user@computer:~$ sudo ntpdate ntp.ubuntu.com
10 Apr 14:28:47 ntpdate[6170]: the NTP socket is in use, exiting

user@computer:~$ sudo ntpq -pn
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 128.249.1.10    129.7.1.66       2 u   38   64    3   12.773  -35183. 3049.62
 91.189.94.4     193.79.237.14    2 u   37   64    3  114.828  -35236. 3049.84
 132.236.56.250  128.118.25.12    2 u   37   64    3   57.186  -35234. 3002.39
 128.4.40.12     128.4.1.1        2 u   36   64    3   59.584  -35283. 3001.93
 128.46.103.93   .INIT.          16 u    -   64    0    0.000    0.000   0.000
 128.46.136.95   .INIT.          16 u    -   64    0    0.000    0.000   0.000
 199.212.17.21   18.26.4.105      2 u   33   64    3   70.509  -35429. 3001.99
user@computer:~$ 
```

---

### Post by Tiler on 2009-04-17
bump

---

### Post by poundjd on 2009-04-29
Tiler, On thing I have noticed is that when I have two NTP servers on my network, and I don&#8217;t see them looking outside the domain to at lease 5 separate systems (sometimes as many as 10) then I often notice problems with time.  I also run a par of NTP servers paired at typically stratum 5 that are synced to a stratum 2 or 3 servers.  I then can rest assured that my time base is pretty good, and while my clients are getting stratum 6 time it is still plenty good for them.    I try to set up a pair NTP servers each with a different list of 10 stratum 2 or 3 servers to sync to, and I have my pair partner.  Then my clients get good time all the time&#8230;..
-jeff

---

### Post by hobbesip on 2009-06-26
I just stumbled on to this thread, and think I can give a few hints.

ntpd updates the system time, not the hardware clock (thus, 'hwclock --systohc', which in many distro's executes upon halt. You may want to add this to cron for a regular interval so the clock is not way off after recovering from an unexpected reboot after a long uptime). Since it's the kernel that's counting the ticks, and not the RTC hardware clock on the motherboard, I think it's safe to rule out hardware.

Is it possible there is a long network delay in NTP traffic between the client and the NTP time sources (routing issues, switching issues, firewalls, ACLs, etc..)? How do your interface statistics look? What about the firewall rules in iptables on this client?

Another thing to check is your drift file, typically in /var/lib/ntp/drift (see the 'driftfile' line in /etc/ntp.conf). This can be a negitive or positive number, typically 2-3 numbers long. ntpd attempts to calculate far off the cheap ossolator is on most mainboards, and keeps track of it here. If it's very high or very low, I suppose it could cause your scenario. If you need to change it, stop ntpd, set it to -133 (mean average on Dell hardware), and restart ntpd.

---

