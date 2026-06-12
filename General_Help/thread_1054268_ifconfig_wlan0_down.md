---
title: "ifconfig wlan0 down"
date: 2009-01-29
forum: General Help
---

### Post by oddworld on 2009-01-29
I used the command 
```
 ifconfig wlan0 down 
```
to temporally disable wifi, but not I do not know how to bring it back up.

```


davis@davis-laptop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
davis@davis-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

davis@davis-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:68:3f:2a  
          inet addr:192.168.1.245  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe68:3f2a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:92675 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60371 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:138579132 (132.1 MB)  TX bytes:4163248 (3.9 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2138 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:106900 (104.3 KB)  TX bytes:106900 (104.3 KB)

davis@davis-laptop:~$ 



```

and 

```


davis@davis-laptop:~$ dmesg | grep -i eth0
[   12.457358] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:15:c5:68:3f:2a
[   34.492733] b44: eth0: Link is up at 100 Mbps, full duplex.
[   34.492741] b44: eth0: Flow control is off for TX and off for RX.
davis@davis-laptop:~$ dmesg | grep -i wlan0
davis@davis-laptop:~$ lsmod
Module                  Size  Used by
ipv6                  311848  10 
af_packet              27272  2 
i915                   38144  2 
drm                   105896  3 i915
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67620  4 rfcomm,l2cap
ppdev                  11400  0 
cpufreq_stats           8416  0 
cpufreq_userspace       6180  0 
cpufreq_ondemand       11152  0 
freq_table              6464  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       3200  0 
cpufreq_conservative    10632  0 
dock                   12960  0 
container               6656  0 
sbs                    17808  0 
sbshc                   8960  1 sbs
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
sbp2                   27272  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
joydev                 15488  0 
evdev                  14976  7 
iwl3945               100592  0 
iwlwifi_mac80211      251876  1 iwl3945
snd_hda_intel         442200  3 
cfg80211               17680  1 iwlwifi_mac80211
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
dcdbas                 11312  0 
sdhci                  21508  0 
video                  23444  0 
output                  5632  1 video
mmc_core               59272  1 sdhci
snd_rawmidi            29856  1 snd_seq_midi
serio_raw               9092  0 
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
battery                16776  0 
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ac                      8328  0 
button                 10912  0 
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
shpchp                 38172  0 
snd                    70856  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              30624  1 
pci_hotplug            34608  1 shpchp
soundcore              10400  1 snd
iTCO_wdt               15312  0 
iTCO_vendor_support     5764  1 iTCO_wdt
pcspkr                  4992  0 
psmouse                46236  0 
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sg                     41880  0 
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
sd_mod                 33280  3 
usbhid                 35680  0 
hid                    44992  1 usbhid
ata_piix               24196  2 
ata_generic             9988  0 
pata_acpi               9856  0 
libata                176560  3 ata_piix,ata_generic,pata_acpi
scsi_mod              178488  5 sbp2,sg,sr_mod,sd_mod,libata
ohci1394               36532  0 
ieee1394              106968  2 sbp2,ohci1394
ehci_hcd               41996  0 
uhci_hcd               29856  0 
b44                    33168  0 
ssb                    39428  1 b44
mii                     7552  1 b44
usbcore               170288  4 usbhid,ehci_hcd,uhci_hcd
thermal                19744  0 
processor              40424  3 thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3 
davis@davis-laptop:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
davis@davis-laptop:~$ 


```

Any help is much appreciated!

---

### Post by SqRt7744 on 2009-01-29
it seems that the driver (module) has been removed. what does dmesg|tail tell you? What wireless card are you using (lspci should help here)? Once you've found out which wireless chip you are using, try reloading the module with 'sudo modprobe -i module_name' (eg. iwl3945, ath5k or whatever it happens to be.)

Why don't you just disable it with a right click on networkmanager?

---

### Post by oddworld on 2009-01-29
```

davis@davis-laptop:~$ ls /etc/network/interfaces 
/etc/network/interfaces
davis@davis-laptop:~$ gedit /etc/network/interfaces 
davis@davis-laptop:~$ sudo auto wlan0
sudo: auto: command not found
davis@davis-laptop:~$ dmesg | grep -i eth0
[   12.457358] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:15:c5:68:3f:2a
[   34.492733] b44: eth0: Link is up at 100 Mbps, full duplex.
[   34.492741] b44: eth0: Flow control is off for TX and off for RX.
davis@davis-laptop:~$ dmesg | grep -i wlan0
davis@davis-laptop:~$ lsmod
Module                  Size  Used by
ipv6                  311848  10 
af_packet              27272  2 
i915                   38144  2 
drm                   105896  3 i915
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67620  4 rfcomm,l2cap
ppdev                  11400  0 
cpufreq_stats           8416  0 
cpufreq_userspace       6180  0 
cpufreq_ondemand       11152  0 
freq_table              6464  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       3200  0 
cpufreq_conservative    10632  0 
dock                   12960  0 
container               6656  0 
sbs                    17808  0 
sbshc                   8960  1 sbs
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
sbp2                   27272  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
joydev                 15488  0 
evdev                  14976  7 
iwl3945               100592  0 
iwlwifi_mac80211      251876  1 iwl3945
snd_hda_intel         442200  3 
cfg80211               17680  1 iwlwifi_mac80211
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
dcdbas                 11312  0 
sdhci                  21508  0 
video                  23444  0 
output                  5632  1 video
mmc_core               59272  1 sdhci
snd_rawmidi            29856  1 snd_seq_midi
serio_raw               9092  0 
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
battery                16776  0 
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ac                      8328  0 
button                 10912  0 
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
shpchp                 38172  0 
snd                    70856  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              30624  1 
pci_hotplug            34608  1 shpchp
soundcore              10400  1 snd
iTCO_wdt               15312  0 
iTCO_vendor_support     5764  1 iTCO_wdt
pcspkr                  4992  0 
psmouse                46236  0 
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sg                     41880  0 
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
sd_mod                 33280  3 
usbhid                 35680  0 
hid                    44992  1 usbhid
ata_piix               24196  2 
ata_generic             9988  0 
pata_acpi               9856  0 
libata                176560  3 ata_piix,ata_generic,pata_acpi
scsi_mod              178488  5 sbp2,sg,sr_mod,sd_mod,libata
ohci1394               36532  0 
ieee1394              106968  2 sbp2,ohci1394
ehci_hcd               41996  0 
uhci_hcd               29856  0 
b44                    33168  0 
ssb                    39428  1 b44
mii                     7552  1 b44
usbcore               170288  4 usbhid,ehci_hcd,uhci_hcd
thermal                19744  0 
processor              40424  3 thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3 
davis@davis-laptop:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
davis@davis-laptop:~$ modprobe cfg80211 
davis@davis-laptop:~$ idmesg|tail
bash: idmesg: command not found
davis@davis-laptop:~$ dmesg|tail
[   55.191556] CPU0 attaching sched-domain:
[   55.191565]  domain 0: span 03
[   55.191568]   groups: 01 02
[   55.191573]   domain 1: span 03
[   55.191576]    groups: 03
[   55.191580] CPU1 attaching sched-domain:
[   55.191582]  domain 0: span 03
[   55.191585]   groups: 02 01
[   55.191590]   domain 1: span 03
[   55.191593]    groups: 03
davis@davis-laptop:~$ clear

davis@davis-laptop:~$ dmesg|tail
[   55.191556] CPU0 attaching sched-domain:
[   55.191565]  domain 0: span 03
[   55.191568]   groups: 01 02
[   55.191573]   domain 1: span 03
[   55.191576]    groups: 03
[   55.191580] CPU1 attaching sched-domain:
[   55.191582]  domain 0: span 03
[   55.191585]   groups: 02 01
[   55.191590]   domain 1: span 03
[   55.191593]    groups: 03
davis@davis-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
davis@davis-laptop:~$ 

```

---

### Post by oddworld on 2009-01-29
I  dont think it did anything

```


davis@davis-laptop:~$ sudo modprobe -i iwl3945
[sudo] password for davis: 
davis@davis-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:68:3f:2a  
          inet addr:192.168.1.245  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe68:3f2a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1806775 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1179396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2714244513 (2.5 GB)  TX bytes:80588594 (76.8 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2138 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:106900 (104.3 KB)  TX bytes:106900 (104.3 KB)

davis@davis-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

davis@davis-laptop:~$ sudo modprobe -i iwlwifi_mac80211
davis@davis-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

davis@davis-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:68:3f:2a  
          inet addr:192.168.1.245  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe68:3f2a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1866740 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1218674 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2804380382 (2.6 GB)  TX bytes:83256262 (79.3 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2138 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:106900 (104.3 KB)  TX bytes:106900 (104.3 KB)

davis@davis-laptop:~$ 


```

---

### Post by SqRt7744 on 2009-01-29
the module is iwl3945. But it is still loaded, so loading it *again* doesn't help.

here's a suggestion: don't stop the wireless card with sudo ifconfig wlan0 down. If you want to disable wireless, try the toggle switch on your computer (or key-combo), or right-click on the network manager icon in the upper right hand corner and disable the wireless that way.

If you've disabled it with an ifconfig wlan down, then you may have to restart network manager or networking to get it up again.
sudo /etc/init.d/networking restart
sudo /etc/init.d/NetworkManager restart

---

### Post by fore_perry on 2010-09-16
I am working on this same issue in 10.04.  What was the resolution to this?
 FYI
I am a new user to Ubuntu and this is a fresh install.

---

