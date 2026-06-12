---
title: "2nd NIC not working"
date: 2009-05-31
forum: General Help
---

### Post by Pnuts on 2009-05-31
On a clean install of Kubuntu 8.10 (Alternate CD) I have a machine with 2 NICs. One on-board and one in a 1x PCI-E slot. Both NICs were in the machine at the time of the installation.

The on-board NIC is functioning correctly, grabbing a DHCP address, etc. while the PCI-E card is not.

Both NICs use the e1000e driver. Both NICs also work correctly if booted to a Ubuntu 9.04 Live CD.

here is an lspci, I bolded the 2 NICs to make it easier to skim:

```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
00:03.2 IDE interface: Intel Corporation 4 Series Chipset PT IDER Controller (rev 03)
00:03.3 Serial controller: Intel Corporation 4 Series Chipset Serial KT Controller (rev 03)
**00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)**
00:1a.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a2)
00:1f.0 ISA bridge: Intel Corporation 82801JD (ICH10D) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801JD/DO (ICH10 Family) SMBus Controller (rev 02)
**03:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection**
```

I have tried adding eth1 to the /etc/network/interfaces file but after restarting the networking service, it returns:

```
eth1: ERROR while getting interface flags: No such device
```

im still rather a newbie at this and am not sure where to go next to get this to work, any help appreciated.

-Pnuts

edit: Also, i have already updated the e1000e.ko file to the one provided with the add-in NIC. Ran depmod and modprobe e1000e, still no luck.

---

### Post by blueridgedog on 2009-05-31
Though I can't tell you the exact problem, what is in your /etc/modules file and what is the output of lsmod?

You may need to put in an alias statement in /etc/modules to activate the second card.  You can try:

```
alias eth0 module_name
```

(where module_name is the module you installed).

---

### Post by Pnuts on 2009-05-31
I didnt really install any modules, I updated an existing one basically. I overwrote /lib/modules/2.6.27-14-generic/kernel/drivers/net/e1000e/e1000e.ko with the version included with the addin NIC. Then did "sudo depmod" and "sudo modprobe e1000e"

lsmod:
```
Module                  Size  Used by
i915                   38656  2 
drm                    86056  3 i915
rfcomm                 44304  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20352  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15748  0 
lp                     17156  0 
acpi_cpufreq           15500  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
cpufreq_userspace      11396  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  2 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
pci_slot               12680  0 
video                  25488  0 
output                 11008  1 video
container              11520  0 
bay                    12160  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
battery                18436  0 
ipv6                  264228  22 
af_packet              25856  2 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
loop                   23052  0 
dcdbas                 15008  0 
joydev                 18368  0 
evdev                  17696  8 
parport_pc             39332  1 
parport                42604  3 ppdev,lp,parport_pc
snd_hda_intel         385072  1 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
psmouse                45200  0 
serio_raw              13444  0 
snd_seq_oss            38528  0 
wmi                    14504  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
intel_agp              33980  1 
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                 14224  0 
pcspkr                 10624  0 
agpgart                42184  3 drm,intel_agp
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
snd                    63268  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133512  2 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sd_mod                 42392  8 
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
crc_t10dif              9984  1 sd_mod
usbhid                 35712  0 
hid                    50560  1 usbhid
sg                     39732  0 
pata_acpi              12160  0 
ahci                   37132  6 
ata_generic            12932  0 
uhci_hcd               30864  0 
ehci_hcd               43788  0 
libata                177952  3 pata_acpi,ahci,ata_generic
scsi_mod              155212  4 sd_mod,sr_mod,sg,libata
usbcore               149488  4 usbhid,uhci_hcd,ehci_hcd
dock                   16656  2 bay,libata
e1000e                113580  0 
raid10                 30464  0 
raid456               135184  0 
async_xor              11520  1 raid456
async_memcpy           10112  1 raid456
async_tx               15312  3 raid456,async_xor,async_memcpy
xor                    23688  2 raid456,async_xor
raid1                  30080  1 
raid0                  15488  2 
multipath              15104  0 
linear                 13440  0 
md_mod                 94108  9 raid10,raid456,raid1,raid0,multipath,linear
thermal                23708  0 
processor              42156  2 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60956  1 
```

/etc/modules:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
fuse
```

---

### Post by Pnuts on 2009-05-31
Just wanted to add, my knowledge is pretty limited. I dont know exactly what these commands do, but in Kubuntu 7.10 I created this script that I ran as sudo and upon completion, both NICs worked.

```
mkdir /lib/modules/2.6.22-14-generic/kernel/drivers/net/e1000e
cp e1000e.ko /lib/modules/2.6.22-14-generic/kernel/drivers/net/e1000e/e1000e.ko
depmod
modprobe e1000e
```

In 8.10 the folder already exists and has the driver present, just both NICs are not working. So I tried doing what I did before without much luck.

-Pnuts

---

### Post by blueridgedog on 2009-05-31
Try putting the following in /etc/modules:

```
alias eth1 e1000e
```

Then you can restart or modprobe it.

---

### Post by Pnuts on 2009-05-31
> **blueridgedog said:**
> Try putting the following in /etc/modules:

```
alias eth1 e1000e
```

Then you can restart or modprobe it.

Added the line, modprobe e1000e - nothing, then restarted and nothing.

after restart I checked my /etc/network/interfaces:

```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```

and did a sudo /etc/init.d/networking restart

getting this following the lines for eth0 getting dhcp:
```
* if-up.d/mountfs[eth0]: waiting for interface eth1 before doing NFS mounts
eth1: ERROR while getting interface flags: No such device
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
```

-Pnuts

Edit: would performing a reinstall with the 2nd NIC removed and then adding it once complete and updated make a difference you think?

---

### Post by Pnuts on 2009-05-31
Well, I really wanted to get this up today, but it looks like it isn't going to happen.

I removed the PCI-E NIC and reinstalled Kubuntu 8.10 with the Alternate CD. After installation I performed all updates (apt-get update and apt-get dist-upgrade). I then shutdown, inserted the PCI-E NIC and rebooted. Nothing. Shutdown and booted a Ubuntu 9.04 live CD to verify the card still works, it does. I have done nothing else to the clean install.

Here is the current lspci:

```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
00:03.2 IDE interface: Intel Corporation 4 Series Chipset PT IDER Controller (rev 03)
00:03.3 Serial controller: Intel Corporation 4 Series Chipset Serial KT Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a2)
00:1f.0 ISA bridge: Intel Corporation 82801JD (ICH10D) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801JD/DO (ICH10 Family) SMBus Controller (rev 02)
03:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection
```

and lsmod:

```
Module                  Size  Used by
ipv6                  264228  22 
af_packet              25856  2 
i915                   38656  2 
drm                    86056  3 i915
rfcomm                 44304  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20352  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ppdev                  15748  0 
acpi_cpufreq           15500  0 
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  2 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
video                  25488  0 
output                 11008  1 video
sbs                    19464  0 
pci_slot               12680  0 
sbshc                  13440  1 sbs
bay                    12160  0 
container              11520  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
loop                   23052  0 
dcdbas                 15008  0 
evdev                  17696  8 
joydev                 18368  0 
pcspkr                 10624  0 
psmouse                45200  0 
serio_raw              13444  0 
snd_hda_intel         385072  1 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
parport_pc             39332  1 
parport                42604  3 ppdev,lp,parport_pc
snd_rawmidi            29824  1 snd_seq_midi
wmi                    14504  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              33980  1 
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
agpgart                42184  3 drm,intel_agp
button                 14224  0 
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
ext3                  133512  2 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
usbhid                 35712  0 
hid                    50560  1 usbhid
sd_mod                 42392  8 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
pata_acpi              12160  0 
ahci                   37132  6 
ehci_hcd               43788  0 
uhci_hcd               30864  0 
ata_generic            12932  0 
usbcore               149488  4 usbhid,ehci_hcd,uhci_hcd
e1000e                113580  0 
libata                177952  3 pata_acpi,ahci,ata_generic
scsi_mod              155212  4 sd_mod,sr_mod,sg,libata
dock                   16656  2 bay,libata
raid10                 30464  0 
raid456               135184  0 
async_xor              11520  1 raid456
async_memcpy           10112  1 raid456
async_tx               15312  3 raid456,async_xor,async_memcpy
xor                    23688  2 raid456,async_xor
raid1                  30080  1 
raid0                  15488  2 
multipath              15104  0 
linear                 13440  0 
md_mod                 94108  9 raid10,raid456,raid1,raid0,multipath,linear
thermal                23708  0 
processor              42156  2 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60956  1 
```

Suggestions from anyone are welcome to get this to work. I have to leave for a few hours, but ill gladly do what ever is required once I return.

Thanks,
Pnuts

---

### Post by Pnuts on 2009-05-31
In case anyone else comes across this in the future, I found the solution.

After I updated the diver module, I had to remove it from the kernel. So I did:

```
rmmod e1000e
```

followed by:

```
modprobe e1000e
```

and the 2nd NIC loaded correctly and grabbed a dhcp address.

-Pnuts

---

### Post by blueridgedog on 2009-05-31
Odd that it did not pick it up after a reboot...

Great that you are up and running.

---

### Post by Pnuts on 2009-05-31
I really didnt think I was going to get it to work and had given up on myself. I went through what you suggested again but I wasnt getting anywhere fast. I did a 3rd reinstall, copied the driver src from the cd again and tried to "make" it. Got some errors so I figured, Ill just DL it from teh intel site.

After doing so, tried to build it. it completed, copied it to the modules and had no luck again. I had about given up and I decided, why not, ill RTFM (Read The F.. Manual) that came in the download. It told me to rmmod if I was replacing an existing driver before i did modprobe and boom, it works...

go figure

-Pnuts

---

