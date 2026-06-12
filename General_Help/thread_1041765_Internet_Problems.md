---
title: "Internet Problems"
date: 2009-01-16
forum: General Help
---

### Post by DeadRobot on 2009-01-16
I am running on a MacbookPro 1,1 with Ubuntu 8.04.

Basically, today I got Ubuntu up and running and EVERYTHING was working great.  I had wireless interent acess and everything.

Then later today I turn on my computer and i just cant get it to connect to the internet.  It doesnt even detect the network.  

I can go back into Mac OSX and get on the internet fine but not with ubuntu.

Here are some results of commands in the terminal:
```




 lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port [8086:27a1] (rev 03)
00:07.0 Performance counters [1101]: Intel Corporation Unknown device [8086:27a3] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M56P [Radeon Mobility X1600] [1002:71c5]
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller [11ab:4362] (rev 22)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
0c:03.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW323 [11c1:5811] (rev 61)




lsusb
Bus 005 Device 008: ID 0930:6545 Toshiba Corp. 
Bus 005 Device 004: ID 05ac:8300 Apple Computer, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 05ac:8205 Apple Computer, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 05ac:8240 Apple Computer, Inc. IR Receiver [build-in]
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 413c:3016 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 05ac:0217 Apple Computer, Inc. 
Bus 001 Device 001: ID 0000:0000  




lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 22
       serial: 00:16:cb:94:8e:72
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0






```

Any idea with whats up?

And is there a way to just restore the whole thing?  basically just wiping out all my stuff and starting with a clean ubuntu?
would that help fix it?

---

### Post by dcstar on 2009-01-16
> **DeadRobot said:**
> I am running on a MacbookPro 1,1 with Ubuntu 8.04.

Basically, today I got Ubuntu up and running and EVERYTHING was working great.  I had wireless interent acess and everything.

Then later today I turn on my computer and i just cant get it to connect to the internet.  It doesnt even detect the network.  
.......

Post this output:

```
ifconfig
netstat -rn
```

---

### Post by MaindotC on 2009-01-16
And
```

iwlist scan

```
Strange that your wireless card was working seeing as how the wireless card not working is a known bug...

---

### Post by FIONEX on 2009-01-16
also post the output of "lsmod".  We need to know if your wireless driver is being loaded.  Sometimes, loading drivers in a certain order is to blame...

---

### Post by DeadRobot on 2009-01-17
Ok thanks guys!

Here are the other results of the commands:
```
 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:cb:94:8e:72  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1206 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1206 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:60300 (58.8 KB)  TX bytes:60300 (58.8 KB)





netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface





 iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.





 lsmod
Module                  Size  Used by
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
usb_storage            73664  1 
libusual               19108  1 usb_storage
ipv6                  267780  10 
radeon                124192  0 
drm                    82452  1 radeon
hci_usb                16540  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  7 hci_usb,rfcomm,l2cap
uinput                 10240  2 
ppdev                  10372  0 
acpi_cpufreq           10796  1 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  2 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
sbs                    15112  0 
container               5632  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
appletouch             11264  0 
usbhid                 32128  0 
hid                    38784  1 usbhid
sky2                   47620  0 
video                  19856  0 
output                  4736  1 video
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
ac                      6916  0 
button                  9232  0 
battery                14212  0 
pcspkr                  4224  0 
evdev                  13056  12 
intel_agp              25492  0 
agpgart                34760  2 drm,intel_agp
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
tpm_infineon           10152  0 
tpm                    16544  1 tpm_infineon
tpm_bios                8320  1 tpm
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
sd_mod                 30720  5 
cdrom                  37408  1 sr_mod
ata_piix               19588  2 
ata_generic             8324  0 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
pata_acpi               8320  0 
libata                159344  3 ata_piix,ata_generic,pata_acpi
scsi_mod              151436  6 usb_storage,sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  8 usb_storage,libusual,hci_usb,appletouch,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              37384  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 

```

Hope those help.

---

### Post by MaindotC on 2009-01-17
Looks like your wireless card is made by Atheros.  Here's a google search for how to get the AR242x driver loaded [http://is.gd/gf0Z](http://is.gd/gf0Z).  I think you can also open Synaptic and do a search for "madwifi" and install the linux-restricted-modules package that matches your kernel version.

---

### Post by DeadRobot on 2009-01-17
Can I install stuff from Synaptic even though I dont have internet?

---

### Post by MaindotC on 2009-01-17
You can if it's on the LiveCD.  However, why don't you just use your wired connection and download it via Synaptic that way?

---

### Post by DeadRobot on 2009-01-17
Ok thanks!

I got madwifi.

But Im not really sure how to install it.

what are the commands you use?  like configure, make and install?

---

### Post by DeadRobot on 2009-01-17
Also, if it doesnt work out, which it probably wont, is there a way I can delete EVERYTHING on the partition i made for Ubuntu?

---

### Post by MaindotC on 2009-01-18
If you downloaded madwifi - which should have been in the pacakage "linux-restricted-modules-<kernel version> then you should be using it.  Type:
```

lsmod

```
and look for something relating to your wireless driver or madwifi.  Is your wireless not working?

---

### Post by DeadRobot on 2009-01-18
well i cant really connect to the wired so I just downloaded it off the internet in Mac OSX, put it on a flash drive and transferred it to the Ubuntu desktop.  So now I have a folder called Madwifi with stuff in it but its definitely not installed yet.

---

### Post by MaindotC on 2009-01-18
You really need to be connected because you need the package that I stated in the above post and it will probably require dependencies that need to be downloaded as well.  There's absolutely no way for you to wire in with your Ubuntu machine?  Are you using your own Internet connection?

If that is absolutely not possible then open the madwifi folder and there should be a file in there that says README.  Follow those directions.

---

### Post by DeadRobot on 2009-01-18
Ugh, I installed it but nothing happend.  Even when I restarted.

Maybe you can download the one from Synaptic and email it to me?

Or is there a way i can just like restore the system?  where it would erase all my files and settings and start fresh with a clean ubuntu?

[email]rpatel10@mcdonogh.org[/email] is my email.

Thank you.

---

### Post by MaindotC on 2009-01-18
Post the output, and read the man page, of lsmod.

This is probably a dumb question, but did you run the Software Updater and download and install all your updates?

---

### Post by DeadRobot on 2009-01-19
Yes, I did do all the updates and stuff.

Output of lsmod:
```

Module                  Size  Used by
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
usb_storage            73664  1 
libusual               19108  1 usb_storage
ipv6                  267780  10 
radeon                124192  0 
drm                    82452  1 radeon
hci_usb                16540  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  7 hci_usb,rfcomm,l2cap
uinput                 10240  2 
ppdev                  10372  0 
acpi_cpufreq           10796  1 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  2 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
sbs                    15112  0 
container               5632  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
appletouch             11264  0 
usbhid                 32128  0 
hid                    38784  1 usbhid
sky2                   47620  0 
video                  19856  0 
output                  4736  1 video
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
ac                      6916  0 
button                  9232  0 
battery                14212  0 
pcspkr                  4224  0 
evdev                  13056  12 
intel_agp              25492  0 
agpgart                34760  2 drm,intel_agp
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
tpm_infineon           10152  0 
tpm                    16544  1 tpm_infineon
tpm_bios                8320  1 tpm
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
sd_mod                 30720  5 
cdrom                  37408  1 sr_mod
ata_piix               19588  2 
ata_generic             8324  0 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
pata_acpi               8320  0 
libata                159344  3 ata_piix,ata_generic,pata_acpi
scsi_mod              151436  6 usb_storage,sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  8 usb_storage,libusual,hci_usb,appletouch,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              37384  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3

```

---

### Post by MaindotC on 2009-01-19
Ok, so you need to insert the madwifi driver that works for your wireless card.  Look at the output of this command:
```

ls /lib/modules/`uname -r`/madwifi

```
These are all the modules that come with madwifi and can be inserted to operate your wireless card.  You can insert them by using:
```

modprobe -a

```

---

### Post by DeadRobot on 2009-01-20
I upgraded to 8.10 and it works fine now.

Thanks! :D

---

