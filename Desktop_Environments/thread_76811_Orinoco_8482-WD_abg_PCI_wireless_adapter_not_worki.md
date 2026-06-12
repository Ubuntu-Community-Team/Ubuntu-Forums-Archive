---
title: "Orinoco 8482-WD a/b/g PCI wireless adapter not working.."
date: 2005-10-15
forum: Desktop Environments
---

### Post by Anything Generic on 2005-10-15
I'm new to the Linux community, and I've recently installed Ubuntu 5.10.  I'm having trouble getting my Orinoco 8482-WD a/b/g PCI wireless adapter to make a network connection.  It looks like it had automatically installed an "Atheros" driver, and I can see the card in network configuration as "ath0".  I've tried connecting to 2 separate networks:

Network 1:
gateway 192.168.0.1
WEP encryption
Hex key

Network 2:
gateway 192.168.2.1
WPA encryption (I don't see WPA in the adapters properties..)
TKIP Passphrase

I've tried both networks without luck.  When activating the card or applying settings, it will do its thing for about 3 minutes trying to apply, but it won't actually get me on the internet.

A wired internet connection works perfectly.. although it is not an option at my home location (router located 2 floors down).  Please help! :)

---

### Post by Anything Generic on 2005-10-16
Alright.. so googling my heart out pointed me towards the wpa_supplicant.  I think i'm getting closer, but still no dice...  I've configured wpa_supplicant.conf in different ways without luck.  Can someone please try troubleshooting?  

==wpa_supplicant.conf==
---------------------
# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
        ssid="ANDERSON"
	scan_ssid=1
	proto=WPA
        key_mgmt=WPA-PSK
	pairwise=TKIP
	psk="mykey"
}


==Output when I go 'sudo wpa_supplicant -i ath0 -c /etc/wpa_supplicant.conf -D madwifi -dd'==
-----------------------------------------------------
eric@unknown:~$ sudo wpa_supplicant -i ath0 -c /etc/wpa_supplicant.conf -D madwifi -dd
Initializing interface 'ath0' conf '/etc/wpa_supplicant.conf' driver 'madwifi'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
Line: 15 - start of a new network block
ssid - hexdump_ascii(len=8):
     41 4e 44 45 52 53 4f 4e                           ANDERSON
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
pairwise: 0x8
PSK (ASCII passphrase) - hexdump_ascii(len=11): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line 22: removed CCMP from group cipher list since it was not allowed for pairwise cipher
Priority group 0
   id=0 ssid='ANDERSON'
Initializing interface (2) 'ath0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: Operation not supported
SIOCGIWRANGE: too old (short) data - assuming WPA is not supported
Own MAC address: 00:20:a6:50:ab:9e
wpa_driver_madwifi_del_key: keyidx=0
wpa_driver_madwifi_del_key: keyidx=1
wpa_driver_madwifi_del_key: keyidx=2
wpa_driver_madwifi_del_key: keyidx=3
wpa_driver_madwifi_set_countermeasures: enabled=0
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=8):
     41 4e 44 45 52 53 4f 4e                           ANDERSON
Wireless event: cmd=0x8b1a len=21
Wireless event: cmd=0x8b19 len=12
Received 274 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:04:e2:7b:80:c2 ssid='ANDERSON' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   selected
Trying to associate with 00:04:e2:7b:80:c2 (SSID='ANDERSON' freq=2462 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
State: SCANNING -> ASSOCIATING
wpa_driver_madwifi_associate
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b1a len=21
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:04:e2:7b:80:c2
State: ASSOCIATING -> ASSOCIATED
Associated to a new BSS: BSSID=ff:ff:ff:ff:ff:ff
No keys have been configured - skip key clearing
Associated with ff:ff:ff:ff:ff:ff
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
EAPOL: SUPP_BE entering state IDLE
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
Setting authentication timeout: 10 sec 0 usec
RX EAPOL from 00:04:e2:7b:80:c2
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 02 89 00 20 00 00 00 00 00 00 01 44 6c 44 c5 04 75 0e ff bc ab 6a f6 9b 0b 89 ef 9d e1 5d 49 88 32 0e 5d d4 63 3e bc 21 9c db 07 c3 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 02 89 00 20 00 00 00 00 00 00 01 44 6c 44 c5 04 75 0e ff bc ab 6a f6 9b 0b 89 ef 9d e1 5d 49 88 32 0e 5d d4 63 3e bc 21 9c db 07 c3 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:04:e2:7b:80:c2 (ver=1)
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Renewed SNonce - hexdump(len=32): 1a aa 3b 74 63 a3 2a f9 2d fe d8 94 15 66 9a 46 6b 43 50 2e fa 09 fd bd 95 a6 8d 3b 07 6a 5a b4
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 01 44 1a aa 3b 74 63 a3 2a f9 2d fe d8 94 15 66 9a 46 6b 43 50 2e fa 09 fd bd 95 a6 8d 3b 07 6a 5a b4 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 63 fc c2 c7 7b 21 83 96 bb 06 af ac 39 08 dd 97 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RX EAPOL from 00:04:e2:7b:80:c2
RX EAPOL - hexdump(len=125): 01 03 00 79 fe 03 c9 00 20 00 00 00 00 00 00 01 45 6c 44 c5 04 75 0e ff bc ab 6a f6 9b 0b 89 ef 9d e1 5d 49 88 32 0e 5d d4 63 3e bc 21 9c db 07 c3 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 32 ba 8d 84 c7 e7 0f 76 9c dc cb 83 14 95 bb b9 00 1a dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
IEEE 802.1X RX: version=1 type=3 length=121
  EAPOL-Key type=254
WPA: RX EAPOL-Key - hexdump(len=125): 01 03 00 79 fe 03 c9 00 20 00 00 00 00 00 00 01 45 6c 44 c5 04 75 0e ff bc ab 6a f6 9b 0b 89 ef 9d e1 5d 49 88 32 0e 5d d4 63 3e bc 21 9c db 07 c3 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 32 ba 8d 84 c7 e7 0f 76 9c dc cb 83 14 95 bb b9 00 1a dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:04:e2:7b:80:c2 (ver=1)
WPA: IE KeyData - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: Sending EAPOL-Key 4/4
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 03 09 00 20 00 00 00 00 00 00 01 45 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 44 2c 19 1f b2 39 6e ce 49 14 5b 1a de b0 be d9 00 00
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_madwifi_set_key: alg=TKIP key_idx=0 set_tx=1 seq_len=6 key_len=32
EAPOL: External notification - portValid=1
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RX EAPOL from 00:04:e2:7b:80:c2
RX EAPOL - hexdump(len=131): 01 03 00 7f fe 03 a1 00 20 00 00 00 00 00 00 01 46 6c 44 c5 04 75 09 ff bc ab 6a f6 9b 0b 89 ef 9d e1 5d 49 88 32 0e 5d d4 63 3e bc 21 9c db 07 be 9d e1 5d 49 88 32 0e 5d d4 63 3e bc 21 9c db 07 8d 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 ed 40 98 6b ee d3 42 9f 3e 44 16 bf 69 41 04 33 00 20 76 35 de ac 07 3d b9 cd a0 34 e4 fc 33 52 ee 25 53 17 bf 2c 20 cc f7 96 05 29 19 db 88 e5 73 94
IEEE 802.1X RX: version=1 type=3 length=127
  EAPOL-Key type=254
WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 7f fe 03 a1 00 20 00 00 00 00 00 00 01 46 6c 44 c5 04 75 09 ff bc ab 6a f6 9b 0b 89 ef 9d e1 5d 49 88 32 0e 5d d4 63 3e bc 21 9c db 07 be 9d e1 5d 49 88 32 0e 5d d4 63 3e bc 21 9c db 07 8d 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 ed 40 98 6b ee d3 42 9f 3e 44 16 bf 69 41 04 33 00 20 76 35 de ac 07 3d b9 cd a0 34 e4 fc 33 52 ee 25 53 17 bf 2c 20 cc f7 96 05 29 19 db 88 e5 73 94
State: GROUP_HANDSHAKE -> GROUP_HANDSHAKE
WPA: RX message 1 of Group Key Handshake from 00:04:e2:7b:80:c2 (ver=1)
WPA: Group Key - hexdump(len=32): [REMOVED]
WPA: Installing GTK to the driver (keyidx=2 tx=0).
WPA: RSC - hexdump(len=6): 8d 00 00 00 00 00
wpa_driver_madwifi_set_key: alg=TKIP key_idx=2 set_tx=0 seq_len=6 key_len=32
WPA: Sending EAPOL-Key 2/2
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 03 21 00 20 00 00 00 00 00 00 01 46 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 8c 83 ba 2e 66 e9 62 30 d2 8b 12 de f8 ef 4c b5 00 00
WPA: Key negotiation completed with 00:04:e2:7b:80:c2 [PTK=TKIP GTK=TKIP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to ff:ff:ff:ff:ff:ff completed (auth)
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
EAPOL: startWhen --> 0
EAPOL: idleWhile --> 0

---------------------

---

### Post by Anything Generic on 2005-10-18
Alright... I resolved the problem.
Turns out that my wired adapter was conflicting with the wireless adapter in the routing table..
I also had to add my gateway to the DNS in adapter properties..
You should see the grin on my face now that it works =)

---

### Post by Anything Generic on 2005-12-14
It seems like I'm being disconnected every 600 seconds (10 minutes) right on the dot!  The downtime is about 5 seconds, before the connection is stable again for another 600 seconds.  Any ideas?

---

