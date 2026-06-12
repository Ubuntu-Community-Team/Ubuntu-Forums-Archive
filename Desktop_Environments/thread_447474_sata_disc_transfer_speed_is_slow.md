---
title: "sata disc transfer speed is slow"
date: 2007-05-18
forum: Desktop Environments
---

### Post by OoooMatron on 2007-05-18
Copying large files takes a long time for me. I am using Ubuntu 7.04 with a new installation.

If i copy a 350mb file from one physical disc to another it takes 1 minute. That's about 6mb/ second which is obviously not optimum. it's not even close to fast. I would expect at least 30-40 from this system.

any ideas on how to fix this? I understand hdparm does not support sata interfaces so that's a no go.

---

### Post by OoooMatron on 2007-05-19
can anyone acknowledge the problem if not the solution?

---

### Post by visorjoe on 2007-05-22
i have same problem but still can't find any answer:(

---

### Post by RAOF on 2007-05-22
hdparm shouldn't be necessary with SATA drives - libata autonegotiates things like DMA and io modes (and if it doesn't, then that's a bug that should be filed).

You could either use hdparm to benchmark the disc(s), or use various tools to copy the file (cp from the terminal, etc) - see whether it's the copy tool or the disc access itself which is slow.

---

### Post by OoooMatron on 2007-05-22
it takes the same time using the command line as it does using nautilus.

/dev/sda:
 IO_support   =  0 (default 16-bit)

thats what hdparm -c /dev/sda produces.

The transfer speed is defintely slow. I also wonder if this is why running quake natively is so slow.

---

### Post by heimo on 2007-05-22
You can test if it's just one disk or both, or just copying from one to the other, using bonnie++ to test speeds on each disk. Which motherboard / chipset?

---

### Post by OoooMatron on 2007-05-22
its the whole system. skype even stutters if i use it while doing something like burning a dvd. never had this problem before.

the board is an ABit AG8.

---

### Post by dwalker109 on 2007-05-23
I'm experiencing the same issue since upgrading. Copying files (even on the same disk) is slow - between 2 and 10MB per second. I have two SATA had drives, both of which have the problem.

sudo hdparm -tT /dev/sda reports:

/dev/sda:
 Timing cached reads:   1952 MB in  2.00 seconds = 975.77 MB/sec
 Timing buffered disk reads:  164 MB in  3.00 seconds =  54.65 MB/sec
dan@Panoramix:~$ sudo hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   1974 MB in  2.00 seconds = 987.01 MB/sec
 Timing buffered disk reads:  182 MB in  3.02 seconds =  60.32 MB/sec

This looks fine to me, but the speed is awful when copying with Nautilus or with the terminal. I couldn't find a bug report for this... anyone filed one?

---

### Post by OoooMatron on 2007-05-24
yes this replicates my problem too. the hdparm test reports the usual numbers but the physical copying remains slow.

doing anything HD intensive, be it copying a file, burning a dvd makes the system sluggish. skype is unusable during a cd burn (never used to be).

it's not the file copying tools, ive tested with the command line and konqueror so it remains a sata issue i think.

i have not filed a report.

---

### Post by NullFile on 2007-05-27
I have the same problem. disk access is slow also.
hdparm shows that all is fine, but  disk access is slow and disk through put is slow.
Oh and one other thing I don't have this problem with arch linux. I have been looking for a fix for sometime now.

---

### Post by gopoo on 2007-05-27
i am asking the obvious....but are the driver detected/installed by the kernel are correct ???

---

### Post by dwalker109 on 2007-05-28
I assumed the drivers are detected correctly - where would I check this?

---

### Post by gopoo on 2007-05-30
take output of lspci , and lsmod , you might have to be root to use this command. 

post here if you dont understand the output..

hope this helps.

---

### Post by dwalker109 on 2007-05-30
Hey there, thanks for the assistance :D

Things look OK to me (lots of ICH7 and Intel 82801 in the output below, which is what I have in the machine), but I'd appreciate any advice you can give:

```

root@Panoramix:/home/dan# lspci
00:00.0 Host bridge: Intel Corporation E7230/3000/3010 Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation E7230/3000/3010 PCI Express Root Port
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 PCI bridge: Intel Corporation 6702PXH PCI Express-to-PCI Bridge A (rev 09)
04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express (rev 11)
06:05.0 VGA compatible controller: XGI - Xabre Graphics Inc Volari Z7
root@Panoramix:/home/dan# lsmod
Module                  Size  Used by
nfnetlink_queue        13504  1 
binfmt_misc            12680  1 
appletalk              38188  0 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
nfs                   240876  0 
nfsd                  218992  17 
exportfs                6912  1 nfsd
lockd                  64904  3 nfs,nfsd
sunrpc                161340  12 nfs,nfsd,lockd
xt_NFQUEUE              2944  3 
xt_limit                3584  8 
xt_tcpudp               4224  39 
iptable_mangle          3712  0 
ipt_LOG                 7680  8 
ipt_MASQUERADE          4608  0 
nf_nat                 19372  1 ipt_MASQUERADE
ipt_TOS                 3200  0 
ipt_REJECT              5632  1 
nf_conntrack_irc        8088  0 
nf_conntrack_ftp       11008  0 
nf_conntrack_ipv4      19468  10 
xt_state                3456  9 
nf_conntrack           62600  6 ipt_MASQUERADE,nf_nat,nf_conntrack_irc,nf_conntrack_ftp,nf_conntrack_ipv4,xt_state
nfnetlink               7704  5 nfnetlink_queue,nf_nat,nf_conntrack_ipv4,nf_conntrack
iptable_filter          3968  1 
ip_tables              13796  2 iptable_mangle,iptable_filter
x_tables               16388  9 xt_NFQUEUE,xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,ip_tables
ppdev                  10116  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
video                  16388  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
dock                   10268  0 
button                  8720  0 
battery                10756  0 
container               5248  0 
ac                      6020  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
af_packet              23816  0 
eeprom                  8336  0 
lm85                   31652  0 
hwmon_vid               4224  1 lm85
i2c_i801                9356  0 
i2c_core               22784  4 i2c_ec,eeprom,lm85,i2c_i801
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
pcspkr                  4224  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
psmouse                38920  0 
serio_raw               7940  0 
ipv6                  268704  100 
evdev                  11008  1 
tsdev                   8768  0 
vfat                   14208  0 
fat                    53916  1 vfat
ext3                  133128  2 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
sd_mod                 23428  5 
cdrom                  37664  1 sr_mod
ata_piix               15492  5 
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  4 sg,sr_mod,sd_mod,libata
floppy                 59524  0 
tg3                   109700  0 
generic                 5124  0 [permanent]
uhci_hcd               25360  0 
ehci_hcd               34188  0 
usbcore               134280  3 uhci_hcd,ehci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

```

Thanks muchly

---

### Post by OoooMatron on 2007-06-05
I have the same hardware listed which matches what I have on my AG8 board. I wonder if this is a problem with this chipset only??? The sata support has never been good for this chipset. About a year ago half the distros werent even recognising it.

where do we go to report this problem?

---

### Post by dwalker109 on 2007-06-10
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/119730](https://bugs.launchpad.net/ubuntu/+bug/119730) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've filed a bug report over on Launchpad (bug #119730). Anyone experiencing this issue should go over there and post their experiences to get it confirmed, partcularly the chipset you're using.

---

### Post by jalagus on 2007-06-12
I don't think this is limited to Intel chipset only as I have nvidia chipset and have exactly the same problem.

---

### Post by dwalker109 on 2007-06-12
Hi

OK, good stuff. Could you post your output of "sudo lspci" and "sudo lsmod" so we can find out what the common factor is here, then update the bug report. 

Cheers

---

### Post by jalagus on 2007-06-12
```

jalagus@mankeli:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
01:08.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
jalagus@mankeli:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
01:08.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
jalagus@mankeli:~$ lsmod
Module                  Size  Used by
rfcomm                 40856  0
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0
cpufreq_powersave       2688  0
cpufreq_stats           7360  0
cpufreq_userspace       5408  0
cpufreq_ondemand        9228  0
cpufreq_conservative     8200  0
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
tc1100_wmi              8068  0
pcc_acpi               13184  0
sony_acpi               6284  0
dev_acpi               12292  0
video                  16388  0
battery                10756  0
container               5248  0
sbs                    15652  0
button                  8720  0
i2c_ec                  6016  1 sbs
dock                   10268  0
ac                      6020  0
asus_acpi              17308  0
backlight               7040  1 asus_acpi
ipv6                  268960  10
nls_utf8                3072  3
ntfs                  107764  3
ext2                   66824  2
mbcache                 9604  1 ext2
lp                     12452  0
fuse                   46612  0
snd_ice1712            65012  3
snd_ice17xx_ak4xxx      5120  1 snd_ice1712
snd_ak4xxx_adda         8192  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427              9984  1 snd_ice1712
snd_ac97_codec         98464  1 snd_ice1712
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 snd_ice1712,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10888  1 snd_pcm
ac97_bus                3200  1 snd_ac97_codec
snd_i2c                 6528  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         9472  1 snd_ice1712
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_rawmidi            25472  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
stv0297                 8448  1
xpad                    9988  0
nvidia               4713780  32
agpgart                35400  1 nvidia
snd                    54020  18 snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_i2c,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
budget_ci              21136  0
budget_core            12292  1 budget_ci
dvb_core               80808  2 budget_ci,budget_core
saa7146                19720  2 budget_ci,budget_core
ttpci_eeprom            3456  1 budget_core
ir_common              31236  1 budget_ci
psmouse                38920  0
serio_raw               7940  0
pcspkr                  4224  0
ide_cd                 32672  0
cdrom                  37664  1 ide_cd
parport_pc             36388  1
parport                36936  3 ppdev,lp,parport_pc
i2c_nforce2             6784  0
k8temp                  6656  0
shpchp                 34324  0
pci_hotplug            32576  1 shpchp
i2c_core               22656  7 i2c_ec,stv0297,nvidia,budget_ci,budget_core,ttpci_eeprom,i2c_nforce2
af_packet              23816  2
tsdev                   8768  0
evdev                  11008  5
reiserfs              247680  2
sg                     36252  0
sd_mod                 23428  10
amd74xx                15260  0 [permanent]
generic                 5124  0 [permanent]
ata_generic             9092  0
usbhid                 26592  0
hid                    27392  1 usbhid
floppy                 59524  0
forcedeth              46728  0
sata_nv                20868  8
libata                125720  2 ata_generic,sata_nv
scsi_mod              142348  3 sg,sd_mod,libata
ehci_hcd               34188  0
ohci_hcd               22532  0
usbcore               134280  5 xpad,usbhid,ehci_hcd,ohci_hcd
thermal                14856  0
processor              31048  1 thermal
fan                     5636  0
fbcon                  42656  0
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0
capability              5896  0
commoncap               8192  1 capability

```

---

### Post by d351GuJu on 2007-06-16
I have the same exact problem, I was trying to copy contents off of my external hdd to internal hdd, and it was extremely slow.  

**Output of lsmod:**

```

Module                  Size  Used by
dm_mod                 59084  0 
loop                   17800  0 
nls_iso8859_1           5120  0 
nls_cp437               6784  0 
vfat                   14208  0 
fat                    53916  1 vfat
vboxdrv                44552  0 
xt_limit                3584  8 
xt_tcpudp               4224  9 
iptable_mangle          3712  0 
ipt_LOG                 7680  8 
ipt_MASQUERADE          4608  0 
nf_nat                 19372  1 ipt_MASQUERADE
ipt_TOS                 3200  0 
ipt_REJECT              5632  1 
nf_conntrack_irc        8088  0 
nf_conntrack_ftp       11008  0 
nf_conntrack_ipv4      19468  7 
xt_state                3456  6 
nf_conntrack           62600  6 ipt_MASQUERADE,nf_nat,nf_conntrack_irc,nf_conntrack_ftp,nf_conntrack_ipv4,xt_state
nfnetlink               7704  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
iptable_filter          3968  1 
ip_tables              13796  2 iptable_mangle,iptable_filter
x_tables               16388  8 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,ip_tables
bluetooth              55908  0 
binfmt_misc            12680  1 
ppdev                  10116  0 
cpufreq_stats           7360  0 
cpufreq_conservative     8200  0 
cpufreq_ondemand        9228  0 
cpufreq_powersave       2688  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5408  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
pcc_acpi               13184  0 
battery                10756  0 
asus_acpi              17308  0 
dock                   10268  0 
video                  16388  0 
button                  8720  0 
container               5248  0 
backlight               7040  1 asus_acpi
sbs                    15652  0 
i2c_ec                  6016  1 sbs
ac                      6020  0 
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  1 
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         7936  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           121248  2 snd_emu10k1_synth
snd_ac97_codec         98464  1 snd_emu10k1
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10888  2 snd_emu10k1,snd_pcm
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9988  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
irtty_sir               9600  0 
sir_dev                17156  1 irtty_sir
nvidia               6837140  32 
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
irda                  201276  2 irtty_sir,sir_dev
af_packet              23816  4 
serio_raw               7940  0 
snd_seq                52592  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9100  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
crc_ccitt               3072  1 irda
agpgart                35400  1 nvidia
snd                    54020  15 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
xpad                    9988  0 
psmouse                38920  0 
emu10k1_gp              4736  0 
gameport               16520  2 emu10k1_gp
usblp                  14848  0 
pcspkr                  4224  0 
sk98lin               156896  0 
soundcore               8672  1 snd
i2c_nforce2             6784  0 
k8temp                  6656  0 
i2c_core               22656  3 i2c_ec,nvidia,i2c_nforce2
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tsdev                   8768  0 
evdev                  11008  4 
ipv6                  268960  10 
usb_storage            72256  1 
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ext3                  133128  3 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
libusual               17936  1 usb_storage
sd_mod                 23428  7 
amd74xx                15260  0 [permanent]
generic                 5124  0 [permanent]
sata_nv                20868  3 
usbhid                 26592  1 
hid                    27392  1 usbhid
sata_sil               12808  0 
skge                   40848  0 
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
ata_generic             9092  0 
floppy                 59524  0 
ehci_hcd               34188  0 
forcedeth              46728  0 
ohci_hcd               22532  0 
usbcore               134280  9 xpad,usblp,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
libata                125720  3 sata_nv,sata_sil,ata_generic
scsi_mod              142348  5 sbp2,usb_storage,sg,sd_mod,libata
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

```

**Output of lspci:**

```
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
01:06.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
01:06.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
01:08.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
01:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1)

```

Thanks!

---

### Post by screaminj3sus on 2007-06-17
Same thing pretty much, Transferring Data from my SATA Drive (Windows) to my IDE Drive (Ubuntu) Takes Ages.

---

### Post by StonedSidney on 2007-07-04
Same thing here but I have an ATI motherboard, with 4379 SATA, and Silicon Image 3124 SATA controller. Slow performance through BOTH controllers!

**HDParm output for the ATI controller**
sid@co305100-a:~$ sudo hdparm -tT /dev/sda1

/dev/sda1:
 Timing cached reads:   1648 MB in  2.00 seconds = 823.95 MB/sec
 Timing buffered disk reads:  162 MB in  3.02 seconds =  53.71 MB/sec

**HDParm Output for the Sil Img controller:**
sid@co305100-a:~$ sudo hdparm -tT /dev/sdb5

/dev/sdb5:
 Timing cached reads:   1640 MB in  2.00 seconds = 819.95 MB/sec
 Timing buffered disk reads:  118 MB in  3.01 seconds =  39.17 MB/sec

Disk accesses are very slow - even file deletes.

Looking at Top's output when something is accessing disk shows a WA wait % that gets over 70% while CPU and RAM are fine i.e. the system performance appears disk-bound.

I am running:
sid@co305100-a:~$ uname -a
Linux co305100-a 2.6.15-28-amd64-generic #1 SMP PREEMPT Tue Mar 13 20:51:52 UTC 2007 x86_64 GNU/Linux

Happy to provide any other info that might help. Thanks for reading.

---

### Post by Nythain on 2007-07-05
i had similar if not same problem... running conky monitoring my io speed
from ide to sata about 6 a sec
from ide to ide about 20 a sec
from sata to ide about 14 a sec
that was using mv from command line, and "move here" in konqueror... so its definately in the way ubuntu decides to write to and from an sata drive

---

### Post by OoooMatron on 2007-07-07
I tested this problem out with PCLINUXOS and I don't suffer the same problem with the transfer. It's much faster.

---

### Post by OoooMatron on 2007-07-22
Ok, gutsy gibbon does not replicate this problem (seems to be ok now, so maybe it was a dodgy kernel version).

Interestingly, when i unplugged the ide dvd burner I didn't have a problem with the sata speed anymore (thanks to the advice of another forum member).  Anyway, the new kernel in GG is working very nicely for me.

I've also changed to reiser now which has further increased the write speed.

---

### Post by dwalker109 on 2007-07-22
That's good to know. I think I can wait a few more months to get this resolved.

---

### Post by robert114 on 2007-07-23
Same problem here! copying files uses a lot of CPU usage

I've got:
AMD X2 4600 
nvidia nforce 570
2 sata discs

---

### Post by StonedSidney on 2007-07-23
Interesting stuff.  I also have an IDE DVD burner connected, so I'll try unplugging it (or just disable in BIOS?) to see if performance improves. I won't miss the burner much as it's only good for reading disks and  making coasters - that's my other main gripe w/ Ubuntu. [Hmmm could it be a related problem?]

**Does anyone else get high WA% in Top** when copying files? I have noticed that Top's output is quite different to System Monitor; Top shows much lower CPU% but high WA% whereas Sys Mon seems to combine these into a total (although I might be imagining this). I *assuume* Top is more accurate.

At work now so I'll post an update later.

---

### Post by Wiebelhaus on 2007-07-23
> **OoooMatron said:**
> can anyone acknowledge the problem if not the solution?

Try the same file in vista , then report back... you'll be about ten years older.

---

### Post by OoooMatron on 2007-07-24
> **StonedSidney said:**
> Interesting stuff.  I also have an IDE DVD burner connected, so I'll try unplugging it (or just disable in BIOS?) to see if performance improves. I won't miss the burner much as it's only good for reading disks and  making coasters - that's my other main gripe w/ Ubuntu. [Hmmm could it be a related problem?]

**Does anyone else get high WA% in Top** when copying files? I have noticed that Top's output is quite different to System Monitor; Top shows much lower CPU% but high WA% whereas Sys Mon seems to combine these into a total (although I might be imagining this). I *assuume* Top is more accurate.

At work now so I'll post an update later.

I have found that the linux cdr tools are not very good with my burner either. I am using Nero LINUX and it burns perfectly at full speed.

I think the fact it uses it's own libraries is the key here. All the other cd software I have tried appear to be mostly front ends for the same programs , hence the same problems.

It doesn't matter if it's gnomebaker, brasero, or the kde one, they all burn slowly for me!

I haven't tried it (and probably won't now) but if you compile your own kernel from the newer branches it might make the SATA problem go away. It's all been great since I installed Gutsy.

---

### Post by OoooMatron on 2007-07-24
> **sx66gns said:**
> Try the same file in vista , then report back... you'll be about ten years older.

I don't understand what you mean :D

And if you think i'm installing that crap on my machine you can think again :D

---

### Post by dwalker109 on 2007-07-24
Maybe I'll disable my burner and see what happens too...

---

### Post by StonedSidney on 2007-07-24
Arrgh. 
Can't seem to disable the IDE burner in BIOS, and sadly the cable's in v.awkward place to remove it; hard to slide m/d tray out. dwalker I'm looking for an update from you mate if you'd be so kind.

So I thought I'd solve my burning prob. instead w/ linux-nero, but no trial version available :( 

Too wasted now, so I'm running an upgrade instead. No small feat as it'll cause me vmware woes in the morning :(

I'll let you know if the upgrade solves anything.

---

### Post by dwalker109 on 2007-07-24
My box is headless, so I'll have a look at the BIOS when I get chance. Let me know how the upgrade goes... I may join you.

---

### Post by UlyssesR on 2007-07-25
/dev/sda:
 Timing cached reads:   550 MB in  2.00 seconds = 274.58 MB/sec
 Timing buffered disk reads:  200 MB in  3.02 seconds =  66.18 MB/sec

I can't find any data to compare with my hardware, but it feels much slower! 

It's a Seagate 7200rpm on sata2.

---

### Post by StonedSidney on 2007-07-25
Wow I guess I really was wasted last night - I didn't do an upgrade but an upDATE. Me moron - just see what I realised at the bottom of this post..

Anyhoo, just re-ran some perf tests after the update:

**Using the ATI m/b controller:**
/dev/sda1:
 Timing cached reads:   1720 MB in  2.00 seconds = 859.95 MB/sec
 Timing buffered disk reads:  172 MB in  3.02 seconds =  56.95 MB/sec
**Using the SIL controller:**
sudo hdparm -tT /dev/sdb5
/dev/sdb5:
 Timing cached reads:   1720 MB in  2.00 seconds = 859.95 MB/sec
 Timing buffered disk reads:  122 MB in  3.03 seconds =  40.23 MB/sec

sid@co305100-a:~$ **uname -a**
Linux co305100-a 2.6.15-28-amd64-generic #1 SMP PREEMPT Wed Jul 18 22:51:22 UTC 2007 x86_64 GNU/Linux

**Real copying results using a 4.4GB movie file:**
(from a 3 drive sata raid5 array to single sata partition on a seperate drive) 
sid@co305100-a:~$ time cp /media/md1/movies/HARD_CANDY.ISO /home/sid/trash/
real    **2m20.789s**
user    0m0.412s
sys     0m31.586s
I think that's roughly 32MB/sec.  How does this compare with everyone else?

What I was also too wasted to realise last night..... there are TWO ends to an IDE cable and the drive-end is easily accessible, along with the drive power cable:oops:, so that's what I'll try right now.

---

### Post by StonedSidney on 2007-07-25
Oh FFS. With the burner power removed, it's SLOWER!
sid@co305100-a:~$ time cp /media/md1/movies/HARD_CANDY.ISO /home/sid/**trash/**
real    2m48.225s
user    0m0.436s
sys     0m38.186s
[small detail: the /trash folder was on a non-raid partition on one of the raid5 drives, which was also the source, so I have corrected it below /sdd5/ is non-raid on a totally sep. drive]

sid@co305100-a:~$ time cp /media/md1/movies/HARD_CANDY.ISO /home/sid/sdd5/
real    2m27.058s
user    0m0.592s
sys     0m50.711s

So, in this best case it's slower than before. 
And **non-raid to non-raid:**
sid@co305100-a:/var/lib/vmware/Virtual Machines$ time cp /home/sid/sdd5/HARD_CANDY.ISO /home/sid/trash/
real    3m37.767s
user    0m0.588s
sys     0m43.651s
Seems very slow.

Think I'll power up that burner again.

Oh and of course:
**ATI**
/dev/sda1:
 Timing cached reads:   1852 MB in  2.00 seconds = 925.94 MB/sec
 Timing buffered disk reads:  172 MB in  3.01 seconds =  57.18 MB/sec
**SIL**
sid@co305100-a:~$ sudo hdparm -tT /dev/sdb5
/dev/sdb5:
 Timing cached reads:   1900 MB in  2.00 seconds = 949.94 MB/sec
 Timing buffered disk reads:  122 MB in  3.01 seconds =  40.50 MB/sec

Which is pretty much the same.

Maybe I'm just expecting too much?

---

### Post by OoooMatron on 2007-07-25
I don't think hdparm is a reliable way to test the transfer speed. The onyl way to do it is to copy a large file and time it with a stopwatch or monitor it in realtime.

/dev/sda:
 Timing cached reads:   1916 MB in  2.00 seconds = 958.44 MB/sec
 Timing buffered disk reads:  174 MB in  3.01 seconds =  57.78 MB/sec

I am getting between up to 50mb/s copying a file from one drive to another now :D

Which is a VAST improvement over before.


700mb transferred in 14s,.

---

### Post by Wiebelhaus on 2007-07-28
> **OoooMatron said:**
> I don't understand what you mean :D

And if you think i'm installing that crap on my machine you can think again :D

I was being a smarty pants , data transfer in vista is the most god awful painful freaking thing ever , network transfer rates.....jebus man forget about it.

btw , this is reports from several hundred work stations , not just an MS hater.

---

### Post by OoooMatron on 2007-07-28
never heard about it. now it makes sense :D

---

### Post by StonedSidney on 2007-07-28
OoooMatron, you're a diamond geezer. 

Linux nero has just burned 2 perfect DVD's - one an ISO, and one a 2*AVI disk. Both work in the lounge DVD player.

This isn't really what this thread started for, but wow my Ubuntu confidence is soaring again.

I'm happy to help with any "analysis" if anyone else has similar probs/config.

---

### Post by OoooMatron on 2007-07-30
> **StonedSidney said:**
> OoooMatron, you're a diamond geezer. 

Linux nero has just burned 2 perfect DVD's - one an ISO, and one a 2*AVI disk. Both work in the lounge DVD player.

This isn't really what this thread started for, but wow my Ubuntu confidence is soaring again.

I'm happy to help with any "analysis" if anyone else has similar probs/config.

Yes, I am sure this is because they use their own low level code rather than the usual command line tools that every other linux burning software uses. They clearly are not up to the job for all the different burners out there.

I've had a lot of discussion about this in the last year and a half and while some people swear blind that apps like brasero and k3b burn flawlessly and full speed every time, my tests for my burner shows differently. With Nero Linux I don't have any burning problems.

It gets quite annoying that people defend the applications they use every day and then you find out they are only burning at 4x :D Then when you say "I have a 16x burner" they usual replies are like "well why do you need to burn that fast anyway?".

---

### Post by StonedSidney on 2007-08-07
Hmmmm although DVD buring is still working perfectly, I now realise that I still can't burn CD's :(

The error I get is "illegal disk" and the disk get thrown out. This is basically the same behaviour with gnome-baker.

I think I'd better start discussing this on a Burning-related thread, instead of distracting the SATA discussion further.

Nero still rocks though!

---

### Post by StonedSidney on 2007-08-08
A found a link on /.  to kernaltrap where Linus and others discuss the slow performance of IO in general and ext3 in particular: [http://kerneltrap.org/node/14148](http://kerneltrap.org/node/14148)

Seems that just adding **noatime,nodiratime** into fstab should speed things up dramatically. I'll try when I get home and post resuults here.

Sadly I can't easily reformat to raiser or anything else without buying another HDD to back-up my data.

---

### Post by dwalker109 on 2007-08-09
Didn't make a lot of difference for me - transfer speed is still hovering around 10MBps. It does seem snappier, but that may just be placebo.

Also, this didn't happen on Edgy anyway...

---

### Post by bsmith1051 on 2007-08-09
VERY interesting discussion on kerneltrap!  However, way down in the list there's someone who says that Ubuntu already defaults to 'noatime' (and is the only distro to do so) ?

---

### Post by OoooMatron on 2007-08-10
I also cannot rip audio cds faster than 4x!

It's very annoying that these fundamental things are quite weak. It's one reason why Windows users don't take linux seriously when many people have these problems.

---

### Post by smdeep on 2007-09-09
Hi
I bought a new Seagate 7200 rpm 160 GB SATA thinking it would be much faster than my 40GB Seagate PATA. But strangely that has not been the case. Everything takes a lot of time to start, e.g., even terminal takes around 10 secs to start!!!

I have an athlon 64 2800 processor, MSI motherboard with nVidia nForce3 chipset.

hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   846 MB in  2.00 seconds = 422.51 MB/sec
 Timing buffered disk reads:  222 MB in  3.02 seconds =  73.44 MB/sec

The cached reads seem to be much slower. Is there any solution to this?

Thanks
Sudeep

---

### Post by robert114 on 2007-09-09
I'm also having a very slow disk performance, but maybe there is some hope...
I upgraded to the testing version of Ubuntu (7.10) And I must say, I believe the disk performance is a bit faster than it was with 7.04.

I don't have any excact data but, I've got the feeling that my machine is a bit more responsive now 

So there is some hope. I also noticed an improvement in my performance by adding the following to my fstab lines:

notail,data=writeback,noatime,nodiratime

So it looks like: 
# /dev/sdb1
UUID=cf984fc6-eaa8-4aea-842b-923b8d13d6f7 /               reiserfs notail,data=writeback,noatime,nodiratime 0          0       1

---

### Post by OoooMatron on 2007-09-11
I will add those lines to my fstab and see if i get any faster performance but things are defintely better with the newer kernels.

Funnily enough, ripping with EAC under wine is faster than any native linux cd ripping tool!

---

### Post by dwalker109 on 2007-09-11
Remember, if this is happening to you, there is a [bug report]("https://bugs.launchpad.net/ubuntu/+bug/119730") open ; it would be useful to add your 2p there as well.

I've heard that this is resolved in newer kernels, so I'm hopeful for 7.10... will be upgrading pretty much as soon as it goes final.

---

### Post by OoooMatron on 2007-10-12
You know, I am on the latest version of Gutsy and now it's taking 2 minutes to tranfer a 700 mb file again!!!! I can't believe it's taken another step backwards. I am going to recompile the older kernel again. :@

---

### Post by bandoba on 2007-10-12
I am very much noob when it comes to Ubuntu and want to confirm something here. My Ubuntu AMD64 Feisty shows that write caching is disabled for Seagate 500GB 7200 RPM disk. This is the line from dmesg.

[   53.378480] SCSI device sdb: write cache: disabled, read cache: enabled, doesn't support DPO or FUA

But Ubuntu 6.10 enables write caching for the same disk. Is it possible for the enable write caching on Feisty and secondly would that improve my writing speed to something better than approx 6.5 MB/s?

TIA.

---

### Post by OoooMatron on 2007-10-13
Ok this gets weirder. I installed the Gutsy RC from scratch and now file transfers are back to normal. What the hell could it be?

---

### Post by Jolly-Swagman on 2007-10-13
On the Sata Drive there is a jumper next to the sata cable if the jumper is there then tranfer rate limited to 150mb/s remove jumper for 300mb/s transfer rate

Hope this helps

Jolly Swagman

---

### Post by bsmith1051 on 2007-10-16
> **OoooMatron]I installed the Gutsy RC from scratch and now file transfers are back to normal. What the hell could it be?[/QUOTE]
They fixed something?  Does Gutsy use the newest kernel, the one with the super-duper-fair scheduler (or whatever it's called) ?

[QUOTE=Jolly-Swagman said:**
> On the Sata Drive there is a jumper next to the sata cable if the jumper is there then tranfer rate limited to 150mb/s remove jumper for 300mb/s transfer rate
I would be seriously surprised if this helps.  I don't think most hard drives are **physically** capable of transferring data at that speed so running the data-link that fast is only going to tie-up the motherboard needlessly.  Of course, I'd love to be proven wrong!

---

### Post by rdelcueto on 2007-10-23
Hi everyone... I was using Feisty on my computer, and decided to upgrade to Gutsy once RC1 was out.
Since Feisty I had been experiencing sluggish behaviour whenever the computer was accessing my hard drives (all Sata). After upgrading to Gutsy RC1, I didn't notice any performance gain.

When I did my Gutsy 2 Gutsy Final upgrade, I decided to do a clean install, and raid (linux software Raid 0) two of my drives, and install my system into that raid device to see if I could improve my computer's performance related with this drive access issue.
When it first booted, the performance difference was noticeable. In general I felt my computer was snappy once again.
After a week of using my new installation, I'm once again having again the drive access sluggish syndrome. So I decided to do some research, and I ended up in this post.

I can experience this every time I use an application that reads/writes intensively, to be specific, apps such as Amarok rebuilding my music library, booting or using any Virtual box VM application that access the drive frequently, moving files from any of my drives (1x reiserfs,  2x Ext3, 1xNTFS). The computer slows down to a point its not longer usable until the reading/writing finishes. My Cpu always shows not being used... if I check my running processes using "top" and I see that indeed no app is eating my cpu, but I have a constant 45~50%wa, sometimes peaking 80-90%wa.

Checking my drive's performance using hdparm -tT, I get this:

/dev/md0: (My Soft Raid Array) SATA/Reiserfs
 Timing cached reads:   1814 MB in  2.00 seconds = 906.98 MB/sec
 Timing buffered disk reads:  240 MB in  3.01 seconds =  79.65 MB/sec

/dev/sda1: SATA/Ext3
 Timing cached reads:   1832 MB in  2.00 seconds = 916.37 MB/sec
 Timing buffered disk reads:  224 MB in  3.01 seconds =  74.53 MB/sec

/dev/sdb1: SATA/Ext3
 Timing cached reads:   1832 MB in  2.00 seconds = 916.14 MB/sec
 Timing buffered disk reads:  180 MB in  3.00 seconds =  59.99 MB/sec

/dev/hda1: IDE/NTFS
 Timing cached reads:   1838 MB in  2.00 seconds = 919.00 MB/sec
 Timing buffered disk reads:  142 MB in  3.03 seconds =  46.91 MB/sec

Apparently the performance of my drives is not bad at all, except from my raid's performance which is far from what I would've expected. =|

Moving a 2,630,778,880 byte file from my sda1 to sdb1 took 1:11 mins, experiencing small pauses and sudden boosts while copying... the speed didn't seem constant in the process. The "top" app registered an average 35%wa in my cpu's. The computer didn't slug down that bad, but I lost snappiness.

Now, if I start VirtualBox with setting (384mb RAM, 8mb VRAM, 8gb Virtual drive), my computer turns literally into a Slug while there's drive activity, having an average of 60%wa in the top app, peaking at 85%. Once the drive access is over, everything is snappy again.

I really don't know what's wrong with my Linux =(
Is anyone else still experiencing similar issues?

My setup is this:
4200+ AMD64 X2
Asus A8n5x Motherboard (Nforce4)
1Gb DDR 433 (PC 3500) (2x512mb)

I'm running Gutsy Final w/ Kernel 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

---

### Post by bandoba on 2007-10-23
I am experiencing similar symptoms on my Feisty Ubuntu AMD64 running on Acer Aspire machine with 500GB SATA disk. When copying files or using VMware virtual machines, my machine slows down and appears to continuously read/write hard drive. I was hoping this won't happen for Gutsy but from your post I am not sure if I should even give it a try.

---

### Post by Fungyo on 2007-11-01
try setting dma settings manually in bios. Mine was set to "Auto".
This increased my speeds from around 3-5mb/s up to 20-25mb/s.

Thanks to pinepain for his help
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730")

My whole system feels more responsive.

---

### Post by SixedUp on 2007-11-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/159521](https://bugs.launchpad.net/ubuntu/+bug/159521) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Are you guys seeing any errors in your \var\log\kern.log  ??  Your symptoms sound similar to mine, except that in addition to appalling performance, I'm getting lots of errors reported too.  I've got a bug open for what I'm seeing with more details if you want to compare notes. I'm now looking to see when these problems were introduced, and if its Ubuntu-specific or not - I see lots of reinstalls in my near future  :(

---

### Post by easytiger74 on 2007-12-18
Just to want to share my 2 cents here, hope it might be helpful to somebody.
I had the same slow performance problem for my new SATA drive as well. What I did is to enable the RAID in BIOS and the transfer speed is back to normal now. I believe it's more BIOS/System compatibility issue here.
BTW,
The motherboard chipset is nforce 6100

---

### Post by Roddles on 2007-12-18
i am using Gutsy 64 bit and i have terrible system performance when using vmware as well. 

hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   5462 MB in  2.00 seconds = 2736.07 MB/sec
 Timing buffered disk reads:  106 MB in  3.00 seconds =  35.28 MB/sec

sometimes it drops to 20MB/sec

The virtual machines are extremely slow - and the overall performance of the laptop is sluggish. Sometimes the machine stops responding for up to 15 seconds while the disk is being accessed.

I have a dell XPS m1710.

# lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
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
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7950 GTX (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

HDD is SATA 120GB and DVD is IDE.

---

### Post by bsmith1051 on 2007-12-19
> **easytiger74 said:**
> I had the same slow performance problem for my new SATA drive as well. What I did is to enable the RAID in BIOS and the transfer speed is back to normal now. I believe it's more BIOS/System compatibility issue here.
What were your 'hdparm -tT' results before/after?  Are you actually running a RAID setup?  I thought the BIOS would refuse to enable RAID unless you actually assigned two drives.

---

### Post by Roddles on 2007-12-20
Hi Guys

My DELL laptop doesnt have specific BIOS drive settings, but I did find a page which had 3 settings for Drive performance (Quiet, Bypass and Performance). The info about it indicates that it is to control drive noise, and that quiet will result in slower drive speeds but quieter operation, performance will result in a noisy drive but faster, and bypass just leaves the drive as it comes. I had it set to performance and the performance of Ubuntu was terrible. I also tried Gentoo, Windows XP and Ubuntu Dapper - all with the same results. I changed the performance page back to Bypass, and it resolved my problem. It seems to definately be a BIOS setting that is causing the issue. Problem is - some people (especially with laptops) cant really change much in BIOS. I was lucky in that this settings fixed my problem. Is fast again now. I am now running Xubuntu Gutsy and loving it. So much speed..... :)

---

### Post by dmarsh on 2007-12-21
Roddles- THANK YOU!  
  I've been struggling with trying to improve disk performance on my M1710 for months- it never occurred to me to bypass the acoustic settings in the BIOS- it makes a HUGE difference on this machine!  I also had some major improvements by building a custom kernel and omitting the IDE driver subsystem completely.  I'm currently on 2.6.23.11.

---

