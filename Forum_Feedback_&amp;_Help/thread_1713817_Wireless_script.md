---
title: "Wireless script"
date: 2011-03-24
forum: Forum Feedback &amp; Help
---

### Post by Hippytaff on 2011-03-24
I have a wireless diagnostic scrip...it' aint great, but it does all the thing that usually take 20 posts to establish - but new users on this forum obviously don't trust some bloke saying run this script I've attached...for obvious reason.

What can I do?

---

### Post by Elfy on 2011-03-24
Not much more than use it and see if they use it.

However, it must be said that if the script is good and works it will still be there and so will you :)

If the script was malicious, the post would be gone fairly quickly as has happened in the past, with the likelihood that you would be as well ...

---

### Post by Hippytaff on 2011-03-24
That's it...the only malicious bit is the fact it asks you if you want to run the script even though the only reason you're running the scripts is because you want to run the script.

thanks for responding :-)

---

### Post by Ozitraveller on 2011-03-24
I like it! :)

Thanks

I also do:
less /etc/udev/rules.d/70-persistent-net.rules
dmesg

---

### Post by Hippytaff on 2011-03-24
> **Ozitraveller said:**
> I like it! :)

Thanks

I also do:
less /etc/udev/rules.d/70-persistent-net.rules
dmesg

cheers for the positive feedback.

and that addition to the script is most welcome - Excellent...I'll add it

---

### Post by Elfy on 2011-03-24
If you could get the results to add code tags I'm sure that will be of enormous help to people reading the results - for an example look for a bootscript result that the OP's not put in code tags :)

Good work though - anything to help people get help is well received.

---

### Post by Hippytaff on 2011-03-24
Thats doable and yes I've seen far to many unruly bootscript RESULTS.txt posts. My obsessive compulsive nature insists I tag them if I see them and if I cannot help I just explain that I'm tagging them for readability...then drs, duck or Rubi usually sort the actual problem :-)

Thank you for the positiveness

---

### Post by coffeecat on 2011-03-24
@Hippytaff, that's an excellent idea. Good luck with it. And if you can get the thing to add in code tags, that's something not even the boot script does - yet! :)

---

### Post by Hippytaff on 2011-03-25
```

************************************
        Ubuntu release 
************************************

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

************************************
        Kernel
************************************

Linux lptp-1 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux

************************************
        pci wireless devices
************************************

06:05.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Hewlett-Packard Company Compaq nw8240/nx8220 [103c:12f6]
    Kernel driver in use: ipw2200
    Kernel modules: ipw2200

************************************
        usb wireless devices
************************************


************************************
        List of network devices
************************************

  *-network:0
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth1
       version: 05
       serial: 00:15:00:17:b6:b5
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.2 latency=128 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:20 memory:b0106000-b0106fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:d8:6e:b8
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:20 ioport:3000(size=256) memory:b0109400-b01094ff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

************************************
          List of drivers
************************************

Module                  Size  Used by
michael_mic             1744  4 
arc4                    1165  2 
lib80211_crypt_tkip     7736  1 
aes_i586                7280  1 
aes_generic            26875  1 aes_i586
lib80211_crypt_ccmp     4477  1 
binfmt_misc             6599  1 
vboxnetadp              6454  0 
vboxnetflt             15152  0 
vboxdrv               190199  2 vboxnetadp,vboxnetflt
parport_pc             26058  0 
ppdev                   5556  0 
pcmcia                 35973  0 
snd_intel8x0           25664  3 
joydev                  8767  0 
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  3 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4588  0 
ipw2200               136715  0 
snd_rawmidi            17783  1 snd_seq_midi
yenta_socket           21518  0 
i915                  295435  4 
libipw                 39808  1 ipw2200
snd_seq_midi_event      6047  1 snd_seq_midi
pcmcia_rsrc            10566  1 yenta_socket
cfg80211              144694  2 ipw2200,libipw
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         30200  1 i915
drm                   168060  4 i915,drm_kms_helper
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
lib80211                5058  4 lib80211_crypt_tkip,lib80211_crypt_ccmp,ipw2200,libipw
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
snd                    49038  12 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
output                  1883  1 video
soundcore                880  1 snd
intel_agp              26566  2 i915
tifm_7xx1               3766  0 
psmouse                59033  0 
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
agpgart                32011  2 drm,intel_agp
tifm_core               6089  1 tifm_7xx1
hp_wmi                  5223  0 
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
lp                      7342  0 
serio_raw               4022  0 
parport                31492  3 parport_pc,ppdev,lp
8139too                19581  0 
sdhci_pci               6601  0 
firewire_ohci          21234  0 
firewire_core          46643  1 firewire_ohci
8139cp                 16934  0 
sdhci                  15922  1 sdhci_pci
led_class               2633  1 sdhci
mii                     4425  2 8139too,8139cp
crc_itu_t               1383  1 firewire_core

************************************
           network info
************************************

eth0      Link encap:Ethernet  HWaddr 00:0a:e4:d8:6e:b8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0x3000 

eth1      Link encap:Ethernet  HWaddr 00:15:00:17:b6:b5  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:ff:fe17:b6b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:896728 errors:14 dropped:14 overruns:0 frame:0
          TX packets:601452 errors:0 dropped:11 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1147759918 (1.1 GB)  TX bytes:51823732 (51.8 MB)
          Interrupt:20 Base address:0x4000 Memory:b0106000-b0106fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1408 (1.4 KB)  TX bytes:1408 (1.4 KB)


************************************
 Wireless specific network info
************************************

lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"TALKTALK-3E3CFB"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 1C:BD:B9:3E:3C:FB   
          Bit Rate:12 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/100  Signal level=-64 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:14  Rx invalid frag:0
          Tx excessive retries:42  Invalid misc:0   Missed beacon:10

************************************
 Rfkill Blocks
************************************

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

************************************
 persistent Rules
************************************

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0a:e4:d8:6e:b8", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4220 (ipw2200)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:15:00:17:b6:b5", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
demsg: No such file or directory

************************************
Fri Mar 25 22:58:21 GMT 2011

```

Got code tags sorted :-)

---

### Post by Hippytaff on 2011-03-25
It's a work in progress, but I've uploaded the script to sourceforge...Thanks matt..hopefully we will improve the script drastically :-)

[http://sourceforge.net/projects/wirelessscript/files/](http://sourceforge.net/projects/wirelessscript/files/)

---

### Post by Elfy on 2011-03-26
> **Hippytaff said:**
> It's a work in progress, but I've uploaded the script to sourceforge...Thanks matt..hopefully we will improve the script drastically :-)

[http://sourceforge.net/projects/wirelessscript/files/](http://sourceforge.net/projects/wirelessscript/files/)

Cracking :)

Code tags - crackinger :P

---

### Post by Hippytaff on 2011-03-29
Thanks to some excellent work by Matt Symes, the wireless-script has undergone a massive improvement...it is continuing to be developed but the improved wireless_script_1.1 is available at [sourceforge]("http://sourceforge.net/projects/wirelessscript/files/")

---

