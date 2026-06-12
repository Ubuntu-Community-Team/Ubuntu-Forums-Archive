---
title: "No internet with latest version of Ubuntu"
date: 2012-10-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by grodriguez330 on 2012-10-01
I am new to Ubuntu, just installed it for the first time on my Dell Latitude D630.
My wireless card does not work, it doesnt show any wireless networks in range.
I believe the card is a broadcom sta. i activated the addtional driver needed, and it says :

This package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware.

Can somebody please help me get my wireless card to work?
My professor (im in computer science) made us install Ubuntu, and Im a noob to linux.

---

### Post by sandyd on 2012-10-01
post output of
```

lshw -C network
lsmod

```

---

### Post by grodriguez330 on 2012-10-01
After pasting that code in terminal this is what I get:

*-network UNCLAIMED
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f6cfc000-f6cfffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:17:16:1e
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=5755m-v3.29 ip=10.28.144.165 latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:f6bf0000-f6bfffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
gabriel@gabriel-Latitude-D630:~$ lsmod
Module                  Size  Used by
rt2800pci              18340  0 
rt2800lib              53264  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48805  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              436455  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              178679  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               252188  3 vboxpci,vboxnetadp,vboxnetflt
binfmt_misc            17292  1 
snd_hda_codec_idt      60251  1 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
pcmcia                 39791  0 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
wl                   2646601  0 
psmouse                86421  0 
serio_raw              13027  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13077  0 
lib80211               14040  1 wl
wmi                    18744  1 dell_wmi
i915                  419070  3 
soundcore              14635  1 snd
drm_kms_helper         45466  1 i915
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
tg3                   141369  0

Thanks for your fast response. :)

---

### Post by sandyd on 2012-10-01
You will probably want this
[http://ubuntuforums.org/showthread.php?t=1816292](http://ubuntuforums.org/showthread.php?t=1816292)

---

