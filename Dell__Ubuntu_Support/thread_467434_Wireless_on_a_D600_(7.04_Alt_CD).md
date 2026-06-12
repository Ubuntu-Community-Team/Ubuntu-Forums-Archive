---
title: "Wireless on a D600 (7.04 Alt CD)"
date: 2007-06-07
forum: Dell  Ubuntu Support
---

### Post by scrupul0us on 2007-06-07
I have the command-line-only install of 7.04

im trying to get my wireless to work

info:

```

1) i installed NDISWRAPPER
apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk

2) lspci
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
--I WENT WITH THE WIRELESS--

3) lspci -n
02:00.0 0200: 14e4:165d (rev 01)
02:03.0 0280: 8086:1043 (rev 04)

4) x-ref to find proper drivers
# Chipset: Intel PRO/Wireless Lan 2100 3B
# pciid: 8086:1043
# Driver: w70n51.inf

5) download driver exe from support.dell.com
Release Title:	Network: Intel (R) Pro/Wireless 2100 LAN miniPCI Adapter, Driver, Windows 2000, Windows XP, Multi Language, Multi System, v.1.2.4.35, 7.1.4.4, A21
Release Date:	7/27/2005
Criticality:	Optional
Description:	Intel PRO/Wireless LAN 2100 3A Mini-PCI Adapter Customer Installer Package

5a) unpack...i get 3 files
-w70n5.sys
-w70n51.sys
-w70n501.inf

6) install driver
ndiswrapper -i w70n501.inf

7) ndiswrapper -l
w70n501 : driver installed
        device (8086:1043) present (alternate driver: ipw2200)

8) load driver
depmod -a
modprobe ndiswrapper

9) tail /var/log/messages
--no messages related to anything im doing--

10) ifconfig and iwconfig
NEITHER SHOW WLAN0

```

however under iwconfig i get:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power:16 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



is eth1 valid??? if so how can i edit the encryption settings?

what am i doing wrong???

i followed this: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

and x-ref'd with: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

any ideas?

---

### Post by scrupul0us on 2007-06-07
so after some more reading i figured that maybe i need to use the broadcom driver instead of the one im using... so i uninstalled the intel one:

ndiswrapper -r w70n501

and installed the XP drivers

the log file now reads:
Jun  7 21:41:58 ICBA kernel: [  134.820000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
Jun  7 21:41:58 ICBA kernel: [  134.856000] usbcore: registered new interface driver ndiswrapper

but when i do a iwconfig i get the same stuff
eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power:16 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



annnnnnnnnnnyone?

p.s. i did blacklist the standard driver

---

### Post by scrupul0us on 2007-06-07
so i wussed out and installed KDE... it sees my wireless just fine... howeve ri cannot connect to my WAP network nor ANY network in my building... help!

---

### Post by kill4killin on 2007-06-08
If you are referring to WPA network, then it is possibly because the current network manager is unable to do dual layer authentication on wpa-eas type networks. However, those kinds of networks are not that common and usually you know if you have that kind of network because they are deffinatly a standard type of protection on a wireless network. Might I inquire as to why you went with KDE and not Gnome, I find KDE to be a little more system heavey then Gnome and it sounds like you are trying to keep your system from getting to bogged down with a window manager, correct me if I am wrong though.

---

### Post by scrupul0us on 2007-06-08
well i got WPA to work... i had to reboot (odd)... i went with KDE b/c idk... im not a x-windows kinda person so ive never experienced one that really grabbed my attention... i just wanted to see if the GUI would make this wireless work...

and now it does...

begs the question... if i uninstall the desktop, will my wireless still work???

what desktop does DSL use (damn small linux)

---

