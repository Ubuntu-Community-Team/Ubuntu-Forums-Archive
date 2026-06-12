---
title: "very weak wifi connection ubuntu 16.04&amp; debian 8"
date: 2016-06-28
forum: Debian
---

### Post by ihab_hamed on 2016-06-28
very weak wifi connection one bar of signle on ubuntu 16.4 & debian 8 , wifi is working well in windows full bars connection
i have tried all solutions i have found on the forum 

i run wireless script on debian and here is the output 

```


########## wireless info START ##########

Report from: 28 Jun 2016 15:26 EET +0200

Booted last: 28 Jun 2016 15:15 EET +0200

Script from: 26 May 2016 21:56 UTC +0000

##### release ###########################

Distributor ID:    Debian
Description:    Debian GNU/Linux 8.5 (jessie)
Release:    8.5
Codename:    jessie

##### kernel ############################

Linux 3.16.0-4-amd64 #1 SMP Debian 3.16.7-ckt25-2+deb8u2 (2016-06-25) x86_64 unknown unknown GNU/Linux

Parameters: ro, quiet

##### desktop ###########################

default

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:21b8]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]
    Kernel driver in use: rt2800pci

##### lsusb #############################

Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 138a:0050 Validity Sensors, Inc. 
Bus 001 Device 003: ID 05c8:036e Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 002: ID 1915:003b Nordic Semiconductor ASA 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

./wireless-info: line 192: rfkill: command not found

##### lsmod #############################

hp_wmi                 13238  0 
sparse_keymap          12818  1 hp_wmi
rt2800pci              13049  0 
rt2800mmio             13390  1 rt2800pci
rt2800lib              81131  2 rt2800pci,rt2800mmio
rt2x00pci              12520  1 rt2800pci
rt2x00mmio             12601  2 rt2800pci,rt2800mmio
rt2x00lib              42331  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
eeprom_93cx6           12625  1 rt2800pci
mac80211              474216  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              405538  2 mac80211,rt2x00lib
crc_ccitt              12347  1 rt2800lib
rfkill                 18867  4 cfg80211,hp_wmi
wmi                    17339  1 hp_wmi

##### interfaces ########################

source /etc/network/interfaces.d/*

auto lo
iface lo inet loopback

##### ifconfig ##########################

./wireless-info: line 202: ifconfig: command not found

##### iwconfig ##########################

./wireless-info: line 211: iwconfig: command not found

##### route #############################

./wireless-info: line 214: route: command not found

##### resolv.conf #######################

nameserver 192.168.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       523     1  0 15:15 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT3290 Wireless 802.11n 1T/1R PCIe (Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter)
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 3.16.0-4-amd64
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Unknown
GENERAL.CON-UUID:                       92b81882-2733-4d40-b404-a7f41c61b558
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     18 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   92b81882-2733-4d40-b404-a7f41c61b558 | Unknown
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
IP4.ADDRESS[1]:                         ip = 192.168.1.3/24, gw = 192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        server_name = TP-LINK
DHCP4.OPTION[5]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[6]:                        ip_address = 192.168.1.3
DHCP4.OPTION[7]:                        requested_static_routes = 1
DHCP4.OPTION[8]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       dhcp_rebinding_time = 226800
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       dhcp_renewal_time = 129600
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1467378919
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       host_name = dhcppc1
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 259200
IP6.ADDRESS[1]:                         ip = fe80::1208:b1ff:feb5:a451/64, gw = ::

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off

SSID            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
ALAMY_output    <MAC 'ALAMY_output' [AN1]>  Infra  4     2427 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA1       no        
Alamy           <MAC 'Alamy' [AN2]>  Infra  9     2452 MHz  54 Mbit/s  27      &#9602;___  WPA2       no        
Unknown         <MAC 'Unknown' [AN3]>  Infra  2     2417 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA1 WPA2  yes     * 
abd.elmaged     <MAC 'abd.elmaged' [AN4]>  Infra  3     2422 MHz  54 Mbit/s  14      &#9602;___  WPA1 WPA2  no        
Alamy Extended  <MAC 'Alamy Extended' [AN5]>  Infra  9     2452 MHz  54 Mbit/s  10      &#9602;___  WPA2       no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

##### NetworkManager profiles ###########

find: `sudo': No such file or directory

Acquisition of admin privileges failed.

##### iw reg get ########################

./wireless-info: line 282: iw: command not found

##### iwlist channels ###################

./wireless-info: line 293: iwlist: command not found

##### iwlist scan #######################

./wireless-info: line 302: sudo: command not found

Acquisition of admin privileges failed.

##### module infos ######################

./wireless-info: line 324: modinfo: command not found
[rt2800pci]

./wireless-info: line 324: modinfo: command not found
[rt2800mmio]

./wireless-info: line 324: modinfo: command not found
[rt2800lib]

./wireless-info: line 324: modinfo: command not found
[rt2x00pci]

./wireless-info: line 324: modinfo: command not found
[rt2x00mmio]

./wireless-info: line 324: modinfo: command not found
[rt2x00lib]

./wireless-info: line 324: modinfo: command not found
[mac80211]

./wireless-info: line 324: modinfo: command not found
[cfg80211]

##### module parameters #################

[rt2800pci]
nohwcrypt: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

find: `/etc/pm/*.d': No such file or directory

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1814:0x3290 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (cdc_ether)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #############################

[    9.258233] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[    9.266285] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[   18.496247] r8169 0000:01:00.0: firmware: failed to load rtl_nic/rtl8168g-3.fw (-2)
[   18.496278] r8169 0000:01:00.0: Direct firmware load failed with error -2
[   18.496838] r8169 0000:01:00.0 eth0: unable to load firmware patch rtl_nic/rtl8168g-3.fw (-12)
[   18.503420] r8169 0000:01:00.0 eth0: link down
[   18.503478] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.504533] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'
[   18.578466] rt2800pci 0000:02:00.0: firmware: direct-loading firmware rt3290.bin
[   18.578479] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.37
[   18.693684] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.213418] wlan0: authenticate with <MAC 'Unknown' [AN3]>
[   20.218810] wlan0: send auth to <MAC 'Unknown' [AN3]> (try 1/3)
[   20.220208] wlan0: authenticated
[   20.222764] wlan0: associate with <MAC 'Unknown' [AN3]> (try 1/3)
[   20.225038] wlan0: RX AssocResp from <MAC 'Unknown' [AN3]> (capab=0x411 status=0 aid=3)
[   20.225110] wlan0: associated
[   20.225133] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############



```

and output of lshw -c network
```

lshw -c network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: d0:bf:9c:21:6a:71
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:58 ioport:5000(size=256) memory:c2604000-c2604fff memory:c2600000-c2603fff
  *-network
       description: Wireless interface
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 10:08:b1:b5:a4:51
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.16.0-4-amd64 firmware=0.37 ip=[192.168.1.3]("http://l.facebook.com/l.php?u=http%3A%2F%2F192.168.1.3%2F&h=4AQFI_RQD") latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:c2510000-c251ffff

```

iwconfig
```

root@debian:/home/ihab# iwconfig
eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Unknown"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 64:70:02:B2:AD:04   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=30/70  Signal level=-80 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1823  Invalid misc:6782   Missed beacon:0

lo        no wireless extensions.



```

---

### Post by howefield on 2016-06-28
Thread moved to the "*Debian*" forum.

---

### Post by ihab_hamed on 2016-06-28
i have tried another network and it work very good and wifi is full bars
but why my home network work very bad on debian and ubuntu and work fine windows ?
is it a router issue ?

---

