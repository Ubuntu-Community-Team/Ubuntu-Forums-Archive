---
title: "Lubuntu displaying colored stripes on the screen after a random time"
date: 2016-01-28
forum: Desktop Environments
---

### Post by Tiago_Arajo_da_C on 2016-01-28
Forgive my English, but after a while random PC use, the display changes to show colored stripes, damaging the work. This only occurs with Lubuntu.
The distro and hardware features are:

$ lspci

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
01:00.0 Modem: Motorola SM56 Data Fax Modem (rev 04)
02:00.0 Ethernet controller: Qualcomm Atheros Attansic L2 Fast Ethernet (rev a0)

$ cat /etc/issue

Ubuntu 15.10 \n \l

$ uname -a

Linux tiago-System-Product-Name 4.2.0-23-generic #28-Ubuntu SMP Sun Dec 27 17:47:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

$ lsmod

Module                  Size  Used by
pci_stub               16384  1
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               454656  3 vboxnetadp,vboxnetflt,vboxpci
binfmt_misc            20480  1
snd_usb_audio         176128  0
snd_usbmidi_lib        32768  1 snd_usb_audio
gspca_zc3xx            53248  0
gspca_main             36864  1 gspca_zc3xx
videodev              172032  2 gspca_main,gspca_zc3xx
media                  24576  1 videodev
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          36864  1
snd_hda_codec         135168  3 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           65536  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  2 snd_usb_audio,snd_hda_codec
snd_pcm               106496  4 snd_usb_audio,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0
gpio_ich               16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
input_leds             16384  0
snd                    81920  14 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
serio_raw              16384  0
soundcore              16384  1 snd
coretemp               16384  0
lpc_ich                24576  0
shpchp                 36864  0
8250_fintek            16384  0
asus_atk0110           20480  0
mac_hid                16384  0
parport_pc             32768  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
uas                    24576  0
usb_storage            69632  1 uas
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
i915                 1130496  3
video                  36864  1 i915
i2c_algo_bit           16384  1 i915
pata_acpi              16384  0
drm_kms_helper        126976  1 i915
floppy                 73728  0
atl2                   32768  0
drm                   356352  5 i915,drm_kms_helper

---

