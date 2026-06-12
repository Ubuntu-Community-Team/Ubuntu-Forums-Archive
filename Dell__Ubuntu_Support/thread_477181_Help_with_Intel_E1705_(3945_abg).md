---
title: "Help with Intel E1705 (3945 a/b/g)"
date: 2007-06-18
forum: Dell  Ubuntu Support
---

### Post by skhelter on 2007-06-18
I installed ndiswrapper and ndisgtk as instructed and have the correct production drivers from <http://support.intel.com/support/notebook/sb/CS-006408.htm>. However, after attempting to use ndisgtk to install said plugins, I still had no connection. I read from <https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper> that a directory can only contain one .inf and one .sys file. Since I had four .inf files (NETw4k32, NETw4x32, NETw4x64, and w29n51) and five .sys files (NETw4k32, NETw4x32, NETw4x64, w29n50, and w29n51), I tried to create directories containing one of each type of file and then proceeding to use ndisgtk again - this still didn't work. Has anyone here had experience with these particular drivers? I am (obviously) a newbie to this sort of thing, so if I seem a bit vague, please feel free to ask me more about the problem.

---

### Post by skhelter on 2007-06-18
bump?

I did some stuff and found that the drivers were already installed, though I still have no connection:

```

brian@brian-laptop:~$ lsmod | grep ipw
ipw3945               124576  1 
ieee80211              35272  1 ipw3945
brian@brian-laptop:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0c:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:a6:03:1e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.1.0mp firmware=13.0 1:0 () link=no multicast=yes wireless=unassociated
       resources: iomemory:dcfff000-dcffffff irq:177
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:38:05:75
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=1.00 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:dcbfe000-dcbfffff irq:177
brian@brian-laptop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:C5:38:05:75  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:166 errors:0 dropped:0 overruns:0 frame:0
          TX packets:166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12572 (12.2 KiB)  TX bytes:12572 (12.2 KiB)

brian@brian-laptop:~$ sudo iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:49149   Missed beacon:0

```

I don't know  what to make of this =/ Would anyone care to chip in?

---

### Post by neptho on 2007-06-19
I had no end of problems with trying to use the crap which is gnome's network-manager'

Here's what I did to make it work (and work properly after a sleep.

First, my /etc/network/interfaces:

```
auto lo
iface lo inet loopback
auto eth1 
iface eth1 inet dhcp
pre-up          /etc/init.d/wifi_wpa.sh start
pre-down        /etc/init.d/wifi_wpa.sh stop
```

Ok, now let's look at this magical /etc/init.d/wifi_wpa.sh:

```
#!/bin/sh
PATH=/bin:/usr/bin:/sbin:/usr/sbin
BIN=/sbin/wpa_supplicant
PIDFILE=/var/run/wpa_supplicant.pid
. /lib/lsb/init-functions

case "$1" in
  start)
if [ -x /sbin/wpa_supplicant ]; then
  $BIN -ieth1 -c /etc/wpa_supplicant.conf -Dwext -w -P $PIDFILE 2>&1 &
fi
    ;;
  stop)
    killall wpa_supplicant
    ;;
  *)
    ;;
esac
exit 0
```

Ok, and the /etc/wpa_supplicant.conf:
```
network={
  ssid="my_ssid_goes_here"
  scan_ssid=1
  psk="my_key_goes_here"
}
#network={
#  key_mgmt=NONE
#  priority=-9999999
#}
```

I can use ifup/ifdown, and it works.. and things return properly from sleep.  Every time I tried to use gnome's network-manager it caused me more pain.  This, despite being less mobile, works fine.

(You may add separate networks in the above, with the odd priority (commented out), I told it to take any encrypted network over unencrypted for preecedence.)

If you follow my note above, remember to chmod 755 /etc/init.d/wifi_wpa.sh, and it would be wise to set /etc/wpa_supplicant.conf 600.

---

### Post by kgr132 on 2007-06-19
I also had a lot of trouble with Gnome's Network Manager. It turned out that it was all related to the fact that after I installed ndiswrapper, the wireless card was assigned to eth1. Unless the interface was called wlan0, my network manager refused to use it. I found I had to edit the following files:

/etc/modeprobe.d/ndiswrapper
/etc/network/interfaces
/etc/iftab

Edit these files and replace any instances of "eth1" with "wlan0" - no quotes, then reboot. I used a terminal window and "sudo gedit" to edit mine. Remember, too, a wise man backs up his files before editing.
Good Luck.
-K-

---

