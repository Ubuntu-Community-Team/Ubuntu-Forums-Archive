---
title: "Problems with sound - Dell Vostro 1720 IDT 92HD8XX"
date: 2011-01-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by slinzex on 2011-01-01
Worked ok last week, don't work last days...
I don't know what has happened, but now if I listen music on headphones , all grate. By the other hand, if I unplug headphones, and listen with built-in hw, no sound is heard. 

Here are the details:


**uname -r**
2.6.32-26-generic
**dpkg -l alsa-***
Deseado=u:desconocido/Instalar/eliminaR/Purgar/H:mantener
| Estado=No/Inst/arch-Cfg/U:desemp/Fallo-cfg/H:medio-inst/W:espera-act/pTe-act
|/ Err?=(nada)/Requiere-reinstalación (Estado,Err: mayúsculas=malo)
||/ Nombre              Versión            Descripción
+++-===================-===================-======================================================
ii  alsa-base           1.0.22.1+dfsg-0ubun ALSA driver configuration files
un  alsa-oss            <ninguna>           (no hay ninguna descripción disponible)
ii  alsa-utils          1.0.22-0ubuntu5     ALSA utilities



**lspci -nn | grep Audio**
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)

[B]cat /proc/asound/card0/codec#0 | grep Codec
[/B]Codec: IDT 92HD81B1C5


**cat /etc/modprobe.d/alsa-base.conf**
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }                   
#                                                                                                      
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }


# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2


**hwinfo --sound**
13: PCI 1b.0: 0403 Audio device                                 
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_293e
  Unique ID: u1Nb.j1M_fil1JBA
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel 82801I (ICH9 Family) HD Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x293e "82801I (ICH9 Family) HD Audio Controller"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x02c0 
  Revision: 0x03
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xf3300000-0xf3303fff (rw,non-prefetchable)
  IRQ: 22 (32453 events)
  Module Alias: "pci:v00008086d0000293Esv00001028sd000002C0bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

---

### Post by slinzex on 2011-01-01
Solved by random solution :D
I've only changed my system language from spanish to english! 
Now the sound works by headphones and without too.:lolflag:

---

