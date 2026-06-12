---
title: "[SOLVED][14.04] pulseaudio failed to load module &quot;module-alsa-card&quot;"
date: 2015-07-01
forum: Desktop Environments
---

### Post by ryan167 on 2015-07-01
Hey fellow users,
I'm not new to Linux, but new to Linux as a desktop OS (especially Ubuntu). Apoligies if the formatting of this post is a little strange or if I posted this somewhere I wasn't supposed to, I'm also new to these forums.

I'm running Ubuntu 14.04 LTS, pretty generic setup with a separate drive for this OS and a separate drive for Windows 8.1.

I have a FIIO E9K with E17 plugged in, alsa seems to play nice and finds the device just fine:
```
ryan@medivh:~$ **aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[B]card 3: DACE17 [FiiO USB DAC-E17], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: DACE17 [FiiO USB DAC-E17], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/B]
```


I can also run this command I found somewhere, and hear a soundfile through the interface and it seems to work fine:
```
ryan@medivh:~$** aplay -Dplughw:3,1 -fcd /usr/share/sounds/alsa/Front_Center.wav**
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
```


However, I cannot select this device in the Sound GUI at all (or pavucontrol). I did some more digging with pulseaudio, but couldn't find anything that seemed to work, however I did note that this occurred when I started pulseaudio from the terminal:
```
ryan@medivh:~$ **pulseaudio**
E: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
E: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="3" name="usb-FiiO_FiiO_USB_DAC-E17-01-DACE17" card_name="alsa_card.usb-FiiO_FiiO_USB_DAC-E17-01-DACE17" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1""): initialization failed.

[I]. . .
W: [pulseaudio] module-udev-detect.c: Tried to configure /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.1/sound/card3 (alsa_card.usb-FiiO_FiiO_USB_DAC-E17-01-DACE17) more often than 5 times in 10s
. . .[/I]

```


So from what I can tell, alsa plays along with my USB device just fine (can see it in alsamixer, etc), but for some reason pulseaudio can't initialize the device.
Does anyone have any idea where I could go from here? I have an option of plugging this device into an audio jack or of course using standard headphones, but I hate the excess whining sound and would love to have it working natively with USB.

Thanks

---

### Post by ryan167 on 2015-07-01
Selfish bump to add that I reinstalled Ubuntu and discovered a probable cause:

 The USB audio device appeared to be working correctly until after I installed proprietary NVIDIA drivers for my video card. Then I'm back to square one.

I have an HDMI device hooked into my graphics card (a small TV).

Any guesses on where to look next?

---

### Post by ryan167 on 2015-07-01
Not sure why, but after running this command, my sound device shows up fine in pulseaudio. This is as solved as it'll get for now for me, until I have the time to dig deeper into the issue:
```

ryan@medivh ~ $ **speaker-test -c 2 -r 48000 -D hw:3,1**
```

---

