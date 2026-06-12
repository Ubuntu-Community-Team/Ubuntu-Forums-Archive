---
title: "NO Audio from HDMI ports"
date: 2024-08-17
forum: Desktop Environments
---

### Post by luiz-carlin on 2024-08-17
Guys, I have a NUC PC that had Ubuntu 23.10, installed from scratch, and everything worked, including the Audio via the HDMI Port.
After updating it to Ubuntu 24.04, The HDMI Audio stopped working. I've seen reports from other users with the same problem.
I've already tried to edit the file "/etc/default/grub" and insert the line "intel_iommu=on,igfx_off" in it, but it still doesn't work.



Additional information follows:
lcarlin@LDA0269:~$ lspci | grep udio
00:1f.3 Audio device: Intel Corporation Alder Lake-N PCH High Definition Audio Controller
lcarlin@LDA0269:~$ 


carlin@LDA0269:~$ aplay -l
**** Lista de Dispositivos PLAYBACK Hardware ****
placa 0: PCH [HDA Intel PCH], dispositivo 3: HDMI 0 [AOC LCD]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0
placa 0: PCH [HDA Intel PCH], dispositivo 7: HDMI 1 [HDMI 1]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0
placa 0: PCH [HDA Intel PCH], dispositivo 8: HDMI 2 [HDMI 2]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0
placa 0: PCH [HDA Intel PCH], dispositivo 9: HDMI 3 [HDMI 3]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0
placa 1: HID [USB Audio and HID], dispositivo 0: USB Audio [USB Audio]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0
lcarlin@LDA0269:~$ 




lcarlin@LDA0269:~$ cat /proc/asound/cards 
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0x6001110000 irq 134
 1 [HID            ]: USB-Audio - USB Audio and HID
                      CSCTEK USB Audio and HID at usb-0000:00:14.0-6, full speed
lcarlin@LDA0269:~$ 


lcarlin@LDA0269:~$ sudo alsa force-reload
Unloading ALSA sound driver modules: snd-seq-midi snd-seq-midi-event snd-sof-pci-intel-tgl snd-sof-intel-hda-common snd-sof-intel-hda snd-sof-pci snd-sof-xtensa-dsp snd-sof snd-sof-utils snd-soc-hdac-hda snd-soc-acpi-intel-match snd-soc-acpi snd-seq-dummy snd-hrtimer snd-sof-intel-hda-mlink snd-hda-ext-core snd-soc-core snd-compress snd-hda-codec-hdmi snd-pcm-dmaengine snd-usb-audio snd-hda-intel snd-intel-dspcfg snd-intel-sdw-acpi snd-hda-codec snd-usbmidi-lib snd-hda-core snd-hwdep snd-ump snd-pcm snd-rawmidi snd-seq snd-seq-device snd-timer (failed: modules still loaded: snd-hrtimer snd-sof-intel-hda-mlink snd-hda-ext-core snd-soc-core snd-compress snd-hda-codec-hdmi snd-pcm-dmaengine snd-usb-audio snd-hda-intel snd-intel-dspcfg snd-intel-sdw-acpi snd-hda-codec snd-usbmidi-lib snd-hda-core snd-hwdep snd-ump snd-pcm snd-rawmidi snd-seq snd-seq-device snd-timer).
Loading ALSA sound driver modules: snd-seq-midi snd-seq-midi-event snd-sof-pci-intel-tgl snd-sof-intel-hda-common snd-sof-intel-hda snd-sof-pci snd-sof-xtensa-dsp snd-sof snd-sof-utils snd-soc-hdac-hda snd-soc-acpi-intel-match snd-soc-acpi snd-seq-dummy snd-hrtimer snd-sof-intel-hda-mlink snd-hda-ext-core snd-soc-core snd-compress snd-hda-codec-hdmi snd-pcm-dmaengine snd-usb-audio snd-hda-intel snd-intel-dspcfg snd-intel-sdw-acpi snd-hda-codec snd-usbmidi-lib snd-hda-core snd-hwdep snd-ump snd-pcm snd-rawmidi snd-seq snd-seq-device snd-timer.
lcarlin@LDA0269:~$ 


lcarlin@LDA0269:~$ sudo systemctl --now --user restart pipewire pipewire-pulse
Failed to connect to bus: Mídia não encontrada
lcarlin@LDA0269:~$ 


lcarlin@LDA0269:/var/log$  lspci -nnk | grep -n -A 4 -i Audio
43:00:1f.3 Audio device [0403]: Intel Corporation Alder Lake-N PCH High Definition Audio Controller [8086:54c8]
44-	DeviceName: Onboard - Sound
45-	Subsystem: Intel Corporation Device [8086:7270]
46-	Kernel driver in use: snd_hda_intel
47-	Kernel modules: snd_hda_intel, snd_sof_pci_intel_tgl
lcarlin@LDA0269:/var/log$ 


lcarlin@LDA0269:~$  lsb_release -a 
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 24.04 LTS
Release:	24.04
Codename:	noble
lcarlin@LDA0269:~$ 


If you need any more information about my system, please write to me. 
I've been having this problem since I updated and I don't know how to solve it! you are my only hope!

---

### Post by hifron on 2024-12-01
```
journalctl -b -r | egrep -i "(alsa|sound|snd)"&&echo ""&&pw-metadata&&echo ""&&cat /proc/asound/devices&&echo ""&&cat /proc/asound/hwdep&&echo ""&&cat /proc/asound/pcm'

aplay -l
aplay -L

pactl list modules short

wpctl status
pw-cli ls

alsactl info
alsactl init
alsactl store

```

maybe some intel driver missing or pipewire audio, for older pulse audio see [https://ubuntuforums.org/showthread.php?t=2477166](https://ubuntuforums.org/showthread.php?t=2477166)

for pipewire [https://docs.pipewire.org/page_pulse_modules.html](https://docs.pipewire.org/page_pulse_modules.html)
[https://ubuntuforums.org/showthread.php?t=2479484](https://ubuntuforums.org/showthread.php?t=2479484)

[https://wiki.debian.org/PipeWire](https://wiki.debian.org/PipeWire)
[https://wiki.debian.org/PulseAudio](https://wiki.debian.org/PulseAudio)

[https://gitlab.com/sebholt/qastools](https://gitlab.com/sebholt/qastools) GUI?
helvum deb or alsa based GUI or ancient OSS gtk to view or edit controls, but special editions of professional software audiostations are available but should be not needed for some essential configs, but also there could be codecs or driver issue...

```

inxi -Az
inxi -F
journalctl -b -r |grep flags
journalctl -b -r |grep pci
lspci

```

[https://docs.kernel.org/sound/hd-audio/notes.html](https://docs.kernel.org/sound/hd-audio/notes.html)
[https://docs.kernel.org/sound/index.html](https://docs.kernel.org/sound/index.html)
[https://github.com/pciutils/pciutils/issues](https://github.com/pciutils/pciutils/issues)

but seems that also some x2 acpi bios bugs could also take place in some settings, but also could be pipewire stereo/surround profile as this is some new area on Linux not so tested

---

