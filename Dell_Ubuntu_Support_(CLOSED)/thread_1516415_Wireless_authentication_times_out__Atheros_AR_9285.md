---
title: "Wireless authentication times out : Atheros AR 9285 Card on Dell Vostro 1014"
date: 2010-06-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sohelmk on 2010-06-23
Hi,
I just got a Dell Vostro 1014 (that happens to be the only model in market with ubuntu, in mainstream). But I still could not connect with wireless network. The network manager detects all networks, but fails to connect, even if wireless is made unsecured. I tried all possible options with Network Manager and manual wlconfig steps from ubuntu forums. The logs show similar errors " Authentication time out". 

**Can someone please suggest a solution?**

Here are key files and outputs of all important commands (file and command in red, output and contents of file in black)
 
Thanks a lot,
Sohel

[COLOR=Red]/etc/wpa_supplicant.conf[/COLOR]

ctrl_interface=/var/run/wpa_supplicant
network={
    ssid="sr"
    psk="passwd"
    key_mgmt=WPA-PSK
    proto=RSN
    pairwise=CCMP TKIP
    group=CCMP TKIP
    peerkey=1
    scan_ssid=1
    eapol_flags=1

}

[COLOR=Red]/etc/network/interfaces

[/COLOR]    auto wlan0
    iface wlan0 inet dhcp

[COLOR=Red]sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo iwconfig wlan0 essid "sr"
sudo iwconfig wlan0 mode managed
[/COLOR]
[COLOR=Red]sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd [/COLOR]

Complete output attached in file

Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 2 - start of a new network block
ssid - hexdump_ascii(len=11):
     73 6f 68 65 6c 72 6f 67 65 72 73                  sr
PSK (ASCII passphrase) - hexdump_ascii(len=9): [REMOVED]
key_mgmt: 0x2
proto: 0x2
pairwise: 0x18
group: 0x18
peerkey=1 (0x1)
scan_ssid=1 (0x1)
eapol_flags=1 (0x1)
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='sr'
Interface wlan0 set UP - waiting a second for the driver to complete initialization
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 20:7c:8f:07:d1:70
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
WPS:  * Wi-Fi Protected Setup State (0)3 set_tx=0 seq_len=0 key_len=0
WPS:  * Version_set_countermeasures
WPS:  * Wi-Fi Protected Setup State (0)
WPS:  * Response Type (2)in the driver
WPS:  * UUID-Eequest: 0 sec 100000 usec
WPS:  * ManufacturerAC address - hexdump(len=16): 0f fe 57 fb a9 9c 5a 1c be af c7 e6 d0 9f 90 d8
WPS:  * Model Nameand Probe Response IEs
WPS:  * Model Number
WPS:  * Serial Number
WPS:  * Primary Device Type
WPS:  * Device Name
WPS:  * Config Methods (0)
WPS:  * RF Bands (3)
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=11):
     73 6f 68 65 6c 72 6f 67 65 72 73                  sr
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 325 bytes of scan results (1 BSSes)
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:13:f7:c5:07:e1 ssid='sr' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:13:f7:c5:07:e1 ssid='sr'
Trying to associate with 00:13:f7:c5:07:e1 (SSID='sr' freq=2417 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2 proto 2
WPA: clearing AP WPA IE
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
[COLOR=Blue]**Authentication with 00:13:f7:c5:07:e1 timed out.**[/COLOR]
Added BSSID 00:13:f7:c5:07:e1 into blacklistc
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED fail=0
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5uth flag
EAPOL: External notification - portEnabled=0UP])
EAPOL: External notification - portValid=0' added
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec=0x1003 ([UP])
State: DISCONNECTED -> SCANNINGface 'wlan0' added
Starting AP scan (broadcast SSID)


[COLOR=Red]sudo ifconfig wlan0 up[/COLOR]
[COLOR=Red]
sudo dhclient wlan0[/COLOR]

Listening on LPF/wlan0/20:7c:8f:07:d1:70
Sending on   LPF/wlan0/20:7c:8f:07:d1:70
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

[COLOR=Red]iwevent[/COLOR]

Waiting for Wireless Events from interfaces...
15:21:50.880747   wlan0    Set Mode:Managed
15:21:51.981400   wlan0    Scan request completed
15:21:51.982040   wlan0    Set Mode:Managed
15:21:51.982063   wlan0    Set Frequency:2.417 GHz (Channel 2)
15:22:02.989309   wlan0    Scan request completed
15:22:02.990026   wlan0    Set Mode:Managed

[COLOR=Red]sudo lspci -s 09:00 -vvv[/COLOR]

09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
        Subsystem: Dell Device 0401
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 29
        Region 0: I/O ports at ce00 [size=256]
        Region 2: Memory at f0204000 (64-bit, prefetchable) [size=4K]
        Region 4: Memory at f0200000 (64-bit, prefetchable) [size=16K]
        [virtual] Expansion ROM at f0220000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 3
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
                Address: 00000000fee0100c  Data: 41a1
        Capabilities: [70] Express (v2) Endpoint, MSI 01
                DevCap: MaxPayload 256 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
                        MaxPayload 128 bytes, MaxReadReq 4096 bytes
                DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
                        ClockPM+ Suprise- LLActRep- BwNot-
                LnkCtl: ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        Capabilities: [ac] MSI-X: Enable- Mask- TabSize=4
                Vector table: BAR=4 offset=00000000
                PBA: BAR=4 offset=00000800
        Capabilities: [cc] Vital Product Data <?>
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Virtual Channel <?>
        Capabilities: [160] Device Serial Number 00-e0-4c-68-00-00-00-0c
        Kernel driver in use: r8169
        Kernel modules: r8169

[COLOR=Red]dmesg [/COLOR]

Complete out attached in file

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-22-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 (Ubuntu 2.6.32-22.36-generic 2.6.32.11+drm33.2)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003dcbf400 (usable)
[    0.000000]  BIOS-e820: 000000003dcbf400 - 000000003dcc1400 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003dcc1400 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x3dcbf max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect

[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask C00000000 write-back
[    0.000000]   1 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   2 base 03DE00000 mask FFFE00000 uncachable
[    0.000000]   3 base 03E000000 mask FFE000000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 000000003de00000 - 0000000040000000 (usable) ==> (reserved)
[    0.000000] e820 update range: 00000000e0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003dcbf400 (usable)
[    0.000000]  modified: 000000003dcbf400 - 000000003dcc1400 (ACPI NVS)
[    0.000000]  modified: 000000003dcc1400 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
--More--(5%)

---

### Post by sohelmk on 2010-06-23
Forgot to mention, I am using latest Ubuntu 10.4 with all updates

I just tried another solution posted in one of the forums, still no luck:

" The thing that finally worked for me was to un-blacklist the ath5k driver in /etc/modprobe.d/blacklist-ath_pci.conf. "

---

### Post by sohelmk on 2010-06-23
Adding some more information if that helps to diagnose the issue:
Attached are the outputs of lshw before and after blacklisting ath_pci

It seems the driver I am using is ath9k

BTW I also tried removing the security from wireless, changed the wlan0 config, but still the error remains same "authentication timeout" I wonder why is it authenticating still? 

Does anyone know how to increase the timeout if that may help


[COLOR=Red]lshw -C network[/COLOR]

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 20:7c:8f:07:d1:70
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f69f0000-f69fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: b8:ac:6f:72:50:6f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.56 latency=0 multicast=yes
       resources: irq:29 ioport:ce00(size=256) memory:f0204000-f0204fff(prefetchable) memory:f0200000-f0203fff(prefetchable) memory:f0220000-f023ffff(prefetchable)
[COLOR=Red]
rfkill list[/COLOR]

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

