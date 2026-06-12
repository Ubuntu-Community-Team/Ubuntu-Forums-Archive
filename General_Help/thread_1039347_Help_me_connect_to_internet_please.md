---
title: "Help me connect to internet please"
date: 2009-01-14
forum: General Help
---

### Post by pedramslhr on 2009-01-14
hi
I connected through an ADSL connection to internet via a modem that is plugged to my Ethernet  port before.
I think it was some days ago that every thing was going well.
Modem is configured to connect to internet automatically, and what I should do is just setting IP addresses.
It is done as it was before but I con not connect to internet or even ping my modem address that is 192.168.1.1

And I should say that I have installed some update that seem to be about network, as I remember.

I'm really confused, help please.
thanks!

---

### Post by matey3 on 2009-01-14
go in the terminal and type in 
ifconfig
and see what address is assigned to eth0

you can also type in 
dhclient
or
/etc/init.d/networking restart
to restart the network.
if you are getting IP address then your DHCP is working, use the terminal and type in
ping google.com
see if you get reply, use control-C to break that or it will keep pinging.
if you get an error message like host is unavailable then you are not connecting to the Internet.
reboot your router/modem and wait a minute and restart the network test.
i am not that good at this myself but I hope someone can help you.

BTW If you use the GUI network administration program, it usually locks your network card (If I remember correctly, been a while) The best thing is to always use the command prompt (terminal) I have had bad luck with the GUI (windows) stuff and networking before)!

---

### Post by pedramslhr on 2009-01-14
It is really strange!
I tried to connect to internet these days.

and now when I started Ubuntu to test your solution, before doing any thing it was connected to internet.

:shock:

---

### Post by redilyn on 2009-01-14
It is possible your ISP was having connectivity issues.

When your internet stops working it is best to try unplugging your modem/router for 1-2 minutes and then plugging it back in.

That was the first thing I always tried when I was a tech support agent @ a call center (worst job ever) and it worked about 60% of the time.

---

### Post by pedramslhr on 2009-01-14
I'm sure problem was not with my ISP. becaause I could access internet in windows while it was not possible in ubuntu

---

### Post by albinootje on 2009-01-14
> **pedramslhr said:**
> 
And I should say that I have installed some update that seem to be about network, as I remember.


Can you please post the output of the following :
```

sudo lshw -C network
lspci
lsmod
sudo dhclient
route -n
cat /etc/resolv.conf
cat /etc/network/interfaces

```
Thanks.

---

### Post by pedramslhr on 2009-01-14
lshw -C network
```
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:57:e5:56
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.10 latency=0 module=r8169 multicast=yes

```
lspci
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
06:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
08:05.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
08:05.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
08:05.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
```
lsmod
```
Module                  Size  Used by
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
sbs                    15112  0 
container               5632  0 
dock                   11280  0 
sbshc                   7680  1 sbs
pppoe                  14528  0 
pppox                   4876  1 pppoe
af_packet              23812  0 
ppp_generic            29588  2 pppoe,pppox
slhc                    7040  1 ppp_generic
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter

x_tables               16132  1 ip_tables
sbp2                   24072  0 
joydev                 13120  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
ipv6                  267780  10 
uvcvideo               58116  0 
snd_hda_intel         344728  6 
compat_ioctl32          2304  1 uvcvideo
snd_pcm_oss            42144  0 
sdhci                  19076  0 
videodev               29440  1 uvcvideo
snd_mixer_oss          17920  1 snd_pcm_oss
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
psmouse                40336  0 
mmc_core               51460  1 sdhci
snd_pcm                78596  3 snd_hda_intel,snd_pcm_oss
nvidia               7825536  36 
serio_raw               7940  0 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
ieee80211_crypt         7040  0 
i2c_core               24832  1 nvidia
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
battery                14212  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ac                      6916  0 
snd                    56996  21 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi_acer                9644  0 
video                  19856  8 
output                  4736  1 video
intel_agp              25492  0 
button                  9232  0 
agpgart                34760  2 nvidia,intel_agp
soundcore               8800  1 snd
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
pcspkr                  4224  0 
evdev                  13056  8 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
dcdbas                  9504  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sg                     36880  0 
ata_piix               19588  0 
sd_mod                 30720  3 
usbhid                 31872  0 
hid                    38784  1 usbhid
ata_generic             8324  0 
ahci                   28420  2 
pata_acpi               8320  0 
ohci1394               33584  0 
libata                159344  4 ata_piix,ata_generic,ahci,pata_acpi
ieee1394               93752  2 sbp2,ohci1394
scsi_mod              151436  5 sbp2,sr_mod,sg,sd_mod,libata
r8169                  32900  0 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  5 uvcvideo,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 

```
route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
```
cat /etc/resolv.conf
```
nameserver 85.15.1.12
nameserver 85.15.1.10
```
cat /etc/network/interfaces
```
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider




iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1



auto eth0

```

---

### Post by albinootje on 2009-01-14
> **pedramslhr said:**
> 
cat /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

```
Thanks!
Are you using Ubuntu with the default Network Manager ?
Or wicd from [http://wicd.sf.net](http://wicd.sf.net) ?
Or did you edit /etc/network/interfaces yourself ?

Perhaps your router doesn't answer ping requests ?
Can you browse to [http://192.168.1.1](http://192.168.1.1) ?
And in a terminal :
```

mtr 192.168.1.1
ping 62.108.1.65

```

---

### Post by pedramslhr on 2009-01-15
sorry I'm late
in fact what I have done is just setting IP addresses and DNS servers through System>administration>network

problem is that it some times works (I can ping 192.168.1.1) and some times doesn't.

---

### Post by albinootje on 2009-01-15
> **pedramslhr said:**
> sorry I'm late
in fact what I have done is just setting IP addresses and DNS servers through System>administration>network

problem is that it some times works (I can ping 192.168.1.1) and some times doesn't.

Please post the output of 
```

dmesg

```
at the moment you can't ping it anymore.

---

### Post by pedramslhr on 2009-01-17
> **albinootje said:**
> Please post the output of 
```

dmesg

```
at the moment you can't ping it anymore.
ok dude. thank you for your attention.
I will post the result whenever it iis not possible to ping modem

---

### Post by pedramslhr on 2009-01-17
OK, I tested it again. and for another time "192.168.1.1" was unreachable.
So as you said I put dmesg command result here now as an attachment.

and what I did was turning off the modem restarting my computer and turning on the modem again. and it works.
But problem seems to continue again next times.
thank you!

---

### Post by albinootje on 2009-01-17
> **pedramslhr said:**
> OK, I tested it again. and for another time "192.168.1.1" was unreachable.


Thanks for the output.
> 
[   31.279698] PCI: Using ACPI for IRQ routing
[   31.279699] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
-- cut --
[    8.706152] NETDEV WATCHDOG: eth0: transmit timed out
[    8.872135] r8169: eth0: link up


Here's a recommendation to try :
[http://graag.blogspot.com/2007/12/netdev-watchdog-eth0-transmit-timed-out.html](http://graag.blogspot.com/2007/12/netdev-watchdog-eth0-transmit-timed-out.html)

---

