---
title: "Anyone else's connection less responsive in linux than windows?"
date: 2005-09-21
forum: Desktop Environments
---

### Post by Xiata on 2005-09-21
Maybe I am doing something wrong, but there seems to be a very long pause for any connection to the internet actually occurs. I sit at Connecting to [www.ubuntuforum.org](www.ubuntuforum.org), or any addresses for a good 5 seconds before things start to get sent to me.

I don't think it is my router that is at fault, since it is the same wireless router I have been using with windows. And it certainly shouldn't be my connection, I have a 10000/1000 connection to the (external) net in my dorm room.

---

### Post by Xiata on 2005-09-21
Current network configurations:
iwconfig ath0:```

ath0      IEEE 802.11g  ESSID:"XiataNET"
          Mode:Managed  Frequency:2.447 GHz  Access Point: ??:??:??:??:??:??
          Bit Rate:54 Mb/s   Tx-Power:50 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off          Encryption key:????-????-????-????-????-????-??   Security mode:restricted
          Power Management:off
          Link Quality=48/94  Signal level=-47 dBm  Noise level=-95 dBm
          Rx invalid nwid:422753  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:114  Invalid misc:114   Missed beacon:0

```ifconfig ath0:
```
ath0      Link encap:Ethernet  HWaddr ??:??:??:??:??:??
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:eaff:fe91:5c1a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:110249 errors:54998 dropped:0 overruns:0 frame:54998
          TX packets:96754 errors:115 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:71509477 (68.1 MiB)  TX bytes:14092551 (13.4 MiB)
          Interrupt:16 Memory:e1020000-e1030000

```
/etc/resolv.conf:
```
 nameserver 129.21.3.17
nameserver 129.21.4.18

```
/etc/network/interfaces:```
auto lo
iface lo inet loopback
mapping hotplug
        script grep
        map eth0 ath0
auto ath0
iface ath0 inet dhcp
wireless-essid XiataNET
wireless-key ??????????????????????????????????

```
Last issued configuration commands to wireless card:
```
iwconfig ath0 essid XiataNET mode managed channel 8 ap any sens -85 nick XiataNET rate 54M rts 250 frag 512 enc restricted ?????????????????????????????????? txpower 50mW
iwpriv ath0 hide_ssid 0 mode 0 wpa 0 ap_bridge 1 turbo 0 dropunencrypted 0 countermeasures 0 roaming 0
```
Wireless card: Gigabyte GN-WIAG01 (mini-pci)
Wireless Driver: madwifi ```
kernel: ath_hal: 0.9.12.14 (AR5210, AR5211, AR5212)
kernel: wlan: 0.8.4.5 (EXPERIMENTAL)
kernel: ath_rate_onoe: 1.0
kernel: ath_pci: 0.9.4.12 (EXPERIMENTAL)
kernel: ath0: Atheros 5212: mem=0x20000000, irq=16

```
Active internet connection related services: mDNSResponder, dhclient

---

### Post by cwaldbieser on 2005-09-21
Does a ping also take a long time?  I was experiencing that kind of slowness with Konqueror, and it turned out to be that IPV6 tunnling was the culprit.  You can turn this off in both Konqueor and Firefox.  For Konqueor, add "KDE_NO_IPV6=true" to /etc/environment.  For Firefox, go to about:config, search for "ipv6" and set that flag to a disabled state.

---

### Post by bob_c_b on 2005-09-21
My NIC driver actually crashes all the time in Windows (Marvell Gigabit) and the latest Win driver actually causes hard freezes with nVidia cards??? In Linux it is rock solid and pretty fast, although my router/switch defaults to 100mbps so I have no idea if the Linux driver supports the higher speed.

---

