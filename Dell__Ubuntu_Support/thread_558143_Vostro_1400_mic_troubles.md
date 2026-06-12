---
title: "Vostro 1400 mic troubles"
date: 2007-09-23
forum: Dell  Ubuntu Support
---

### Post by stubish on 2007-09-23
Ok, I've checked the other threads I could find for this unit and the 1420n and no luck yet. Bear in mind I've been using ubuntu (and linux) for 3 weeks now... so I'm a beginner.

My microphone is not working, it's the internal mics next to the webcam (the webcam is also not working, but I have no need just yet for that).

How to proceed? I've tried both the gmix and alsamixer (terminal) no luck...

Thanks in advance for the help.

Stuart

---

### Post by linuxwizard on 2007-09-23
[https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)

[http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone](http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone)

---

### Post by stubish on 2007-09-23
Hi,
   Thanks for the quick reply and the great threads. I've been right through both of these, nothing muted all stuff up, funnily enough no boosts in switches, and of course no levels in vumeter. Here's the error I recieve when I try and run the test from the sound preferences for the alsa mixer:

gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.

I'm not sure if that means anything.

Neither the OSS mixer or the ALSA mixer produce any results.

Next steps?

---

### Post by linuxwizard on 2007-09-23
What sound card are you using ? And is that mic for the webcam are is it separate ?

---

### Post by stubish on 2007-09-24
best I can tell, I'm running an intel 82801H HD audio device. here's the lsmod

********************************************
Module                  Size  Used by
usbhid                 26592  0 
hid                    27392  1 usbhid
ipv6                  268960  10 
binfmt_misc            12680  1 
ppdev                  10116  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
container               5248  0 
sbs                    15652  0 
dock                   10268  0 
battery                10756  0 
i2c_ec                  6016  1 sbs
asus_acpi              17308  0 
button                  8720  0 
acpi_cpufreq           10056  2 
ac                      6020  0 
backlight               7040  1 asus_acpi
cpufreq_powersave       2688  0 
video                  16388  0 
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  1 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
ndiswrapper           194608  0 
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
piix                   10756  0 [permanent]
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  3 
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
joydev                 10816  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
uvcvideo               42500  0 
nvidia               7249940  30 
videodev               28160  1 uvcvideo
v4l1_compat            15236  2 uvcvideo,videodev
v4l2_common            25216  2 uvcvideo,videodev
i2c_core               22656  2 i2c_ec,nvidia
serio_raw               7940  0 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sdhci                  18700  0 
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
intel_agp              26140  1 
agpgart                35400  2 nvidia,intel_agp
mmc_core               26756  1 sdhci
pcspkr                  4224  0 
af_packet              23816  12 
psmouse                38920  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tsdev                   8768  0 
evdev                  11008  5 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  4 
generic                 5124  0 [permanent]
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
ehci_hcd               34188  0 
ata_generic             9092  0 
ahci                   22020  3 
libata                125720  2 ata_generic,ahci
scsi_mod              142348  4 sbp2,sg,sd_mod,libata
tg3                   109700  0 
uhci_hcd               25360  0 
usbcore               134280  6 usbhid,ndiswrapper,uvcvideo,ehci_hcd,uhci_hcd
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
*******************************

and my ls pci

******************************
00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation Mobile SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0427 (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation Unknown device 1713 (rev 02)
0c:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
**************************************

The webcam is seperate, there is tutorials up for that. I've just not actived it yet.

---

### Post by stubish on 2007-09-24
ok, according to Windows my sound device is a sigmatel HD audio device. this may help.

more info from linux device manager reveals a stac92xx device?

---

### Post by linuxwizard on 2007-09-24
Are you using Feisty ? And have you installed all the latest updates including kernel update ? I have seen issues with snd_hda_intel and their is a bug reported on the kernel at Launchpad on it with sound &/or mic issues. Some have update to the latest version of ALSA and still had issues but their is a work around for it in that bug report.Below thread is one that I know of with no sound. Do a search in the forum for more info/issues on your sound card..
[http://ubuntuforums.org/showthread.php?t=541929&page=2](http://ubuntuforums.org/showthread.php?t=541929&page=2)


[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by irwjager on 2007-09-26
Hi all,

Got the same problem; internal mic not working on Vostro 1400
Spent a good few days trying different things but to no avail.
My 'lsusb' looks like this;

Bus 007 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 013: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 012: ID 0a5c:4502 Broadcom Corp. 
Bus 003 Device 011: ID 413c:8126 Dell Computer Corp. 
Bus 003 Device 010: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

I don't seem to have any USB audio device (the camera does show up). Does that mean the mic is not a regular USB audio device? I'm pretty convinced i'm not supposed to record from the soundcard (card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]) but from a different source... Please correct me if i'm wrong !

This is where the camera initializes (taken from 'dmesg');

[   19.016000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   19.164000] Linux video capture interface: v2.00
[   19.348000] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   19.348000] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   19.352000] usbcore: registered new interface driver uvcvideo
[   19.352000] USB Video Class driver (v0.1.0)
[   19.568000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 21
[   19.568000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   20.416000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)

I've seen other outputs of webcams that show an audio USB device being initialized right after the camera.

I've compiled the latest ALSA drivers into my kernel (2.6.22-12-generic) and i'm running the latest Gutsy developer code (been updating every hour).

Would any of the guru's have any pointers? I'm rather new to Linux, but willing to learn :)

Thanks,

Ivo

---

### Post by adithyu85 on 2007-10-23
Hi all,

I have exacly the same problem. Internal mic doesn't work. Haven't checked plugging a mic into the mic jack, though.

Has anybody got it working?

---

### Post by daageep on 2007-10-23
i'm interested also :)

i finally got suspend working though, so i'm happy.

---

### Post by Mishok on 2007-10-24
This probably ties into all the other troubles people have been having with sigmatel card. I have a 1400, and I am facing a similar problem. On top of that, the laptop speakers don't work, yet if i plug in my headphones into the jack everything is fine.

---

### Post by supaman2slick on 2007-10-27
> **daageep said:**
> i'm interested also :)

i finally got suspend working though, so i'm happy.

Can you enlighten us on how to get suspend to work? I keep messing up my install playing with suspend. It goes down okay, but comes up with compiz not showing any of my panels. 



As for the sound issue. I have the vostro 1400 with the sigmatel hd sound and all you have to do is this:

add the following line to /etc/modprobe.d/alsa-base

options snd-hda-intel model=5stack

---

### Post by ukripper on 2008-04-01
> **Mishok said:**
> This probably ties into all the other troubles people have been having with sigmatel card. I have a 1400, and I am facing a similar problem. On top of that, the laptop speakers don't work, yet if i plug in my headphones into the jack everything is fine.
Do this to make your sound work from speakers 
```
sudo apt-get install linux-backports-modules-generic
```

Then add to sudo gedit /etc/modprobe.d/alsa-base :
```

options snd-hda-intel probe_mask=1 model=3stack
```

save and reboot.

---

