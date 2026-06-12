---
title: "Wireless internet slow speed"
date: 2011-02-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by naglis on 2011-02-21
Hi, I'm having problems with my wireless internet speed on Dell Latitude E6500. I get up to 2 MB/s on Windows 7, but on Ubuntu it's somewhere ~120 kB/s. I've searched through the forum and found that others solved this problem by running:
```
sudo iwconfig wlan0 rate 54M
```
But in my case it goes up to 2 MB/s for max. 5 minutes and then goes back to the "normal" 120 and then it also starts to reconnect every now and then, thus making it really annoying.

Adding
```
iwconfig wlan0 rate 54M
```
to **/etc/rc.local**, as one would expect, gives the same results.

To make thins more specific, this is my configuration:
**cat /etc/lsb-release**
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
```

**lspci -nn | grep -i net**
```

00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
0c:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
```

**sudo lshw -C network**
```

  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:fa:75:5a
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 firmware=1.7-7 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f6ae0000-f6afffff memory:f6adb000-f6adbfff ioport:efe0(size=32)
  *-network
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 00
       serial: 00:24:d6:69:12:98
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-25-generic firmware=8.24.2.12 ip=192.168.1.81 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:47 memory:f69fe000-f69fffff
```

**lsmod**
```

Module                  Size  Used by
iwlagn                178948  0 
iwlcore               127415  1 iwlagn
mac80211              231959  2 iwlagn,iwlcore
cfg80211              144694  3 iwlagn,iwlcore,mac80211
ndiswrapper           184207  0 
isofs                  30022  1 
aes_i586                7280  187 
aes_generic            26875  1 aes_i586
rfcomm                 33811  4 
binfmt_misc             6599  1 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  16 rfcomm,bnep
parport_pc             26058  0 
ppdev                   5556  0 
dm_crypt               11385  0 
joydev                  8767  0 
btusb                  10969  2 
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
arc4                    1165  2 
snd_hda_codec_intelhdmi     9812  1 
snd_hda_codec_idt      54919  1 
snd_hda_intel          22203  4 
snd_hda_codec          87552  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  3 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 35973  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi_aio            1733  0 
uvcvideo               55847  0 
dell_wmi                2852  0 
snd                    49038  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
dell_laptop             5730  0 
dcdbas                  5402  1 dell_laptop
yenta_socket           21518  0 
pcmcia_rsrc            10566  1 yenta_socket
psmouse                59033  0 
serio_raw               4022  0 
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
i915                  295243  3 
drm_kms_helper         30200  1 i915
drm                   168092  3 i915,drm_kms_helper
usbhid                 36882  0 
hid                    67742  1 usbhid
firewire_ohci          21234  0 
intel_agp              26566  2 i915
ahci                   19198  3 
sdhci_pci               6339  0 
sdhci                  15890  1 sdhci_pci
e1000e                132956  0 
led_class               2633  1 sdhci
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
agpgart                32011  2 drm,intel_agp
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
output                  1883  1 video
libahci                21728  1 ahci
```

**iwconfig**
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"namuciai"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:22:33:34:71:9E   
          Bit Rate=12 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

**ifconfig**
```

eth0      Link encap:Ethernet  HWaddr 00:24:e8:fa:75:5a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Memory:f6ae0000-f6b00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:773 errors:0 dropped:0 overruns:0 frame:0
          TX packets:773 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:77056 (77.0 KB)  TX bytes:77056 (77.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:d6:69:12:98  
          inet addr:192.168.1.81  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:d6ff:fe69:1298/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:508638 errors:0 dropped:0 overruns:0 frame:0
          TX packets:413924 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:586250226 (586.2 MB)  TX bytes:219915991 (219.9 MB)
```

**sudo iwlist scan**
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 02 - Address: 00:22:33:34:71:9E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"namuciai"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006132b3c8c6
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 00086E616D7563696169
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
```

**uname -r -m **
```

2.6.35-25-generic i686
```

**cat  /etc/network/interfaces**
```

auto lo
iface lo inet loopback
```

**nm-tool**
```

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        00:24:E8:FA:75:5A

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto namuciai] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             connected
  Default:           yes
  HW Address:        00:24:D6:69:12:98

  Capabilities:
    Speed:           12 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    petrsat:         Infra, 00:1D:7E:C6:B5:83, Freq 2462 MHz, Rate 54 Mb/s, Strength 31 WEP
    PKC:             Infra, 00:C0:CA:35:30:4C, Freq 2447 MHz, Rate 54 Mb/s, Strength 44 WPA2
    ZEBRA:           Infra, 00:13:21:57:D6:DD, Freq 2447 MHz, Rate 11 Mb/s, Strength 38
    Radius-6:        Infra, 00:18:39:F7:A1:B9, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA2
    BIBLIA_AX_AP:    Infra, 00:40:96:5A:DC:CA, Freq 2457 MHz, Rate 11 Mb/s, Strength 38
    *namuciai:       Infra, 00:22:33:34:71:9E, Freq 2462 MHz, Rate 54 Mb/s, Strength 70 WPA
    gwgnamai:        Infra, 00:16:E6:30:72:2F, Freq 2417 MHz, Rate 54 Mb/s, Strength 60 WEP
    namai_:          Infra, 00:22:B0:4B:63:81, Freq 2422 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.81
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254
```

Thanks for any help

---

### Post by naglis on 2011-03-11
anyone?

---

### Post by naglis on 2011-05-18
Seems to have been solved in natty. Hadn't had a problem whatsoever.

---

