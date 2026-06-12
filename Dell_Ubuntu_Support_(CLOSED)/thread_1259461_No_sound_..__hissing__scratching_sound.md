---
title: "No sound ..  hissing / scratching sound"
date: 2009-09-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dognose2 on 2009-09-06
I have a Dell Dimension E520 ..  The sound has always been a bit hit or miss, but usually fixed with a reboot.   Lately, it's completely gone and replaced with a scratchy sort of intermittent noise.  

I've tried going into sound settings and selected different devices.. ALSA or Pulseaudio or HDA Intel STAC92xx but all with the same results.. 

Is the sound circuit fried or is there a software diagnosis?

update: Ubuntu 9.04

---

### Post by Sam Lars on 2009-09-07
If you go into the volume mixer, check the PCM to make sure it's not all the way down. I think it's
```
gnome-volume-control
```

---

### Post by dognose2 on 2009-09-08
I've checked all the sound levels, and have also tried earphones instead of the speakers.  still no luck. 

Is there a way to check the integrity of the hardware?

---

### Post by dognose2 on 2009-09-08
hwinfo 

  34: udi = '/org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0_oss_pcm_0'
  info.capabilities = { 'oss', 'access_control' }
  oss.device_id = 'STAC92xx Analog'
  oss.device = 0 (0x0)
  oss.type = 'pcm'
  access_control.file = '/dev/audio'
  linux.device_file = '/dev/audio'
  info.callouts.add = { 'hal-acl-tool --add-device' }
  linux.hotplug_type = 2 (0x2)
  access_control.type = 'sound'
  info.callouts.remove = { 'hal-acl-tool --remove-device' }
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/audio'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0'
  info.product = 'STAC92xx Analog OSS PCM Device'
  info.subsystem = 'sound'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0_oss_pcm_0'
  info.category = 'oss'
  oss.device_file = '/dev/audio'
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0'
  oss.card = 0 (0x0)
  oss.card_id = 'HDA Intel'
  linux.subsystem = 'sound'

---

### Post by Sam Lars on 2009-09-14
I suppose you could try a different OS, maybe a different version of Ubuntu or a different version of Linux altogether.
Could you maybe post a screenshot of your mixer settings?

---

