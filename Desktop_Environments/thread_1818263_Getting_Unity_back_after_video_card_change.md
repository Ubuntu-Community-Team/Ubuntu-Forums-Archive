---
title: "Getting Unity back after video card change"
date: 2011-08-04
forum: Desktop Environments
---

### Post by jeff8houses on 2011-08-04
I have an Asus/Intel setup with integrated graphics that has been running Unity no problem for a while. I temporarily installed a separate NVidia card to do some hardware compatibility testing for another system that apparently couldn't hack it for Unity and forced it back to Classic. With the Nvidia card removed and going back to the integrated video setup I can't seem to get Unity running again. At the login I've toggled back and forth between Ubuntu (Unity) and Classic to no avail. Is there some way to reactivate it? Thanks so much!

Jeff

---

### Post by gordintoronto on 2011-08-04
Did you install an Nvidia driver? Before removing a video card, it's best to remove its driver.

---

### Post by jeff8houses on 2011-08-04
Looking under "additional drivers" I don't see anything. If I put the Nvidia card back in will it show up so I may uninstall it? I'm asking before doing as it's a major pain to pull the computer out from where it sits. Thanks!

---

### Post by gordintoronto on 2011-08-04
I don't know! Sorry.

---

### Post by wildmanne39 on 2011-08-04
Hi, run these two commands please:
```
lsmod
```
```
sudo lspci -k
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by jeff8houses on 2011-08-05
```
jeff@Alice:~$ lsmod
Module                  Size  Used by
snd_usb_audio         112426  0 
snd_usbmidi_lib        25139  1 snd_usb_audio
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   21708  1 
fat                    61374  1 vfat
cryptd                 20510  0 
aes_x86_64             17208  2 
aes_generic            38279  1 aes_x86_64
binfmt_misc            17565  1 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_realtek   336771  1 
snd_hda_intel          33211  1 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  2 snd_usb_audio,snd_hda_codec
snd_pcm                96391  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
i915                  514975  2 
snd_seq_midi           13324  0 
snd_rawmidi            30486  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
arc4                   12529  2 
drm_kms_helper         42136  1 i915
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
ath5k                 155466  0 
drm                   227495  3 i915,drm_kms_helper
ath                    23773  1 ath5k
mac80211              294370  1 ath5k
snd                    67382  14 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                  17113  0 
parport_pc             36959  1 
soundcore              12680  1 snd
cfg80211              178528  3 ath5k,ath,mac80211
i2c_algo_bit           13400  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19438  1 i915
psmouse                73535  0 
serio_raw              13166  0 
lp                     17825  0 
asus_atk0110           17976  0 
parport                46458  3 ppdev,parport_pc,lp
usb_storage            53538  1 
uas                    17996  0 
r8169                  48022  0 
jeff@Alice:~$ sudo lspci -k
[sudo] password for jeff: 
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 836d
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 836d
    Kernel driver in use: i915
    Kernel modules: i915
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 836d
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device 840b
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
    Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard
    Kernel driver in use: ata_piix
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard
    Kernel driver in use: ata_piix
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard
    Kernel driver in use: r8169
    Kernel modules: r8169
03:01.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
    Subsystem: D-Link System Inc Device 3a1b
    Kernel driver in use: ath5k
    Kernel modules: ath5k
jeff@Alice:~$ 

```

---

### Post by wildmanne39 on 2011-08-05
Hi, post the results of this command please:
```
lsmod | grep i915
```
Thank you

---

### Post by jeff8houses on 2011-08-05
```
jeff@Alice:~$ lsmod | grep i915
i915                  514975  2 
drm_kms_helper         42136  1 i915
drm                   227495  3 i915,drm_kms_helper
i2c_algo_bit           13400  1 i915
video                  19438  1 i915

```

---

### Post by wildmanne39 on 2011-08-05
Hi, I need to see the output of this command now.
```
modinfo i915
```
Thank you

---

### Post by x-D on 2011-08-05
Do you know what Video Card you are going to be putting in? Try to make it a big name Video Card, such as NVIDIA etc... so that the Drivers are more likely to be supported for 3D mode, as to allow Unity to be run, uninstall the current drivers before removal, as they will conflict with the new Video Card!

Hope this helped... :)

:guitar:

---

### Post by ds_shellback on 2011-08-06
Hi if you're choosing ano graphics card, the following link helps - at the moment I'm also running Intel i915 integrated graphics which just creeps above unity minimum requirements and works fine. (I have an older machine with integrated 865G graphics that will only run 2D.:()

[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements]("https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements")

If you want to reconfigure graphics there is an option for this if you run in safe graphics mode.

To access this, select run in safe graphics mode from the grub menu (hold shift key during boot if your machine only has one OS and doesn't display the grub menu by default) from this you can access reconfigure graphics in the subsequent menu - I've always found this to work fine.

If you installed the proprietary Nvidia driver when you were using the plug in card you will need to un-install that.:P

---

