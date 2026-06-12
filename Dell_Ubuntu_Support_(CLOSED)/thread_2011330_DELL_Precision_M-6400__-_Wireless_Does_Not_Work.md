---
title: "DELL Precision M-6400  - Wireless Does Not Work"
date: 2012-06-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kartook on 2012-06-27
Hi , 

I recently install new version 12.04-64bit . 
But i cant use Wireless  and compiz 


Info : 


[COLOR=Blue]kartook:~$ lspci -nn | grep -i vga[/COLOR]
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G92 [Quadro FX 3700M] [10de:061e] (rev a2)
kartook:~$ 
kartook:~$ 

[COLOR=Blue]kartook:~$ sudo lshw -C display[/COLOR]
[sudo] password for kartook: 
  *-display               
       description: VGA compatible controller
       product: G92 [Quadro FX 3700M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f5000000-f5ffffff memory:e0000000-efffffff memory:f2000000-f3ffffff ioport:df00(size=128) memory:f6e00000-f6e1ffff
kartook:~$ 


kartook:~$ 
[COLOR=Blue]kartook:~$ lsmod | grep -i nvidia[/COLOR]
nvidia              12319264  42 
kartook:~$ 


kartook:~$ 
[COLOR=Blue]artook:~$ apt-cache policy nvidia-current[/COLOR]
nvidia-current:
  Installed: 295.40-0ubuntu1
  Candidate: 295.40-0ubuntu1
  Version table:
 *** 295.40-0ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/restricted amd64 Packages
        100 /var/lib/dpkg/status
kartook:~$ 

kartook:~$ 
[COLOR=Blue]kartook:~$ grep -i glx /var/log/Xorg.0.log[/COLOR]
[    24.719] (II) LoadModule: "glx"
[    24.719] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    24.730] (II) Module glx: vendor="NVIDIA Corporation"
[    24.730] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:57:38 PDT 2012
[    24.730] (II) Loading extension GLX
[    28.058] (II) Loading extension NV-GLX
[    28.138] (II) Initializing extension GLX
kartook:~$ 
kartook:~$

---

### Post by wildmanne39 on 2012-06-28
Hi, I can probably help with the wireless issue but if people start posting about the compiz issue we will need to start another thread, it is suppose to be one thread for each issue.

Please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod

``` 
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by kartook on 2012-06-28
Thanks for your help and time . Wireless is much needed help .. thanks much 

refer below .... :guitar:

kartook@kartook:~$ [COLOR=RoyalBlue]cat /etc/lsb-release; uname -a[/COLOR]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux kartook 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
kartook@kartook:~$ 
kartook@kartook:~$ 
kartook@kartook:~$ [COLOR=RoyalBlue]lspci -nnk | grep -iA2 net[/COLOR]
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5761e Gigabit Ethernet PCIe [14e4:1680] (rev 10)
    Subsystem: Dell Device [1028:0251]
    Kernel driver in use: tg3
--
0c:00.0 Network controller [0280]: Intel Corporation Ultimate N WiFi Link 5300 [8086:4235]
    Subsystem: Intel Corporation Device [8086:1121]
    Kernel driver in use: iwlwifi
kartook@kartook:~$ 
kartook@kartook:~$ 
kartook@kartook:~$[COLOR=RoyalBlue] iwconfig[/COLOR]
lo        no wireless extensions.

vmnet8    no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

vmnet1    no wireless extensions.

kartook@kartook:~$ 
kartook@kartook:~$ 
kartook@kartook:~$ 
kartook@kartook:~$[COLOR=RoyalBlue] rfkill list all[/COLOR]
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
kartook@kartook:~$ 
kartook@kartook:~$ 
kartook@kartook:~$ 
kartook@kartook:~$[COLOR=RoyalBlue] lsmod[/COLOR]
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
vmnet                  55571  17 
vsock                  52475  2 
vmci                   82479  2 vsock
vmmon                  80498  3 
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  12 
binfmt_misc            17540  1 
vesafb                 13844  1 
btusb                  18288  2 
bluetooth             180104  23 bnep,rfcomm,btusb
nvidia              12319264  42 
snd_hda_codec_idt      70795  1 
arc4                   12529  2 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
pcmcia                 49310  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
video                  19596  0 
wmi                    19256  1 dell_wmi
yenta_socket           28084  0 
pcmcia_rsrc            18430  1 yenta_socket
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_timer              29990  2 snd_pcm,snd_seq
r852                   18277  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
sm_common              16865  1 r852
nand                   54955  2 r852,sm_common
nand_ids               12723  1 nand
mtd                    33087  2 sm_common,nand
nand_bch               13147  1 nand
bch                    22061  1 nand_bch
dell_laptop            18119  0 
nand_ecc               13230  1 nand
dcdbas                 14490  1 dell_laptop
snd                    78855  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlwifi               332672  0 
r592                   18144  0 
mac80211              506816  1 iwlwifi
memstick               16569  1 r592
cfg80211              205544  2 iwlwifi,mac80211
psmouse                87692  0 
joydev                 17693  0 
soundcore              15091  1 snd
serio_raw              13211  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
usbhid                 47199  0 
hid                    99559  1 usbhid
tg3                   152032  0 
kartook@kartook:~$ 
kartook@kartook:~$ 
kartook@kartook:~$

---

### Post by wildmanne39 on 2012-06-28
Hi, please do:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Then:
```
echo "blacklist dell_laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot
Thanks

---

### Post by kartook on 2012-06-29
kartook@kartook:~$ [COLOR=Navy]echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf[/COLOR]
[sudo] password for kartook: 
options iwlwifi 11n_disable=1
kartook@kartook:~$ 
kartook@kartook:~$ 
kartook@kartook:~$ 
kartook@kartook:~$ [COLOR=Navy]sudo modprobe -rfv iwlwifi[/COLOR]
rmmod /lib/modules/3.2.0-26-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
rmmod /lib/modules/3.2.0-26-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.2.0-26-generic/kernel/net/wireless/cfg80211.ko
kartook@kartook:~$ 
kartook@kartook:~$ 
kartook@kartook:~$ 
kartook@kartook:~$ 
kartook@kartook:~$ [COLOR=Navy]sudo modprobe -v iwlwifi[/COLOR]
insmod /lib/modules/3.2.0-26-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.2.0-26-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.2.0-26-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 11n_disable=1
kartook@kartook:~$ 
kartook@kartook:~$ 
kartook@kartook:~$ 
kartook@kartook:~$ [COLOR=Navy]echo "blacklist dell_laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf[/COLOR]
blacklist dell_laptop
kartook@kartook:~$ 
kartook@kartook:~$ 
kartook@kartook:~$ 
kartook@kartook:~$

---

### Post by wildmanne39 on 2012-06-29
Hi, I am guessing the wireless did not connect? then we move to the next step.

Please post the output of:
```
nm-tool
```
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

### Post by kartook on 2012-06-29
kartook@kartook:~$[COLOR=Navy] nm-tool[/COLOR]

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        00:22:19:E5:B3:82

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.10.205.120
    Prefix:          24 (255.255.255.0)
    Gateway:         192.10.205.160

    DNS:             192.10.205.200
    DNS:             192.10.206.5
    DNS:             192.10.206.19


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             unavailable
  Default:           no
  HW Address:        00:21:6A:2E:CE:28

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


kartook@kartook:~$ 
kartook@kartook:~$ 
kartook@kartook:~$ 
kartook@kartook:~$ [COLOR=Navy]sudo cat /var/log/syslog | grep -e iwl -e firmware -e wpa -e wlan -e etork | tail -n55[/COLOR]
[sudo] password for kartook: 
Jun 29 10:10:20 kartook NetworkManager[1112]: <info> (wlan0): bringing up device.
Jun 29 10:10:20 kartook NetworkManager[1112]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun 29 10:10:20 kartook kernel: [   18.140608] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 29 10:11:28 kartook vmnetBridge: RTM_NEWLINK: name:wlan0 index:3 flags:0x00001002
Jun 29 10:11:30 kartook vmnet-natd: RTM_NEWLINK: name:wlan0 index:3 flags:0x00001002
Jun 29 10:15:05 kartook vmnet-natd: RTM_DELLINK: name:wlan0 index:3 flags:0x00001002
Jun 29 10:15:05 kartook vmnetBridge: RTM_DELLINK: name:wlan0 index:3 flags:0x00001002
Jun 29 10:15:05 kartook avahi-daemon[1093]: Withdrawing workstation service for wlan0.
Jun 29 10:15:05 kartook NetworkManager[1112]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/wlan0, iface: wlan0)
Jun 29 10:15:05 kartook NetworkManager[1112]: <info> (wlan0): now unmanaged
Jun 29 10:15:05 kartook NetworkManager[1112]: <info> (wlan0): device state change: unavailable -> unmanaged (reason 'removed') [20 10 36]
Jun 29 10:15:05 kartook kernel: [  302.688414] iwlwifi 0000:0c:00.0: PCI INT A disabled
Jun 29 10:15:13 kartook kernel: [  311.423927] iwlwifi 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 29 10:15:13 kartook kernel: [  311.423959] iwlwifi 0000:0c:00.0: setting latency timer to 64
Jun 29 10:15:13 kartook kernel: [  311.423985] iwlwifi 0000:0c:00.0: pci_resource_len = 0x00002000
Jun 29 10:15:13 kartook kernel: [  311.423987] iwlwifi 0000:0c:00.0: pci_resource_base = ffffc900065c8000
Jun 29 10:15:13 kartook kernel: [  311.423989] iwlwifi 0000:0c:00.0: HW Revision ID = 0x0
Jun 29 10:15:13 kartook kernel: [  311.424255] iwlwifi 0000:0c:00.0: irq 49 for MSI/MSI-X
Jun 29 10:15:13 kartook kernel: [  311.424352] iwlwifi 0000:0c:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
Jun 29 10:15:13 kartook kernel: [  311.424469] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
Jun 29 10:15:13 kartook kernel: [  311.446758] iwlwifi 0000:0c:00.0: device EEPROM VER=0x120, CALIB=0x4
Jun 29 10:15:13 kartook kernel: [  311.446760] iwlwifi 0000:0c:00.0: Device SKU: 0Xf0
Jun 29 10:15:13 kartook kernel: [  311.446774] iwlwifi 0000:0c:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Jun 29 10:15:13 kartook vmnet-natd: RTM_NEWLINK: name:wlan0 index:6 flags:0x00001002
Jun 29 10:15:13 kartook vmnetBridge: RTM_NEWLINK: name:wlan0 index:6 flags:0x00001002
Jun 29 10:15:13 kartook kernel: [  311.449722] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692
Jun 29 10:15:13 kartook kernel: [  311.450304] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
Jun 29 10:15:13 kartook NetworkManager[1112]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/wlan0, iface: wlan0)
Jun 29 10:15:13 kartook NetworkManager[1112]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun 29 10:15:13 kartook NetworkManager[1112]: <info> (wlan0): using nl80211 for WiFi device control
Jun 29 10:15:13 kartook NetworkManager[1112]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 6)
Jun 29 10:15:13 kartook NetworkManager[1112]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/2
Jun 29 10:15:13 kartook NetworkManager[1112]: <info> (wlan0): now managed
Jun 29 10:15:13 kartook NetworkManager[1112]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 29 10:15:13 kartook NetworkManager[1112]: <info> (wlan0): bringing up device.
Jun 29 10:15:13 kartook NetworkManager[1112]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun 29 10:15:13 kartook kernel: [  311.484790] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 29 10:18:19 kartook kernel: [    0.000000]  [<ffffffff810672af>] warn_slowpath_common+0x7f/0xc0
Jun 29 10:18:19 kartook kernel: [    0.000000]  [<ffffffff8106734f>] warn_slowpath_fmt_taint+0x3f/0x50
Jun 29 10:18:19 kartook kernel: [   10.987442] iwlwifi 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 29 10:18:19 kartook kernel: [   10.987472] iwlwifi 0000:0c:00.0: setting latency timer to 64
Jun 29 10:18:19 kartook kernel: [   10.987500] iwlwifi 0000:0c:00.0: pci_resource_len = 0x00002000
Jun 29 10:18:19 kartook kernel: [   10.987502] iwlwifi 0000:0c:00.0: pci_resource_base = ffffc900065d4000
Jun 29 10:18:19 kartook kernel: [   10.987504] iwlwifi 0000:0c:00.0: HW Revision ID = 0x0
Jun 29 10:18:19 kartook kernel: [   10.987650] iwlwifi 0000:0c:00.0: irq 48 for MSI/MSI-X
Jun 29 10:18:19 kartook kernel: [   10.987741] iwlwifi 0000:0c:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
Jun 29 10:18:19 kartook kernel: [   10.987872] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
Jun 29 10:18:19 kartook kernel: [   11.011213] iwlwifi 0000:0c:00.0: device EEPROM VER=0x120, CALIB=0x4
Jun 29 10:18:19 kartook kernel: [   11.011217] iwlwifi 0000:0c:00.0: Device SKU: 0Xf0
Jun 29 10:18:19 kartook kernel: [   11.017355] iwlwifi 0000:0c:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Jun 29 10:18:19 kartook kernel: [   11.220927] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692
Jun 29 10:18:19 kartook kernel: [   11.226313] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
Jun 29 10:18:19 kartook kernel: [   26.088354] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 29 10:18:20 kartook vmnetBridge: RTM_NEWLINK: name:wlan0 index:3 flags:0x00001002
Jun 29 10:18:21 kartook vmnet-natd: RTM_NEWLINK: name:wlan0 index:3 flags:0x00001002
kartook@kartook:~$ 
kartook@kartook:~$ 
kartook@kartook:~$ 
kartook@kartook:~$

---

### Post by wildmanne39 on 2012-06-29
Hi, it looks like an issue with network manager please [COLOR="Red"]do in this order[/COLOR]:
```
sudo apt-get install wicd
```
Then:
```
sudo apt-get purge network-manager network-manager-gnome
```
I believe dhcp has to be set to dhclient.
Thanks

---

### Post by kartook on 2012-07-07
Working Great ... Sorry for the delay ... 

Thanks for your time and support

---

### Post by wildmanne39 on 2012-07-07
Hi, that is great, please mark the thread solved and if you still need help with compiz start a new thread with a descriptive title.
Thanks

---

