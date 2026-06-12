---
title: "problems in sound ans visual effects in dell studio i5"
date: 2010-03-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by utsav.jain on 2010-03-07
my laptop configuration is
dell studio 1558 
processor i5 label
the problem is coming in sound and visual effects of ubuntu9.10
i am not able to hear sound and apply visual effects
pls help me


thanks in advance
description of my processor


00:00.0 Host bridge: Intel Corporation Arrandale DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Arrandale PCI Express x16 Root Port (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
02:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
02:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
04:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)
07:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
07:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
07:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
07:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
ff:00.0 Host bridge: Intel Corporation QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Device 2d12 (rev 02)
ff:02.3 Host bridge: Intel Corporation Device 2d13 (rev 02)

---

### Post by MelDJ on 2010-03-07
for visual effects, go o system-admin-hardware drivers. see if there are drivers available for your card. if not, get the driver from the ati site.
i have a dell 1555 and i found that the ati  from the ati site work while the one in hardware drivers doesnt 

for sound see: [http://ubuntuforums.org/showthread.php?t=1294252](http://ubuntuforums.org/showthread.php?t=1294252)

---

### Post by teh603 on 2010-03-08
He's got an Arrandale. From my limited experience, Arrandale chipsets aren't properly supported unless you want to try using the Lucid alpha.

---

### Post by utsav.jain on 2010-03-11
thanks i got my visual working 
but the sound is still not coming 
i have changed file 
alsa-base.config
and entered command 
sudo alsa force-reload
the output was


lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/utsav/.gvfs
      Output information may be incomplete.
Terminating processes: 5218lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/utsav/.gvfs
      Output information may be incomplete.
 5586lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/utsav/.gvfs
      Output information may be incomplete.
 5607lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/utsav/.gvfs
      Output information may be incomplete.
 5628lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/utsav/.gvfs
      Output information may be incomplete.
 (with SIGKILL:) 5649lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/utsav/.gvfs
      Output information may be incomplete.
 (failed: processes still using sound devices: 5670(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/utsav/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 5670(pulseaudio). 
Unloading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-pcm-oss snd-mixer-oss snd-hda-codec-atihdmi snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc (failed: modules still loaded: snd-hda-codec-atihdmi snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-pcm-oss snd-mixer-oss snd-hda-codec-atihdmi snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc.


i have also installed every package given in the thread it still not working 
PLS HELP ME
i am newbie to ubuntu so pls also tell any expected error i could have done in doing above procedure

---

### Post by utsav.jain on 2010-03-13
thank you again but automaticaly today when i opened vlc player the sound is coming

---

