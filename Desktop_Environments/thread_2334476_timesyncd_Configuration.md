---
title: "timesyncd Configuration"
date: 2016-08-19
forum: Desktop Environments
---

### Post by motobeats on 2016-08-19
I am using the desktop version of 16.04 and I have my time synced over the internet but can't find where the NTP service used is defined. Have already looked through the timesyncd and systemd documentation.

Finally used tcpdump to find that my laptop uses golem.canonical.com when using the internet synced time option. Where is this set?

I actually pass the ntp server to use via DHCP. Why isn't that one being used?

---

### Post by motobeats on 2016-08-20
Found this. So it confirms I am using the default NTP provider. How do I get 16.04 to use the provider at the IP address I send with DHCP?

> ubuntu:~$ systemctl status systemd-timesyncd.service
&#9679; systemd-timesyncd.service - Network Time Synchronization
   Loaded: loaded (/lib/systemd/system/systemd-timesyncd.service; enabled; vendor preset: enabled)
  Drop-In: /lib/systemd/system/systemd-timesyncd.service.d
           &#9492;&#9472;disable-with-time-daemon.conf
   Active: active (running) since Fri 2016-08-19 17:34:19 EDT; 6h ago
     Docs: man:systemd-timesyncd.service(8)
 Main PID: 10152 (systemd-timesyn)
   Status: "Synchronized to time server 91.189.89.199:123 (ntp.ubuntu.com)."
   CGroup: /system.slice/systemd-timesyncd.service
           &#9492;&#9472;10152 /lib/systemd/systemd-timesyncd


---

### Post by motobeats on 2016-08-20
I think this is the issue
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1578663](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1578663)
I'm running systemd 229. Not sure how to display any subversion info.

---

### Post by motobeats on 2016-08-20
I released and requested my DHCP lease in quick succession (sudo dhclient -r , sudo dhclient) and then watched traffic on port 123. My desktop uses the NTP server set by the DHCP server 3 or 4 times (tried it a few times) and then switches over to one that must be part of ntp.ubuntu.com

**From TCPDUMP**
> 22:01:25.605699 IP portege-ubuntu.moto.lan.39051 > gateway.moto.ntp: NTPv4, Client, length 48
22:01:25.605898 IP gateway.moto.ntp > portege-ubuntu.moto.lan.39051: NTPv4, Server, length 48
22:03:33.855707 IP portege-ubuntu.moto.lan.59899 > gateway.moto.ntp: NTPv4, Client, length 48
22:03:33.855879 IP gateway.moto.ntp > portege-ubuntu.moto.lan.59899: NTPv4, Server, length 48
22:04:11.536747 IP portege-ubuntu.moto.lan.56221 > alphyn.canonical.com.ntp: NTPv4, Client, length 48
22:04:11.560999 IP alphyn.canonical.com.ntp > portege-ubuntu.moto.lan.56221: NTPv4, Server, length 48

**DHCP does set the NTP for a little but this reverts to what I posted previously with ntp.ubuntu.com as the NTP provider.**
> portege-ubuntu:~$ systemctl status systemd-timesyncd.service
&#9679; systemd-timesyncd.service - Network Time Synchronization
   Loaded: loaded (/lib/systemd/system/systemd-timesyncd.service; enabled; vendor preset: enabled)
  Drop-In: /lib/systemd/system/systemd-timesyncd.service.d
           &#9492;&#9472;disable-with-time-daemon.conf
   Active: active (running) since Sat 2016-08-20 22:24:03 EDT; 3s ago
     Docs: man:systemd-timesyncd.service(8)
 Main PID: 9469 (systemd-timesyn)
   Status: "Synchronized to time server 192.168.11.1:123 (192.168.11.1)."
   CGroup: /system.slice/systemd-timesyncd.service
           &#9492;&#9472;9469 /lib/systemd/systemd-timesyncd

---

### Post by motobeats on 2016-08-24
Anyone have an idea why DHCP is able to set my NTP server but after a few minutes it gets set back to ntp.ubuntu.com?

> -- Logs begin at Sun 2016-08-21 00:17:02 EDT, end at Wed 2016-08-24 21:01:43 EDT. --
Aug 21 09:11:37 portege-ubuntu systemd-timesyncd[15762]: Synchronized to time server 192.168.11.1:123 (192.168.11.1).
Aug 21 09:11:56 portege-ubuntu systemd-timesyncd[15780]: Synchronized to time server 91.189.91.157:123 (ntp.ubuntu.com).
Aug 21 17:46:08 portege-ubuntu systemd-timesyncd[20508]: Synchronized to time server 192.168.11.1:123 (192.168.11.1).
Aug 21 17:51:47 portege-ubuntu systemd-timesyncd[20559]: Synchronized to time server 91.189.89.198:123 (ntp.ubuntu.com).




---

