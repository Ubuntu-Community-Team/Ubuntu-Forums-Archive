---
title: "Wireless very slow to connect after boot."
date: 2009-08-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MartynT on 2009-08-08
When I first switch on 10v (8.04 - pretty much as delivered - has the 1510 'n' wireless card) it I look at the NetworkManager icon, but nothing is going on.

If I click it there are no wireless networks shown (there are several in my area including my own which has a very strong signal.)

After a while (30 - 90 seconds) the NetworkManager icon wakes up (green comet circling two gray spots) and if I click the icon now I can see several routers.

Wait another 30 - 60 seconds and a password dialog pops up, click OK (the gray spots have gon green at this point and the tool tip claims it's waiting for an IP address).
Wait another 30 - 60 seconds and it pops up again.  
Repeat 2 or 3 times more before NetworkManager reports that I am disconnected.

Now I click on the icon and select my router, the comet circles the gray spots for ~30 seconds, the go green and then after another 30 seconds I connect.

Does anyone have any idea what might be causing this ?  Even better, does anyone have any suggestions on how I can troubles shoot this ?

My /var/log/syslog contains lots of this stuff (look at the jumps in time around the "took too long" errors")

```
Aug  8 09:21:27 martyn NetworkManager: <info>  Config: set interface ap_scan to 1
Aug  8 09:21:28 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2
Aug  8 09:21:52 martyn NetworkManager: <info>  Activation (eth1/wireless): association took too long.
Aug  8 09:21:52 martyn NetworkManager: <info>  (eth1): device state change: 5 -> 6
Aug  8 09:21:52 martyn NetworkManager: <info>  Activation (eth1/wireless): asking for new secrets
Aug  8 09:21:52 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 0
Aug  8 09:21:52 martyn nm-applet: <info>  New secrets for Auto DrayTek/802-11-wireless-security requested; ask the user
Aug  8 09:21:54 martyn NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Aug  8 09:21:54 martyn NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Aug  8 09:21:54 martyn NetworkManager: <info>  (eth1): device state change: 6 -> 4
Aug  8 09:21:54 martyn NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Aug  8 09:21:54 martyn NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Aug  8 09:21:54 martyn NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Aug  8 09:21:54 martyn NetworkManager: <info>  (eth1): device state change: 4 -> 5
Aug  8 09:21:54 martyn NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto DrayTek' has security, and secrets exist.  No new secrets needed.
Aug  8 09:21:54 martyn NetworkManager: <info>  Config: added 'ssid' value 'DrayTek'
Aug  8 09:21:54 martyn NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Aug  8 09:21:54 martyn NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Aug  8 09:21:54 martyn NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Aug  8 09:21:54 martyn NetworkManager: <info>  Config: added 'proto' value 'WPA RSN'
Aug  8 09:21:54 martyn NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP'
Aug  8 09:21:54 martyn NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP'
Aug  8 09:21:54 martyn NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Aug  8 09:21:54 martyn NetworkManager: <info>  Config: set interface ap_scan to 1
Aug  8 09:21:54 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2
Aug  8 09:22:19 martyn NetworkManager: <info>  Activation (eth1/wireless): association took too long.
Aug  8 09:22:19 martyn NetworkManager: <info>  (eth1): device state change: 5 -> 6
Aug  8 09:22:19 martyn NetworkManager: <info>  Activation (eth1/wireless): asking for new secrets

```

Here's some info about my card

```
martyn@martyn:~$ dmesg | grep eth1
[   39.785033] eth1: Broadcom BCM432b 802.11 Wireless Controller 5.10.79.10
[   50.385091] eth1: no IPv6 routers present
martyn@martyn:~$ lspci -vnn | grep 14e4
03:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)


```

---

### Post by quantumottle on 2009-08-21
It's unfortunate that you got no replies as it sounds like you and I have identical problems. I've been searching for answers but found nothing so far. Have you solved your problem? If so I'd really appreciate a follow up. Thanks in advance...

---

### Post by MartynT on 2009-08-23
Yesterday my 10v wouldn't connect at all.  A dozen or so reconnect attempts and always the same failure to connect.

My router is configured to give the same IPs to all my various devices (PCs, laptops, printer, iPhones, etc.).  So I edited the connection details (rt click NetworkManager icon -> Edit Connections.

Under IPv4 I changed 
Method: Manual
Added an Address 192.168.1.114 (.14 is what my router is configured to assign).  Netmask 24 (I put in 255.255.255.0 but Network Manager changed that to 24).  Gateway 192.168.1.1 (That's the IP of my router).

I also set DNS Servers:  And Search Domains: to my router IP.

After that it finally connected and did again today.

So there seems to be a problem between wpa_supplicant, the dhcp request and my router.  Not sure exactly where the finger of blame should be pointing or where/how to re-point it ;-)

The other day I found this thread "[Manual Network Configuration without the need for Network Manager]("http://ubuntuforums.org/showthread.php?t=571188")".

I haven't yet had time to investigate but I'm hoping it will teach me what NetworkManager is doing, what all that "device state change: 5 -> 6
" stuff in the syslog means and how to fix the problem.

I'll post back what I find.

---

### Post by MartynT on 2009-08-23
My NetworkManager just went into a tailspin of repeatedly connecting and then disconnecting every 1 - 2 minutes.  At no time during these cycles did I ever get internet connectivity.

I ended up killing NetworkManager and nm-system-settings and restarting NetworkManager.  After that it reconnected and stayed connected (so far).

My syslog is full of stuff like this.  I don't like the look of this lot :-

NetworkManager: <WARN>  nm_device_wifi_disable_encryption(): error setting key for device eth1: Invalid argument
nm-dispatcher.action: nm_dispatcher_action: Invalid connection: 'NMSettingWirelessSecurity' / 'wep-key0' invalid: 1
NetworkManager: <WARN>  nm_device_wifi_disable_encryption(): error setting key for device eth1: Invalid argument 
NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Missing link name TLV (errno = Invalid argument) 



```
Aug 23 13:09:04 martyn NetworkManager: <info>  Activation (eth1/wireless): association took too long. 
Aug 23 13:09:04 martyn NetworkManager: <info>  (eth1): device state change: 5 -> 9 
Aug 23 13:09:04 martyn NetworkManager: <info>  Activation (eth1) failed for access point (DrayTek) 
Aug 23 13:09:04 martyn NetworkManager: <info>  Marking connection 'Auto DrayTek' invalid. 
Aug 23 13:09:04 martyn NetworkManager: <info>  Activation (eth1) failed. 
Aug 23 13:09:04 martyn NetworkManager: <info>  (eth1): device state change: 9 -> 3 
Aug 23 13:09:04 martyn NetworkManager: <info>  (eth1): deactivating device (reason: 0). 
Aug 23 13:09:04 martyn NetworkManager: <WARN>  nm_device_wifi_disable_encryption(): error setting key for device eth1: Invalid argument 
Aug 23 13:14:29 martyn ntpd[24552]: no servers reachable
Aug 23 13:15:23 martyn NetworkManager: <info>  Activation (eth1) starting connection 'Auto DrayTek' 
Aug 23 13:15:23 martyn NetworkManager: <info>  (eth1): device state change: 3 -> 4 
Aug 23 13:15:23 martyn NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 23 13:15:23 martyn NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Aug 23 13:15:23 martyn NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Aug 23 13:15:23 martyn NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Aug 23 13:15:23 martyn NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Aug 23 13:15:23 martyn NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Aug 23 13:15:23 martyn NetworkManager: <info>  Activation (eth1/wireless): access point 'Auto DrayTek' has security, but secrets are required. 
Aug 23 13:15:23 martyn NetworkManager: <info>  (eth1): device state change: 5 -> 6 
Aug 23 13:15:23 martyn NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Aug 23 13:15:23 martyn NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 23 13:15:23 martyn NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Aug 23 13:15:23 martyn NetworkManager: <info>  (eth1): device state change: 6 -> 4 
Aug 23 13:15:23 martyn NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Aug 23 13:15:23 martyn NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Aug 23 13:15:23 martyn NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Aug 23 13:15:23 martyn NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Aug 23 13:15:23 martyn NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto DrayTek' has security, and secrets exist.  No new secrets needed. 
Aug 23 13:15:23 martyn NetworkManager: <info>  Config: added 'ssid' value 'DrayTek' 
Aug 23 13:15:23 martyn NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Aug 23 13:15:23 martyn NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Aug 23 13:15:23 martyn NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Aug 23 13:15:23 martyn NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Aug 23 13:15:23 martyn NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Aug 23 13:15:23 martyn NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Aug 23 13:15:23 martyn NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Aug 23 13:15:23 martyn NetworkManager: <info>  Config: set interface ap_scan to 1 
Aug 23 13:15:23 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 0 
Aug 23 13:15:23 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Aug 23 13:15:28 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 3 
Aug 23 13:15:33 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 0 
Aug 23 13:15:33 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Aug 23 13:15:35 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 4 
Aug 23 13:15:37 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 5 
Aug 23 13:15:38 martyn NetworkManager: <info>  eth1: link timed out. 
Aug 23 13:15:38 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 5 -> 6 
Aug 23 13:15:38 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 7 
Aug 23 13:15:38 martyn NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'DrayTek'. 
Aug 23 13:15:38 martyn NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Aug 23 13:15:38 martyn NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Aug 23 13:15:38 martyn NetworkManager: <info>  (eth1): device state change: 5 -> 7 
Aug 23 13:15:38 martyn NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Aug 23 13:15:38 martyn NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Aug 23 13:15:38 martyn NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Aug 23 13:15:38 martyn NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Aug 23 13:15:38 martyn NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Aug 23 13:15:38 martyn NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Aug 23 13:15:38 martyn avahi-daemon[4411]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.14.
Aug 23 13:15:38 martyn avahi-daemon[4411]: New relevant interface eth1.IPv4 for mDNS.
Aug 23 13:15:38 martyn avahi-daemon[4411]: Registering new address record for 192.168.1.14 on eth1.IPv4.
Aug 23 13:15:39 martyn NetworkManager: <info>  (eth1): device state change: 7 -> 8 
Aug 23 13:15:39 martyn NetworkManager: <WARN>  nm_system_replace_default_ip4_route(): replace_default_ip4_route() returned error Success (0) 
Aug 23 13:15:39 martyn NetworkManager: <info>  Policy set 'Auto DrayTek' (eth1) as default for routing and DNS. 
Aug 23 13:15:39 martyn NetworkManager: <info>  Activation (eth1) successful, device activated. 
Aug 23 13:15:39 martyn NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Aug 23 13:15:39 martyn nm-dispatcher.action: nm_dispatcher_action: Invalid connection: 'NMSettingWirelessSecurity' / 'wep-key0' invalid: 1
Aug 23 13:15:39 martyn ntpd[24552]: ntpd exiting on signal 15
Aug 23 13:15:52 martyn ntpdate[24794]: adjust time server 193.62.22.98 offset 0.019503 sec
Aug 23 13:15:52 martyn ntpd[24821]: ntpd 4.2.4p4@1.1520-o Wed May 13 21:05:14 UTC 2009 (1)
Aug 23 13:15:52 martyn ntpd[24822]: precision = 2.000 usec
Aug 23 13:15:52 martyn ntpd[24822]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Aug 23 13:15:52 martyn ntpd[24822]: Listening on interface #1 wildcard, ::#123 Disabled
Aug 23 13:15:52 martyn ntpd[24822]: Listening on interface #2 lo, ::1#123 Enabled
Aug 23 13:15:52 martyn ntpd[24822]: Listening on interface #3 eth1, fe80::225:56ff:fe6b:f70b#123 Enabled
Aug 23 13:15:52 martyn ntpd[24822]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Aug 23 13:15:52 martyn ntpd[24822]: Listening on interface #5 eth1, 192.168.1.14#123 Enabled
Aug 23 13:15:52 martyn ntpd[24822]: kernel time sync status 0040
Aug 23 13:15:52 martyn ntpd[24822]: frequency initialized -74.535 PPM from /var/lib/ntp/ntp.drift
Aug 23 13:15:56 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 3 
Aug 23 13:16:01 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 0 
Aug 23 13:16:01 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Aug 23 13:16:03 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 4 
Aug 23 13:16:04 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 5 
Aug 23 13:16:12 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 5 -> 3 
Aug 23 13:16:16 martyn NetworkManager: <info>  (eth1): device state change: 8 -> 3 
Aug 23 13:16:16 martyn NetworkManager: <info>  (eth1): deactivating device (reason: 11). 
Aug 23 13:16:16 martyn NetworkManager: <WARN>  nm_device_wifi_disable_encryption(): error setting key for device eth1: Invalid argument 
Aug 23 13:16:16 martyn NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Missing link name TLV (errno = Invalid argument) 
Aug 23 13:16:16 martyn avahi-daemon[4411]: Withdrawing address record for 192.168.1.14 on eth1.
Aug 23 13:16:16 martyn avahi-daemon[4411]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.14.
Aug 23 13:16:16 martyn avahi-daemon[4411]: Interface eth1.IPv4 no longer relevant for mDNS.
Aug 23 13:16:16 martyn NetworkManager: <info>  Activation (eth1) starting connection 'Auto DrayTek' 
Aug 23 13:16:16 martyn NetworkManager: <info>  (eth1): device state change: 3 -> 4 
Aug 23 13:16:16 martyn NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 23 13:16:16 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 0 
Aug 23 13:16:16 martyn NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Aug 23 13:16:16 martyn NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Aug 23 13:16:16 martyn NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Aug 23 13:16:16 martyn NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Aug 23 13:16:16 martyn NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Aug 23 13:16:16 martyn NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto DrayTek' has security, and secrets exist.  No new secrets needed. 
Aug 23 13:16:16 martyn NetworkManager: <info>  Config: added 'ssid' value 'DrayTek' 
Aug 23 13:16:16 martyn NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Aug 23 13:16:16 martyn NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Aug 23 13:16:16 martyn NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Aug 23 13:16:16 martyn NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Aug 23 13:16:16 martyn NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Aug 23 13:16:16 martyn NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Aug 23 13:16:16 martyn NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Aug 23 13:16:16 martyn NetworkManager: <info>  Config: set interface ap_scan to 1 
Aug 23 13:16:16 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Aug 23 13:16:16 martyn nm-dispatcher.action: nm_dispatcher_action: Invalid connection: 'NMSettingWirelessSecurity' / 'wep-key0' invalid: 1
Aug 23 13:16:17 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 0 
Aug 23 13:16:17 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Aug 23 13:16:23 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 4 
Aug 23 13:16:23 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 0 
Aug 23 13:16:29 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Aug 23 13:16:32 martyn NetworkManager: <info>  eth1: link timed out. 
Aug 23 13:16:39 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 3 
Aug 23 13:16:41 martyn NetworkManager: <info>  Activation (eth1/wireless): association took too long. 
Aug 23 13:16:41 martyn NetworkManager: <info>  (eth1): device state change: 5 -> 6 
Aug 23 13:16:41 martyn NetworkManager: <info>  Activation (eth1/wireless): asking for new secrets 
Aug 23 13:16:41 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 0 
Aug 23 13:16:41 martyn NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 23 13:16:41 martyn NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Aug 23 13:16:41 martyn NetworkManager: <info>  (eth1): device state change: 6 -> 4 
Aug 23 13:16:41 martyn NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Aug 23 13:16:41 martyn NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Aug 23 13:16:41 martyn NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Aug 23 13:16:41 martyn NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Aug 23 13:16:41 martyn NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto DrayTek' has security, and secrets exist.  No new secrets needed. 
Aug 23 13:16:41 martyn NetworkManager: <info>  Config: added 'ssid' value 'DrayTek' 
Aug 23 13:16:41 martyn NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Aug 23 13:16:41 martyn NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Aug 23 13:16:41 martyn NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Aug 23 13:16:41 martyn NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Aug 23 13:16:41 martyn NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Aug 23 13:16:41 martyn NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Aug 23 13:16:41 martyn NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Aug 23 13:16:41 martyn NetworkManager: <info>  Config: set interface ap_scan to 1 
Aug 23 13:16:41 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Aug 23 13:16:43 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 4 
Aug 23 13:16:43 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 5 
Aug 23 13:16:52 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 5 -> 3 
Aug 23 13:16:53 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 0 
Aug 23 13:16:57 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Aug 23 13:16:59 martyn ntpd[24822]: sendto(130.88.200.4) (fd=21): Invalid argument
Aug 23 13:17:00 martyn ntpd[24822]: sendto(91.189.94.4) (fd=21): Invalid argument
Aug 23 13:17:01 martyn ntpd[24822]: sendto(130.88.202.49) (fd=21): Invalid argument
Aug 23 13:17:02 martyn ntpd[24822]: sendto(193.62.22.98) (fd=21): Invalid argument
Aug 23 13:17:02 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 0 
Aug 23 13:17:03 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Aug 23 13:17:06 martyn NetworkManager: <info>  Activation (eth1/wireless): association took too long. 
Aug 23 13:17:06 martyn NetworkManager: <info>  (eth1): device state change: 5 -> 6 
Aug 23 13:17:06 martyn NetworkManager: <info>  Activation (eth1/wireless): asking for new secrets 
Aug 23 13:17:06 martyn NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 23 13:17:06 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 0 
Aug 23 13:17:06 martyn NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Aug 23 13:17:06 martyn NetworkManager: <info>  (eth1): device state change: 6 -> 4 
Aug 23 13:17:06 martyn NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Aug 23 13:17:06 martyn NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Aug 23 13:17:06 martyn NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Aug 23 13:17:06 martyn NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Aug 23 13:17:06 martyn NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto DrayTek' has security, and secrets exist.  No new secrets needed. 
Aug 23 13:17:06 martyn NetworkManager: <info>  Config: added 'ssid' value 'DrayTek' 
Aug 23 13:17:06 martyn NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Aug 23 13:17:06 martyn NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Aug 23 13:17:06 martyn NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Aug 23 13:17:06 martyn NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Aug 23 13:17:06 martyn NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Aug 23 13:17:06 martyn NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Aug 23 13:17:06 martyn NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Aug 23 13:17:06 martyn NetworkManager: <info>  Config: set interface ap_scan to 1 
Aug 23 13:17:06 martyn NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Aug 23 13:17:28 martyn NetworkManager: <info>  (eth1): device state change: 5 -> 2 
Aug 23 13:17:28 martyn NetworkManager: <info>  (eth1): deactivating device (reason: 0). 
Aug 23 13:17:28 martyn NetworkManager: <WARN>  nm_device_wifi_disable_encryption(): error setting key for device eth1: Invalid argument 
Aug 23 13:17:28 martyn NetworkManager: <info>  (eth1): taking down device. 
Aug 23 13:17:28 martyn avahi-daemon[4411]: Withdrawing address record for fe80::225:56ff:fe6b:f70b on eth1.
Aug 23 13:17:35 martyn NetworkManager: <WARN>  nm_device_wifi_set_enabled(): not in expected unavailable state! 
Aug 23 13:17:35 martyn NetworkManager: <info>  (eth1): bringing up device. 
Aug 23 13:17:35 martyn NetworkManager: <info>  (eth1): device state change: 2 -> 3 
Aug 23 13:17:35 martyn NetworkManager: <info>  (eth1): supplicant interface state change: 1 -> 2. 
```

---

### Post by quantumottle on 2009-08-27
It appears I was wrong, you and do not have similar problems MartynT. Your issues seem to be a little more complicated than mine. I'm able to connect, it just connects very slowly, sometimes disconnecting and then reconnecting, finally staying connected after the 2nd connection. 

I hope you are able to find a solution, best of luck to you...

---

### Post by Gausian on 2009-08-28
Ive had a lot of success with wicd instead of network manager.  i have a well supported wifi card (intel 4965), and had problems with network manager losing connections, not connecting, or just plain being a b!tch.

wicd is in synaptec and it will uninstall network manager automatically.  i havent had any problems since switching. 

if it doesnt work you can always switch back to network manager.  thats the beauty of linux.

---

### Post by MartynT on 2009-08-29
quantumottle, the trouble you've described is exactly what mine is like most of the time .... but sometimes I have other troubles.

Last weekend I spent three hours trying to get connected.
This weekend it just connected with no trouble !!

I'll definitely give wicd a go.  It can't be worse and if it is I'll just go back.

Thanks.

---

### Post by Magical Tiger on 2009-08-29
I agree with Gausian, I have had problems with Network manager so I switched to Wicd and no problems. Just make sure you dl the Wicd .deb before uninstalling network manager.

---

### Post by MartynT on 2009-08-30
I just tried (and failed) to add the wicd repository to synaptic

Following the instructions here [http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php") I get the error

```
Failed to fetch http://apt.wicd.net/dists/hardy/Release  Unable to find expected entry  extras/binary-lpia/Packages in Meta-index file (malformed Release file?)
```

And it's true,there are binaries for every architecture under the sun, except the one sold by DELL.

Do I really have to build from source ?

---

### Post by Gausian on 2009-08-30
> **MartynT said:**
> I just tried (and failed) to add the wicd repository to synaptic

Following the instructions here [http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php") I get the error

```
Failed to fetch http://apt.wicd.net/dists/hardy/Release  Unable to find expected entry  extras/binary-lpia/Packages in Meta-index file (malformed Release file?)
```

And it's true,there are binaries for every architecture under the sun, except the one sold by DELL.

Do I really have to build from source ?

If you're using Jaunty, wicd is already in the repo.  search for it in synaptec.

---

### Post by kogger on 2009-09-05
I'm having similar problems with being able to connect quickly. My computer is rather consistent, though; it'll wait a bit, start connecting, after a while ask for authorization (which it already has), click Cancel, re-select it from the network manager's list, and then it finally connects. I found that clicking OK when it asks for authorization makes it take longer; clicking Cancel and re-selecting it for some reason helps it go faster.

---

### Post by Cowchip7 on 2009-09-05
My wireless is a little slow connecting as well. However, it never failed to connect. I don't mind waiting. My wife has a Lenovo running Vista and it takes just as long to connect! :D:D

My Mac iBook connected to wifi faster than anything I ever seen. 10 seconds and you're up and running!

---

### Post by jnorthr on 2009-09-05
have your tried relocating some of your hardware or routers or wireless bits ? Nearby signals from other users, radios, TV's etc can cause interence with your signals. Sometimes signals are reflected by metal in walls and what your system receives is not a direct signal but a reflected signal, subject to distortion.

Just a thought.:rolleyes:

---

### Post by urugTON on 2009-09-17
I noticed the original post was for 8.04.  Whether everyone else is speaking of that release or not, I'm not clear.

FWIW, I have a Vostro 1510.  I also have an Intel 3945 so my experience may not fit the problem here.

All that said, I had to screw around a bit to get my wireless to work on 8.04.  Ended up backporting drivers, knocking off network manager and installing Wicd.  That all changed with 8.10.  Wireless just worked as soon as I booted the LiveCD.  Same for 9.04.  No problems with wireless since 8.10.  

I'd give the 9.04 LiveCD a try.

FWIW, my 1510 sometimes has no keyboard or mouse after booting 9.04.  Edit the kernel line to include the text (w/o quotes) "i8042.reset".  It'll look something like:

kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=d36a5a02-1f19-4252-a8cd-6d03ea7b70da ro quiet splash i8042.reset

You can use grub to edit the line when booting off the LiveCD, BTW.

And yes, even with the keyboard issue I'd try 9.04 rather than 8.10.  It works better for me.

Hope the suggestion works.

---

### Post by hwasungmars on 2009-09-18
Hello,

I had a similar problem. It took roughly an additional minute for my wireless card to be up even after the full Gnome loaded. I was using Sony Vaio VGN-C series, and was lucky enough to find a solution. I installed wicd via Synaptic (Ubuntu 9.04), and now it works beautifully.

Judging by the laptop's WLAN light, the wireless card is actually activated even before Gnome loads, and wireless is connected even before the desktop is loaded. 

In summary,

My system: Vaio VGN-C series
Symptoms: Wirless card takes more than a minute to connect after boot
Solution: Install wicd (via Synaptic or apt-get)
Ubuntu version: 9.04

I hope this works for others too! Good luck!

Update: I have just found that wicd does not support vpnc out of the box. But you can always use the command line approach. Apparently, vpnc will be supported on wicd 2.0.

---

### Post by jtayl22 on 2009-11-18
I had miserable wireless performance on my Mac Book Pro with Broadcom BCM432b 802.11 Wireless Controller, Broadcom STA proprietary driver and Ubuntu 9.10 until I disabled TKIP on my wireless router. Everything is fine now that the only option on the router is AES. The change didn't disrupt any of the other 10 or so wireless devices around the house. HTH.

---

### Post by quantumottle on 2010-07-06
> **Gausian said:**
> Ive had a lot of success with wicd instead of network manager.  <snip>

Just wanted to say THANK YOU to Gausian for the great tip. WICD not only solved all of my problems, but I've been telling everyone I know to switch to WICD and dump Network manager and it's 100% successful so far (even with Lucid 10.04). Thanks again!!!

---

