---
title: "Wireless Access"
date: 2006-03-12
forum: Desktop Environments
---

### Post by PCBrandon on 2006-03-12
Hi all,

I'm completely new to Linux. I have been able to setup a dual boot system with Windows XP Professional SP2 and Ubuntu Linux successfully. However, this is as far as I have gotten. 

During setup of Ubuntu, it found my internal Intel Wireless 2200BG 802.11bg. However, once it tried to connect to my wireless router, it failed and I told it to skip that step and continue setup.

Now that I'm in Ubuntu, I still haven't been able to connect to my router. This is what I know so far:

Router Specs:
Model: Linsys SRX 200
SSID: JDAB10412
Key: nnnnnxxxx (where n is a number and x is a capital letter)

I am  trying to configure it through System > Administration > Networking. I can connect to a direct ethernet connection to that same router, but not through wireless.

Any ideas?

---

### Post by thnogueira on 2006-03-12
What kind of key are you using? If it's wpa, take a look at:
[https://wiki.ubuntu.com/WPAHowto]("https://wiki.ubuntu.com/WPAHowto")

---

### Post by PCBrandon on 2006-03-12
Thanks for the reply. My security is WPA Personal with TKIP encryption. 

I did the following according to that article:

I went to install the Universal Packages from the linked supplied in the Wiki ([https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages)](https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages)). 

That part seemed to work out fine. I then proceeded the next step in the Wiki and typed:

sudo apt-get install wpasupplicant

That seemed to install correctly too. The next part is where I got confused. It talked about editing /etc/wpa_supplicant.conf and /etc/wpasupplicant. So, I typed:

sudo gedit /etc/wpa_supplicant.conf 

That file now looks like this (with the correct key):

[PHP]# Minimal /etc/wpa_supplicant.conf to associate with open
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
        ssid="JDAB10214"
        #psk="*****"
	proto=WPA
        key_mgmt=WPA-PSK
        psk=945609a382413e64d57daef00eb5fab3ae228716e1e440981c004bc61dccc98c
}[/PHP]


That is the only file I editted. The next step in the Wiki was testing it. So I typed in the command and it failed, so I typed in the command appended with -dd to get diagnostics I guess. This is what I got:

> Initializing interface 'eth0' conf '/etc/wpa_supplicant.conf' driver 'madwifi'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
Line: 16 - start of a new network block
ssid - hexdump_ascii(len=9):
     4a 44 41 42 31 30 32 31 34                        JDAB10214
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='JDAB10214'
Initializing interface (2) 'eth0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: Operation not supported
ioctl[SIOCSIWMODE]: Operation not supported
Could not configure driver to use managed mode
ioctl[SIOCGIWRANGE]: Operation not supported
ioctl[IEEE80211_IOCTL_SETPARAM]: Operation not supported
wpa_driver_madwifi_init: failed to set wpa_supplicant-based roaming
ioctl[SIOCSIWAP]: Operation not supported
Failed to initialize driver interface



Any suggestions? :(

---

### Post by PCBrandon on 2006-03-12
Hm, I was entering in the wrong connction for the command to test (I used eth0 instead of eth1).

This is what I get now:

> Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'madwifi'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
Line: 16 - start of a new network block
ssid - hexdump_ascii(len=9):
     4a 44 41 42 31 30 32 31 34                        JDAB10214
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='JDAB10214'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: Operation not supported
SIOCGIWRANGE: too old (short) data - assuming WPA is not supported
Own MAC address: 00:13:ce:9a:cd:f6
wpa_driver_madwifi_del_key: keyidx=0
ioctl[IEEE80211_IOCTL_DELKEY]: Invalid argument
wpa_driver_madwifi_del_key: keyidx=1
ioctl[IEEE80211_IOCTL_DELKEY]: Invalid argument
wpa_driver_madwifi_del_key: keyidx=2
ioctl[IEEE80211_IOCTL_DELKEY]: Invalid argument
wpa_driver_madwifi_del_key: keyidx=3
ioctl[IEEE80211_IOCTL_DELKEY]: Invalid argument
wpa_driver_madwifi_set_countermeasures: enabled=0
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Wireless event: cmd=0x8b1a len=12
State: SCANNING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_madwifi_set_drop_unencrypted: enabled=0
wpa_driver_madwifi_set_countermeasures: enabled=0
No keys have been configured - skip key clearing


---

### Post by thnogueira on 2006-03-12
I'm gonna post mine:
```

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
        ssid="intra"
	scan_ssid=1
	key_mgmt=WPA-PSK
	proto=WPA
	pairwise= CCMP TKIP
	group= CCMP TKIP
	key_mgmt=WPA-PSK
        psk=" (i've put my pass between "") "
}



```

I hope it heps.

---

### Post by PCBrandon on 2006-03-12
Thanks again for the reply. I copied yours and pasted it into mine and changed it to my settings. This is what I get when I test it:

> Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'madwifi'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
Line: 15 - start of a new network block
ssid - hexdump_ascii(len=9):
     4a 44 41 42 31 30 34 31 32                        JDAB10412
scan_ssid=1 (0x1)
key_mgmt: 0x2
proto: 0x1
pairwise: 0x18
group: 0x18
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=9): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='JDAB10412'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: Operation not supported
SIOCGIWRANGE: too old (short) data - assuming WPA is not supported
Own MAC address: 00:13:ce:9a:cd:f6
wpa_driver_madwifi_del_key: keyidx=0
ioctl[IEEE80211_IOCTL_DELKEY]: Invalid argument
wpa_driver_madwifi_del_key: keyidx=1
ioctl[IEEE80211_IOCTL_DELKEY]: Invalid argument
wpa_driver_madwifi_del_key: keyidx=2
ioctl[IEEE80211_IOCTL_DELKEY]: Invalid argument
wpa_driver_madwifi_del_key: keyidx=3
ioctl[IEEE80211_IOCTL_DELKEY]: Invalid argument
wpa_driver_madwifi_set_countermeasures: enabled=0
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Using existing control interface directory.
bind(PF_UNIX): Address already in use
ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/eth1' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.
wpa_driver_madwifi_set_drop_unencrypted: enabled=0
wpa_driver_madwifi_set_countermeasures: enabled=0
No keys have been configured - skip key clearing


---

### Post by flosofl on 2006-03-13
I think you are using the wrong driver.  In your output I see it's using "madwifi".  According to everything I've seen, you want to use 'ipw' as the driver parameter for wpa_supplicant.  (I have seen some documents claim that 'wext' is the driver to use for the 2200, but I can't find it anymore).

Here is a Wiki for wpa_supplicant: [Wpa Supplicant ArchWiki]("http://wiki.archlinux.org/index.php/Wpa_supplicant")

EDIT:  Found it in the the Wiki:

"For intel 2200 cards using the latest driver (1.0.8 at the time of this writing) and kernel 2.6.13 or higher you would use "-D wext" (not -D ipw as you would with older versions)"

EDIT (again...):  What is in your /etc/default/wpasupplicant file?  Does it have the default values (i.e. OPTIONS="-i ath0 -D madwifi -c /etc/wpa_supplicant.conf")?   If so, that is mostl likely your problem.

---

