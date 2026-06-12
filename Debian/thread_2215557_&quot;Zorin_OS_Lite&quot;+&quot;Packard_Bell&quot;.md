---
title: "&quot;Zorin OS Lite&quot;+&quot;Packard Bell&quot;+&quot;Wireless 3945ABG&quot;=&quot;No Wifi&quot; (Help?)"
date: 2014-04-07
forum: Debian
---

### Post by angelpear on 2014-04-07
Hello. 

First of all, sorry for my English. It's very basic. 

I am a new linux user and I have problems with the wifi on a laptop. 

The laptop is a Packard Bell Easy Note MX. I installed "Zorin OS Lite 6.2". Everything works fine except the wifi. 

My network card is a "Intel PRO / Wireless 3945ABG [Golan]" 

At first, I was able to detect wifi networks. I put the key and was trying to connect. Every 30 seconds the pc back to ask me the wifi password. Never connected. 

I've tried on several different networks. Always the same. I started reading forums and I started putting commands in the Terminal. Nothing worked and now not even detected wifi networks. I can only use the wired connection. 

I've seen you ask for certain information to solve well. I put what comes out of the commands you are asking.


nm-tool
```
NetworkManager Tool

State: connected (global)

- Device: eth0  [Conexión cableada 1] -----------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        00:18:F3:33:74:DE

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.201
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             unavailable
  Default:           no
  HW Address:        00:13:02:9B:A0:2E

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

```

iwconfig
```
lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Frequency:2.447 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

```

rfkill list all
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

sudo iwlist scan
```
lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

eth0      Interface doesn't support scanning.


```

lsmod | grep iwl
```
iwl3945                73145  0 
iwl_legacy             71334  1 iwl3945
mac80211              436493  2 iwl3945,iwl_legacy
cfg80211              178877  3 iwl3945,iwl_legacy,mac80211
```

sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan -e wpa -e etwork | tail -n55
```
Apr  7 12:28:04 PackardBell-T12J NetworkManager[936]: <info> WiFi hardware radio set enabled
Apr  7 12:28:04 PackardBell-T12J NetworkManager[936]: <info> WiFi now enabled by radio killswitch
Apr  7 12:28:04 PackardBell-T12J NetworkManager[936]: <info> (wlan0): bringing up device.
Apr  7 12:28:04 PackardBell-T12J kernel: [  151.862291] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  7 12:28:04 PackardBell-T12J wpa_supplicant[1740]: ctrl_iface exists and seems to be in use - cannot override it
Apr  7 12:28:04 PackardBell-T12J wpa_supplicant[1740]: Delete '/var/run/wpa_supplicant/wlan0' manually if it is not used anymore
Apr  7 12:28:04 PackardBell-T12J wpa_supplicant[1740]: Failed to initialize control interface '/var/run/wpa_supplicant'.#012You may have another wpa_supplicant process already running or the file was#012left by an unclean termination of wpa_supplicant in which case you will need#012to manually remove this file before starting wpa_supplicant again.
Apr  7 12:28:04 PackardBell-T12J NetworkManager[936]: <error> [1396866484.531272] [nm-supplicant-interface.c:804] interface_add_cb(): (wlan0): error adding interface: wpa_supplicant couldn't grab this interface.
Apr  7 12:28:04 PackardBell-T12J NetworkManager[936]: dbus_g_proxy_cancel_call: assertion `pending != NULL' failed
Apr  7 12:28:04 PackardBell-T12J NetworkManager[936]: <info> (wlan0): supplicant interface state: starting -> down
Apr  7 12:28:04 PackardBell-T12J NetworkManager[936]: <warn> Trying to remove a non-existant call id.
Apr  7 12:28:06 PackardBell-T12J kernel: [  154.118533] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  7 12:28:06 PackardBell-T12J dhclient: Listening on LPF/wlan0/00:13:02:9b:a0:2e
Apr  7 12:28:06 PackardBell-T12J dhclient: Sending on   LPF/wlan0/00:13:02:9b:a0:2e
Apr  7 12:28:06 PackardBell-T12J kernel: [  154.306424] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  7 12:28:06 PackardBell-T12J kernel: [  154.306495] wlan0: direct probe to 72:7d:5e:7d:8c:38 (try 1/3)
Apr  7 12:29:23 PackardBell-T12J NetworkManager[936]: <info> (eth0): carrier now ON (device state 20)
Apr  7 12:29:23 PackardBell-T12J NetworkManager[936]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Apr  7 12:29:23 PackardBell-T12J NetworkManager[936]: <info> Auto-activating connection 'Conexión cableada 1'.
Apr  7 12:29:23 PackardBell-T12J NetworkManager[936]: <info> Activation (eth0) starting connection 'Conexión cableada 1'
Apr  7 12:29:23 PackardBell-T12J NetworkManager[936]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr  7 12:29:23 PackardBell-T12J NetworkManager[936]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr  7 12:29:23 PackardBell-T12J NetworkManager[936]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr  7 12:29:23 PackardBell-T12J NetworkManager[936]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr  7 12:29:23 PackardBell-T12J NetworkManager[936]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr  7 12:29:23 PackardBell-T12J NetworkManager[936]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr  7 12:29:23 PackardBell-T12J NetworkManager[936]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr  7 12:29:23 PackardBell-T12J NetworkManager[936]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr  7 12:29:23 PackardBell-T12J NetworkManager[936]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr  7 12:29:23 PackardBell-T12J NetworkManager[936]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr  7 12:29:23 PackardBell-T12J NetworkManager[936]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr  7 12:29:23 PackardBell-T12J NetworkManager[936]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr  7 12:29:23 PackardBell-T12J NetworkManager[936]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr  7 12:29:23 PackardBell-T12J NetworkManager[936]: <info> dhclient started with pid 2056
Apr  7 12:29:23 PackardBell-T12J NetworkManager[936]: <info> Activation (eth0) Beginning IP6 addrconf.
Apr  7 12:29:23 PackardBell-T12J NetworkManager[936]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr  7 12:29:23 PackardBell-T12J NetworkManager[936]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Apr  7 12:29:26 PackardBell-T12J NetworkManager[936]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Apr  7 12:29:26 PackardBell-T12J NetworkManager[936]: <info>   address 192.168.0.201
Apr  7 12:29:26 PackardBell-T12J NetworkManager[936]: <info>   prefix 24 (255.255.255.0)
Apr  7 12:29:26 PackardBell-T12J NetworkManager[936]: <info>   gateway 192.168.0.1
Apr  7 12:29:26 PackardBell-T12J NetworkManager[936]: <info>   nameserver '192.168.0.1'
Apr  7 12:29:26 PackardBell-T12J NetworkManager[936]: <info>   nameserver '192.168.0.1'
Apr  7 12:29:26 PackardBell-T12J NetworkManager[936]: <info>   domain name 'localdomain'
Apr  7 12:29:26 PackardBell-T12J NetworkManager[936]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr  7 12:29:26 PackardBell-T12J NetworkManager[936]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Apr  7 12:29:27 PackardBell-T12J NetworkManager[936]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Apr  7 12:29:27 PackardBell-T12J NetworkManager[936]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Apr  7 12:29:27 PackardBell-T12J NetworkManager[936]: <info> Policy set 'Conexión cableada 1' (eth0) as default for IPv4 routing and DNS.
Apr  7 12:29:27 PackardBell-T12J NetworkManager[936]: <info> Activation (eth0) successful, device activated.
Apr  7 12:29:27 PackardBell-T12J NetworkManager[936]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Apr  7 12:29:43 PackardBell-T12J NetworkManager[936]: <info> (eth0): IP6 addrconf timed out or failed.
Apr  7 12:29:43 PackardBell-T12J NetworkManager[936]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr  7 12:29:43 PackardBell-T12J NetworkManager[936]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr  7 12:29:43 PackardBell-T12J NetworkManager[936]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
```

I hope I have put it all clear. Thank you so much.

---

### Post by varunendra on 2014-04-10
Welcome to Ubuntu Forums angelpear !

Please try these -
```
sudo modprobe -rv iwl3945
sudo modprobe -v iwl_legacy bt_coex_active=N
sudo modprobe -v iwl3945 swcrypto=1
```
This will reload the drivers with some parameters that may sometimes help. The changes are temporary and will be lost at next boot or after a driver reload cycle. If they help, we can make them permanent. If they don't, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by angelpear on 2014-04-11
Hello. 
Great, it worked the first try! 
I put the script and I could connect the wifi with no problems. (Right now I'm writing using the wifi) 
Thank you very much. 
How can we make these settings permanent?

---

### Post by varunendra on 2014-04-11
> **angelpear said:**
> How can we make these settings permanent?

To make them permanent, we have to create a couple of .conf files in /etc/modprobe.d directory with desired driver parameters. The following commands will create the files with required parameters -
```
echo "options iwl_legacy bt_coex_active=N" | sudo tee /etc/modprobe.d/iwl_legacy.conf
echo "options iwl3945 swcrypto=1" | sudo tee /etc/modprobe.d/iwl3945.conf
```

Please note that you may actually need only one of these files (in other words, only one of the driver parameters). I suggest you try the second one above alone first. If it solves the problem, you don't need the first one.

---

### Post by angelpear on 2014-04-17
Thank you very much. 

First I tried the second line. But did not work.
I tried with the two lines. Connects well to start. But only for a few starts. If I turn off and turn on 4 or 5 times it fails again. If I write all

sudo modprobe -rv iwl3945
sudo modprobe -v iwl_legacy bt_coex_active=N
sudo modprobe -v iwl3945 swcrypto=1&#65279;
echo "options iwl_legacy bt_coex_active=N" | sudo tee /etc/modprobe.d/iwl_legacy.conf
echo "options iwl3945 swcrypto=1" | sudo tee /etc/modprobe.d/iwl3945.conf

I have everything right for another few starts. Is there any way to make it permanent?

Thank you so much.

---

### Post by varunendra on 2014-04-18
> **angelpear said:**
> ..If I write all

[B][COLOR="#800000"]sudo modprobe -rv iwl3945
sudo modprobe -v iwl_legacy bt_coex_active=N
sudo modprobe -v iwl3945 swcrypto=1&#65279;[/COLOR]
[COLOR="#0000CD"]echo "options iwl_legacy bt_coex_active=N" | sudo tee /etc/modprobe.d/iwl_legacy.conf
echo "options iwl3945 swcrypto=1" | sudo tee /etc/modprobe.d/iwl3945.conf[/COLOR][/B]

I have everything right for another few starts. Is there any way to make it permanent?

Of the highlighted parts (commands) above, whatever the **[COLOR="#800000"]first three[/COLOR]** do is made permanent by the **[COLOR="#0000CD"]last two[/COLOR]**. There should be no need to run the first three commands since the files created by the last two commands already do (at startup) what is done by them manually.

When the problem occurs again, please check the output of -
```
iwconfig
```
Does "Power Management" appear to be "off"? If it appears to be "on", try this -
```
sudo iwconfig wlan0 off
```

If the power management is already off, or if turning it on doesn't help, please post the 'wireless_script' report as I asked in post #2. Run the script when the wifi is working so that it can also show the router's signal type and quality.

---

### Post by howefield on 2014-04-18
Thread moved to the "*Other OS/Distro Support*" forum.

---

### Post by angelpear on 2014-04-19
Hello. 

Today I tried to restart and "turn on / off" several times. Everything seems it works. 

It is also true that I have updated the entire system. And I installed new icons and anything else. I think it looks good on updated. 

Next week I'll try it for a few days. If all goes well we can give it as solved. 

With the wifi working this is what I have:

wireless_script
```
########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux PackardBell-T12J 3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:55:18 UTC 2014 i686 i686 i386 GNU/Linux

##### lspci #####

03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:1001]
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945

06:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Packard Bell B.V. Device [1631:c022]
    Kernel driver in use: 8139too

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 174f:a821 Syntek Web Cam - Packard Bell BU45, PB Easynote MX66-208W

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11abg  ESSID:"vodafone8C3A"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0

##### route #####

Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

##### resolv.conf #####

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [vodafone8C3A] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *vodafone8C3A:   Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 71 WPA
    WLAN_7A78:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA
    WLAN_42:         Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 39 WEP
    WLAN_6D8E:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA

  IPv4 Settings:
    Address:         192.168.0.202
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"vodafone8C3A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000026b673016a
                    Extra: Last beacon: 444ms ago
                    IE: Unknown: 000C766F6461666F6E6538433341
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A8E1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1609000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DDA20050F204104A0001101044000102103B00010310470010BC329E001DD811B28601727D5E7D8C381021001D48756177656920546563686E6F6C6F6769657320436F2E2C204C74642E1023001C48756177656920576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F204000110110009487561776569415053100800020084103C000100
                    IE: Unknown: 0B05040004127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706455320010D10
                    IE: Unknown: DD1E00904C338E1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3409000700000000000000000000000000000000000000
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"WLAN_7A78"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004025f33d13f
                    Extra: Last beacon: 5580ms ago
                    IE: Unknown: 0009574C414E5F37413738
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500000B127A
                    IE: Unknown: DD07000C4307000000
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"WLAN_6D8E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000056211dccfe0
                    Extra: Last beacon: 5424ms ago
                    IE: Unknown: 0009574C414E5F36443845
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DDA20050F204104A0001101044000102103B0001031047001063041253101920061228001915D46D8E1021001B5265616C74656B2053656D69636F6E647563746F7220436F72702E1023000752544C383637311024000D45562D323030362D30372D32371042000F3132333435363738393031323334371054000800060050F2040001101100174F4253455256412054454C45434F4D2C20415734303632100800020086
          Cell 04 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"WLAN_42"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004a8debb3ce
                    Extra: Last beacon: 5364ms ago
                    IE: Unknown: 0007574C414E5F3432
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0103
                    IE: Unknown: 32080C1218243048606C

##### iwlist channel #####

wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Current Frequency:2.452 GHz (Channel 9)

##### lsmod #####

iwl3945                73145  0 
iwl_legacy             71334  1 iwl3945
mac80211              436493  2 iwl3945,iwl_legacy
cfg80211              178877  3 iwl3945,iwl_legacy,mac80211

##### modinfo #####

filename:       /lib/modules/3.2.0-60-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     301B04B4010DED41B0830D0
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        iwl-legacy,cfg80211,mac80211
intree:         Y
vermagic:       3.2.0-60-generic SMP mod_unload modversions 686 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

filename:       /lib/modules/3.2.0-60-generic/kernel/drivers/net/wireless/iwlegacy/iwl-legacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     E722FD105B84D0374546E93
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.2.0-60-generic SMP mod_unload modversions 686 
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

##### modules #####

lp
lp
lp

##### blacklist #####

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

##### udev rules #####

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1e.0/0000:06:07.0 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x148f:0x5370 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #####

[   18.474067] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   18.474073] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   18.474156] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.474173] iwl3945 0000:03:00.0: setting latency timer to 64
[   18.550297] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   18.550303] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   18.550462] iwl3945 0000:03:00.0: irq 44 for MSI/MSI-X
[   18.595092] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   20.518472] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   20.595958] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.596376] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.064045] wlan0: authenticate with <MAC address removed> (try 1)
[   30.065902] wlan0: authenticated
[   30.069123] wlan0: associate with <MAC address removed> (try 1)
[   30.071851] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[   30.071858] wlan0: associated
[   30.073590] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   32.137946] wlan0: IPv6 duplicate address fe80::213:2ff:fe9b:a02e detected!

########## wireless info END ############
```

With these results, everything seems to work fine. 
If it fails again I write the results as not working.

You can not imagine how grateful I am that you're helping me. Thank you very much for sparing some of your time.

---

### Post by varunendra on 2014-04-19
It's all right. Every solved case gives us pleasure, satisfaction, confidence and a feel of achievement. So offering help here is not as selfless as it might seem to you. :)

Some suggestions to optimize your current setup -

**1)** In your router/access-point, change the encryption type to WPA2 with AES (CCMP). Currently it is set to WPA (1) with AES which is a non-standard combination (WPA (1) requires 'TKIP' which is a less secure and inefficient encryption algorithm).

**2)** Apart from the encryption type, also change the channel to 1 or 11. Currently it is set to channel 9. If available, you may also try any of the 5 GHz channels (listed under "iwlist channel" section of the script). Both these changes have to be made in the router/access-point, not in the OS (your OS will automatically adapt itself to these changes in the router). Reboot the router after saving any changes.

**3)** Now that Ubuntu 14.04 is finally released, you might wish to try its ISO in Live mode to see if it gives you any significantly better performance. If you wish to try it, it is highly recommended to use [torrents]("http://www.ubuntu.com/download/alternative-downloads") to download the ISO. It is not only a faster download, but also ensures the integrity of the downloaded data.

---

### Post by angelpear on 2014-04-20
Hello. 
A new day and everything works fine. 
Thanks to your help, we can take it for solved. 

About your tips: 

1) You're right. I'll change to use "WPA2 with AES." Also I will use MAC filtering. 

2) I can not. I use a router "Huawei HG556a" which is Vodafone. Unfortunately I am limited to 2.4 GHz Today I found that in my area all 5GHz channels are free. I'll remember that if I change the router. 

3) Ubuntu 14.04 LTS? Fantastic news! I installed Zorin OS 6 because it is LTS (until April 2017). I'm using Zorin in the two PC's that I will not have on hand (one for my sister and one for my parents. They have never used linux so I looked for something that was simple in its change from Windows XP to Linux. For these two PCs I need simple things that do not cause problems. And they have to be similar to Win XP / Win 7. On my PC I can test the new version, but it must be Lubuntu, because it is a netbook. Thanks for the tip, I'll remember.

---

