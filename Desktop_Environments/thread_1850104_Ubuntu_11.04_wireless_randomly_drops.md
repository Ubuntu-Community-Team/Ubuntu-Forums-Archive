---
title: "Ubuntu 11.04 wireless randomly drops"
date: 2011-09-25
forum: Desktop Environments
---

### Post by sentinelace on 2011-09-25
For some reason I get random disconnects on my wireless.  Works fine on all my other laptops running windows.  Any advice?

---

### Post by garvinrick4 on 2011-09-25
[http://sourceforge.net/projects/wirelessscript/files/](http://sourceforge.net/projects/wirelessscript/files/)

Download the 2.1 version of this wireless script to Desktop or drop on Desktop and open a terminal and copy and paste these.
```
cd Desktop
``````
chmod +x wireless_script_2.1.sh
``````
sudo ./wireless_script_2.1.sh
```Choose wireless card by number and hit enter and then enter when done.
Will have results file on desktop open and copy and paste here:
After you paste highlight whole thing and hit the # sign in upper right of message box
and will put in a nice box to read. It will tell what is going wrong with wireless.

---

### Post by sentinelace on 2011-10-17
Sorry for the delay as I have been dealing with the issue but it still remains.  Anything better in the new kernel 11.10?  Here is the output:

```
[code]
Version: 2.0 (Development)
Mon Oct 17 20:55:02 EDT 2011

******************************************************************************************
Running networking services
******************************************************************************************
network-manager is installed
network-manager start/running, process 837
network-manager is running
******************************************************************************************
    Ubuntu release 
******************************************************************************************

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

******************************************************************************************
    Kernel
******************************************************************************************

Linux jason-Laptop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

******************************************************************************************
      lshw  List of network devices
******************************************************************************************

  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f1ffc000-f1ffffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:81:cd:9b
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=5755m-v3.29 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:47 memory:f1bf0000-f1bfffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7e:bd:e0:5d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=410.2160 ip=192.168.4.15 link=yes multicast=yes wireless=IEEE 802.11bg

******************************************************************************************
    pci devices
******************************************************************************************

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
    Subsystem: Dell Device [1028:01ff]
    Kernel driver in use: tg3

******************************************************************************************
    usb devices
******************************************************************************************

Bus 007 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 007 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
******************************************************************************************
    List of drivers
******************************************************************************************

Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
binfmt_misc            13213  1 
lirc_dev               18720  0 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
joydev                 17322  0 
snd_seq_midi           13132  0 
arc4                   12473  2 
snd_rawmidi            25269  1 snd_seq_midi
pcmcia                 39671  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
b43                   296610  0 
nouveau               621970  2 
mac80211              257001  1 b43
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27230  0 
dell_laptop            13515  0 
pcmcia_rsrc            18292  1 yenta_socket
dell_wmi               12601  0 
soundcore              12600  1 snd
cfg80211              156212  2 b43,mac80211
sparse_keymap          13666  1 dell_wmi
ttm                    65184  1 nouveau
tpm_tis                13993  0 
psmouse                73312  0 
drm_kms_helper         40745  1 nouveau
dcdbas                 14054  1 dell_laptop
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
drm                   180037  4 nouveau,ttm,drm_kms_helper
ndiswrapper           192828  0 
tpm                    21251  1 tpm_tis
tpm_bios               13460  1 tpm
i2c_algo_bit           13184  1 nouveau
ssb                    45942  1 b43
serio_raw              12990  0 
video                  18951  1 nouveau
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
firewire_ohci          31504  0 
tg3                   131476  0 
libahci                25548  1 ahci
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core

******************************************************************************************
interfaces
******************************************************************************************
auto lo
iface lo inet loopback


******************************************************************************************
resolv.conf
******************************************************************************************
# Generated by NetworkManager
nameserver 4.2.2.2

******************************************************************************************
Modules file
******************************************************************************************
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
ndiswrapper
ndiswrapper

******************************************************************************************
Blacklist file
******************************************************************************************
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
#blacklist bcm43xx

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

******************************************************************************************
Files in folder /etc/modprobe.d/*
******************************************************************************************
/etc/modprobe.d/alsa-base.conf
/etc/modprobe.d/blacklist
/etc/modprobe.d/blacklist-ath_pci.conf
/etc/modprobe.d/blacklist.conf
/etc/modprobe.d/blacklist-firewire.conf
/etc/modprobe.d/blacklist-framebuffer.conf
/etc/modprobe.d/blacklist-local.conf
/etc/modprobe.d/blacklist-modem.conf
/etc/modprobe.d/blacklist-oss.conf
/etc/modprobe.d/blacklist-rare-network.conf
/etc/modprobe.d/blacklist-watchdog.conf
/etc/modprobe.d/ndiswrapper.conf

******************************************************************************************
NetworkManager.state
******************************************************************************************

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

******************************************************************************************
nm_applet_file
******************************************************************************************
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false


******************************************************************************************
  network info 
******************************************************************************************

: error fetching interface information: Device not found
DEBUG: Interface value null in call_get_and_parse_route
```

---

### Post by bkratz on 2011-10-18
> **sentinelace said:**
> Sorry for the delay as I have been dealing with the issue but it still remains.  Anything better in the new kernel 11.10?  Here is the output:

```
[code]
Version: 2.0 (Development)
Mon Oct 17 20:55:02 EDT 2011

******************************************************************************************
Running networking services
******************************************************************************************
network-manager is installed
network-manager start/running, process 837
network-manager is running
******************************************************************************************
    Ubuntu release 
******************************************************************************************

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

******************************************************************************************
    Kernel
******************************************************************************************

Linux jason-Laptop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

******************************************************************************************
      lshw  List of network devices
******************************************************************************************

  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f1ffc000-f1ffffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:81:cd:9b
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=5755m-v3.29 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:47 memory:f1bf0000-f1bfffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7e:bd:e0:5d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=410.2160 ip=192.168.4.15 link=yes multicast=yes wireless=IEEE 802.11bg

******************************************************************************************
    pci devices
******************************************************************************************

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
    Subsystem: Dell Device [1028:01ff]
    Kernel driver in use: tg3

******************************************************************************************
    usb devices
******************************************************************************************

Bus 007 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 007 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
******************************************************************************************
    List of drivers
******************************************************************************************

Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
binfmt_misc            13213  1 
lirc_dev               18720  0 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
joydev                 17322  0 
snd_seq_midi           13132  0 
arc4                   12473  2 
snd_rawmidi            25269  1 snd_seq_midi
pcmcia                 39671  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
[COLOR=Red]b43                   296610  0 [/COLOR]
nouveau               621970  2 
mac80211              257001  1 b43
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27230  0 
dell_laptop            13515  0 
pcmcia_rsrc            18292  1 yenta_socket
dell_wmi               12601  0 
soundcore              12600  1 snd
cfg80211              156212  2 b43,mac80211
sparse_keymap          13666  1 dell_wmi
ttm                    65184  1 nouveau
tpm_tis                13993  0 
psmouse                73312  0 
drm_kms_helper         40745  1 nouveau
dcdbas                 14054  1 dell_laptop
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
drm                   180037  4 nouveau,ttm,drm_kms_helper
[COLOR=Red]ndiswrapper           192828  0 [/COLOR]
tpm                    21251  1 tpm_tis
tpm_bios               13460  1 tpm
i2c_algo_bit           13184  1 nouveau
ssb                    45942  1 b43
serio_raw              12990  0 
video                  18951  1 nouveau
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
firewire_ohci          31504  0 
tg3                   131476  0 
libahci                25548  1 ahci
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core

******************************************************************************************
interfaces
******************************************************************************************
auto lo
iface lo inet loopback


******************************************************************************************
resolv.conf
******************************************************************************************
# Generated by NetworkManager
nameserver 4.2.2.2

******************************************************************************************
Modules file
******************************************************************************************
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
ndiswrapper
ndiswrapper

******************************************************************************************
Blacklist file
******************************************************************************************
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
#blacklist bcm43xx

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

******************************************************************************************
Files in folder /etc/modprobe.d/*
******************************************************************************************
/etc/modprobe.d/alsa-base.conf
/etc/modprobe.d/blacklist
/etc/modprobe.d/blacklist-ath_pci.conf
/etc/modprobe.d/blacklist.conf
/etc/modprobe.d/blacklist-firewire.conf
/etc/modprobe.d/blacklist-framebuffer.conf
/etc/modprobe.d/blacklist-local.conf
/etc/modprobe.d/blacklist-modem.conf
/etc/modprobe.d/blacklist-oss.conf
/etc/modprobe.d/blacklist-rare-network.conf
/etc/modprobe.d/blacklist-watchdog.conf
/etc/modprobe.d/ndiswrapper.conf

******************************************************************************************
NetworkManager.state
******************************************************************************************

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

******************************************************************************************
nm_applet_file
******************************************************************************************
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false


******************************************************************************************
  network info 
******************************************************************************************

: error fetching interface information: Device not found
DEBUG: Interface value null in call_get_and_parse_route
```



Since you are running the correct driver for your card (b43) I believe I  would try removing ndiswrapper (you must have tried it sometime) since  there seems to be some random happenings sometime and having multiple drivers often causes problems. You could either do  it with synaptic ( how I would!) or

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a


```

---

### Post by sentinelace on 2011-11-27
I am still getting a ton of drops.  Kernel issue?  Here is my code now

```
[code]
Version: 2.0 (Development)
Sun Nov 27 23:00:38 EST 2011

******************************************************************************************
Running networking services
******************************************************************************************
network-manager is installed
network-manager start/running, process 659
network-manager is running
******************************************************************************************
    Ubuntu release 
******************************************************************************************

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

******************************************************************************************
    Kernel
******************************************************************************************

Linux jasonp-Laptop 2.6.38-12-generic #51-Ubuntu SMP Wed Sep 28 14:25:20 UTC 2011 i686 i686 i386 GNU/Linux

******************************************************************************************
      lshw  List of network devices
******************************************************************************************

  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f1ffc000-f1ffffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:81:cd:9b
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=5755m-v3.29 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:47 memory:f1bf0000-f1bfffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7e:bd:e0:5d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-12-generic firmware=410.2160 ip=192.168.5.24 link=yes multicast=yes wireless=IEEE 802.11bg

******************************************************************************************
    pci devices
******************************************************************************************

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
    Subsystem: Dell Device [1028:01ff]
    Kernel driver in use: tg3

******************************************************************************************
    usb devices
******************************************************************************************

Bus 007 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 007 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
******************************************************************************************
    List of drivers
******************************************************************************************

Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
joydev                 17322  0 
arc4                   12473  2 
snd_hda_codec_idt      60537  1 
b43                   296610  0 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
nouveau               621925  2 
pcmcia                 39671  0 
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    65184  1 nouveau
mac80211              257001  1 b43
drm_kms_helper         40971  1 nouveau
dell_laptop            13515  0 
dell_wmi               12601  0 
sparse_keymap          13666  1 dell_wmi
yenta_socket           27230  0 
soundcore              12600  1 snd
drm                   184164  4 nouveau,ttm,drm_kms_helper
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
cfg80211              156212  2 b43,mac80211
psmouse                73312  0 
dcdbas                 14054  1 dell_laptop
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
tpm_tis                13993  0 
i2c_algo_bit           13184  1 nouveau
tpm                    21251  1 tpm_tis
tpm_bios               13460  1 tpm
video                  18951  1 nouveau
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ahci                   21591  2 
tg3                   131476  0 
libahci                25548  1 ahci
ssb                    45942  1 b43

******************************************************************************************
interfaces
******************************************************************************************
auto lo
iface lo inet loopback


******************************************************************************************
resolv.conf
******************************************************************************************
# Generated by NetworkManager
domain neo.rr.com
search neo.rr.com
nameserver 209.18.47.61
nameserver 209.18.47.62

******************************************************************************************
Modules file
******************************************************************************************
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

******************************************************************************************
Blacklist file
******************************************************************************************
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

******************************************************************************************
Files in folder /etc/modprobe.d/*
******************************************************************************************
/etc/modprobe.d/alsa-base.conf
/etc/modprobe.d/blacklist-ath_pci.conf
/etc/modprobe.d/blacklist.conf
/etc/modprobe.d/blacklist-firewire.conf
/etc/modprobe.d/blacklist-framebuffer.conf
/etc/modprobe.d/blacklist-modem.conf
/etc/modprobe.d/blacklist-oss.conf
/etc/modprobe.d/blacklist-rare-network.conf
/etc/modprobe.d/blacklist-watchdog.conf

******************************************************************************************
NetworkManager.state
******************************************************************************************

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

******************************************************************************************
nm_applet_file
******************************************************************************************
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

no-auto-default=00:1c:23:81:cd:9b,

[ifupdown]
managed=false


******************************************************************************************
  network info 
******************************************************************************************

: error fetching interface information: Device not found
DEBUG: Interface value null in call_get_and_parse_route
```

---

