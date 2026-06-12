---
title: "No Connectivity on Wireless"
date: 2006-09-27
forum: Desktop Environments
---

### Post by spacecowboy706 on 2006-09-27
Using Ubuntu 6.06 and i have tried switching from wired to wireless by going to SYSTEM - ADMINISTRATIVE - NETWORKING and then DEACTIVITING the ethernet card and ACTIVATING the Wireless Connection.

When i do this, under the connection type it get the following: the ethernet connection will say "The interface eth0 is not active" and the wireless connection will say "The interface ra0 is active"

Under the Wired connection I have tried using DHCP and STATIC IP ADDRESS. Under DHCP the wired portion will connect fine and if i switch it to STATIC it will work fine also. and of course i am entering the correct information for the IP address, Subnet Mask and Default Gateway.

Under the Wireless connection I have tried using DHCP and STATIC IP ADDRESS. Under DHCP the wireless portion will NOT connect fine and if i switch it to STATIC it will NOT work also. and of course i am entering the correct information for the IP address, Subnet Mask and Default Gateway

I fear that i may be having a driver issue or something along these lines, but with my first week of Ubuntu and linux in general, i dont know how to check this.

I have temporarily disabled all wireless encryption like my WEP and MAC filter and this still has not helped. 

I have also power cycled the modem and router with no success there as well. I use cable internet with a motorrolla surfboard 5120 modem, and Linksys wrt54g router. The wired card is a Linksys lne100tx Etherfast and the wireless card is a Linksys WMP54G wireless G PCI card.

Both of course function properly under WinXP Pro SP2... <--- But I dont like using that anymore since I'm hooked on Ubuntu... I'll never go back.

Somebody please help?

---

### Post by spacecowboy706 on 2006-09-27
Man this is one busy forum . . . Patiently waiting [-(

Found another link inside this forum that was related and it was asking for this stuff, so I though I might add it in here as well:

xxxxx@xxxxxx-desktop:~$ **lspci**

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:04.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:04.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:04.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:0a.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
0000:00:0b.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:00:0d.0 Multimedia audio controller: Creative Labs SB Audigy LS
0000:00:11.0 Mass storage controller: Promise Technology, Inc. PDC20265 (FastTrak100 Lite/Ultra100) (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)

xxxxxx@xxxxxx-desktop:~$ **iwconfig**

lo        no wireless extensions.
ra0       RT2500 Wireless  ESSID:""
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:1 Mb/s   Tx-Power:0 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
eth0      no wireless extensions.
rausb0    RT2500USB WLAN  ESSID:""
          Mode:Managed  Frequency=2.412 GHz
          RTS thr:off   Fragment thr:off
          Link Quality=0/70  Signal level:-120 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
sit0      no wireless extensions.


xxxxxx@xxxxxx-desktop:~$ **ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:12:17:58:F9:F1
          inet addr:192.168.1.96  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:fe58:f9f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3834 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3518 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4411156 (4.2 MiB)  TX bytes:445840 (435.3 KiB)
          Interrupt:10 Base address:0xa400
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:343 errors:0 dropped:0 overruns:0 frame:0
          TX packets:343 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:14452 (14.1 KiB)  TX bytes:14452 (14.1 KiB

---

### Post by koshari on 2006-09-27
ok first things first , i take it you are getting a signal, or can see your access point in airsnort?

---

### Post by spacecowboy706 on 2006-09-27
added the above to my second post.... and yes when i click on the wireless PCI card i can see my ESSID already entered in the drop down box.... BUT... only half of the ssid name appears like this:

the actual ssid is: Cr@ck3d&h@cK3d
but the only part that shows is: Cr@ck3d

shouldnt the whole name appaer?

PS.. I don't know what airsnort is... im not using a MAC if thats what it is for... I built this desktop from scratch all for under 100 dollers and salvaged parts from about 50 other desktops. :D

PSS... there is a USB receiver as well attached, but im not worried about it working, as it used for sniffing in XP.

---

### Post by koshari on 2006-09-28
airsnort is a program that will scan for any wifi connections , so it will tell you if your hardware is detecting the access signal,

---

### Post by spacecowboy706 on 2006-09-28
Ok I have now installed Airsnort, what next.

---

### Post by koshari on 2006-10-08
run airsnort and see if it can scan your access point.

---

