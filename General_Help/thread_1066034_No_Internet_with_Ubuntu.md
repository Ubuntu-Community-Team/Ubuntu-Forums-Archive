---
title: "No Internet with Ubuntu"
date: 2009-02-10
forum: General Help
---

### Post by ajdeagle on 2009-02-10
After the last instance in a vast succession of system crashes and data loss in, I swore never to run windows again. Microsoft is a shitty company. Every product they make sucks. I had to send my xbox 360 back 6 times to be fixed. Now it's broken again.

So, I attempted to make the switch to Linux. The system installed and looks great. The only problem is that it refuses to connect to the internet. It shows connections but it will only connect to the strongest signals, and then it is slow and disconnects after a few minutes. With Vista, my laptop (a gateway p-6301) could connect easily to a variety of networks. Now, I can't connect to anything. I have no idea what I'm doing with Linux and I can't learn, because I can't get online, except by waiting for a computer to be free in the computer lab at school. Does anyone have any suggestions as to how to fix my problem? I'd rather smash my computer than put windows back on it, but a computer without the internet is almost useless.

---

### Post by Neural oD on 2009-02-10
Firstly you need to find out a bit more information about your card - I would suggest running this on the command line, so go to Applications --> Accessories --> Terminal, then in the command line type this in: sudo lshw -C network 
This should give you fairly detailed info on your wireless card. Once you post specifics - we are able to help you. So you could just copy and paste that output here - and we can go from there

---

### Post by ajdeagle on 2009-02-10
Ok, will do. Thanks.

---

### Post by jbrown96 on 2009-02-10
I understand your frustration; unfortuantely this is one of the most inconvienant types of problems to have. In order to figure out your problem, I'm going to need to output of several files. This will be significantly easier if you have a flash drive or other sort of removable media. That way, you can save the output in text files (copying and pasting into gedit) then transfer them to an internet capable computer. 

I need the following information from the command line, which is available Apps===>Accessories===>Terminal. You can also open the text editor available in accessories as well. Then save the files in there on the flash drive.
If you have a wireless switch, make sure it is turned on before you boot!

1) to determine your hardware ```
lspci
```
2) to determine your network interfaces ```
ifconfig && iwconfig
```
3) to see if the driver loaded ```
lsmod
```
4) try to scan for wireless networks ```
iwlist scan
```
5) determine your kernel version ```
uname -a
```

This is probably overkill, but it's nice to have lots of information and it should keep you from having to provide more in the future.

---

### Post by JK3mp on 2009-02-10
If you give the provided information above it should be easy to solve. A rather common problem with wireless card capabilities. Did you install the wireless drivers for you wireless card? Or did it work like that from startup? Could be a wireless drivers not corrrect one. But ones attempting to get it to work...but failing.

---

### Post by ajdeagle on 2009-02-11
It installed drivers automatically when I installed the os. I was able to connect to the wireless network up here at school, but it stopped working after 2 or 3 minutes, even though the signal reads as maximum strength. Now it won't reconnect. I have all the requested codes. Here goes:


Ok here's all the requested information:

Ok here's the information:


andrew@al42:~$ sudo lshw -C network

[sudo] password for andrew:
 
  *-network
       description: Ethernet interface

       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       
       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 0

       bus info: pci@0000:04:00.0

       logical name: eth0

       version: 01

       serial: 00:e0:b8:db:49:b0

       capacity: 1GB/s

       width: 64 bits

       clock: 33MHz

       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair

  *-network:0

       description: Wireless interface

       physical id: 1

       logical name: wlan0

       serial: 00:c0:a8:fe:e7:56

       capabilities: ethernet physical wireless

       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

  *-network:1 DISABLED

       description: Ethernet interface

       physical id: 2

       logical name: pan0

       serial: 2e:ca:7a:0a:e4:2a

       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



--------------------------------------------------------------------------------------------------------------------------------------------------------------------------



1)



andrew@al42:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)

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

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)



-----------------------------------------------------------------------------------------------------------------------------------------------------------------------



2)



andrew@al42:~$ ifconfig && iwconfig

eth0      Link encap:Ethernet  HWaddr 00:e0:b8:db:49:b0
  
        UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:217 Base address:0xc000



lo        Link encap:Local Loopback
  
        inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:363 errors:0 dropped:0 overruns:0 frame:0

          TX packets:363 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0
 
         RX bytes:26506 (26.5 KB)  TX bytes:26506 (26.5 KB)



wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:fe:e7:56
  
        inet6 addr: fe80::2c0:a8ff:fefe:e756/64 Scope:Link

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:1294 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1487 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000
 
          RX bytes:1250993 (1.2 MB)  TX bytes:248556 (248.5 KB)



wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-FE-E7-56-37-35-00-00-00-00-00-00-00-00

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



lo        no wireless extensions.



eth0      no wireless extensions.



wmaster0  no wireless extensions.



wlan0     IEEE 802.11bg  ESSID:"SMU-GUEST"
  
        Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1A:A2:82:37:01
   
       Bit Rate=12 Mb/s   Tx-Power=27 dBm
   
       Retry min limit:7   RTS thr:off   Fragment thr=2352 B

          Power Management:off

          Link Quality=88/100  Signal level:-27 dBm

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



pan0      no wireless extensions.




------------------------------------------------------------------------------------------------------------------------------------------------------------



3)



andrew@al42:~$ lsmod

Module                  Size  Used by

ipv6                  263972  10
af_packet              25728  3
i915                   38144  2 

drm                    86056  3 i915

binfmt_misc            16904  1 

rfcomm                 44432  0 

sco                    18308  2 

bridge                 56980  0 

stp                    10628  1 bridge

bnep                   20480  2 

l2cap                  30464  6 rfcomm,bnep

bluetooth              61924  6 rfcomm,sco,bnep,l2cap

ppdev                  15620  0 

acpi_cpufreq           15500  1 

cpufreq_powersave       9856  0 

cpufreq_conservative    14600  0 

cpufreq_stats          13188  0 

cpufreq_ondemand       14988  1 

freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand

cpufreq_userspace      11396  0 
container              11520  0 

sbs                    19464  0 

sbshc                  13440  1 sbs

pci_slot               12552  0 

iptable_filter         10752  0 

ip_tables              19600  1 iptable_filter

x_tables               22916  1 ip_tables

parport_pc             39204  0 

lp                     17156  0 

parport                42604  3 ppdev,parport_pc,lp

joydev                 18368  0 
arc4                    9984  2 

ecb                    10880  2 

crypto_blkcipher       25476  1 ecb

pcspkr                 10624  0 

evdev                  17696  11 

psmouse                45200  0 

serio_raw              13444  0 
rtl8187                53120  0 

mac80211              216820  1 rtl8187

iTCO_wdt               18596  0 

iTCO_vendor_support    11652  1 iTCO_wdt

eeprom_93cx6           10240  1 rtl8187

snd_hda_intel         381488  3 

battery                18436  0 

cfg80211               32392  2 rtl8187,mac80211

snd_pcm_oss            46848  0 

snd_mixer_oss          22784  1 snd_pcm_oss

ac                     12292  0 

snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss

snd_seq_dummy          10884  0 

snd_seq_oss            38528  0
snd_seq_midi           14336  0 

snd_rawmidi            29824  1 snd_seq_midi

snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi

snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

snd_timer              29960  2 snd_pcm,snd_seq

snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

video                  25104  0 

output                 11008  1 video

snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

soundcore              15328  1 snd

wmi                    14504  0 

button                 14224  0 

shpchp                 37908  0 

pci_hotplug            35236  1 
shpchp
snd_page_alloc   16136  2 snd_hda_intel,snd_pcm

intel_agp              33724  1 

agpgart                42184  3 drm,intel_agp

ext3                  133256  1 

jbd                    55444  1 ext3

mbcache                16004  1 ext3

sr_mod                 22212  0 

cdrom                  43168  1 sr_mod

sd_mod                 42264  3 

crc_t10dif              9984  1 sd_mod

ata_piix               24580  0 

ata_generic            12932  0 

sg                     39732  0 

usb_storage            81728  0 

libusual               27156  1 usb_storage

pata_acpi              12160  0 

ahci                   37132  2 

libata                177312  4 ata_piix,ata_generic,pata_acpi,ahci

scsi_mod              155212  5 sr_mod,sd_mod,sg,usb_storage,libata

dock                   16656  1 libata

r8169                  35972  0 

ehci_hcd               43276  0 

uhci_hcd               30736  0 

usbcore               148848  6 rtl8187,usb_storage,libusual,ehci_hcd,uhci_hcd

thermal                23708  0 

processor              42156  4 acpi_cpufreq,thermal

fan                    12548  0 

fbcon                  47648  0 

tileblit               10880  1 fbcon

font                   16512  1 fbcon

bitblit                13824  1 fbcon

softcursor              9984  1 bitblit

fuse                   60828  3 



--------------------------------------------------------------------------------------------------------------------------------------------------------



4)



andrew@al42:~$ iwlist scan

lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.



wmaster0  Interface doesn't support scanning.



wlan0     Scan completed :

          Cell 01 - Address: 00:1A:A2:82:37:01

                    ESSID:"SMU-GUEST"

                    Mode:Master

                    Channel:1

                    Frequency:2.412 GHz (Channel 1)

                    Quality=84/100  Signal level:-29 dBm

                    Encryption key:off

                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

                    Extra:tsf=0000002b8a6c60e3

                    Extra: Last beacon: 96ms ago



pan0      Interface doesn't support scanning.



---------------------------------------------------------------------------------------------------------------------------------------------



5)



andrew@al42:~$ uname -a

Linux al42 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux

---

### Post by ajdeagle on 2009-02-23
Does anyone know how to fix this? I posted all the requested information.

---

