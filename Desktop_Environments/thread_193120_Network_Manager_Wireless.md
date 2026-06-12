---
title: "Network Manager Wireless"
date: 2006-06-09
forum: Desktop Environments
---

### Post by denisesballs on 2006-06-09
I've gotten my broadcom wireless working fine in Dapper with Ndiswrapper following the wiki instructions. I can't go back and forth between the NIC and the wireless through network-admin. However with Network Manager, I can see both interfaces, but when I try to connect to the same wireless network, it hangs and hangs and eventually dies. Anyone have an idea why?

---

### Post by andersonmanly on 2006-06-09
You're trying to go from a wireless connection to a wired connection on the same network? Are you using encryption on the wireless? Do a 'tail -f /var/log/syslog' ... it might give you a clue as to what's going on.

---

### Post by denisesballs on 2006-06-09
[QUOTE=andersonmanly]You're trying to go from a wireless connection to a wired connection on the same network? Are you using encryption on the wireless? Do a 'tail -f /var/log/syslog' ... it might give you a clue as to what's going on.[/QUOTE]

No, and no. My wired network is 192.168.1 and the wireless is 192.168.5. When going through network-admin and setting them both to DHCP I can go back and forth activating on and deactivating either no problem and connecting. When I use networkmanager, The wired comes up on boot, and when I try to connect the wireless it just hangs and hangs and eventually gives up and goes back to wired.

Edit to add I had it working on the same model different laptop.

---

### Post by denisesballs on 2006-06-09
Here's the output from my syslog when I try connecting to my wireless network, which it picks up and I connect to no problem with network-admin.

```
Jun  9 16:29:32 localhost NetworkManager: <information>^IUpdating allowed wireless network lists.
Jun  9 16:29:32 localhost NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): nm-dbus-nmi.c:522 (nm_dbus_get_networks_cb): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..
Jun  9 16:29:32 localhost NetworkManager: <information>^Imatch
Jun  9 16:29:56 localhost last message repeated 5 times
Jun  9 16:29:56 localhost NetworkManager: <debug info>^I[1149884996.331317] nm_device_802_11_wireless_get_activation_ap (): Forcing AP 'linksys'
Jun  9 16:29:56 localhost NetworkManager: <information>^IUser Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / linksys
Jun  9 16:29:56 localhost NetworkManager: <information>^IDeactivating device wlan0.
Jun  9 16:29:58 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jun  9 16:29:58 localhost NetworkManager: <information>^IDevice wlan0 activation scheduled...
Jun  9 16:29:58 localhost NetworkManager: <information>^IDeactivating device eth0.
Jun  9 16:29:58 localhost dhclient: DHCPRELEASE on eth0 to 192.168.1.3 port 67
Jun  9 16:29:58 localhost avahi-daemon[4537]: Withdrawing address record for 192.168.1.140 on eth0.
Jun  9 16:29:58 localhost avahi-daemon[4537]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.140.
Jun  9 16:29:58 localhost avahi-daemon[4537]: iface.c: interface_mdns_mcast_join() called but no local address available.
Jun  9 16:29:58 localhost avahi-daemon[4537]: Interface eth0.IPv4 no longer relevant for mDNS.
Jun  9 16:29:59 localhost NetworkManager: <information>^IActivation (wlan0) started...
Jun  9 16:29:59 localhost NetworkManager: <information>^IActivation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  9 16:29:59 localhost NetworkManager: <information>^IActivation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  9 16:29:59 localhost NetworkManager: <information>^IActivation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  9 16:29:59 localhost NetworkManager: <information>^IActivation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  9 16:29:59 localhost NetworkManager: <information>^IActivation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  9 16:29:59 localhost NetworkManager: <information>^IActivation (wlan0/wireless): access point 'linksys' is unencrypted, no key needed.
Jun  9 16:29:59 localhost NetworkManager: <information>^Imatch
Jun  9 16:29:59 localhost last message repeated 8 times
Jun  9 16:30:00 localhost NetworkManager: <information>^ISUP: sending command 'INTERFACE_ADD wlan0^I^Indiswrapper^I/var/run/wpa_supplicant^I'
Jun  9 16:30:00 localhost NetworkManager: <information>^ISUP: response was 'OK'
Jun  9 16:30:00 localhost NetworkManager: <information>^ISUP: sending command 'AP_SCAN 1'
Jun  9 16:30:00 localhost NetworkManager: <information>^ISUP: response was 'OK'
Jun  9 16:30:00 localhost NetworkManager: <information>^ISUP: sending command 'ADD_NETWORK'
Jun  9 16:30:00 localhost NetworkManager: <information>^ISUP: response was '0'
Jun  9 16:30:00 localhost NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 ssid 6c696e6b737973'
Jun  9 16:30:00 localhost NetworkManager: <information>^ISUP: response was 'OK'
Jun  9 16:30:00 localhost NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 key_mgmt NONE'
Jun  9 16:30:00 localhost NetworkManager: <information>^ISUP: response was 'OK'
Jun  9 16:30:00 localhost NetworkManager: <information>^ISUP: sending command 'ENABLE_NETWORK 0'
Jun  9 16:30:00 localhost NetworkManager: <information>^ISUP: response was 'OK'
Jun  9 16:30:00 localhost NetworkManager: <information>^IActivation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Global control interface '/var/run/wpa_supplicant-global'
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): RX global ctrl_iface - hexdump_ascii(len=57):
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126):      49 4e 54 45 52 46 41 43 45 5f 41 44 44 20 77 6c   INTERFACE_ADD wl
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126):      61 6e 30 09 09 6e 64 69 73 77 72 61 70 70 65 72   an0__ndiswrapper
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126):      09 2f 76 61 72 2f 72 75 6e 2f 77 70 61 5f 73 75   _/var/run/wpa_su
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126):      70 70 6c 69 63 61 6e 74 09                        pplicant_
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): CTRL_IFACE GLOBAL INTERFACE_ADD 'wlan0^I^Indiswrapper^I/var/run/wpa_supplicant^I'
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Initializing interface 'wlan0' conf 'N/A' driver 'ndiswrapper' ctrl_interface '/var/run/wpa_supplicant'
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Initializing interface (2) 'wlan0'
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): EAPOL: SUPP_PAE entering state DISCONNECTED
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): EAPOL: KEY_RX entering state NO_KEY_RECEIVE
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): EAPOL: SUPP_BE entering state INITIALIZE
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): EAP: EAP entering state DISABLED
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): EAPOL: External notification - portEnabled=0
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): EAPOL: External notification - portValid=0
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): SIOCGIWRANGE: WE(compiled)=19 WE(source)=18 enc_capa=0xf
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126):   capabilities: key_mgmt 0xf enc 0xf
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Own MAC address: 00:16:ce:2a:fb:ab
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): idx=0 set_tx=0 seq_len=0 key_len=0
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Setting scan request: 0 sec 100000 usec
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Added interface wlan0
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Wireless event: cmd=0x8b06 len=8
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): RX ctrl_iface - hexdump_ascii(len=9):
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126):      41 50 5f 53 43 41 4e 20 31                        AP_SCAN 1
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): RX ctrl_iface - hexdump_ascii(len=11):
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126):      41 44 44 5f 4e 45 54 57 4f 52 4b                  ADD_NETWORK
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): CTRL_IFACE: ADD_NETWORK
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): RX ctrl_iface - hexdump_ascii(len=33):
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 73 73   SET_NETWORK 0 ss
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126):      69 64 20 36 63 36 39 36 65 36 62 37 33 37 39 37   id 6c696e6b73797
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126):      33                                                3
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): CTRL_IFACE: SET_NETWORK id=0 name='ssid' value='6c696e6b737973'
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): ssid - hexdump_ascii(len=7):
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126):      6c 69 6e 6b 73 79 73                              linksys
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): xdump_ascii(len=27):
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 6b 65   SET_NETWORK 0 ke
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126):      79 5f 6d 67 6d 74 20 4e 4f 4e 45                  y_mgmt NONE
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): CTRL_IFACE: SET_NETWORK id=0 name='key_mgmt' value='NONE'
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): key_mgmt: 0x4
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): RX ctrl_iface - hexdump_ascii(len=16):
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126):      45 4e 41 42 4c 45 5f 4e 45 54 57 4f 52 4b 20 30   ENABLE_NETWORK 0
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): CTRL_IFACE: ENABLE_NETWORK id=0
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Setting scan request: 0 sec 0 usec
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): State: DISCONNECTED -> SCANNING
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Starting AP scan (broadcast SSID)
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): RX ctrl_iface - hexdump_ascii(len=6):
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126):      41 54 54 41 43 48                                 ATTACH
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): CTRL_IFACE monitor attached - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 35 31 32 2d 31 00 30 00
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Scan timeout - try to get results
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Received 224 bytes of scan results (1 BSSes)
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Scan results: 1
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Selecting BSS from priority group 0
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): 0: 00:13:10:d5:61:06 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126):    skip - no WPA/RSN IE
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): 5:61:06 ssid='linksys'
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Trying to associate with 00:13:10:d5:61:06 (SSID='linksys' freq=2437 MHz)
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 35 31 32 2d 31 00 30 00
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Cancelling scan request
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): WPA: clearing own WPA/RSN IE
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Automatic auth_alg selection: 0x1
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): WPA: clearing AP WPA IE
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): WPA: clearing AP RSN IE
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): WPA: clearing own WPA/RSN IE
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): No keys have been configured - skip key clearing
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): State: SCANNING -> ASSOCIATING
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Setting authentication timeout: 10 sec 0 usec
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): EAPOL: External notification - portControl=ForceAuthorized
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Authentication with 00:00:00:00:00:00 timed out.
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 35 31 32 2d 31 00 30 00
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Added BSSID 00:00:00:00:00:00 into blacklist
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): State: ASSOCIATING -> DISCONNECTED
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): No keys have been configured - skip key clearing
Jun  9 16:30:13 localhost NetworkManager: <information>^Iwpa_supplicant(5126): EAPOL: External notification - portEnabled=0
Jun  9 16:30:45 localhost kernel: [4294789.925000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): notification - portValid=0
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Setting scan request: 0 sec 0 usec
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): State: DISCONNECTED -> SCANNING
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Starting AP scan (broadcast SSID)
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Scan timeout - try to get results
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Received 224 bytes of scan results (1 BSSes)
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Scan results: 1
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Selecting BSS from priority group 0
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): 0: 00:13:10:d5:61:06 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126):    skip - no WPA/RSN IE
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126):    selected non-WPA AP 00:13:10:d5:61:06 ssid='linksys'
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Trying to associate with 00:13:10:d5:61:06 (SSID='linksys' freq=2437 MHz)
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 35 31 32 2d 31 00 30 00
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Cancelling scan request
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): WPA: clearing own WPA/RSN IE
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Automatic auth_alg selection: 0x1
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): WPA: clearing AP WPA IE
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): WPA: clearing AP RSN IE
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): WPA: clearing own WPA/RSN IE
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): No keys have been configured - skip key clearing
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): State: SCANNING -> ASSOCIATING
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Setting authentication timeout: 10 sec 0 usec
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): EAPOL: External notification - portControl=ForceAuthorized
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): 0:00:00:00:00:00 timed out.
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 35 31 32 2d 31 00 30 00
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): BSSID 00:00:00:00:00:00 blacklist count incremented to 2
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): State: ASSOCIATING -> DISCONNECTED
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): No keys have been configured - skip key clearing
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): EAPOL: External notification - portEnabled=0
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): EAPOL: External notification - portValid=0
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Setting scan request: 0 sec 0 usec
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): State: DISCONNECTED -> SCANNING
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Starting AP scan (broadcast SSID)
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Scan timeout - try to get results
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Received 224 bytes of scan results (1 BSSes)
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Scan results: 1
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Selecting BSS from priority group 0
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): 0: 00:13:10:d5:61:06 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126):    skip - no WPA/RSN IE
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126):    selected non-WPA AP 00:13:10:d5:61:06 ssid='linksys'
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Trying to associate with 00:13:10:d5:61:06 (SSID='linksys' freq=2437 MHz)
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): f 34 35 31 32 2d 31 00 30 00
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Cancelling scan request
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): WPA: clearing own WPA/RSN IE
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Automatic auth_alg selection: 0x1
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): WPA: clearing AP WPA IE
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): WPA: clearing AP RSN IE
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): WPA: clearing own WPA/RSN IE
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): No keys have been configured - skip key clearing
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): State: SCANNING -> ASSOCIATING
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Setting authentication timeout: 10 sec 0 usec
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): EAPOL: External notification - portControl=ForceAuthorized
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Authentication with 00:00:00:00:00:00 timed out.
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 35 31 32 2d 31 00 30 00
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): BSSID 00:00:00:00:00:00 blacklist count incremented to 3
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): State: ASSOCIATING -> DISCONNECTED
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): No keys have been configured - skip key clearing
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): EAPOL: External notification - portEnabled=0
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): EAPOL: External notification - portValid=0
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Setting scan request: 0 sec 0 usec
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): State: DISCONNECTED -> SCANNING
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Starting AP scan (broadcast SSID)
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Scan timeout - try to get results
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Received 224 bytes of scan results (1 BSSes)
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Scan results: 1
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): lecting BSS from priority group 0
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): 0: 00:13:10:d5:61:06 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126):    skip - no WPA/RSN IE
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126):    selected non-WPA AP 00:13:10:d5:61:06 ssid='linksys'
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Trying to associate with 00:13:10:d5:61:06 (SSID='linksys' freq=2437 MHz)
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 35 31 32 2d 31 00 30 00
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Cancelling scan request
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): WPA: clearing own WPA/RSN IE
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Automatic auth_alg selection: 0x1
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): WPA: clearing AP WPA IE
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): WPA: clearing AP RSN IE
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): WPA: clearing own WPA/RSN IE
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): No keys have been configured - skip key clearing
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): State: SCANNING -> ASSOCIATING
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Setting authentication timeout: 10 sec 0 usec
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): EAPOL: External notification - portControl=ForceAuthorized
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): Authentication with 00:00:00:00:00:00 timed out.
Jun  9 16:30:52 localhost NetworkManager: <information>^Iwpa_supplicant(5126): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 35 31 32 2d 31 00 30 00
Jun  9 16:31:00 localhost NetworkManager: <information>^IActivation (wlan0/wireless): association took too long (>60s), failing activation.
Jun  9 16:31:00 localhost NetworkManager: <information>^IActivation (wlan0) failure scheduled...
Jun  9 16:31:00 localhost NetworkManager: <information>^IActivation (wlan0) failed for access point (linksys)
Jun  9 16:31:00 localhost NetworkManager: <information>^IActivation (wlan0) failed.
Jun  9 16:31:00 localhost NetworkManager: <information>^IDeactivating device wlan0.
Jun  9 16:31:02 localhost NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'.
Jun  9 16:31:02 localhost NetworkManager: <information>^IWill activate connection 'eth0'.
Jun  9 16:31:02 localhost NetworkManager: <information>^IDevice eth0 activation scheduled...
Jun  9 16:31:02 localhost NetworkManager: <information>^Imatch
Jun  9 16:31:02 localhost NetworkManager: <information>^IActivation (eth0) started...
Jun  9 16:31:02 localhost NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  9 16:31:02 localhost NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started...
Jun  9 16:31:02 localhost NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jun  9 16:31:02 localhost NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jun  9 16:31:02 localhost NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting...
Jun  9 16:31:02 localhost NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful.
Jun  9 16:31:02 localhost NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  9 16:31:02 localhost NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete.
Jun  9 16:31:02 localhost NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun  9 16:31:02 localhost NetworkManager: <information>^Imatch
Jun  9 16:31:02 localhost last message repeated 5 times
Jun  9 16:31:03 localhost NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction.
Jun  9 16:31:03 localhost NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0
Jun  9 16:31:03 localhost NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun  9 16:31:04 localhost NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0
Jun  9 16:31:06 localhost NetworkManager: <information>^IOld device 'eth0' activating, won't change.
Jun  9 16:31:07 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jun  9 16:31:07 localhost dhclient: DHCPOFFER from 192.168.1.3
Jun  9 16:31:07 localhost dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun  9 16:31:07 localhost dhclient: DHCPACK from 192.168.1.3
Jun  9 16:31:07 localhost avahi-daemon[4537]: New relevant interface eth0.IPv4 for mDNS.
Jun  9 16:31:07 localhost avahi-daemon[4537]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.140.
Jun  9 16:31:07 localhost avahi-daemon[4537]: Registering new address record for 192.168.1.140 on eth0.
Jun  9 16:31:07 localhost NetworkManager: <information>^IDHCP daemon state is now 2 (bound) for interface eth0
Jun  9 16:31:07 localhost NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled...
Jun  9 16:31:07 localhost NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started...
Jun  9 16:31:07 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jun  9 16:31:07 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun  9 16:31:07 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jun  9 16:31:07 localhost NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon:
Jun  9 16:31:07 localhost NetworkManager: <information>^I  address 192.168.1.140
Jun  9 16:31:07 localhost NetworkManager: <information>^I  netmask 255.255.255.0
Jun  9 16:31:07 localhost NetworkManager: <information>^I  broadcast 192.168.1.255
Jun  9 16:31:07 localhost NetworkManager: <information>^I  gateway 192.168.1.254
Jun  9 16:31:07 localhost NetworkManager: <information>^I  nameserver 192.168.1.3
Jun  9 16:31:07 localhost NetworkManager: <information>^I  domain name 'thecybersource.com.int'
Jun  9 16:31:07 localhost NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jun  9 16:31:07 localhost NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete.
Jun  9 16:31:07 localhost NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jun  9 16:31:07 localhost avahi-daemon[4537]: Withdrawing address record for 192.168.1.140 on eth0.
```

---

### Post by andersonmanly on 2006-06-09
Try forcing the connection by clicking "Connect to another wireless network..." under the NetworkManager menu...entering the SSID ('linksys' I assume) with no encryption.

---

### Post by denisesballs on 2006-06-09
No luck. It does the exact same thing. This is so bizarre.

---

