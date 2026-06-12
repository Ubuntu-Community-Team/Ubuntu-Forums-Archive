---
title: "Dell Inspiron 3437 Wireless not working after update"
date: 2014-03-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by yec on 2014-03-09
Hi, 
my wireless network not working after update 

 I have LAN network working, but when log in Ubuntu, wireless network turn off 

 I try to fix  with this  solutions:
a)
```

sudo apt-get install linux-headers-generic 
sudo apt-get install --reinstall bcmwl-kernel-source 
sudo modprobe wl
```

reboot after this commands, and wireless not working 

2)
```

sudo rfkill unblock all
```
nothing display 

3)
copy the b43 folder 
[http://ubuntuforums.org/showthread.php?t=1974013](http://ubuntuforums.org/showthread.php?t=1974013)
wireless still not working 


this is the result of some commands, 


```
lsmod 
```
> Module                  Size  Used by
b43                   379088  0 
mac80211              555318  1 b43
cfg80211              208382  2 b43,mac80211
ssb                    53131  1 b43
bcma                   35762  1 b43
pci_stub               12623  1 
vboxpci                23237  0 
vboxnetadp             25671  0 
vboxnetflt             27613  0 
vboxdrv               320275  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32867  0 
ppdev                  17114  0 
bnep                   18240  2 
rfcomm                 47562  0 
bluetooth             212001  10 bnep,rfcomm
coretemp               13642  0 
kvm_intel             137888  0 
kvm                   422160  1 kvm_intel
ghash_clmulni_intel    13221  0 
aesni_intel            51134  0 
cryptd                 20531  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
snd_hda_codec_realtek    46366  1 
snd_hda_codec_hdmi     36726  1 
uvcvideo               78117  0 
videobuf2_core         33025  1 uvcvideo
videodev              125126  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
snd_hda_intel          43682  5 
snd_hda_codec         188269  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
dm_multipath           23306  0 
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
mac_hid                13254  0 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
i915_hsw              620520  2 
psmouse               102541  0 
snd                    83674  20 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         49259  1 i915_hsw
scsi_dh                14589  1 dm_multipath
serio_raw              13216  0 
microcode              23030  0 
drm                   290595  2 i915_hsw,drm_kms_helper
i2c_algo_bit           13565  1 i915_hsw
soundcore              15092  1 snd
video                  19653  1 i915_hsw
intel_ips              18332  1 i915_hsw
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
dm_raid45              78156  0 
ahci                   25869  2 
libahci                31434  1 ahci
xor                    17153  1 dm_raid45
dm_mirror              22204  0 
dm_region_hash         20962  1 dm_mirror
dm_log                 18565  3 dm_raid45,dm_mirror,dm_region_hash
r8169                  62741  0 
btrfs                 781180  0 
zlib_deflate           27140  1 btrfs
libcrc32c              12645  1 btrfs

```
lsusb
```
> Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:58c2 Realtek Semiconductor Corp. 


```
sudo lshw -c network
```
>   *-network NO RECLAMADO
       descripción: Network controller
       producto: QCA9565 / AR9565 Wireless Network Adapter
       fabricante: Qualcomm Atheros
       id físico: 0
       información del bus: pci@0000:06:00.0
       versión: 01
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list
       configuración: latency=0
       recursos: memoria:f7d00000-f7d7ffff memoria:f7d80000-f7d8ffff
  *-network
       descripción: Ethernet interface
       producto: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0
       información del bus: pci@0000:07:00.0
       nombre lógico: eth0
       versión: 08
       serie: e0:db:55:c1:6c:81
       tamaño: 100Mbit/s
       capacidad: 100Mbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.4 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       recursos: irq:57 ioport:e000(size=256) memoria:f7c04000-f7c04fff memoria:f7c00000-f7c03fff

```
 lspci -nn -d 14e4:
dmesg | grep b43
rfkill list all
```

this commands display nothing, i dont understand why 


Help me please, I need some hand

---

### Post by varunendra on 2014-03-11
Welcome to the forums yec!

It seems you have been trying all sorts of Broadcom chip fixes, while your system has an Atheros wireless card, no a Broadcom.

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

