---
title: "Wireless Just Stopped Working"
date: 2006-07-17
forum: Desktop Environments
---

### Post by Jerim on 2006-07-17
I have had wireless working for a while now. I took my laptop over to my new apartment. I haven't moved my wireless router over to the new location, but I did see the free wireless connection that the apartment complex offers. I logged on.

I decided to go over to the old apartment for a few things. I started to log onto the wireless network, but I noticed that it would not list any wireless networks. The icon at the top has a line through it. It is the icon that sort of looks like a USB cable, or maybe it looks like a mouse to some people. It is named "Networkmanager Applet 0.6.2." When I click on it, instead of getting a list of networks, I get "No Network Devices Have Been Found."

I go to "Networking" under "System." In there, the wireless connection has a new icon, but it still says active. (The icon used to be a wavy line, but now it has a PCMCIA card.) I can set eth1 as the gateway. However, up on the top taskbar on my desktop, there is an icon that looks like two little computers. It no longer offers eth1 as a choice. The icon is named "Network Monitor 0.6.2."

I promise that I haven't changed any of the settings. It took me so long to get wireless working the first time. I have tried to do sudo ifdown eth1 and sudo ifup eth1 and it just keeps searching for a DHCP lease. Any help will be appreciated. I can provide any information that is requested.

---

### Post by philippe_carlo on 2006-07-17
Sometimes, the radio gets turned of for no apparent reason (e.g. accidental key stroke). Check if it is turned on. On my laptop, this can be done with Fn+F5, but it may be different on yours.

---

### Post by Jerim on 2006-07-17
Thanks for the tip. I checked it and it was disabled for some reason. I enabled it. On bootup, when Ubuntu is Configuring Network Devices, the wireless light will come on for about 10 seconds and then go off. When I get to the desktop, I can go to the Networking Panel and set eth1 to the gateway. The wireless light will come on for a few seconds and then go right off.

The Networkmanager Applet no longer has a line through it, but it only offers one option, "Wired." It used to offer wireled and a list of wireless networks in the area. (BTW, I am sitting right next to a wireless router.) The Network Monitor still only shows lo and eth0 as the available options. Not eth1.

---

### Post by philippe_carlo on 2006-07-17
> **Jerim said:**
> Thanks for the tip. I checked it and it was disabled for some reason. I enabled it. On bootup, when Ubuntu is Configuring Network Devices, the wireless light will come on for about 10 seconds and then go off. When I get to the desktop, I can go to the Networking Panel and set eth1 to the gateway. The wireless light will come on for a few seconds and then go right off.

The Networkmanager Applet no longer has a line through it, but it only offers one option, "Wired." It used to offer wireled and a list of wireless networks in the area. (BTW, I am sitting right next to a wireless router.) The Network Monitor still only shows lo and eth0 as the available options. Not eth1.

Time to get our feet wet, I'm afraid. I will need some more info. What is the type of wireless network card, which modules does it need? Can you check wether they are loaded (with lsmod)?

Is your interface listed in the output of ifconfig. Can you maybe post the output of 'sudo ifconfig' and 'sudo iwconfig'? What does 'sudo iwlist eth1 scan' give you?

---

### Post by Jerim on 2006-07-17
The wireless card is the Broadcom Airport 54. (Built-in wireless on an Inspiron B130.) 

I am using ndiswrapper to load the windows driver. lsmod is showing that it is loaded.

Ifconfig does show eth1. Here is the output of ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:14:22:92:B0:00
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fe92:b000/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5091 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11056 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3765211 (3.5 MiB)  TX bytes:1138449 (1.0 MiB)
          Interrupt:217

eth1      Link encap:Ethernet  HWaddr 00:14:A4:58:BD:BC
          inet6 addr: fe80::214:a4ff:fe58:bdbc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Memory:dfbfe000-dfc00000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

Iwconfig shows eth1. Here is the output of iwconfig:

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management min timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by philippe_carlo on 2006-07-17
Seems like there is nothing wrong with you network card, since it is properly listed. Let's try connecting the command-line way:
```

sudo iwconfig eth1 essid "<NETWORK NAME HERE>"
sudo dhclient eth1

```

Let me know.

---

### Post by Jerim on 2006-07-18
It will connect to the essid, but the light goes off after about 3 seconds. When I run the dhclient command, it never finds an IP address.

I setup my wireless card using this tutorial;  [http://www.ubuntuforums.org/showthread.php?t=190177](http://www.ubuntuforums.org/showthread.php?t=190177)

---

