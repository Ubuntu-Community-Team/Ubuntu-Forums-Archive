---
title: "SOUND problem /dev/dsp missing"
date: 2005-12-04
forum: Desktop Environments
---

### Post by muted on 2005-12-04
Alright i have most sound working (dont ask me why) but all programs that wants my /dev/dsp fails since it doesnt exist..

Beep for instace works because i use something like hw:0,0 instead of /dev/dsp (am i right? I am a complete newbie, but i think that is whats the case)

However, it does not help to write hw:0,0 in many programs, resulting in an errormessage!

How do i create a new /dev/dsp and should i even????

```
jacob@ubuntu:~$ lsmod
Module                  Size  Used by
ipv6                  217408  8
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
af_packet              20232  2
tsdev                   7616  0
at76c503_rfmd          42500  0
at76c503               79584  1 at76c503_rfmd
at76_usbdfu             5380  1 at76c503
ohci1394               30644  0
emu10k1_gp              3712  0
gameport               14472  2 emu10k1_gp
snd_emu10k1            96772  2
snd_rawmidi            22816  1 snd_emu10k1
snd_seq_device          8204  2 snd_emu10k1,snd_rawmidi
snd_util_mem            4480  1 snd_emu10k1
snd_hwdep               8608  1 snd_emu10k1
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
snd_intel8x0           30144  0
snd_ac97_codec         72188  2 snd_emu10k1,snd_intel8x0
snd_pcm                78344  4 snd_emu10k1,snd_intel8x0,snd_ac97_codec
snd_timer              21764  2 snd_emu10k1,snd_pcm
snd                    48644  11 snd_emu10k1,snd_rawmidi,snd_seq_device,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  3 snd_emu10k1,snd_intel8x0,snd_pcm
i2c_nforce2             6528  0
nls_iso8859_1           4224  1
nls_cp437               5888  1
vfat                   12288  1
fat                    46492  1 vfat
dm_mod                 50364  1
evdev                   9088  2
nvidiafb               50204  0
i2c_algo_bit            8584  1 nvidiafb
i2c_core               19728  4 i2c_acpi_ec,i2c_nforce2,nvidiafb,i2c_algo_bit
nvidia               3711364  12
agpgart                32328  1 nvidia
sr_mod                 15652  0
sbp2                   21128  0
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0
mousedev               10912  0
lp                     11460  0
parport                32072  1 lp
md                     40656  0
ext3                  115976  2
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
usbhid                 30688  0
skge                   33040  0
tulip                  45088  0
forcedeth              19072  0
ehci_hcd               29448  0
ohci_hcd               18564  0
usbcore               104188  7 at76c503_rfmd,at76c503,at76_usbdfu,usbhid,ehci_hcd,ohci_hcd
ide_cd                 36996  0
cdrom                  33952  2 sr_mod,ide_cd
ide_disk               16128  8
ide_generic             1664  0
sata_nv                 9092  0
libata                 47876  1 sata_nv
scsi_mod              124872  3 sr_mod,sbp2,libata
amd74xx                12828  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,amd74xx
unix                   24624  664
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  3 nvidiafb,vesafb,vga16fb
cfbimgblt               2944  3 nvidiafb,vesafb,vga16fb
cfbfillrect             3840  3 nvidiafb,vesafb,vga16fb
cfbcopyarea             4480  3 nvidiafb,vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

```

```
jacob@ubuntu:~$ lspci
0000:00:00.0 Memory controller: nVidia Corporation: Unknown device 005e (rev a3)0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 0050 (rev a3)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 0052 (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 005a (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 005b (rev a3)
0000:00:04.0 Multimedia audio controller: nVidia Corporation: Unknown device 0059 (rev a2)
0000:00:06.0 IDE interface: nVidia Corporation: Unknown device 0053 (rev a2)
0000:00:07.0 IDE interface: nVidia Corporation: Unknown device 0054 (rev a3)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 0055 (rev a3)
0000:00:09.0 PCI bridge: nVidia Corporation: Unknown device 005c (rev a2)
0000:00:0a.0 Bridge: nVidia Corporation: Unknown device 0057 (rev a3)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0c.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0d.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:06.0 Ethernet controller: Macronix, Inc. [MXIC] MX987x5 (rev 25)
0000:01:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 05)
0000:01:07.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 05)
0000:01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:01:0a.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Gigabit Ethernet 10/100/1000Base-T Adapter (rev 13)
0000:05:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0140 (rev a2)

```

Its the SB! Live platinum i wish to get working!

Thanks in advance

---

### Post by muted on 2005-12-05
*bump*

---

### Post by cwaldbieser on 2005-12-05
[QUOTE=muted]*bump*[/QUOTE]
/dev/dsp gets created when your sound drivers get loaded.  Your lsmod output shows that soundcore and other modules were loaded, so it really is a puzzle.

Is there anything in dmesg that might give a clue?

---

### Post by yaztromo on 2005-12-05
Just to say I have the same problem. I need /dev/dsp for UAE but it isn't there. Otherwise sound works fine.

I have an Audigy 2.

---

### Post by virbonus on 2005-12-06
I have the same problem except that I have no sound. The output of lsmod and lspci are shown below. There's nothing that I could see referring to any sound driver in dmesg. Any help would be much appreciated.

lsrlr@ubuntu:~$ lsmod
Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
pcmcia                 24584  2
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
af_packet              20232  2
wlan_wep                5888  1
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
ath_pci                69148  0
ath_rate_sample        14344  1 ath_pci
wlan                  120988  4 wlan_wep,ath_pci,ath_rate_sample
ath_hal               148432  3 ath_pci,ath_rate_sample
yenta_socket           22540  2
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_piix4               8336  0
i2c_core               19728  2 i2c_acpi_ec,i2c_piix4
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
sb_lib                 42288  0
uart401                11204  1 sb_lib
sound                  70444  2 sb_lib,uart401
soundcore               9184  2 sb_lib,sound
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
usbhid                 30688  0
uhci_hcd               28048  0
usbcore               104188  3 usbhid,uhci_hcd
ide_disk               16128  3
ide_generic             1664  0
piix                    9476  1
ide_core              125268  3 ide_disk,ide_generic,piix
unix                   24624  693
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon


rlr@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 430TX - 82439TX MTXC (rev 01)
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:08.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (rev 01)
0000:00:09.0 FireWire (IEEE 1394): Sony Corporation CXD1947Q i.LINK Controller (rev 01)
0000:00:0a.0 CardBus bridge: Ricoh Co Ltd RL5c475
0000:01:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
rlr@ubuntu:~$

---

