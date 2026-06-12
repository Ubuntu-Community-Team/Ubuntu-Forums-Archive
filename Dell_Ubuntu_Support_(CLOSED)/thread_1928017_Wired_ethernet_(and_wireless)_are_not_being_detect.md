---
title: "Wired ethernet (and wireless) are not being detected"
date: 2012-02-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dspi on 2012-02-19
I have a Dell Inspiron N5010 which is dual booted with Windows7 and Ubuntu 11.10 (64-bit)
However, in Ubuntu, the wired ethernet (and wireless) are not being detected.  (In windows it's fine.)

Which drivers need to be installed, and how do I install them.

All help appreciated.

Here are a few specs:


Network Card/Driver:
```

lspci -vvnn | grep 14e4
RETURNS:
12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

```Kernel:  (Running Ubuntu 11.10 64-bit)
```

uname -r
RETURNS:
3.0.0-12-generic 

```Check for loaded drivers:
```

lsmod | grep "b43\|ssb\|wl\|brc\|bcma"
RETURNS:
wl                   2568210  0 
lib80211               14991  1 wl
bcma                   20219  0 
brcmsmac              631693  0 
brcmutil               17837  1 brcmsmac
mac80211              310872  1 brcmsmac
cfg80211              199587  2 brcmsmac,mac80211
crc_ccitt              12667  1 brcmsmac

``````

ifconfig
RETURNS:
eth0      Link encap:Ethernet  HWaddr f0:4d:a2:a2:f4:52  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:50 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10176 (10.1 KB)  TX bytes:10176 (10.1 KB)

wlan0     Link encap:Ethernet  HWaddr 1c:65:9d:79:73:e5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

``````

lspci -nn
RETURNS:
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DMI [8086:d132] (rev 11)
00:03.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express Root Port 1 [8086:d138] (rev 11)
00:08.0 System peripheral [0880]: Intel Corporation Core Processor System Management Registers [8086:d155] (rev 11)
00:08.1 System peripheral [0880]: Intel Corporation Core Processor Semaphore and Scratchpad Registers [8086:d156] (rev 11)
00:08.2 System peripheral [0880]: Intel Corporation Core Processor System Control and Status Registers [8086:d157] (rev 11)
00:08.3 System peripheral [0880]: Intel Corporation Core Processor Miscellaneous Registers [8086:d158] (rev 11)
00:10.0 System peripheral [0880]: Intel Corporation Core Processor QPI Link [8086:d150] (rev 11)
00:10.1 System peripheral [0880]: Intel Corporation Core Processor QPI Routing and Protocol Registers [8086:d151] (rev 11)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 06)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b0b] (rev 06)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b2f] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Madison [AMD Radeon HD 5000M Series] [1002:68c1]
02:00.1 Audio device [0403]: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series] [1002:aa60]
12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
13:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers [8086:2c52] (rev 04)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2c81] (rev 04)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2c90] (rev 04)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2c91] (rev 04)
ff:03.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller [8086:2c98] (rev 04)
ff:03.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder [8086:2c99] (rev 04)
ff:03.4 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Test Registers [8086:2c9c] (rev 04)
ff:04.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers [8086:2ca0] (rev 04)
ff:04.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers [8086:2ca1] (rev 04)
ff:04.2 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers [8086:2ca2] (rev 04)
ff:04.3 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers [8086:2ca3] (rev 04)
ff:05.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers [8086:2ca8] (rev 04)
ff:05.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers [8086:2ca9] (rev 04)
ff:05.2 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers [8086:2caa] (rev 04)
ff:05.3 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers [8086:2cab] (rev 04)

``````

cat /etc/network/interfaces 
RETURNS:
auto lo
iface lo inet loopback

``````

cat /etc/NetworkManager/NetworkManager.conf 
RETURNS:
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

``````

dmesg | grep -e eth0 -e bcm
RETURNS:
[    1.813632] r8169 0000:13:00.0: eth0: RTL8102e at 0xffffc9000065c000, f0:4d:a2:a2:f4:52, XID 04e00000 IRQ 50
[   21.920874] r8169 0000:13:00.0: eth0: link down
[   21.921203] ADDRCONF(NETDEV_UP): eth0: link is not ready

``````

sudo lshw -C Network
RETURNS:
  *-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:12:00.0
       logical name: wlan0
       version: 01
       serial: 1c:65:9d:79:73:e5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.0.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbd00000-fbd03fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: eth0
       version: 02
       serial: f0:4d:a2:a2:f4:52
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:50 ioport:d000(size=256) memory:d0c10000-d0c10fff memory:d0c00000-d0c0ffff memory:fb300000-fb31ffff

```Thanks

---

### Post by wildmanne39 on 2012-02-20
Hi, to start pleasee black list these drivers:```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
echo "blacklist brcmutil" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then unplug your wired connection and 
```
sudo modprobe wl
```
Thanks

---

### Post by dspi on 2012-02-20
Thanks wildmanne39,

I have blacklisted the drivers as you advised.

I then plugged in the wired connection, but it didn't connect.

I hope these **new** outputs can get us further:

```

lsmod | grep "b43\|ssb\|wl\|brc\|bcma"
RETURNS:
wl                   2568210  0 
lib80211               14991  2 lib80211_crypt_tkip,wl

``````

dmesg | grep -e eth0 -e bcm
RETURNS:
[    1.810732] r8169 0000:13:00.0: eth0: RTL8102e at 0xffffc9000064e000, f0:4d:a2:a2:f4:52, XID 04e00000 IRQ 51
[   12.013221] r8169 0000:13:00.0: eth0: link down
[   12.013617] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  193.951637] r8169 0000:13:00.0: eth0: link up
[  193.952403] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  194.035078] r8169 0000:13:00.0: eth0: link down
[  204.500291] eth0: no IPv6 routers present
[  208.553797] r8169 0000:13:00.0: eth0: link up
[  208.637234] r8169 0000:13:00.0: eth0: link down

```Does *eth0: link up* mean that we're getting somewhere?

Thanks

---

### Post by wildmanne39 on 2012-02-20
Hi dspi, I am working on getting your wireless to work first I do not know as much about wired connections, that is why I asked you to unplug your wired connection after you ran those commands so we could test your wireless connection. Please post the output of:
```
nm-tool
iwconfig
rfkill list all
sudo iwlist scan
ndiswrapper -l
lsmod
```
unplug your wired connection before running theses commandsw please.
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eth1 -e etork | tail -n75
```
Thanks

---

### Post by dspi on 2012-02-20
Here are the outputs:
 
```

nm-tool
RETURNS:
NetworkManager Tool
State: disconnected
- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        1C:65:9D:79:73:E5
  Capabilities:
  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes
  Wireless Access Points 
 
- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        F0:4D:A2:A2:F4:52
  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s
  Wired Properties
    Carrier:         off

```
 
 
```

iwconfig
RETURNS:
lo        no wireless extensions.
eth0      no wireless extensions.
eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:244
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```
 
 
```

rfkill list all
RETURNS:
0: brcmwl-0: Wireless LAN
 Soft blocked: no
 Hard blocked: no
1: dell-wifi: Wireless LAN
 Soft blocked: no
 Hard blocked: no
2: dell-bluetooth: Bluetooth
 Soft blocked: no
 Hard blocked: no
4: hci0: Bluetooth
 Soft blocked: no
 Hard blocked: no

```
 
 
```

sudo iwlist scan
RETURNS:
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
eth1      No scan results

```
 
 
```

ndiswrapper -l
RETURNS:
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common

```
Should I install this?...can I just download it and install it instead of using the software manager (since I can't connect to the internet in Ubuntu)?
 
 
```

lsmod
RETURNS:
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
usb_storage            57901  1 
uas                    18027  0 
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32040  1 
bnep                   18436  2 
rfcomm                 47946  8 
joydev                 17693  0 
binfmt_misc            17540  1 
btusb                  18600  2 
bluetooth             166112  23 bnep,rfcomm,btusb
snd_hda_codec_idt      70553  1 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_hda_intel          33390  3 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
dell_laptop            13831  0 
dcdbas                 14490  1 dell_laptop
lib80211_crypt_tkip    17390  0 
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
usbhid                 47198  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
hid                    95463  1 usbhid
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    19256  1 dell_wmi
radeon               1015995  3 
uvcvideo               72711  0 
video                  19412  0 
videodev               93004  1 uvcvideo
wl                   2568210  0 
v4l2_compat_ioctl32    17083  1 videodev
ttm                    76805  1 radeon
drm_kms_helper         42558  1 radeon
drm                   236330  5 radeon,ttm,drm_kms_helper
mei                    41480  0 
psmouse                73882  0 
serio_raw              13166  0 
i2c_algo_bit           13423  1 radeon
lib80211               14991  2 lib80211_crypt_tkip,wl
i7core_edac            27942  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
edac_core              53746  3 i7core_edac
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   26002  2 
libahci                26861  1 ahci
r8169                  52788  0 

```
 
 
```

sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eth1 -e etork | tail -n75
RETURNS:
Feb 20 13:58:04 Inspiron-N5010 NetworkManager[930]: <info> wpa_supplicant started
Feb 20 13:58:04 Inspiron-N5010 wpa_supplicant[1002]: nl80211: 'nl80211' generic netlink not found
Feb 20 13:58:04 Inspiron-N5010 NetworkManager[930]: <info> (eth1): supplicant interface state: starting -> ready
Feb 20 13:58:04 Inspiron-N5010 NetworkManager[930]: <info> (eth1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Feb 20 13:58:04 Inspiron-N5010 NetworkManager[930]: <info> (eth1): supplicant interface state: ready -> inactive
Feb 20 13:58:05 Inspiron-N5010 avahi-daemon[915]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::1e65:9dff:fe79:73e5.
Feb 20 13:58:05 Inspiron-N5010 avahi-daemon[915]: New relevant interface eth1.IPv6 for mDNS.
Feb 20 13:58:05 Inspiron-N5010 avahi-daemon[915]: Registering new address record for fe80::1e65:9dff:fe79:73e5 on eth1.*.
Feb 20 13:58:15 Inspiron-N5010 kernel: [   22.253327] eth1: no IPv6 routers present
Feb 20 14:01:21 Inspiron-N5010 NetworkManager[930]: <info> (eth1): device state change: disconnected -> unavailable (reason 'none') [30 20 0]
Feb 20 14:01:21 Inspiron-N5010 NetworkManager[930]: <info> (eth1): deactivating device (reason 'none') [0]
Feb 20 14:01:21 Inspiron-N5010 NetworkManager[930]: <info> (eth1): taking down device.
Feb 20 14:01:21 Inspiron-N5010 avahi-daemon[915]: Interface eth1.IPv6 no longer relevant for mDNS.
Feb 20 14:01:21 Inspiron-N5010 avahi-daemon[915]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::1e65:9dff:fe79:73e5.
Feb 20 14:01:21 Inspiron-N5010 avahi-daemon[915]: Withdrawing address record for fe80::1e65:9dff:fe79:73e5 on eth1.
Feb 20 14:12:43 Inspiron-N5010 NetworkManager[930]: <info> (eth1): bringing up device.
Feb 20 14:12:43 Inspiron-N5010 wpa_supplicant[1002]: nl80211: 'nl80211' generic netlink not found
Feb 20 14:12:43 Inspiron-N5010 NetworkManager[930]: <info> (eth1): supplicant interface state: starting -> ready
Feb 20 14:12:43 Inspiron-N5010 NetworkManager[930]: <info> (eth1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Feb 20 14:12:43 Inspiron-N5010 NetworkManager[930]: <info> (eth1): supplicant interface state: ready -> inactive
Feb 20 14:12:45 Inspiron-N5010 avahi-daemon[915]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::1e65:9dff:fe79:73e5.
Feb 20 14:12:45 Inspiron-N5010 avahi-daemon[915]: New relevant interface eth1.IPv6 for mDNS.
Feb 20 14:12:45 Inspiron-N5010 avahi-daemon[915]: Registering new address record for fe80::1e65:9dff:fe79:73e5 on eth1.*.
Feb 20 14:12:54 Inspiron-N5010 kernel: [  901.754296] eth1: no IPv6 routers present
Feb 20 22:56:42 Inspiron-N5010 kernel: [   10.635194] wl: module license 'MIXED/Proprietary' taints kernel.
Feb 20 22:56:42 Inspiron-N5010 kernel: [   10.642688] wl 0000:12:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 20 22:56:42 Inspiron-N5010 kernel: [   10.642703] wl 0000:12:00.0: setting latency timer to 64
Feb 20 22:56:42 Inspiron-N5010 kernel: [   10.807007] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.38
Feb 20 22:56:42 Inspiron-N5010 NetworkManager[902]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:12:00.0/net/eth1, iface: eth1)
Feb 20 22:56:42 Inspiron-N5010 NetworkManager[902]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:12:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Feb 20 22:56:42 Inspiron-N5010 NetworkManager[902]: <info> monitoring kernel firmware directory '/lib/firmware'.
Feb 20 22:56:42 Inspiron-N5010 NetworkManager[902]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:12:00.0/net/eth1/rfkill0) (driver (unknown))
Feb 20 22:56:42 Inspiron-N5010 NetworkManager[902]: <error> [1329771402.497510] [nm-device-wifi.c:3081] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
Feb 20 22:56:42 Inspiron-N5010 NetworkManager[902]: <info> (eth1): driver supports SSID scans (scan_capa 0x01).
Feb 20 22:56:42 Inspiron-N5010 NetworkManager[902]: <info> (eth1): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
Feb 20 22:56:42 Inspiron-N5010 NetworkManager[902]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Feb 20 22:56:42 Inspiron-N5010 NetworkManager[902]: <info> (eth1): now managed
Feb 20 22:56:42 Inspiron-N5010 NetworkManager[902]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb 20 22:56:42 Inspiron-N5010 NetworkManager[902]: <info> (eth1): bringing up device.
Feb 20 22:56:42 Inspiron-N5010 NetworkManager[902]: <info> (eth1): preparing device.
Feb 20 22:56:42 Inspiron-N5010 NetworkManager[902]: <info> (eth1): deactivating device (reason 'managed') [2]
Feb 20 22:56:42 Inspiron-N5010 dbus[887]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Feb 20 22:56:42 Inspiron-N5010 dbus[887]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Feb 20 22:56:42 Inspiron-N5010 NetworkManager[902]: <info> wpa_supplicant started
Feb 20 22:56:42 Inspiron-N5010 wpa_supplicant[922]: nl80211: 'nl80211' generic netlink not found
Feb 20 22:56:42 Inspiron-N5010 NetworkManager[902]: <info> (eth1): supplicant interface state: starting -> ready
Feb 20 22:56:42 Inspiron-N5010 NetworkManager[902]: <info> (eth1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Feb 20 22:56:42 Inspiron-N5010 NetworkManager[902]: <info> (eth1): supplicant interface state: ready -> inactive
Feb 20 22:56:44 Inspiron-N5010 avahi-daemon[898]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::1e65:9dff:fe79:73e5.
Feb 20 22:56:44 Inspiron-N5010 avahi-daemon[898]: New relevant interface eth1.IPv6 for mDNS.
Feb 20 22:56:44 Inspiron-N5010 avahi-daemon[898]: Registering new address record for fe80::1e65:9dff:fe79:73e5 on eth1.*.
Feb 20 22:56:53 Inspiron-N5010 kernel: [   22.317382] eth1: no IPv6 routers present
Feb 20 22:57:12 Inspiron-N5010 NetworkManager[902]: <info> (eth1): now unmanaged
Feb 20 22:57:12 Inspiron-N5010 NetworkManager[902]: <info> (eth1): device state change: disconnected -> unmanaged (reason 'sleeping') [30 10 37]
Feb 20 22:57:12 Inspiron-N5010 NetworkManager[902]: <info> (eth1): cleaning up...
Feb 20 22:57:12 Inspiron-N5010 NetworkManager[902]: <info> (eth1): taking down device.
Feb 20 22:57:12 Inspiron-N5010 avahi-daemon[898]: Interface eth1.IPv6 no longer relevant for mDNS.
Feb 20 22:57:12 Inspiron-N5010 avahi-daemon[898]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::1e65:9dff:fe79:73e5.
Feb 20 22:57:12 Inspiron-N5010 avahi-daemon[898]: Withdrawing address record for fe80::1e65:9dff:fe79:73e5 on eth1.
Feb 20 23:18:40 Inspiron-N5010 kernel: [   44.605092] wl 0000:12:00.0: PCI INT A disabled
Feb 20 23:18:40 Inspiron-N5010 kernel: [   46.610308] wl 0000:12:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 20 23:18:40 Inspiron-N5010 kernel: [   46.610331] wl 0000:12:00.0: setting latency timer to 64
Feb 20 23:18:40 Inspiron-N5010 NetworkManager[902]: <info> (eth1): now managed
Feb 20 23:18:40 Inspiron-N5010 NetworkManager[902]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb 20 23:18:40 Inspiron-N5010 NetworkManager[902]: <info> (eth1): bringing up device.
Feb 20 23:18:40 Inspiron-N5010 NetworkManager[902]: <info> (eth1): preparing device.
Feb 20 23:18:40 Inspiron-N5010 NetworkManager[902]: <info> (eth1): deactivating device (reason 'managed') [2]
Feb 20 23:18:40 Inspiron-N5010 wpa_supplicant[922]: nl80211: 'nl80211' generic netlink not found
Feb 20 23:18:41 Inspiron-N5010 NetworkManager[902]: <info> (eth1): supplicant interface state: starting -> ready
Feb 20 23:18:41 Inspiron-N5010 NetworkManager[902]: <info> (eth1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Feb 20 23:18:41 Inspiron-N5010 NetworkManager[902]: <info> (eth1): supplicant interface state: ready -> inactive
Feb 20 23:18:42 Inspiron-N5010 avahi-daemon[898]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::1e65:9dff:fe79:73e5.
Feb 20 23:18:42 Inspiron-N5010 avahi-daemon[898]: New relevant interface eth1.IPv6 for mDNS.
Feb 20 23:18:42 Inspiron-N5010 avahi-daemon[898]: Registering new address record for fe80::1e65:9dff:fe79:73e5 on eth1.*.
Feb 20 23:18:51 Inspiron-N5010 kernel: [   59.922458] eth1: no IPv6 routers present

```

---

### Post by ratcheer on 2012-02-20
For the wired connection, go look at the Realtek website and see if they have a better driver for your card/chipset. If they do, I will help you get it installed. The default driver r8169 causes those sort of problems for many users.

[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

Tim

---

### Post by ratcheer on 2012-02-20
Here is a driver for your ethernet card:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=7&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8100E/RTL8101E/RTL8102E-GR/RTL8103E%28L%29%3Cbr%3ERTL8102E%28L%29/RTL8101E/RTL8103T%3Cbr%3ERTL8401/RTL8401P/RTL8105E%3Cbr%3ERTL8402](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=7&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8100E/RTL8101E/RTL8102E-GR/RTL8103E%28L%29%3Cbr%3ERTL8102E%28L%29/RTL8101E/RTL8103T%3Cbr%3ERTL8401/RTL8401P/RTL8105E%3Cbr%3ERTL8402)

---

### Post by dspi on 2012-02-20
Thanks for the link ratcheer.
 
None of the *Unix (Linux)* drivers specify Ubuntu.
Can I use the one labeled *LINUX driver for kernel 2.6.X and 2.4.X (Support x86 and x64)*?
 
Do I just install it?
(I can't check for dependencies, obviously)

---

### Post by ratcheer on 2012-02-20
Well, you might have to make a minor edit to the make file to allow it to compile for 3.0. But, it worked for me as long as I needed to use it.

The installation is not Ubuntu-like. You have to compile and install the module into the kernel. Like I said, I'll help you if you want to try it.

Also, there is a possibility that you could find the driver in some PPA and install it, Ubuntu style.

Tim

---

### Post by wildmanne39 on 2012-02-20
Hi, no do not install ndiswrapper, I was just making sure it was not installed.

Please do:
```
sudo ifconfig eth1 down
sudo iwconfig eth1 mode Managed
sudo ifconfig eth1 up
```
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
and remove ```
blacklist brcmutil
```
then save, close gedit and reboot.
Thanks

---

### Post by dspi on 2012-02-21
Ok,  I've followed those instructions (wildmanne39's).  Still no joy.  What should I do now?

Thanks

---

### Post by dspi on 2012-02-21
> **ratcheer said:**
> Well, you might have to make a minor edit to  the make file to allow it to compile for 3.0. But, it worked for me as  long as I needed to use it.

The installation is not Ubuntu-like. You have to compile and install the  module into the kernel. Like I said, I'll help you if you want to try  it.

Also, there is a possibility that you could find the driver in some PPA and install it, Ubuntu style.

Tim

Ok, ratcheer,  lets try it.

I've now downloaded the driver labeled[I] LINUX driver for kernel 2.6.X and 2.4.X (Support x86 and x64)
[/I]How do I compile and install.

Thanks

---

### Post by roelforg on 2012-02-21
Try this:
determine which eth is wired, (i'd guess eth0)
Issue this (replace <eth> with the name from your wired nic):
```

sudo bash
/etc/init.d/networking restart
ifdown <eth>
ifup <eth>
dhclient <eth>

```
 
Works 60% of the time.
Resets net, reboots <eth> and then issues a dhcp update

---

### Post by ratcheer on 2012-02-21
> **dspi said:**
> Ok, ratcheer,  lets try it.

I've now downloaded the driver labeled[I] LINUX driver for kernel 2.6.X and 2.4.X (Support x86 and x64)
[/I]How do I compile and install.

Thanks

Ok, first make sure it is the right driver. Is it r8168 version 8.027?

Make sure you have packages build-essential and linux-headers-<your kernel version> installed on your system.

If so, cd to the r8168-8.027.00 directory and run "sudo ./autorun.sh"

If that fails because of the kernel version, we will have to edit one of the makefiles.

If it succeeds, do the following set of procedures:

sudo depmod -a

Edit file /etc/modprobe.d/blacklist.conf. Add a line that says "blacklist r8169" (no quote marks)

Edit file /etc/initramfs-tools/modules. Add a line that says "r8168"

Run: sudo update-initramfs -v -u -k `uname -r`
Note that in the above line, those are NOT single-quote marks, they are grave accents.

Reboot. When the system is back up, run "sudo lspci -v". Inspect the section for your ethernet card. It should show "Module in use: r8168". And you should be able to connect via ethernet.

Tim

---

### Post by wildmanne39 on 2012-02-21
Hi, please post the output of:
```
sudo iwlist scan
cat /etc/modprobe.d/blacklist.conf
```
Thanks

---

### Post by dspi on 2012-02-21
Ok:
 
```

sudo iwlist scan
RETURNS:
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
eth1      No scan results

```
 
```

cat /etc/modprobe.d/blacklist.conf
RETURNS:
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.
# evbug is a debug tool that should be loaded explicitly
blacklist evbug
# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd
# replaced by e100
blacklist eepro100
# replaced by tulip
blacklist de4x5
# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394
# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m
# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2
# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps
# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi
# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp
# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr
# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
#Blacklisting drivers as per ubuntuforums.org/showthread.php?t=1928017 #2
blacklist bcma
blacklist brcmsmac

```
 
Thanks

---

### Post by wildmanne39 on 2012-02-21
Hi, I think the problem is that we need to run updates then reinstall the sta driver for your wireless, do you have another way of connecting to the internet like tethering with your cell phone? 

If not you can follow these directions for doing it with no internet but many people have trouble getting it to work that way.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
Thanks

---

### Post by dspi on 2012-02-22
> **ratcheer said:**
> Ok, first make sure it is the right driver. Is it r8168 version 8.027?

Make sure you have packages build-essential and linux-headers-<your kernel version> installed on your system.

If so, cd to the r8168-8.027.00 directory and run "sudo ./autorun.sh"

If that fails because of the kernel version, we will have to edit one of the makefiles.

If it succeeds, do the following set of procedures:

sudo depmod -a

Edit file /etc/modprobe.d/blacklist.conf. Add a line that says "blacklist r8169" (no quote marks)

Edit file /etc/initramfs-tools/modules. Add a line that says "r8168"

Run: sudo update-initramfs -v -u -k `uname -r`
Note that in the above line, those are NOT single-quote marks, they are grave accents.

Reboot. When the system is back up, run "sudo lspci -v". Inspect the section for your ethernet card. It should show "Module in use: r8168". And you should be able to connect via ethernet.

Tim


I have downloaded version *r8168-8.028.00*.
*linux-headers-3.0.0-12* is installed, however *build-essential *is not.
I suppose this is also complex to install without an internet connection, because of the dependencies?

---

### Post by ratcheer on 2012-02-22
Version [I]r8168-8.028.00 will be great. I didn't know it existed, but like I said earlier, for some reason r8169 has started working on my system. So, I'm not having to do all this, anymore.

And yes, you must have build-essential installed to compile it. So, since you have no internet connectivity, perhaps you can download a .deb of build-essential on another machine, move it to your machine by sneaker net, and install it with "sudo dpkg -i".

Tim
[/I]

---

### Post by ratcheer on 2012-02-22
> **ratcheer said:**
> Version [I]r8168-8.028.00 will be great. I didn't know it existed, but like I said earlier, for some reason r8169 has started working on my system. So, I'm not having to do all this, anymore.

[/I]

Wow, this is weird. I was syrfing happily using driver r8169 about 30 minutes ago. Then it just quit. I thought it was the router, so I unplugged it and plugged it back up. Still no go with the wired connection. I turned on wireless and was able to connect, again.

So, I also installed [I]r8168-8.028.00, and my wired connection works, again.

Tim
[/I]

---

### Post by ratcheer on 2012-02-22
FYI - When I reinstalled with this latest script, I did not have to do all the stuff beginning with "sudo depmod -a". The script handled everything. My ethernet connection came up without even rebooting.

Also, no make file editing was needed. I am on kernel 3.0.0-16, and the script ran without a hitch, as is.

Tim

---

### Post by dspi on 2012-03-21
Thanks everyone for your help and suggestions.
I've not posted for a while, since I had not tried anything further...was just booting into Windows.

I had the idea to buy a USB Wifi adaptor, and just bypass the internal one, but never got round to it.

However, I've recently moved to a new apartment, and got a new modem/wireless router.  By chance, I booted into Ubuntu today.  I then saw my wireless network, typed in the password, and it works!!!

So, although my problem is solved, I'd desperately like to know how this can be.
Since I didn't make changes to the software, it must be external to this computer.
(Also, it seems that the wired connection still doesn't work.)

Thanks

---

### Post by wildmanne39 on 2012-03-21
Hi, some routers work better with linux then others but it is possible that there is a setting different in your router then in the other one.
Thanks

---

