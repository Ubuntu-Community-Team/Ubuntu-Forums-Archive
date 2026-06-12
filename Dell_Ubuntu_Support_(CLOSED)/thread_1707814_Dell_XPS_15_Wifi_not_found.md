---
title: "Dell XPS 15 Wifi not found"
date: 2011-03-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Darque1137 on 2011-03-15
I just got my shiny new Dell XPS 15 - good stuff.  However, I'm having a problem getting wifi to work.  It's the Core i7 model and the NVIDIA graphics card (a separate problem that I'll deal with later - it's mostly for Windows goodies anyway).  It came with Windows 7 64-bit, and wifi worked great out of the box in Windows.  However, when I set up a dual-boot with Ubuntu 10.10, it doesn't even see the wireless card.  I reinstalled Ubuntu, this time 64-bit, and it's the exact same.

Info:

```
lspci
00:00.0 Host bridge: Intel Corporation Sandy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Cougar Point LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1)
03:00.0 Network controller: Intel Corporation Device 008a (rev 34)
04:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

``````
sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f1b00000-f1b01fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 06
       serial: 14:fe:b5:98:fe:a7
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.104 latency=0 link=yes multicast=yes port=MII speed=1GB/s
       resources: irq:48 ioport:2000(size=256) memory:f1804000-f1804fff memory:f1800000-f1803fff

``````
sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f1b00000-f1b01fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 06
       serial: 14:fe:b5:98:fe:a7
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.104 latency=0 link=yes multicast=yes port=MII speed=1GB/s
       resources: irq:48 ioport:2000(size=256) memory:f1804000-f1804fff memory:f1800000-f1803fff

``````
lsmod
Module                  Size  Used by
rfcomm                 40787  4 
binfmt_misc             7984  1 
sco                     9986  2 
bnep                   11985  2 
l2cap                  42304  16 rfcomm,bnep
parport_pc             30086  0 
ppdev                   6804  0 
joydev                 11395  0 
snd_hda_codec_intelhdmi    11032  1 
snd_hda_codec_realtek   300173  1 
i915                  334721  3 
snd_hda_intel          26147  2 
snd_hda_codec         100951  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
nouveau               569328  0 
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
ttm                    68212  1 nouveau
uvcvideo               62379  0 
drm_kms_helper         32836  2 i915,nouveau
psmouse                62080  0 
videodev               49359  1 uvcvideo
btusb                  12929  2 
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12614  1 videodev
bluetooth              59245  9 rfcomm,sco,bnep,l2cap,btusb
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    64181  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_wmi                3372  0 
dell_wmi_aio            1682  0 
sparse_keymap           3837  1 dell_wmi_aio
serio_raw               4910  0 
dell_laptop             6722  0 
dcdbas                  6910  1 dell_laptop
drm                   206198  5 i915,nouveau,ttm,drm_kms_helper
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
i2c_algo_bit            6208  2 i915,nouveau
xhci_hcd               60496  0 
intel_agp              32334  2 i915
video                  22176  1 i915
output                  2527  1 video
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
ahci                   22210  3 
libahci                26148  1 ahci
r8169                  42254  0 
mii                     5261  1 r8169

```I think these are the relevant commands...  I've been using Ubuntu for some time now, but I'm more of a casual user than a power-user - my last computer, a Dell Inspiron 700m, worked more or less fine, so I never went through this much troubleshooting on it.  Any help is appreciated - thank you!

---

### Post by Darque1137 on 2011-03-15
I should also add that it has the Intel Centrino Wireless-N 1030 with Bluetooth.

I saw elsewhere that one possible fix was to boot up Windows, cycle the wireless off and on, and then switch back to Ubuntu - didn't work.

---

### Post by nm_geo on 2011-03-16
> **Darque1137 said:**
> I should also add that it has the Intel Centrino Wireless-N 1030 with Bluetooth.

I saw elsewhere that one possible fix was to boot up Windows, cycle the wireless off and on, and then switch back to Ubuntu - didn't work.

You might try 
```
rfkill list
```paste results

I have also seen where the dell_laptop modules causes problems on some XPS dells.

[http://game-engine.co.uk/2010/06/ubuntu-10-04-and-dell-studio-xps-16-wireless-problems/](http://game-engine.co.uk/2010/06/ubuntu-10-04-and-dell-studio-xps-16-wireless-problems/)

Also try the 

```
sudo rmmod dell_laptop
```If this work you may need to blacklist the module

---

### Post by Darque1137 on 2011-03-17
Thanks, nm_geo!

```
rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```After the rmmod dell_laptop command, rfkill list returns this:

```
rfkill list
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

Edit: After reboot, nothing seems to have changed.  Left-clicking the network indicator still only shows the wired connection, and nothing for wireless.  I'm still a little confused as to why Bluetooth appears to be working, while wifi isn't - aren't they both on the same device?  Or is that the problem?

---

### Post by nm_geo on 2011-03-17
The good thing is the rfkill is not being blocked on anything.  The bad thing is as you know your wireless is not being seen or has a driver assigned. I have no personal experience with your new laptop and the wireless situation, but I don't mind trying.

Let's get something that might help.  Your choice... go to Synaptic and download 

hwinfo and it's dependency libhd16

or 
```
sudo apt-get install hwinfo
```Run this code
```
sudo hwinfo --netcard
```

---

### Post by Darque1137 on 2011-03-18
Yeah, this laptop doesn't have the usual hardware combination, either - the other threads I've seen pertaining to the XPS 15 never seem to line up square with what I'm seeing on my computer.  So thank you for helping here!  The good thing is that my old trusty-rusty laptop is still up and running, so I'm not in too much of a time crunch to get this thing sorted out.

Here are the results:
```
sudo hwinfo --netcard
> hal.1: read hal dataprocess 2108: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
24: PCI 300.0: 0280 Network controller                          
  [Created at pci.318]
  Unique ID: svHJ.W0gXacZVVbE
  Parent ID: qTvu.AnbCFkUXWo0
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:03:00.0
  SysFS BusID: 0000:03:00.0
  Hardware Class: network
  Model: "Intel Network controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x008a 
  SubVendor: pci 0x8086 "Intel Corporation"
  SubDevice: pci 0x5325 
  Revision: 0x34
  Memory Range: 0xf1b00000-0xf1b01fff (rw,non-prefetchable)
  IRQ: 11 (no events)
  Module Alias: "pci:v00008086d0000008Asv00008086sd00005325bc02sc80i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #15 (PCI bridge)

26: PCI 600.0: 0200 Ethernet controller
  [Created at pci.318]
  Unique ID: rBUF.iHyiMM6h1ED
  Parent ID: HnsE.I59C5EnOkR2
  SysFS ID: /devices/pci0000:00/0000:00:1c.5/0000:06:00.0
  SysFS BusID: 0000:06:00.0
  Hardware Class: network
  Model: "Realtek RTL8111/8168B PCI Express Gigabit Ethernet controller"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8168 "RTL8111/8168B PCI Express Gigabit Ethernet controller"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x050e 
  Revision: 0x06
  Driver: "r8169"
  Driver Modules: "r8169"
  Device File: eth0
  I/O Ports: 0x2000-0x2fff (rw)
  Memory Range: 0xf1804000-0xf1804fff (ro,non-prefetchable)
  Memory Range: 0xf1800000-0xf1803fff (ro,non-prefetchable)
  IRQ: 49 (1239 events)
  HW Address: 14:fe:b5:98:fe:a7
  Link detected: yes
  Module Alias: "pci:v000010ECd00008168sv00001028sd0000050Ebc02sc00i00"
  Driver Info #0:
    Driver Status: r8169 is active
    Driver Activation Cmd: "modprobe r8169"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #18 (PCI bridge)

```

---

### Post by nm_geo on 2011-03-18
You have fully updated your Maverick with ethernet right?  In particular the linux-firmare...


I thought all Intel wireless drivers were already a part of the kernel.

```
uname -a
```Website with some information:

[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

specific info:
# For Ubuntu 10.10 Maverick users (one of the following depending on the installed kernel. Most user should choose generic):
sudo apt-get install linux-backports-modules-compat-wireless-2.6.36-maverick-generic
sudo apt-get install linux-backports-modules-compat-wireless-2.6.36-maverick-generic-pae
sudo apt-get install linux-backports-modules-compat-wireless-2.6.36-maverick-server

Perhaps these will help.  I just don't know.

---

### Post by zornp on 2011-03-19
from what I've heard, you have to switch Bluetooth on as well to make the WiFi work!
that is all. (:

---

### Post by Darque1137 on 2011-03-19
```
uname -a
Linux XPS-Laptop 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 GNU/Linux

```

I really, really thought I was all updated, but just a few minutes ago when I put in this command, an update started, with a new kernel...  did it just come out today?  Regardless, now I'm all updated again, and nothing is changed, so I don't think that's it.

I'll dig around in that compat stuff, and see if I can find anything useful.

zornp, it appears that Bluetooth is working.  The wifi on/off hotkey, Fn+F2, turns Bluetooth on and off, and it can scan for devices.  The Bluetooth icon is in the notification area, and I can access its options.  (I happen not to have anything that uses Bluetooth yet to test it with - you gotta start somewhere, right?)  I'm wondering if Ubuntu is seeing this as just one device, a Bluetooth device, and not wifi as well.  If so, I'd trade Bluetooth for wifi, if it can only do one at a time - this is the last sticking point before I can get this computer into normal daily use, and clearly I'm not using Bluetooth much yet.

Yeah, I could use Windows, but that would make the children cry.  Besides, I've gotten rather used to Ubuntu - I haven't really even used Windows since XP, so 7 might as well be in a foreign language.  It does, however, let me test all the hardware, and lets me know just how far I have to go to get this thing up to 100%: wifi, NVIDIA card, webcam, HDMI out, use of external hard drive, wireless display, and whatever else they crammed into this thing that I haven't even found yet.  I also wonder how much of this will be solved with 11.04 - I think this computer hadn't even hit the market yet when 10.10 was released, and it's not exactly a rare model.  So 11.04 should help out with at least some of this stuff, right?

---

### Post by zornp on 2011-03-19
so I suppose your WiFi is working now?
That issue ain't really an Ubuntu one.. more of a problem with the wireless card driver.
Seems like Intel isn't keeping the linux drivers as up to date as the window's ones /: (like graphic cards)

---

### Post by nm_geo on 2011-03-19
Darque1137 I would assume your linux-firmware is updated too, but it might not hurt to check.

This coding is used by launchpad wireless helper and might (and I stress might) help us here.

```
sudo apt-get update; sudo apt-get install hwinfo grep; sudo lshw -C network; rfkill list; sudo iwlist scanning; cat /etc/network/interfaces; cat /etc/lsb-release; lspci -nn; lsusb; sudo lshw -short; uname -a; dmesg | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|ound|p54|prism|rtl|rt2|rt3|rt6|rt7|usb|witch|wl';  iwconfig; cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl'; sudo hwinfo --netcard ; cat /var/lib/NetworkManager/NetworkManager.state; sudo lsmod 

```Just copy paste in terminal;
Lots of info in that long string of commands.

---

### Post by Darque1137 on 2011-03-19
```
sudo apt-get update; sudo apt-get install hwinfo grep; sudo lshw -C network; rfkill list; sudo iwlist scanning; cat /etc/network/interfaces; cat /etc/lsb-release; lspci -nn; lsusb; sudo lshw -short; uname -a; dmesg | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|ound|p54|prism|rtl|rt2|rt3|rt6|rt7|usb|witch|wl';  iwconfig; cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl'; sudo hwinfo --netcard ; cat /var/lib/NetworkManager/NetworkManager.state; sudo lsmod
[sudo] password for darren: 
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release.gpg               
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Get:1 http://extras.ubuntu.com maverick Release.gpg [72B]            
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg        
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US 
Hit http://extras.ubuntu.com maverick Release                        
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security Release
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release                    
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://extras.ubuntu.com maverick/main Sources                             
Hit http://security.ubuntu.com maverick-security/main Sources        
Hit http://us.archive.ubuntu.com maverick-updates Release            
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://extras.ubuntu.com maverick/main amd64 Packages                      
Hit http://security.ubuntu.com maverick-security/restricted Sources  
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main amd64 Packages
Hit http://security.ubuntu.com maverick-security/restricted amd64 Packages
Hit http://security.ubuntu.com maverick-security/universe amd64 Packages
Hit http://security.ubuntu.com maverick-security/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com maverick/main Sources
Hit http://us.archive.ubuntu.com maverick/restricted Sources
Hit http://us.archive.ubuntu.com maverick/universe Sources
Hit http://us.archive.ubuntu.com maverick/multiverse Sources
Hit http://us.archive.ubuntu.com maverick/main amd64 Packages
Hit http://us.archive.ubuntu.com maverick/restricted amd64 Packages
Hit http://us.archive.ubuntu.com maverick/universe amd64 Packages
Hit http://us.archive.ubuntu.com maverick/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com maverick-updates/main Sources
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-updates/main amd64 Packages
Hit http://us.archive.ubuntu.com maverick-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com maverick-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com maverick-updates/multiverse amd64 Packages
Fetched 72B in 1s (70B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grep is already the newest version.
hwinfo is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f1b00000-f1b01fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 06
       serial: 14:fe:b5:98:fe:a7
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.104 latency=0 link=yes multicast=yes port=MII speed=1GB/s
       resources: irq:48 ioport:2000(size=256) memory:f1804000-f1804fff memory:f1800000-f1803fff
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

auto lo
iface lo inet loopback

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
00:00.0 Host bridge [0600]: Intel Corporation Sandy Bridge DRAM Controller [8086:0104] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Sandy Bridge PCI Express Root Port [8086:0101] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Sandy Bridge Integrated Graphics Controller [8086:0126] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b5)
00:1c.1 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 2 [8086:1c12] (rev b5)
00:1c.3 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 4 [8086:1c16] (rev b5)
00:1c.4 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 5 [8086:1c18] (rev b5)
00:1c.5 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 6 [8086:1c1a] (rev b5)
00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation Cougar Point LPC Controller [8086:1c4b] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation Cougar Point 6 port SATA AHCI Controller [8086:1c03] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 05)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0df4] (rev a1)
03:00.0 Network controller [0280]: Intel Corporation Device [8086:008a] (rev 34)
04:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
Bus 002 Device 003: ID 8086:0189 Intel Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0408:2fb1 Quanta Computer, Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
H/W path           Device      Class          Description
=========================================================
                               system         Dell System XPS L502X
/0                             bus            Motherboard
/0/0                           memory         128KiB BIOS
/0/19                          processor      Intel(R) Core(TM) i7-2720QM CPU @ 
/0/19/1a                       memory         64KiB L1 cache
/0/19/1b                       memory         256KiB L2 cache
/0/19/1c                       memory         6MiB L3 cache
/0/1d                          memory         8GiB System Memory
/0/1d/0                        memory         4GiB SODIMM Synchronous 1333 MHz (
/0/1d/1                        memory         4GiB SODIMM Synchronous 1333 MHz (
/0/100                         bridge         Sandy Bridge DRAM Controller
/0/100/1                       bridge         Sandy Bridge PCI Express Root Port
/0/100/1/0                     display        nVidia Corporation
/0/100/2                       display        Sandy Bridge Integrated Graphics C
/0/100/16                      communication  Cougar Point HECI Controller #1
/0/100/1a                      bus            Cougar Point USB Enhanced Host Con
/0/100/1b                      multimedia     Cougar Point High Definition Audio
/0/100/1c                      bridge         Cougar Point PCI Express Root Port
/0/100/1c.1                    bridge         Cougar Point PCI Express Root Port
/0/100/1c.1/0                  network        Intel Corporation
/0/100/1c.3                    bridge         Cougar Point PCI Express Root Port
/0/100/1c.3/0                  bus            uPD720200 USB 3.0 Host Controller
/0/100/1c.4                    bridge         Cougar Point PCI Express Root Port
/0/100/1c.5                    bridge         Cougar Point PCI Express Root Port
/0/100/1c.5/0      eth0        network        RTL8111/8168B PCI Express Gigabit 
/0/100/1d                      bus            Cougar Point USB Enhanced Host Con
/0/100/1f                      bridge         Cougar Point LPC Controller
/0/100/1f.2        scsi0       storage        Cougar Point 6 port SATA AHCI Cont
/0/100/1f.2/0      /dev/sda    disk           500GB ST9500420AS
/0/100/1f.2/0/1    /dev/sda1   volume         101MiB Windows FAT volume
/0/100/1f.2/0/2    /dev/sda2   volume         14GiB Windows NTFS volume
/0/100/1f.2/0/3    /dev/sda3   volume         93GiB Windows NTFS volume
/0/100/1f.2/0/4    /dev/sda4   volume         357GiB Extended partition
/0/100/1f.2/0/4/5  /dev/sda5   volume         27GiB Linux filesystem partition
/0/100/1f.2/0/4/6  /dev/sda6   volume         14GiB Linux swap / Solaris partiti
/0/100/1f.2/0/4/7  /dev/sda7   volume         314GiB Linux filesystem partition
/0/100/1f.2/1      /dev/cdrom  disk           DVD+-RW TS-L633J
/0/100/1f.3                    bus            Cougar Point SMBus Controller
/1                             power          DELL
Linux XPS-Laptop 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 GNU/Linux
[    0.000000] No AGP bridge found
[    0.000000] No NUMA configuration found
[    0.000000] No AGP bridge found
[    1.607588] ACPI: No dock devices found.
[    1.694224] HEST: Table is not found!
[    1.694572] usbcore: registered new interface driver usbfs
[    1.694580] usbcore: registered new interface driver hub
[    1.694599] usbcore: registered new device driver usb
[    1.695101] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.697121] Switching to clocksource tsc
[    1.705825] pnp: PnP ACPI: found 11 devices
[    1.867979] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    1.868801] ACPI: Lid Switch [LID0]
[    1.872689] ERST: Table is not found!
[    1.901589] hub 1-0:1.0: USB hub found
[    1.931540] hub 2-0:1.0: USB hub found
[    1.936632] device-mapper: multipath: version 1.1.1 loaded
[    1.936634] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.941323] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.980530] r8169 0000:06:00.0: eth0: RTL8168b/8111b at 0xffffc90005800000, 14:fe:b5:98:fe:a7, XID 0c200000 IRQ 48
[    2.037842] ata2: SATA max UDMA/133 abar m2048@0xf1c08000 port 0xf1c08180 irq 49
[    2.216793] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    2.367287] hub 1-1:1.0: USB hub found
[    2.496468] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    2.646977] hub 2-1:1.0: USB hub found
[    2.726464] usb 1-1.4: new high speed USB device using ehci_hcd and address 3
[    2.926223] usb 2-1.5: new full speed USB device using ehci_hcd and address 3
[   11.878222] lp: driver loaded but no devices found
[   11.919799] usb usb3: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[   11.919920] hub 3-0:1.0: USB hub found
[   11.948237] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_2HDM (0408:2fb1)
[   11.950900] uvcvideo: No streaming interface found for terminal 6.
[   11.950964] input: Laptop_Integrated_Webcam_2HDM as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input6
[   11.951010] usbcore: registered new interface driver uvcvideo
[   11.999324] usbcore: registered new interface driver btusb
[   12.294815] VGA switcheroo: detected DSM switching method \_SB_.PCI0.PEG0.PEGP handle
[   14.049281] Console: switching to colour frame buffer device 170x48
[   14.097932] r8169 0000:06:00.0: eth0: link up
[   14.097938] r8169 0000:06:00.0: eth0: link up
[   24.265687] eth0: no IPv6 routers present
[ 2785.885831] usb usb3: USB disconnect, address 1
[ 2788.289206] btusb_intr_complete: hci0 urb ffff880226825600 failed to resubmit (1)
[ 2788.289243] btusb_bulk_complete: hci0 urb ffff8802268253c0 failed to resubmit (1)
[ 2788.289393] btusb_bulk_complete: hci0 urb ffff880226825f00 failed to resubmit (1)
[ 2790.396540] SMP alternatives: switching to UP code
[ 2790.406056] SMP alternatives: switching to SMP code
[ 2792.738904] PM: resume of drv:usb dev:1-1 complete after 217.254 msecs
[ 2792.738939] PM: resume of drv:usb dev:2-1 complete after 217.250 msecs
[ 2792.828911] usb 1-1.4: reset high speed USB device using ehci_hcd and address 3
[ 2793.022229] usb 2-1.5: reset full speed USB device using ehci_hcd and address 3
[ 2793.080954] PM: resume of drv:usb dev:1-1.4 complete after 559.624 msecs
[ 2793.080988] PM: resume of drv:usb dev:1-1.4:1.2 complete after 559.633 msecs
[ 2793.132132] btusb 2-1.5:1.0: no reset_resume for driver btusb?
[ 2793.132140] btusb 2-1.5:1.1: no reset_resume for driver btusb?
[ 2793.388339] PM: resume of drv:usb dev:2-1.5 complete after 867.328 msecs
[ 2793.388351] PM: resume of drv:usb dev:2-1.5:1.1 complete after 867.323 msecs
[ 2793.388384] PM: resume of drv:usb dev:2-1.5:1.0 complete after 867.364 msecs
[ 2794.384277] r8169 0000:06:00.0: eth0: link down
[ 2794.384291] r8169 0000:06:00.0: eth0: link down
[ 2794.385719] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2794.409666] usb usb3: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[ 2794.409738] hub 3-0:1.0: USB hub found
[ 2796.421248] r8169 0000:06:00.0: eth0: link up
[ 2796.422713] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2807.056712] eth0: no IPv6 routers present
lo        no wireless extensions.

eth0      no wireless extensions.

# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt
options iwlagn 11n_disable=0
> hal.1: read hal dataprocess 2845: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
24: PCI 300.0: 0280 Network controller                          
  [Created at pci.318]
  Unique ID: svHJ.W0gXacZVVbE
  Parent ID: qTvu.AnbCFkUXWo0
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:03:00.0
  SysFS BusID: 0000:03:00.0
  Hardware Class: network
  Model: "Intel Network controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x008a 
  SubVendor: pci 0x8086 "Intel Corporation"
  SubDevice: pci 0x5325 
  Revision: 0x34
  Memory Range: 0xf1b00000-0xf1b01fff (rw,non-prefetchable)
  IRQ: 11 (no events)
  Module Alias: "pci:v00008086d0000008Asv00008086sd00005325bc02sc80i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #15 (PCI bridge)

26: PCI 600.0: 0200 Ethernet controller
  [Created at pci.318]
  Unique ID: rBUF.iHyiMM6h1ED
  Parent ID: HnsE.I59C5EnOkR2
  SysFS ID: /devices/pci0000:00/0000:00:1c.5/0000:06:00.0
  SysFS BusID: 0000:06:00.0
  Hardware Class: network
  Model: "Realtek RTL8111/8168B PCI Express Gigabit Ethernet controller"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8168 "RTL8111/8168B PCI Express Gigabit Ethernet controller"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x050e 
  Revision: 0x06
  Driver: "r8169"
  Driver Modules: "r8169"
  Device File: eth0
  I/O Ports: 0x2000-0x2fff (rw)
  Memory Range: 0xf1804000-0xf1804fff (ro,non-prefetchable)
  Memory Range: 0xf1800000-0xf1803fff (ro,non-prefetchable)
  IRQ: 48 (29895 events)
  HW Address: 14:fe:b5:98:fe:a7
  Link detected: yes
  Module Alias: "pci:v000010ECd00008168sv00001028sd0000050Ebc02sc00i00"
  Driver Info #0:
    Driver Status: r8169 is active
    Driver Activation Cmd: "modprobe r8169"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #18 (PCI bridge)

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
Module                  Size  Used by
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_intelhdmi    11032  1 
rfcomm                 40787  4 
snd_hda_codec_realtek   300173  1 
sco                     9986  2 
bnep                   11985  2 
binfmt_misc             7984  1 
l2cap                  42304  16 rfcomm,bnep
snd_hda_intel          26147  2 
snd_hda_codec         100951  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
i915                  334721  3 
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 11395  0 
intel_agp              32334  2 i915
snd                    64181  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
nouveau               569328  0 
ttm                    68212  1 nouveau
dcdbas                  6910  0 
drm_kms_helper         32836  2 i915,nouveau
drm                   206198  5 i915,nouveau,ttm,drm_kms_helper
i2c_algo_bit            6208  2 i915,nouveau
btusb                  12929  2 
bluetooth              59245  9 rfcomm,sco,bnep,l2cap,btusb
uvcvideo               62379  0 
videodev               49359  1 uvcvideo
psmouse                63366  0 
v4l1_compat            15519  2 uvcvideo,videodev
xhci_hcd               60496  0 
video                  22176  1 i915
serio_raw               4910  0 
v4l2_compat_ioctl32    12614  1 videodev
output                  2527  1 video
lp                     10201  0 
dell_wmi                3372  0 
parport                37032  3 parport_pc,ppdev,lp
ahci                   22210  3 
r8169                  42254  0 
libahci                26148  1 ahci
mii                     5261  1 r8169

```

What's a D-Bus?  (Like, other than something to ride in the city?)

---

### Post by nm_geo on 2011-03-20
I was doing a search on your network controller and found a message where a German guy had the same problem. He said he re-installed Maverick 10.10 from USB drive and he was able to get the wireless working after that.  Might be something to try, I am at a loss. I had to get Google to translate the message LOL

Google this 

Network controller [0280]: Intel Corporation Device [8086:008a] (rev 34)

---

### Post by seess on 2011-03-22
> **zornp said:**
> so I suppose your WiFi is working now?
That issue ain't really an Ubuntu one.. more of a problem[r4](http://www.r4-ds-r4i.fr) with the wireless card driver.
Seems like Intel isn't keeping the linux drivers as up to date as the window's ones /: (like graphic cards)
That sounds good, but it is a little difficult to do it. I have similar experience.

---

### Post by bakeha on 2011-03-24
I have this problem as well on a new Dell XPS 15. I thought that the wireless card was supported on Linux when I bought the machine. The nvidia drivers are a problem as well.

---

### Post by bigman921 on 2011-03-29
I just worked this out in fedora, but since I saw this issue here I thought I'd cross the streams.  The nice folks at intel let me know that fedora 14's kernel (2.6.36) is just too old and doesn't have the right modules in it.  I upgraded to 2.6.38 and it worked perfectly.  I have no idea on ubuntu's kernels but thats the first thing I'd check.

Marc

---

### Post by Xbuntu1 on 2011-03-29
did any one try to go to system>Administration>Additional Drivers....I found the drivers here for wifi on my Dell inspiron

---

### Post by ezwrighter on 2011-04-01
Confirm this exact issue on a Brand new Dell XPS 15, running from a Live CD of 10.10 with Intel Centrino Advanced-N 6230 mini-pci card.

I am going to try the 11.04 beta that came out yesterday and see if the problem still persists with the newer Kernel.

---

### Post by ezwrighter on 2011-04-01
11.04 Beta 1 resolves this issue.  I assume it relates to the latest kernel update and probably fixed intel drivers.  Hopefully we are getting close on the 11.04 release so I can get this bad boy dual booting!  Windows for Games and Linux for real work....

---

### Post by andersonvom on 2011-04-02
I have a Centrino Wireless-1030 and, thanks to **[COLOR=Blue][this post]("http://ubuntuforums.org/showpost.php?p=10622097&postcount=3")[/COLOR]**, just solved this issue **[COLOR=Blue][updating the kernel to 2.6.38]("http://berm0o0da.wordpress.com/2011/01/31/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa/")[/COLOR]** and then updating everything else on the system.

Let us know if that works for you too.

---

### Post by Darque1137 on 2011-04-03
Thanks to some other issues, I sort of put this on the back burner until I could test-drive the new Natty Narwhal 11.04...  Success!

One thing, though: Natty wouldn't install with the live CD's additional software option, which would allow for Flash.  If I tried, all I got was a Grub prompt at boot, although I had already noticed that the wifi worked on the live CD.  I retried the install without that, and it worked.  Now, let's see if installing Flash will break anything.

Edit: A few minutes later...

Installing Flash again broke the system.  But, instructions [here]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/527273") saved the day...  at least until I want something out of the partners repository, I guess.

But still, I think that means 11.04 was the fix I needed.

---

### Post by ashikaga on 2011-04-04
> **ezwrighter said:**
> 11.04 Beta 1 resolves this issue.  I assume it relates to the latest kernel update and probably fixed intel drivers.  Hopefully we are getting close on the 11.04 release so I can get this bad boy dual booting!  Windows for Games and Linux for real work....

I've got 11.04 Beta 1 installed alongside Win 7, can confirm also that wireless works.

---

### Post by nm_geo on 2011-04-04
> **Darque1137 said:**
> Thanks to some other issues, I sort of put this on the back burner until I could test-drive the new Natty Narwhal 11.04...  Success!

One thing, though: Natty wouldn't install with the live CD's additional software option, which would allow for Flash.  If I tried, all I got was a Grub prompt at boot, although I had already noticed that the wifi worked on the live CD.  I retried the install without that, and it worked.  Now, let's see if installing Flash will break anything.

Edit: A few minutes later...

Installing Flash again broke the system.  But, instructions [here]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/527273") saved the day...  at least until I want something out of the partners repository, I guess.

But still, I think that means 11.04 was the fix I needed.

Darque1137

Would you run the 

```
sudo lshw -C network 
```and post here just curious.  Glad Natty worked for you it makes sense as Natty 11.04 has the most current stable kernel.  Be sure to keep it up-to-date and since it has just moved into beta stage it will require frequent updates.
:P
Some of the testers are having good luck installing Natty by disconnecting their ethernet cable during the install.  You might want to visit the Natty Forum.
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

---

### Post by Darque1137 on 2011-04-07
```
*-network               
       description: Wireless interface
       product: Centrino Wireless-N 1030
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: bc:77:37:09:9b:e2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=17.168.5.2 build 35905 ip=192.168.1.136 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:53 memory:f1b00000-f1b01fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 06
       serial: 14:fe:b5:98:fe:a7
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f1804000-f1804fff memory:f1800000-f1803fff

```

And this is after yet another big update last night...  Hey, look, it finally recognizes the wireless card, not as a standard Intel product, but as a Centrino Wireless-N 1030.  Sweet!

---

### Post by wmaciel on 2011-04-15
Hi, sorry to piggy back on this thread, but I thought it would be better than to open a new one.

I'm having the same problem Darque was having, but upgrading to Natty didn't work.

I also have the Centrino 1030 on a Dell XPS 15, and from what I've read on the post my specification pretty much match Darque's.

Do you have any other hint I could follow to solve this?

Thank you

---

### Post by wmaciel on 2011-04-15
I was browsing the internet searching for any clue and then I ran across this page:

[http://intellinuxwireless.org/](http://intellinuxwireless.org/)

which says that:
Intel® Centrino® Wireless-N 1030 requires a minimum kernel version of 2.6.36

Checking my old laptop with maverick, I saw that the kernel version is 2.6.35

I'm guessing, that's it?
I'll have to wait for the Natty release?
Isn't there a way to update the kernel or to download a driver directly?

Please, I need your help, guys.

---

### Post by nm_geo on 2011-04-16
> **wmaciel said:**
> I was browsing the internet searching for any clue and then I ran across this page:

[http://intellinuxwireless.org/](http://intellinuxwireless.org/)

which says that:
Intel® Centrino® Wireless-N 1030 requires a minimum kernel version of 2.6.36

Checking my old laptop with maverick, I saw that the kernel version is 2.6.35

I'm guessing, that's it?
I'll have to wait for the Natty release?
Isn't there a way to update the kernel or to download a driver directly?

Please, I need your help, guys.

The Natty 11.04 is in the last stage of testing and pretty stable.  I started testing when it first was available and believe me it is much better now.  

You could get the latest current daily build for your machine install it and give it a try or wait a short while.  That is up to you.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Then if you have problems this forum is all about Natty.

[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

2010/10/28 Developer Summit
2010/11/25 Feature Definition Freeze
2010/12/02 **Alpha 1**  	
2010/12/30 Debian Import Freeze
2011/02/03 **Alpha 2**
2011/02/24 Feature Freeze
2011/03/03 **Alpha 3**
2011/03/24 UI Freeze
2011/03/31 **Beta 1**
2011/04/14 **Beta 2** & Final Freeze
2011/04/28 **[COLOR=Red]Ubuntu 11.04[/COLOR]**

---

### Post by theunsheydenrych on 2011-04-22
I can confirm that the wifi is working after i installed the 2.6.38 kernel.

I have a Dell XPS 17 702x , with Ubuntu 10.04 (Lucid Lynx)

You helped a lot in sorting this issue out, thanks

---

