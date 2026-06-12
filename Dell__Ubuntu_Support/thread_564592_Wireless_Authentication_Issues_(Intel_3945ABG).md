---
title: "Wireless Authentication Issues (Intel 3945ABG)"
date: 2007-10-01
forum: Dell  Ubuntu Support
---

### Post by ctpaterson on 2007-10-01
I hope this isn't a tired retread, but after receiving my Dell Inspiron 1520 last week, taking the pre-installed Vista out back to tell it about the rabbits, and getting Feisty setup, I'm mostly good except for wireless.

I have an Intel PRO/Wireless 3945 card.  I can't authenticate on the WEP that I have at home or at work.  I connect fine to open wireless networks.  I have not had the opportunity to try a WPA secured network.  I'm looking for any help/advice that I can get.  I have been googling, and trolling the threads, here is what I've tried/can confirm:

That the card is present (at the bottom)...
paterson@bilbo:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation Mobile SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0407 (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
[B]0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
[/B]

That the ipw3945 driver is present and loaded...
paterson@bilbo:~$ lsmod
Module                  Size  Used by
arc4                    2944  2 
ecb                     4480  2 
blkcipher               6784  1 ecb
ieee80211_crypt_wep     6144  1 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
ppdev                  10116  0 
acpi_cpufreq           10056  1 
cpufreq_conservative     8200  0 
cpufreq_userspace       5408  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  1 
cpufreq_stats           7360  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
battery                10756  0 
asus_acpi              17308  0 
video                  16388  14 
dock                   10268  0 
button                  8720  0 
container               5248  0 
backlight               7040  1 asus_acpi
sbs                    15652  0 
i2c_ec                  6016  1 sbs
ac                      6020  0 
ipv6                  268960  14 
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
piix                   10756  0 [permanent]
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
snd_hda_intel          21912  4 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
joydev                 10816  0 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               42500  0 
snd_timer              23684  3 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
af_packet              23816  2 
usbhid                 26592  0 
**ipw3945               118816  1 **
videodev               28160  1 uvcvideo
v4l1_compat            15236  2 uvcvideo,videodev
v4l2_common            25216  2 uvcvideo,videodev
hid                    27392  1 usbhid
hci_usb                18204  2 
nvidia               6224240  26 
ieee80211              34760  1 ipw3945
ieee80211_crypt         7040  2 ieee80211_crypt_wep,ieee80211
bluetooth              55908  7 rfcomm,l2cap,hci_usb
i2c_core               22656  2 i2c_ec,nvidia
sdhci                  18700  0 
mmc_core               26756  1 sdhci
snd                    54020  16 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
serio_raw               7940  0 
intel_agp              26140  1 
agpgart                35400  2 nvidia,intel_agp
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
pcspkr                  4224  0 
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
psmouse                38920  0 
tsdev                   8768  0 
evdev                  11008  5 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  3 
ata_piix               15492  2 
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  4 sbp2,sg,sd_mod,libata
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
b44                    28044  0 
mii                     6528  1 b44
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  6 uvcvideo,usbhid,hci_usb,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

I have a wireless interface...
paterson@bilbo:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Wireless1"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:16:C8:66:79:E0   
          Bit Rate:2 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/100  Signal level=-89 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:159  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3728   Missed beacon:0

It can see the wireless network, obviously, but not authenticate.

I have tried entering my key in via the NetworkManager.  I have tried entering it on the command-line, using the iwconfig command.  I have tried entering it via the /etc/networking/interfaces file.  I have entered it here and there.  I have entered it everywhere.

I also burned a beta CD of Gutsy on the weekend, and tried running wireless of the live CD (as it had version 1.2.2 of ipw3945, and feisty has 1.2.0) - still no joy.

This is either a real stumper, or I'm doing one small thing consistently wrong (more likely the latter).  I know what you're thinking; the key...well keys (since I've tried this on two networks).  I've checked, and re-typed, and turned the masking off so I can see what I'm typing - I'm pretty sure I'm doing it right.

I've got workarounds at home and work - but I'd really like to get this working.  Can anyone help?

Thanks.

---

### Post by ctpaterson on 2007-10-01
Well, after many hours of diagnosis, digging, and alternate drivers, it turned out that I was entering my key in NetworkManager as "WEP 128 bit Passphrase" when it should have been "WEP 64/128 bit Hex"

Deep down, I figured it was something like that.  Glad to see it resolved.

---

### Post by louca on 2007-10-02
Same thing happened to me...

---

