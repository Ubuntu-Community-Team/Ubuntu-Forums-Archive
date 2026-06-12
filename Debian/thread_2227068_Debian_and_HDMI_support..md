---
title: "Debian and HDMI support."
date: 2014-05-30
forum: Debian
---

### Post by codingman on 2014-05-30
I currently have a laptop with an Intel HDMI port, and have connected it to an AVR that has 7.1 channel capabilities (though currently set to 5.1). Earlier this week, it would work properly even with:

```
# pasuspender -- speaker-test -D hdmi -c 8 FL,FC,FR,RR,RRC,RLC,RL,LFE
```

Producing pink noise throughout the room. Now, however it does not work. I've tried changing the output in the Gnome System Settings, but that did not help. I tried:

```
# alsactl init
```

Which gives:

```
Found hardware: "HDA-Intel" "Intel IbexPeak HDMI" "HDA:10ec0269,11790622,00100100 HDA:80862804,11790001,00100000" "0x1179" "0x0001"
Hardware is initialized using a generic method

```

I have also tried unmuting everything in alsamixer, as well as messing around in pavucontrol, but to still no avail.

```
# cat /proc/asound/modules
```

Gives me:

```
 0 snd_hda_intel
```

```
# pactl stat
```

Gives me:

```

Currently in use: 4 blocks containing 277.7 KiB bytes total.
Allocated during whole lifetime: 273887 blocks containing 1.5 GiB bytes total.
Sample cache size: 149.8 KiB
Server String: unix:/tmp/pulse-8NSJeYBrQrLA/native
Library Protocol Version: 26
Server Protocol Version: 26
Is Local: yes
Client Index: 728
Tile Size: 65472
User Name: codingman
Host Name: *****
Server Name: pulseaudio
Server Version: 2.0
Default Sample Specification: s16le 2ch 44100Hz
Default Channel Map: front-left,front-right
Default Sink: alsa_output.pci-0000_00_1b.0.hdmi-surround-extra1
Default Source: alsa_input.pci-0000_00_1b.0.analog-stereo
Cookie: c4b0:c4ff

```

Notice the line of the "Default Sink".

```
# lsmod | grep snd
```

Returns:

```

snd_hda_codec_hdmi     30824  1 
snd_hda_codec_realtek   188851  1 
snd_hda_intel          26259  2 
snd_hda_codec          78031  3 snd_hda_intel,snd_hda_codec_realtek,snd_hda_codec_hdmi
snd_hwdep              13186  1 snd_hda_codec
snd_pcm                68083  3 snd_hda_codec,snd_hda_intel,snd_hda_codec_hdmi
snd_page_alloc         13003  2 snd_pcm,snd_hda_intel
snd_seq                45126  0 
snd_seq_device         13176  1 snd_seq
snd_timer              22917  2 snd_seq,snd_pcm
snd                    52889  13 snd_timer,snd_seq_device,snd_seq,snd_pcm,snd_hwdep,snd_hda_codec,snd_hda_intel,snd_hda_codec_realtek,snd_hda_codec_hdmi
soundcore              13065  1 snd

```

```
# pactl list sinks
```

Gives:

```

Sink #6
    State: SUSPENDED
    Name: alsa_output.pci-0000_00_1b.0.hdmi-surround-extra1
    Description: Built-in Audio Digital Surround 5.1 (HDMI)
    Driver: module-alsa-card.c
    Sample Specification: s16le 6ch 44100Hz
    Channel Map: front-left,front-right,rear-left,rear-right,front-center,lfe
    Owner Module: 4
    Mute: no
    Volume: 0: 100% 1: 100% 2: 100% 3: 100% 4: 100% 5: 100%
            0: -0.08 dB 1: -0.08 dB 2: -0.08 dB 3: -0.08 dB 4: -0.08 dB 5: -0.08 dB
            balance 0.00
    Base Volume: 100%
                 0.00 dB
    Monitor Source: alsa_output.pci-0000_00_1b.0.hdmi-surround-extra1.monitor
    Latency: 0 usec, configured 0 usec
    Flags: HARDWARE DECIBEL_VOLUME LATENCY SET_FORMATS 
    Properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "HDMI 1"
        alsa.id = "HDMI 1"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "7"
        alsa.card = "0"
        alsa.card_name = "HDA Intel"
        alsa.long_card_name = "HDA Intel at 0xd4620000 irq 43"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.name = "5 Series/3400 Series Chipset High Definition Audio"
        device.form_factor = "internal"
        device.string = "hdmi:0,1"
        device.buffering.buffer_size = "65520"
        device.buffering.fragment_size = "32760"
        device.access_mode = "mmap+timer"
        device.profile.name = "hdmi-surround-extra1"
        device.profile.description = "Digital Surround 5.1 (HDMI)"
        device.description = "Built-in Audio Digital Surround 5.1 (HDMI)"
        alsa.mixer_name = "Intel IbexPeak HDMI"
        alsa.components = "HDA:10ec0269,11790622,00100100 HDA:80862804,11790001,00100000"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Ports:
        hdmi-output-1: HDMI / DisplayPort 2 (priority: 5800)
    Active Port: hdmi-output-1
    Formats:
        dts-iec61937, format.rate = "[ 32000, 44100, 48000, 88200, 96000, 176400, 192000 ]"
        pcm

```

Any suggestions are welcome!

---

