---
title: "Arg! networking  problems"
date: 2005-12-03
forum: Desktop Environments
---

### Post by ShortE on 2005-12-03
Hey all,

This is my first time useing linux at all, so bear that in mind.  I'm trying to hook up to my own network, but I can't seem to use the internet, even when I appear to be connected.  My router is set to channel 6, my network is named "forest" and there is no wep on it at the moment, although it appears in the network manager with a key over it.  Here are some diagnostic thingys I have done in my bumbling n00b fashion, but I can't interprit them and any advice would be very helpful:

abbi@Gump:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"WLAN"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:30:BD:C2:D3:6A
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=32/100  Signal level=-79 dBm  Noise level=-79 dBm
          Rx invalid nwid:76251  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:66  Invalid misc:281475   Missed beacon:32

eth0      IEEE 802.11-DS  ESSID:"WLAN"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:30:BD:C2:D3:6A
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=32/100  Signal level=-79 dBm  Noise level=-79 dBm
          Rx invalid nwid:76251  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:66  Invalid misc:281475   Missed beacon:32

sit0      no wireless extensions.

abbi@Gump:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
abbi@Gump:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"forest"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:E0:98:C8:15:78
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-41 dBm  Noise level=-90 dBm
          Rx invalid nwid:79042  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:79  Invalid misc:284911   Missed beacon:37

eth0      IEEE 802.11-DS  ESSID:"forest"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:E0:98:C8:15:78
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-41 dBm  Noise level=-90 dBm
          Rx invalid nwid:79043  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:79  Invalid misc:284912   Missed beacon:37

sit0      no wireless extensions.

abbi@Gump:~$ dhclient eth 0
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
eth0: unknown hardware address type 801
can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted
abbi@Gump:~$ sudo dhclient eth0
Password:
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
eth0: unknown hardware address type 801
sit0: unknown hardware address type 776
eth0: unknown hardware address type 801
Listening on LPF/eth0/
Sending on   LPF/eth0/
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
abbi@Gump:~$ sudo iwlis eth0 scan
sudo: iwlis: command not found
abbi@Gump:~$ sudo iwlist eth0 scan
eth0      Scan completed :
          Cell 01 - Address: 00:12:0E:01:0F:9E
                    ESSID:"05B406889322"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality:34/100  Signal level=-78 dBm  Noise level=-85 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:22 Mb/s
          Cell 02 - Address: 00:13:10:54:F8:5E
                    ESSID:"Silverwork"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality:17/100  Signal level=-87 dBm  Noise level=-85 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:54 Mb/s
          Cell 03 - Address: 00:0F:3D:4E:DD:06
                    ESSID:"SD_net"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality:14/100  Signal level=-89 dBm  Noise level=-85 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
          Cell 04 - Address: 00:13:46:0B:AB:00
                    ESSID:"default"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality:5/100  Signal level=-90 dBm  Noise level=-85 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
          Cell 05 - Address: 00:90:4B:DB:E0:2B
                    ESSID:"HotSteamingTurd"
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality:28/100  Signal level=-81 dBm  Noise level=-85 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
          Cell 06 - Address: 00:30:BD:F0:9E:46
                    ESSID:"belkin54g"
                    Mode:Master
                    Frequency:2.467 GHz (Channel 12)
                    Quality:15/100  Signal level=-88 dBm  Noise level=-85 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:54 Mb/s
          Cell 07 - Address: 00:30:BD:C2:D3:6A
                    ESSID:"WLAN"
                    Mode:Master
                    Frequency:2.467 GHz (Channel 12)
                    Quality:14/100  Signal level=-89 dBm  Noise level=-85 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
          Cell 08 - Address: 00:E0:98:C8:15:78
                    ESSID:"forest"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality:100/100  Signal level=-42 dBm  Noise level=-85 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:22 Mb/s

abbi@Gump:~$ sudo iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"forest"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:E0:98:C8:15:78
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=100/100  Signal level=-42 dBm  Noise level=-91 dBm
          Rx invalid nwid:90469  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:91  Invalid misc:295148   Missed beacon:37

eth0      IEEE 802.11-DS  ESSID:"forest"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:E0:98:C8:15:78
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=100/100  Signal level=-42 dBm  Noise level=-91 dBm
          Rx invalid nwid:90473  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:91  Invalid misc:295154   Missed beacon:37

sit0      no wireless extensions.

abbi@Gump:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8601 [Apollo ProMedia] (rev 05)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8601 [Apollo ProMedia AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
0000:00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
0000:00:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)
0000:00:0b.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
0000:01:00.0 VGA compatible controller: Trident Microsystems CyberBlade i1 (rev 6a)
abbi@Gump:~$ lsusb -v

Bus 001 Device 002: ID 0930:6533 Toshiba Corp. 512M USB Stick
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0930 Toshiba Corp.
  idProduct          0x6533 512M USB Stick
  bcdDevice            1.00
  iManufacturer           1
  iProduct                2
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval             255
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval             255
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted

Bus 001 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3
  iProduct                2
  iSerial                 1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
abbi@Gump:~$ sudo lshw -C network
  *-network
       description: Cisco Systems
       physical id: 0
       version: 350 Series Wireless LAN Adapter
       slot: Socket 0
       resources: irq:3
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:07:0e:b9:9c:85
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS
abbi@Gump:~$

---

### Post by Ampersand on 2005-12-03
Can you ping your router? Other things worth checking if you haven't already are the settings in System - Administration - Networking from the gnome menu. Make sure that the DNS settings are correct, and that the correct interface is set as the default &c. Is the network meant to be in managed or ad-hoc mode?

---

### Post by arpunk on 2005-12-03
Thats probably a misconfiguration in your dns, try pinging your router ip and other clients connected on the network, if you can ping them, then its your dns settings, re-check them on *System*, *Administration*, *Networking* menu.

---

