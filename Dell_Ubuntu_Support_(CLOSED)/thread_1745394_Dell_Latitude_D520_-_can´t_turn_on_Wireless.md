---
title: "Dell Latitude D520 - can´t turn on Wireless"
date: 2011-05-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mstjohn1974 on 2011-05-01
I just installed Ubuntu 11.04 on my laptop and I am not able to turn on  the wireless. I had Ubuntu 10.04 LTS running before and it worked out of  the box and now its not anymore. Any Ideas what I need to do to get it  working again?

Here are some information about my Laptop:

lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS,  943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
02:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)


lsmod
Module                               Size  Used by
parport_pc                         32111  0 
ppdev                                 12849  0 
snd_hda_codec_idt           60537  1 
binfmt_misc                       13213  1 
snd_hda_intel                    24140  2 
snd_hda_codec                90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep                        13274  1 snd_hda_codec
b44                                    35301  0 
snd_pcm                           80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi                    13132  0 
snd_rawmidi                     25269  1 snd_seq_midi
i915                                   450944  3 
snd_seq_midi_event        14475  1 snd_seq_midi
snd_seq                            51291  2 snd_seq_midi,snd_seq_midi_event
ssb                                    45942  1 b44
wl                                       2642531  0 
snd_timer                          28659  2 snd_pcm,snd_seq
joydev                               17322  0 
dell_wmi                            12601  0 
snd_seq_device               14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper               40745  1 i915
sparse_keymap                13666  1 dell_wmi
dell_laptop                         13515  0 
dcdbas                              14054  1 dell_laptop
drm                                    180037  4 i915,drm_kms_helper
pcmcia                               39671  0 
snd                                     55295  13  snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit                        13184  1 i915
psmouse                            73312  0 
soundcore                         12600  1 snd
yenta_socket                     27230  0 
pcmcia_rsrc                      18292  1 yenta_socket
pcmcia_core                     21505  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw                          12990  0 
lib80211                              14570  1 wl
snd_page_alloc                 14073  2 snd_hda_intel,snd_pcm
video                                  18951  1 i915
lp                                        13349  0 
parport                               36746  3 parport_pc,ppdev,lp
firewire_ohci                      31504  0 
firewire_core                      56138  1 firewire_ohci
crc_itu_t                             12627  1 firewire_core

I have the Broadcom STA Wireless Driver enables like I had it on my 10.04 LTS!
I can hit the Key Combination Fn + F2 but nothing happens.

Any thought? Ideas?

thanks I appreciate each reply.

---

### Post by mörgæs on 2011-05-01
Was it an upgrade or a fresh install?

---

### Post by mstjohn1974 on 2011-05-01
I did either way...first I did an upgrade from 10.04LTS to 11.04 and then I swapped the hard drive and did an fresh install. The results are the same in both cases.

---

### Post by Traktion on 2011-05-01
This may help: [http://ubuntuforums.org/showpost.php?p=10752323&postcount=12](http://ubuntuforums.org/showpost.php?p=10752323&postcount=12)

---

### Post by mstjohn1974 on 2011-05-01
I tried it but no luck still not working

---

### Post by mörgæs on 2011-05-01
There is a lot of advice here:
[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

---

### Post by mstjohn1974 on 2011-05-01
Very cool, 
the last post actually guided me to the answer. It was not exactly like it was described in method 1 but very close. What I needed to do was just installing the package 'firmware-b43-installer' and after a reboot it finally came up.

The installation of the package the the recommended post suggested actually failed and I just tried the other one.


Thank you very much, it's working now.

visit [http://blog.ubuntuvideocast.com](http://blog.ubuntuvideocast.com)

---

### Post by mörgæs on 2011-05-02
You are welcome. Please mark the thread 'solved'.

---

