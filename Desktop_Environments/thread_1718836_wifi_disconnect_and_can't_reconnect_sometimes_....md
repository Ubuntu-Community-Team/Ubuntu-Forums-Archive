---
title: "wifi disconnect and can't reconnect sometimes ..."
date: 2011-03-31
forum: Desktop Environments
---

### Post by juju43 on 2011-03-31
Hello,

I'm using ubuntu 10.10 up-to-date on a samsung n230 netbook  and sometimes I have strange network behavior.
I'm using standard network-manager with more or less luck.

As of today, I managed to use wifi access at some place but it seems on some period, I'm disconnected and can't reconnect before a long time. Router is checked, restarted, there is no change there.
NetworkManager keep trying to reconnect and asking for new password

But, in command-line, I have no problem to see the network
$ sudo iwlist eth1 scan 
eth1      Scan completed :
          Cell 01 - Address: 00:27:19:1F:A5:EF
                    ESSID:"AP"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-80 dBm  Noise level:-87 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

Any ideas what the problem is or how to debug this ?

Thanks.
Cheers,

---

### Post by juju43 on 2011-03-31
more logs, while nm tries to reconnect multiple times ...

$ sudo iwevent 
Waiting for Wireless Events from interfaces...
08:28:36.845975   eth1     Set Mode:Managed
08:28:36.846165   eth1     Set Frequency:24.12 GHz
08:28:36.846322   eth1     Set ESSID:"AP"
08:28:37.625074   eth1     New Access Point/Cell address:00:27:00:00:A5:EF
08:28:37.687368   eth1     Registered node:00:27:19:1F:A5:EF
08:28:37.687429   eth1     Custom driver event:Conn Success 00 00

08:29:28.799924   eth1     Custom driver event:Conn Disassoc 00 08
08:29:28.799985   eth1     New Access Point/Cell address:Not-Associated
08:29:28.800024   eth1     Set ESSID:"\x0B\xE1\x1A\x1C\x7F#\xF8)\xF8\xA4\x1B\x13\xB5\xCAN\xE8\x9828\xE0yM=4\xBC_Nw\xFA\xCBl\x05"
08:29:29.598360   eth1     Custom driver event:Conn NoNetworks 03 00

08:29:39.824296   eth1     Set Mode:Managed
08:29:39.824380   eth1     Set Frequency:24.12 GHz
08:29:39.824466   eth1     Set ESSID:"AP"
08:29:40.714362   eth1     New Access Point/Cell address:00:27:00:00:A5:EF
08:29:40.763597   eth1     Registered node:00:27:19:1F:A5:EF
08:29:40.763686   eth1     Custom driver event:Conn Success 00 00
08:30:29.881775   eth1     Custom driver event:Conn Disassoc 00 08
08:30:29.881841   eth1     New Access Point/Cell address:Not-Associated
08:30:29.881881   eth1     Set ESSID:"\xAC\x86!+\xAA\x1AU\xA2\xBEp\xB5s;\x04\\xD36\x94\xB3\xAF\xE2\xF0\xE4\x9EO2\x15I\xFD\x82N\xA9"
08:30:30.763315   eth1     Custom driver event:Conn NoNetworks 03 00

---

### Post by micklinghoff on 2011-04-05
Hi there,

I'm having the exact same problem: wireless works for some time, but sometimes for no apparent reason, I get disconnected and can't reconnect, password prompt keeps popping up... 

So I'd also appreciate if someone could reply to this thread ;)

Cheers,

Martin
PS: I know there's no issue with my router, as other devices in the same room stay connected without any problems...

---

### Post by juju43 on 2011-04-05
I found more trace in /var/log/daemon.log between NetworkManager and wpa_supplicant messages.

No explanation but in practice, I need to move near the router to reconnect. After, I can going back to my place (about ~20 meters far from router and having 2 wifi bar)

---

### Post by Copper Bezel on 2011-04-05
If you can identify the kernel module that runs the WLAN card, you can restart it using the commands *rmmod* and *modprobe*. It's a Broadcom chipset - run *lspci* to  get specifics - but I'm seeing that the module is *maybe* just called wl?

For instance, if I want to restart my Atheros 9*** adapter's driver, it's

```
rmmod ath9k
modprobe ath9k
```

That should help us narrow down possibilities. Everything that causes cancer in rats causes Linux to lose WLAN, including research. = (

---

### Post by andrzejs on 2011-04-08
Hello

I have exact problem and i'm using Realtek chip:
_lspci_ command shows:
```
05:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
```

what should i type  in the _rmmod and modprobe_ context to reconnect?

in /var/log/daemon.log i see these entries:
```
Apr  8 19:01:49 desktop wpa_supplicant[1166]: Authentication with 00:00:00:00:00:00 timed out.
Apr  8 19:01:55 desktop NetworkManager[1000]: <warn> (wlan0): link timed out.
Apr  8 19:08:51 desktop NetworkManager[1000]: <warn> Failed to update connection secrets: 1 802-1x
Apr  8 19:08:51 desktop NetworkManager[1000]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr  8 19:08:51 desktop NetworkManager[1000]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr  8 19:08:51 desktop NetworkManager[1000]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr  8 19:08:51 desktop NetworkManager[1000]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr  8 19:08:51 desktop NetworkManager[1000]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr  8 19:08:51 desktop NetworkManager[1000]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr  8 19:08:51 desktop NetworkManager[1000]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr  8 19:08:51 desktop NetworkManager[1000]: <info> Activation (wlan0/wireless): connection 'XXX-321564' has security, and secrets exist.  No new secrets needed.
Apr  8 19:08:51 desktop NetworkManager[1000]: <info> Config: added 'ssid' value 'XXX-321564'
Apr  8 19:08:51 desktop NetworkManager[1000]: <info> Config: added 'scan_ssid' value '1'
Apr  8 19:08:51 desktop NetworkManager[1000]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr  8 19:08:51 desktop NetworkManager[1000]: <info> Config: added 'psk' value '<omitted>'
Apr  8 19:08:51 desktop NetworkManager[1000]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr  8 19:08:51 desktop NetworkManager[1000]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr  8 19:08:51 desktop NetworkManager[1000]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr  8 19:08:51 desktop NetworkManager[1000]: <info> Config: set interface ap_scan to 1
Apr  8 19:08:51 desktop NetworkManager[1000]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr  8 19:09:52 desktop NetworkManager[1000]: <warn> Activation (wlan0/wireless): association took too long.
Apr  8 19:09:52 desktop NetworkManager[1000]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr  8 19:09:52 desktop NetworkManager[1000]: <warn> Activation (wlan0/wireless): asking for new secrets
Apr  8 19:09:52 desktop NetworkManager[1000]: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr  8 19:10:07 desktop NetworkManager[1000]: <warn> (wlan0): link timed out.
Apr  8 19:13:11 desktop NetworkManager[1000]: <warn> Failed to update connection secrets: 1 802-1x
Apr  8 19:13:11 desktop NetworkManager[1000]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr  8 19:13:11 desktop NetworkManager[1000]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr  8 19:13:11 desktop NetworkManager[1000]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr  8 19:13:11 desktop NetworkManager[1000]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr  8 19:13:11 desktop NetworkManager[1000]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr  8 19:13:11 desktop NetworkManager[1000]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr  8 19:13:11 desktop NetworkManager[1000]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr  8 19:13:11 desktop NetworkManager[1000]: <info> Activation (wlan0/wireless): connection 'XXX-321564' has security, and secrets exist.  No new secrets needed.
Apr  8 19:13:11 desktop NetworkManager[1000]: <info> Config: added 'ssid' value 'XXX-321564'
Apr  8 19:13:11 desktop NetworkManager[1000]: <info> Config: added 'scan_ssid' value '1'
Apr  8 19:13:11 desktop NetworkManager[1000]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr  8 19:13:11 desktop NetworkManager[1000]: <info> Config: added 'psk' value '<omitted>'
Apr  8 19:13:11 desktop NetworkManager[1000]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr  8 19:13:11 desktop NetworkManager[1000]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr  8 19:13:11 desktop NetworkManager[1000]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr  8 19:13:11 desktop NetworkManager[1000]: <info> Config: set interface ap_scan to 1
Apr  8 19:13:11 desktop NetworkManager[1000]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr  8 19:13:29 desktop NetworkManager[1000]: <info> (wlan0): device state change: 5 -> 3 (reason 38)
Apr  8 19:13:29 desktop NetworkManager[1000]: <info> (wlan0): deactivating device (reason: 38).
Apr  8 19:13:29 desktop NetworkManager[1000]: <error> [1302279209.430232] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
```

I'm currently on Kubuntu 10.10. I had exact problem with Ubuntu 10.10 and Fedora 14. I thought it's the Gnome bug, so i switched to KDE, but problem remains.

---

### Post by Stray Wolf on 2011-04-08
Try toggling your wifi switch - worked for me!

---

### Post by andrzejs on 2011-04-08
well, i'm on desktop PC with PCI wlan adapter, and there is no switch on it :)

---

### Post by juju43 on 2011-04-19
On my side,

$ lsmod|grep -i wl
wl                   1959533  0 
lib80211                5058  2 lib80211_crypt_tkip,wl

$ lspci |grep -i broadcom
05:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)

for now, working, but no real solution except what said above.

---

