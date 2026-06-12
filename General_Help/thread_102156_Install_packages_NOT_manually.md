---
title: "Install packages NOT manually??"
date: 2005-12-11
forum: General Help
---

### Post by Ravendark on 2005-12-11
2 days ago I decided to give ubuntu 5.10 a try on my laptop. Yesterday I destroyed my system trying to manually install packages that I needed because I cannot connect to the internet with ubuntu and use apt-get (and I reinstalled it again).

So my question is:
Can i manually download the files I need and use a tool to install it for me? Something to check the deps and if I need some packs that are missing to tell me about it?
Because everytime i try to install a -dev pack I get a bunch of dep errors link this pack needs this dep and this and this...

Thanks!

---

### Post by mherring on 2005-12-11
I would think that the better approach would be to get the internet connection working.  What is the issue there?

---

### Post by aysiu on 2005-12-11
I agree with mherring.
It'd be better to get your internet working.

However, if you absolutely must install without internet working, this may help:
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

---

### Post by Ravendark on 2005-12-11
Wireless internet is a pain for me!:( 
I am using a broadcom wireless card which works ok with ndiswrapper.
But i havent been able to connect.
I am at the university's accomodation and there is a cisco wireless access point in every floor.
Wireless settings in windows:

In the association tab:
* Network Authentication: Open
* Data Encyption: WEP
* The key is provided for me automatically

Authentication tab:
* Enable IEEE 802.1x authentication for this network
* EAP type: Protected EAP (PEAP)

PEAP Properties:
* Validate server certificate
* There is a certification checked (calcourt.cer) and
* Select Authentication method: Secured password (EAP-MSCHAP v2)

I am using wpa_supplicant but no luck.
I get the following output:

```
root@blashyrkh:/home/raven# wpa_supplicant -d -iwlan0 -c/etc/wpa_supplicant.conf -Dndiswrapper
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Priority group 0
   id=0 ssid='SSID-WAP-WAccess-CALCOURT'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: No such device
SIOCGIWRANGE: too old (short) data - assuming WPA is not supported
Own MAC address: 00:14:a5:04:7c:10
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
Setting scan request: 0 sec 100000 usec
Added interface wlan0
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b2a len=12
Wireless event: cmd=0x8b2a len=12
Wireless event: cmd=0x8b2a len=12
Wireless event: cmd=0x8b2a len=12
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 413 bytes of scan results (2 BSSes)
Scan results: 2
Selecting BSS from priority group 0
0: 00:0d:29:ac:d8:0c ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 00:0c:41:9d:b1:66 ssid='Blacktower' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
No suitable AP found.
```

My wpa_supplicant config:
```
ctrl_interface=/var/run/wpa_supplicant

network={
	ssid="SSID-WAP-WAccess-CALCOURT"
	key_mgmt=IEEE8021X
	eap=PEAP
	phase2="auth=MSCHAPV2"
	identity="gkyril10"
	password="********"
	ca_cert="/etc/cert/calcourt.pem"
}

```

But no luck!:confused: :( :(

---

