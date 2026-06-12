---
title: "pulseaudio becomes suspended when switch desktop environment"
date: 2015-05-25
forum: Desktop Environments
---

### Post by odror on 2015-05-25
I have pulsesaudio running on ubuntu 15.04 desktop on vt7

I have a container running arch on vt8 using the PULSE_SERVER on vt7

as soon as I switch form vt7 to vt8 the puseaudio sinks becomes suspended. If I am switching to any of the terminals tty1-7
I have no problem. Even If the container uses that terminal. I get IDLE instead of SUSPENDED. There is something in the X11 environment that causes that conflict.

I suspect that there is a conflict. I cannot tell where it is coming form. Possibly from one of the the modules.
any help will be appreciated.

vt8: *pactl list sinks*:

```

Sink #1
        State: SUSPENDED <--------------------------------------------------------
        Name: alsa_output.pci-0000_00_1b.0.analog-stereo
        Description: Built-in Audio Analog Stereo
        Driver: module-alsa-card.c
        Sample Specification: s16le 2ch 44100Hz
        Channel Map: front-left,front-right
        Owner Module: 7
        Mute: no
        Volume: front-left: 58409 /  89% / -3.00 dB,   front-right: 58409 /  89% / -3.00 dB
                balance 0.00
        Base Volume: 65536 / 100% / 0.00 dB
        Monitor Source: alsa_output.pci-0000_00_1b.0.analog-stereo.monitor
        Latency: 0 usec, configured 0 usec
        Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
        Properties:
                alsa.resolution_bits = "16"
                device.api = "alsa"
                device.class = "sound"
                alsa.class = "generic"
                alsa.subclass = "generic-mix"
                alsa.name = "92HD89E2 Analog"
                alsa.id = "92HD89E2 Analog"
                alsa.subdevice = "0"
                alsa.subdevice_name = "subdevice #0"
                alsa.device = "0"
                alsa.card = "0"
                alsa.card_name = "HDA Intel PCH"
                alsa.long_card_name = "HDA Intel PCH at 0xf7110000 irq 30"
                alsa.driver_name = "snd_hda_intel"
                device.bus_path = "pci-0000:00:1b.0"
                sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
                device.bus = "pci"
                device.vendor.id = "8086"
                device.vendor.name = "Intel Corporation"
                device.product.id = "8c20"
                device.product.name = "8 Series/C220 Series Chipset High Definition Audio Controller"
                device.form_factor = "internal"
                device.string = "front:0"
                device.buffering.buffer_size = "65536"
                device.buffering.fragment_size = "32768"
                device.access_mode = "mmap+timer"
                device.profile.name = "analog-stereo"
                device.profile.description = "Analog Stereo"
                device.description = "Built-in Audio Analog Stereo"
                alsa.mixer_name = "IDT 92HD89E2"
                alsa.components = "HDA:111d76c7,103c2af3,00100102"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"
        Ports:
                analog-output: Analog Output (priority: 9900)
        Active Port: analog-output
        Formats:
                pcm
```

vt8: *pactl list modules | grep Name*

```
        Name: module-device-restore
	Name: module-stream-restore
	Name: module-card-restore
	Name: module-augment-properties
	Name: module-switch-on-port-available
	Name: module-udev-detect
	Name: module-alsa-card
	Name: module-alsa-card
	Name: module-bluetooth-policy
	Name: module-bluetooth-discover
	Name: module-bluez4-discover
	Name: module-esound-protocol-unix
	Name: module-native-protocol-unix
	Name: module-native-protocol-tcp
	Name: module-gconf
	Name: module-default-device-restore
	Name: module-rescue-streams
	Name: module-intended-roles
	Name: module-systemd-login
	Name: module-position-event-sounds
	Name: module-filter-heuristics
	Name: module-filter-apply


```

---

### Post by dino99 on 2015-05-26
seems a good candidate for a bug report  ;)

---

