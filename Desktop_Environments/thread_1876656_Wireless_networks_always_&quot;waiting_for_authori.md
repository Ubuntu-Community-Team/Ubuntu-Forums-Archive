---
title: "Wireless networks always &quot;waiting for authorization&quot;"
date: 2011-11-06
forum: Desktop Environments
---

### Post by speck360 on 2011-11-06
I'm using kubuntu on two computers and having problems to connect on wireless encrypted networks (wep, wpa or wpa2). The connection stays "waiting for authorization" and never connects.

Here are some details about these two hosts:

**Host 1**:
```
lspci | grep Network
12:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)
```

lsmod
```
$ lsmod
Module                  Size  Used by
btusb                  18600  2 
parport_pc             36962  0 
ppdev                  17113  0 
dm_crypt               23199  0 
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
bnep                   18436  2 
rfcomm                 47946  12 
bluetooth             166112  23 btusb,bnep,rfcomm
joydev                 17693  0 
bcma                   20219  0 
arc4                   12529  2                                                                                                                                                                 
dell_wmi               12681  0                                                                                                                                                                 
sparse_keymap          13890  1 dell_wmi                                                                                                                                                        
snd_hda_codec_hdmi     32040  1                                                                                                                                                                 
snd_hda_codec_idt      70553  1                                                                                                                                                                 
dell_laptop            13831  0                                                                                                                                                                 
dcdbas                 14490  1 dell_laptop
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
psmouse                73882  0 
serio_raw              13166  0 
brcmsmac              631693  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
brcmutil               17837  1 brcmsmac
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              310872  1 brcmsmac
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199587  2 brcmsmac,mac80211
intel_ips              18089  0 
crc_ccitt              12667  1 brcmsmac
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41480  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
ahci                   26002  3 
libahci                26861  1 ahci
r8169                  52788  0 
i915                  566711  9 
wmi                    19256  1 dell_wmi
drm_kms_helper         42558  1 i915
drm                   236330  5 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
```

```
sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:12:00.0
       logical name: wlan0
       version: 01
       serial: 5c:ac:4c:64:dd:e0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.0.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:fbb00000-fbb03fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: eth0
       version: 03
       serial: b8:ac:6f:c4:83:3b
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-2.fw ip=192.168.2.2 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 ioport:e000(size=256) memory:d0b04000-d0b04fff memory:d0b00000-d0b03fff memory:fba00000-fba1ffff
```

**Host 2**:

```
lspci | grep Network
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
```

```
lsmod
Module                  Size  Used by
usb_storage            53538  0 
uas                    17996  0 
joydev                 17606  0 
rfcomm                 47694  12 
parport_pc             36959  0 
ppdev                  17113  0 
sco                    18187  2 
bnep                   18308  2 
l2cap                  53570  16 rfcomm,bnep
dm_crypt               22993  0 
arc4                   12529  2 
snd_hda_codec_si3054    13084  1 
snd_hda_codec_realtek   336771  1 
snd_hda_intel          33176  2 
snd_hda_codec         103804  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
iwlagn                333716  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
hp_wmi                 13706  0 
sparse_keymap          13898  1 hp_wmi
btusb                  18600  2 
uvcvideo               72195  0 
r852                   18246  0 
sm_common              16817  1 r852
snd_timer              29602  2 snd_pcm,snd_seq
bluetooth              72320  9 rfcomm,sco,bnep,l2cap,btusb
psmouse                73535  0 
nand                   55112  2 r852,sm_common
nand_ids               12723  1 nand
nand_ecc               13230  1 nand
serio_raw              13166  0 
iwlcore               167502  1 iwlagn
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               82052  1 uvcvideo
mac80211              294370  2 iwlagn,iwlcore
mtd                    27900  2 sm_common,nand
v4l2_compat_ioctl32    17078  1 videodev
snd                    67382  14 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              178528  3 iwlagn,iwlcore,mac80211
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
i915                  515121  3 
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
drm_kms_helper         42136  1 i915
crc_itu_t              12707  1 firewire_core
drm                   227534  4 i915,drm_kms_helper
ahci                   25951  3 
r8169                  48022  0 
libahci                26642  1 ahci
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
```

```
sudo lshw -C network
[sudo] password for anselmo: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 61
       serial: 00:21:5c:05:e7:17
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-11-generic firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:46 memory:f4000000-f4001fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:68:a7:99:49
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:c000(size=256) memory:f8200000-f8200fff memory:c0000000-c001ffff
```

---

### Post by Wilker on 2011-11-27
i have exactly the same problem. i simply can't connect to a hidden ssid.

---

### Post by speck360 on 2011-12-01
My solution was change the passphrase to another using numbers, characters and special characters.

Maybe you should set the network to show the ssid.

Best regards.

---

### Post by inobe on 2011-12-01
delete all previous connections, restart network services or reboot.

click wireless connection, enter password.

---

